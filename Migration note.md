# EF core 6 migration


## 確認套件

- EFCore

![](https://i.imgur.com/arjobfH.png)


  警告 若將 EntityFramework 也下載，將會呼叫到共用參數，導致無法順利執行
  
  記得移除非必要套件!
  
  ![](https://i.imgur.com/akvwwJ7.png)


</br>
</br>
</br>
</br>


1. 在 Program 註冊資料庫連線字串

```csharp=
//Register
builder.Services.AddDbContext<CadtechDBContext>(options=>
options.UseSqlServer(builder.Configuration.GetConnectionString("SQLSRV")));
```

2. 新增資料庫 migration


![](https://i.imgur.com/JKdoF2Z.png)

3. 先重建專案，確認專案無任何錯誤

4. 啟用 Migration
```
Enable-Migrations
```

5. 加入 Migragtion 檔案名稱

```
Add-Migration InitMigration
```

若有指定的 Context 要加參數
```
Add-Migration InitMigration -Context DBContext
```


6. Update 更新 Migration to DB
```
Update-Database -Context DBContext
```


無報錯，顯示 done 即完成資料庫

![](https://i.imgur.com/1KJ6qvq.png)
