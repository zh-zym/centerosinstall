#### 本教程根据center os 7.2进行部署

#### 1 、 jdk安装
    
#####    1.1 到jdk官网找jdk下载链接
    官网链接
    http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
    
#####    1.2 登陆服务器
    
    wget jdk下载链接下载到服务器本地
    #安装jdk
    wget http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/jdk-8u161-linux-x64.rpm?AuthParam=1519484372_fbcaeebfd2d6617c144dd47d58a047ad
#####   1.3  更改下载下来的文件名字，让文件名字为rpm结尾
    mv jdk-8u161-linux-x64.rpm?AuthParam=1519484372_fbcaeebfd2d6617c144dd47d58a047ad jdk-8u161-linux-x64.rpm
    rpm -ivh jdk-8u161-linux-x64.rpm 
##### 1.4验证安装是否成功
    
    javac 或者 java -version
    
#### 2 tomcat 安装
    
    
##### 安装tomcat 
  要什么版本  直接到tomcat官网找
 官网地址
 https://tomcat.apache.org/download-80.cgi
 
     下载源码包
            wget http://mirrors.hust.edu.cn/apache/tomcat/tomcat-8/v8.0.50/bin/apache-tomcat-8.0.50.tar.gz
      
     安装      
            tar zxvf apache-tomcat-8.0.50.tar.gz 
            mv apache-tomcat-8.0.50 /install/tomcat
            cd /install/tomcat/bin
            #启动tomcat
            ./startup.sh 
            #关闭tomcat
            ./shutdown.sh 
#### 测试是否成功 ： 
            
     本地访问  ip：加端口号
            
##### 3 安装nginx
    
    
    #安装make：
    yum -y install gcc automake autoconf libtool make
    
    
    安装前提 
    在安装nginx前，需要确保系统安装了g++、gcc、openssl-devel、pcre-devel和zlib-devel软件。安装必须软件： 
    
    #安装g++:
    yum install gcc gcc-c++
    yum -y install zlib zlib-devel openssl openssl--devel pcre pcre-devel 
    

####   下载nginx 
    wget http://nginx.org/download/nginx-1.12.2.tar.gz
    
##### 解压
    tar -zxvf nginx-1.12.2.tar.gz
    cd  nginx-1.12.2
    ./configure
    make
    make install
    #启动
    /usr/local/nginx/sbin/nginx 
    
    #关闭
##### 查看nginx占用进程
    ps -ef|grep nginx
#### 杀死nginx进程  
     
    标号为1 运行目录为 /usr/local/nginx/sbin/nginx   
    那个的进程编号
    kill -QUIT 2072
#### 杀掉进程
    kill -9 21651
####    --指定配置文件启动
    /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
    
####  nginx 配置文件地址
    /usr/local/nginx/config/nginx.conf
    
    #配置包含目录在下配置根据default进行配置就行
    /usr/local/nginx/config/server-item/
    
#####  nginx附加说明
    #查看配置文件是否正确
#####    方法一：进入nginx安装目录sbin下，输入命令./nginx -t
    看到如下显示nginx.conf syntax is ok
    nginx.conf test is successful
    说明配置文件正确！
#####    重启Nginx服务
    方法一：进入nginx可执行目录sbin下 默认安装情况下是/usr/local/nginx/sbin/，
    输入命令./nginx -s reload 即可
    方法二：查找当前nginx进程号，然后输入命令：kill -HUP 进程号 实现重启nginx服务
    
#####  mysql 数据库安装

          wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
          wget http://repo.mysql.com/mysql-community-release-el6-5.noarch.rpm

  安装
        
        rpm -ivh mysql-community-release-el7-5.noarch.rpm  
       
  数据库5.6           
          
        rpm -ivh mysql-community-release-el6-5.noarch.rpm   
        
  然后
        
         yum install  mysql mysql-server mysql-libs mysql-server;
         
         
  检查是否安装
         rpm -qa|grep -i mysql
         
  启动mysql服务
        
         service mysql start
         
  以root身份打开数据库
  
         mysql -u root
         
#### linux 查看端口占用

  netstat -tunlp |grep 3306   
  
  
     
记录下安装过程，有疑问请联系  zh878998515@gmail.com 
   
  @yy      
     
         
         
    
    
    
    