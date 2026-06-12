---
title: "HOWTO: Ubuntu 8.04 Tomcat+Cocoon for Oracle ApEx PDF printing"
date: 2008-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Waappu on 2008-12-07
This tutorial is for people who wants enable PDF printing for Oracle Application Express version 3.1 or greater.
I have tested this on Ubuntu 8.04 server, Oracle XE Universal and Apex versions from 3.1 to 3.2.1.

First set enviroment variables adding rows to your .bashrc
```
nano ~/.bashrc
```
Add lines end to file
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export CATALINA_HOME=/usr/share/tomcat5.5
```

Logoff and login again so that enviroment variables taken use.

Install Unrar, Java and Tomcat
```
sudo apt-get install unrar sun-java6-jre sun-java6-jdk libtomcat5.5-java tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
```

Stop Tomcat
```
sudo /etc/init.d/tomcat5.5 stop
```

Create user for Tomcat admin and manager editing file /usr/share/tomcat5.5/conf/tomcat-users.xml.
Replace "yourusername" and "yourpasswd"  string you like use to username and password.
```
sudo nano /usr/share/tomcat5.5/conf/tomcat-users.xml
```
Add between tags <tomcat-users> and </tomcat-users> rows
```
<role rolename="manager"/>
<role rolename="admin"/>
<user username="yourusername" password="yourpasswd" roles="admin,manager"/>
```

Set JAVA_HOME
```
sudo nano /etc/default/tomcat5.5
```
Add line end of file
```
JAVA_HOME=/usr/lib/jvm/java-6-sun
```

Create policy for Cocoon
```
sudo nano /etc/tomcat5.5/policy.d/05cocoon.policy
```
And paste this to file
```
grant codeBase "file:/var/lib/tomcat5.5/webapps/cocoon/-" {
    permission java.security.AllPermission;
};
```

Download Cocoon source:
```
cd /tmp
wget http://mirror.eunet.fi/apache/cocoon/cocoon-2.1.11-src.tar.gz
tar -xvvzf cocoon-2.1.11-src.tar.gz
```

Build Cocoon war file
```
cd /tmp/cocoon-2.1.11
sh build.sh war
```

Copy war file to Tomcat webapps folder
```
sudo cp /tmp/cocoon-2.1.11/build/cocoon/cocoon.war /var/lib/tomcat5.5/webapps
```

Start Tomcat
```
sudo /etc/init.d/tomcat5.5 start
```

Get fop_post for ApEx and place it to Tomcat webapps Cocoon folder
```
wget http://rste.net.googlepages.com/fop_post.rar
unrar x fop_post.rar
sudo mv fop_post /var/lib/tomcat5.5/webapps/cocoon
```

Now Tomcat mainpage can be access from [http://localhost:8180/](http://localhost:8180/)

Set up ApEx:
- Login to your ApEx INTERNAL workspace
- Go to Manage Service -> Instance Settings
- Change Report Printing configuration

Print Server: 			Standard
Print Server Host Address:	localhost
Print Server Port: 		8180
Print Server Script: 		/cocoon/fop_post/

Now you can enable PDF printing on your ApEx application reports

I have used below links to build up this guide. So credit goes to
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)
[http://carlback.blogspot.com/2007/03/apex-cocoon-pdf-and-more.html](http://carlback.blogspot.com/2007/03/apex-cocoon-pdf-and-more.html)
[http://rste.blogspot.com/2008/07/excel-export-from-apex-cocoon.html](http://rste.blogspot.com/2008/07/excel-export-from-apex-cocoon.html)
[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)
[http://howto.landure.fr/gnu-linux/debian-4-0-etch-en/install-cocoon-2-1-x-and-fop-0-9x-on-debian-4-0-etch/view?set_language=en](http://howto.landure.fr/gnu-linux/debian-4-0-etch-en/install-cocoon-2-1-x-and-fop-0-9x-on-debian-4-0-etch/view?set_language=en)
[http://www.poveravoce.net/blog/?p=85](http://www.poveravoce.net/blog/?p=85)


Edit:
When you configure Apex instance you can also select
**Print Server: Advanced (requires Oracle BI Publisher)**
Then you get more options to print your interactive report.

Tomcat has by default limit on POST size.
That prevent you download large PDF file

You can change maxPostSize parametter to e.g. unlimited

Open /etc/tomcat5.5/server.xml
```
sudo nano /etc/tomcat5.5/server.xml
```
find line maxSpareThreads="75" and add after that to new line
```
maxPostSize="0"
```

Also you need increase Java memory.
Edit /etc/default/tomcat5.5
```
sudo nano /etc/default/tomcat5.5
```
and line end of file
```
JAVA_OPTS="-Xms1024m -Xmx2049m -XX:MaxPermSize=512m -XX:PermSize=512m -XX:+CMSClassUnloadingEnabled -XX:+CMSPermGenSweepingEnabled"
```[I]**Note**: in example I have allocated max 2GB Java memory with parametter -Xmx2049m. You can allocate about only half of your physical memory.
This seems to be issue that printing needs lot of memory.[/I]

After changes restart Tomcat
```
sudo /etc/init.d/tomcat5.5 restart
```[I]**Note**: if you use e.g. HTTP server or Apache reverse proxy 
to connect database/Apex there might be also limitation for Post size.
If you use Embed PL/SQL gateway (EPG) there should not be limits. At least I have not find any on Oracle XE EPG.[/I]



I am still testing/experimenting those Java memory settings so if some one use this guide and understand better 
Java memory parameters , please post your comments

---

