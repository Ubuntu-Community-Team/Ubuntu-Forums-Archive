---
title: "getting a jsp to run ..."
date: 2009-03-27
forum: Programming Talk
---

### Post by sefs on 2009-03-27
Hi all i have apache2 (using virtual host) and tomcat installed here.  I used this tutorial...[http://www.mogilowski.net/?p=121](http://www.mogilowski.net/?p=121)

I can reach the tomcat welcomepage at [http://servername:8180](http://servername:8180)


And i have also integrated it to work behind apache as in the tutorial 

my virtualhost has domain mydomain.lan

home folder of this virtual host is /home/mydomain/

webfiles go into /home/mydomain/public_html

and i want to run jsp files from within /home/mydomain/public_html/jsp

the virtual host section of apache2 looks like this...
```

<VirtualHost 192.168.1.56:80>
ServerName mydomain.lan
ServerAlias www.mydomain.lan
DocumentRoot /home/mydomain/public_html
ErrorLog /var/log/virtualmin/mydomain.lan_error_log
CustomLog /var/log/virtualmin/mydomain.lan_access_log combined
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/mydomain/public_html>
Options -Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
<Directory /home/mydomain/cgi-bin>
allow from all
</Directory>
JkMount /jsp/*.jsp ajp13_worker
</VirtualHost>

```

and in server.xml i have

```

<!-- mydomain.lan -->
<host name="mydomain.lan" appBase="/home/mydomain/public_html" unpackWARs="true" autoDeploy="true">
<context path="" docBase="jsp" debug="0" reloadable="true"/>
<valve className="org.apache.catalina.valves.AccessLogValve" directory="/var/log/virtualmin"  prefix="mydomain.lan.tomcat_access_" suffix=".log" pattern="common" resolveHosts="false"/>
</host>

```


i've put the test.jsp file into /home/mydomain/public_html/jsp

and tried to access it via [http://mydomain.lan/jsp/test.jsp](http://mydomain.lan/jsp/test.jsp)  but all i get is this error

HTTP Status 404 -
type Status report
message
description The requested resource () is not available.


Any ideas what i am doing wrong?

Thanks.

---

