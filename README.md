# hostloc_getPoints

小鸡定时获取hostloc积分

github action大规模失效，mjj平均一人10鸡，以下可以部署到自己的小鸡上

**第一步**下载下列代码
https://github.com/Jox2018/hostloc_getPoints/blob/main/hostloc_auto_get_points.py

**第二步**把175，176行代码改为

```
username = "账户"
password = "密码"
```

**第三步**上面文件上传到小鸡

**第四步**在小鸡里新建crontab任务

```
crontab -e
```


添加

```shell
10 2 * * * sleep 5;cd /root/hostloc/ && /usr/local/bin/python3 /root/hostloc/hostloc_auto_get_points.py
```

/root/hostloc/为你上传的路径
/usr/local/bin/python3为你小鸡python3的引用路径

**提示**

1.如果提示以下错误

```python
Traceback (most recent call last):
  File "/root/hostloc/hostloc_auto_get_points.py", line 6, in
   ...
```

请安装request模块

```shell
pip3 install requests
```

2.老哥们可先运行成功以后再添加crontab任务

```shell
cd /root/hostloc/ && /usr/local/bin/python3 /root/hostloc/hostloc_auto_get_points.py
```



env
HOSTLOC_USERNAME=username1,username2...
HOSTLOC_PASSWORD=password1,password2...

# 云函数定时获取hostloc积分
第一步 创建云函数

![image-20211222140319531](https://user-images.githubusercontent.com/31206471/147045704-5f39ffa7-e7b1-4a67-bcdb-6ef6da5f8297.png)


第二步 下载代码`hostloc_scf_auto_get_points.py`

将代码复制进去后点击完成

![image-20211222140918163](https://user-images.githubusercontent.com/31206471/147045720-f3bf70b0-3946-4d8e-bfc8-97474535164b.png)


`hostloc_scf_auto_get_points.py`



第二步 把175，176行代码改为

```
username = "账户"
password = "密码"
```

第三步 设置执行超时时间

正常情况下脚本需要76秒左右，所以我设置成300秒

![image-20211222141305458](https://user-images.githubusercontent.com/31206471/147045881-063a8602-dde3-4812-bd0e-f058a58e93a6.png)


第四步 云函数安装模块pyaes

~~~
pip3 install pyaes -t ./src
~~~

![image-20211222141145382](https://user-images.githubusercontent.com/31206471/147045864-43a0533f-4581-4589-b88e-8e4b64c00350.png)


然后就可以部署测试了





第五步 创建触发器

![image-20211222142400222](https://user-images.githubusercontent.com/31206471/147045539-9381c530-bf32-45d0-bd5b-3ecae4f5a3d0.png)

