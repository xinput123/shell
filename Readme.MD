### show-busy-java-threads 用法
```
# 从所有运行的Java进程中找出最消耗CPU的线程（缺省5个），打印出其线程栈
sh show-busy-java-threads.sh  

# 手动指定要分析的Java进程Id，以保证只会显示你关心的那个Java进程的信息
sh show-busy-java-threads.sh -p <指定的Java进程Id>  

# 多次执行；这2个参数的使用方式类似vmstat命令
sh show-busy-java-threads.sh -p <重复执行的间隔秒数> [<重复执行的次数>]  

# 记录到文件以方便回溯查看
sh show-busy-java-threads.sh -a <运行输出的记录到的文件>   

# 指定jstack输出文件的存储目录，方便记录以后续分析
sh show-busy-java-threads.sh -S <存储jstack输出文件的目录>  
```

### show-duplicate-java-classes 用法
找出Java Lib（Java库，即Jar文件）或Class目录（类目录）中的重复类。
全系统支持（Python实现，安装Python即可），如Linux、Mac、Windows。

```
# 查找当前目录下所有Jar中的重复类
sh show-duplicate-java-classes.sh

# 查找多个指定目录下所有Jar中的重复类
sh show-duplicate-java-classes.sh path/to/lib_dir1 /path/to/lib_dir2
```

### find-in-jars 用法
```
# 在当前目录下所有`jar`文件里，查找类或资源文件。
sh find-in-jars.sh 'log4j\.properties'
sh find-in-jars.sh 'log4j\.xml$'
sh find-in-jars.sh log4j\\.xml$ # 和上面命令一样，Shell转义的不同写法而已
sh find-in-jars.sh 'log4j\.(properties|xml)$'

# -d选项 指定 查找目录（覆盖缺省的当前目录）
sh find-in-jars.sh 'log4j\.properties$' -d /path/to/find/directory

# 支持多个查找目录，多次指定这个选项即可
sh find-in-jars.sh 'log4j\.properties' -d /path/to/find/directory1 -d /path/to/find/directory2

# -a选项 指定 查找结果中的Jar文件使用绝对路径,分享给别人时，Jar文件路径是完整的，方便别人找到文件
sh find-in-jars.sh 'log4j\.properties' -a
```