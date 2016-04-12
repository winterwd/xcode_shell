#xcode_shell

##总共有三个文件build，ipa-build，upload
* ipa-build 打包并上传FTP
* build 单独的打包
* upload 上传至FTP


##编译 xcode project or workspace

执行脚本命令后，如果编译打包成功，会在工程路径下生成 "ipa-build"目录，存放生成的ipa文件

####注意！
***ipa-build 文件夹是用来上传至FTP，如果需要上传其他文件，则需要提前创建ipa-build文件夹，放入需要上传的文件***
***如果需要上传文件至FTP，需要提前配置FTP信息，具体查看upload代码***

####使用：  

***编译 xcode project***

	ipa-build [-u] <project directory> [-c <project configuration>]

***编译 xcode workspace***

	ipa-build [-u] <workspace directory> -w -s <schemeName> [-c <project configuration>]

####可选参数:

	-u          是否上传至ftp 不写默认不上传
	-w          编译workspace
	-s NAME     对应workspace下需要编译的scheme
	-c NAME     工程的configuration,默认为Release
	
####例子:

***编译 xcode project***
    
iOS工程路径 ~/iosProject，脚本文件路径 ~/xcode-shell，如果你需要打包Release，并上传至FTP 命令：

	cd ~/xcode-shell
	./ipa-build -u ~/iosProject

***编译 xcode workspace***

iOS工程路径 ~/iosProject，工程scheme名为test，脚本文件路径 ~/xcode-shell，如果你需要打包Debug，不需上传至FTP 命令：

	cd ~/xcode-shell
	./ipa-build ~/iosProject -w -s test -c Debug

----
######打包命令代码参考自[webfrogs/xcode_shell](https://github.com/webfrogs/xcode_shell.git)
