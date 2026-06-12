---
title: "HOWTO : Apache2 + Tomcat5"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Cavalierski on 2006-07-20
[COLOR="DarkOrchid"]# All the modified or additional information will be updated on this post in order for everyone to get alwasys up-to date information.[/COLOR]

This how to explains you the way to set up apache (http server) + tomcat (servlet container). Tomcat itself can work standalone http server however when we consider about the performance, it's better to use the connector to bind apache and tomcat. (If you really need the performance, RESIN is one of the best servlet container though)

[COLOR="Red"]About the connector development of mod-jk2 has been end since 15 November 2004. So please use mod-jk instead.[/COLOR]

**1) Install the needed package**
First of all, let's install the packages needed.
```

sudo apt-get install apache2-mpm-prefork apache2-common apache2-utils
sudo apt-get install sun-java5-jdk tomcat5 tomcat5-admin tomcat5-webapps
sudo apt-get install libapache2-mod-jk

```

**2) Setting up**
Now let's enable the module and set up the conf file
```

sudo a2enmod
#then type
jk

sudo vim /etc/apache2/mods-enabled/jk.load
#Add the following lines
--
LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so

JkWorkersFile /etc/apache2/workers.properties
JkLogFile /var/log/apache2/mod_jk.log
JkLogLevel debug
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "

JkMount /jsp-examples worker1
JkMount /jsp-examples/* worker1

JkMount /servlets-examples worker1
JkMount /servlets-examples/* worker1
--

```
Then create workers file
```

sudo vi /etc/apache2/workers.properties
# Then write following lines 
--
workers.tomcat_home=/usr/share/tomcat5
workers.java_home=/usr/lib/jvm/java-1.5.0-sun
ps=/
worker.list=worker1
worker.worker1.port=8009
worker.worker1.host=localhost
worker.worker1.type=ajp13
worker.worker1.lbfactor=1
--

```

Ok set up is done. Now try whether everything is ok
```

/etc/init.d/apache2 stop
/etc/init.d/tomcat5 stop
/etc/init.d/tomcat5 start
/etc/init.d/apache2 start

# Then access to the page with your browser
http://localhost/servlets-examples/
or
http://localhost/jsp-examples

```

**Option) Server Start up script**
It's done. If you often change the setting and need to restart the servers, it's better to prepare the script. It's possible to create very nice script but as I'm java developper and I'm not so familier with shell script I made small one...

```

vi server.sh
--
#!/bin/bash
/etc/init.d/apache2 stop
/etc/init.d/tomcat5 stop
/etc/init.d/tomcat5 start
/etc/init.d/apache2 start
--
chmod +x server.sh
sudo ./server.sh

```

Now everything is done!:) 

# Then if you need the environment for the development such as versioning system for your code, please refer to:[Subversion Server + Client]("http://ubuntuforums.org/showthread.php?t=187739")

---

### Post by vinodis on 2006-07-24
Thank you!

---

### Post by springDude on 2006-07-25
Hi,

Regarding the last code section 
vi server.sh
--
> #!/bin/zsh
/etc/init.d/apache2 stop
/etc/init.d/tomcat5 stop
/etc/init.d/tomcat5 start
/etc/init.d/apache2 start
--
chmod +x server.sh
sudo ./server.sh 

What's the script for tomcat5??

Thanks,

springDUde

---

### Post by Cavalierski on 2006-07-25
> **springDude said:**
> Hi,

Regarding the last code section 
vi server.sh
--


What's the script for tomcat5??

Thanks,

springDUde

Hi, if you change the config related to jk module, you need to reboot the http & servlet container server. And there are rules about the order of stop and start both server.This small script does it.

---

### Post by pelgrim on 2006-07-28
Hi,

I followed all instructions,
and tomcat works ...
that is, it works for /servlets-examples ...

I have my own worker defined in /java
it worked fine in Mandrake,
but for some reason it refused to work in ubuntu

I added these lines

JkMount /java worker1
JkMount /java/* worker1

This should be enough I thought, apparently nog.

What am I missing ?

---

### Post by Cavalierski on 2006-07-28
> **pelgrim said:**
> 
I added these lines

JkMount /java worker1
JkMount /java/* worker1

This should be enough I thought, apparently nog.

What am I missing ?

Hi, if you could give me more detail, I could be more helpful.
Q1) What kind of response returned from the server if you access to /java ?

You might deploy the file under apache root path. Do you deploy /java under tomcat path? which perhaps under **/usr/share/tomcat5/webapps** if it is default setting.

---

### Post by pelgrim on 2006-07-28
I'm deploying under webapps
next to servlet-examples I made a java directory
where I put my servlets
(/java/WEB-INF/classes/*)
all these subdirectories are located in
/usr/share/tomcat5

The response in firefox is a blanc page, empty source code ...

These pages are working perfectly on mandrake, 
so no problem with them.

---

### Post by Cavalierski on 2006-07-28
> **pelgrim said:**
> 
The response in firefox is a blanc page, empty source code ...

These pages are working perfectly on mandrake, 
so no problem with them.

Ok then , it seems to be the connector related issue.

First of all, please check if you set the correct path to java.

--
```

sudo cat /etc/apache2/workers.properties
--
workers.tomcat_home=/usr/share/tomcat5
workers.java_home=/usr/lib/jvm/java-1.5.0-sun
```

Then if it is ok, please refer to the log of tomcat and connector.
Can you check the log of jk module and tomcat? They are in /var/log/apache2/mod_jk.log and /var/log/tomcat5/<hostname>.log

In order to see the realtime log,you can run console type 
```
tail -f /var/log/apache2/mod_jk.log
#to stop, <CTRL>+c

```
Then you can access the page to see what kind of logs are output.

Tell me what kind of error is outputed in log file.

---

### Post by pelgrim on 2006-07-28
workers.properties is ok.

in /var/log/apache2/error.log I found this

when I was accessing [http://host/java/servlet/classname](http://host/java/servlet/classname)

I found in the log
File does not exist: /var/www/classname

this looks very strange :?:

---

### Post by Cavalierski on 2006-07-28
Please check again your /etc/apache2/workers.properties .
In the host line, try this
--

#worker.worker1.host=localhost <- comment this line and insert the next line
worker.worker1.host=127.0.0.1

--

And make sure to restart the servers.
Hope this will solve the problem :p

---

### Post by pelgrim on 2006-07-28
I found out there are 2 identical directory trees with the example classes,
one in 
usr/share/tomcat5
and one in
/var/lib/tomcat5

starting to get confusing ...

anyway, 
when I access any html page in the java subdir,
I can read it, no problem.
when accessing a servelt in java
/java/servlet/...
I get error like this
The requested resource (/java/servlet/class...) is not available.

The class is there, 
java has an identical directory structure like servlet-examples ...

Don't know if I'm anything closer to a solution, I hope so :confused:

Even more weird:

I copy a simple HelloServlet.class file 
into the class root of servlet-examples.

Just to make sure, I restart tomcat and apache

it produces the same error like if it's not there ...
The requested resource (......) is not available.

---

### Post by Cavalierski on 2006-07-28
Answer of the first question,
```

% ls -l /usr/share/tomcat5/webapps
lrwxrwxrwx 1 root root 24 2006-07-28 17:02 /usr/share/tomcat5/webapps -> /var/lib/tomcat5/webapps
```

Symlink :p 

Will you provide more info..

---

### Post by pelgrim on 2006-07-28
sorry,

but I figured that one out with "trail and error" ;) 

/var/lib/tomcat5 is the one that's used ...

Ok, I guess I figured it out ...

Servlets must be defined in web.xml

That's new to me !!!

Was not needed at my development environment I had before in win XP,
and it wasn't needed on my mandrake, also tomcat5 ...

ok, so final question about this:
how to avoid specifying every single servlet I make in web.xml ?
This would be a very nasty and time consuming thing to do in the future for me,
since this is mostly a development environment ...

---

### Post by Cavalierski on 2006-07-28
> **pelgrim said:**
> sorry,

but I figured that one out with "trail and error" ;) 

/var/lib/tomcat5 is the one that's used ...

Well then it seems that web.xml is not properly set as html is ok to be forwared by jk from apache.

Please check WEB-INF/web.xml if servlet and servlet-mapping tags are set properly.
--
 ```
   <servlet>
      <servlet-name>
          WhateverName
      </servlet-name>
      <servlet-class>
          ClassName
      </servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>
            WhateverName
        </servlet-name>
        <url-pattern>
            /AnyPathYouLike
        </url-pattern>
    </servlet-mapping>
```

--

---

### Post by pelgrim on 2006-07-28
ok, thanx a lot for your help
I appreciate it.

So, final question,
how to avoid defining everything in web.xml

This was not needed on my mandrake server,
also running tomcat5 ...
Like said before,
this is mainly a development environment,
defining everything in web.xml in the future will
be very anoying and time consuming ...

---

### Post by Cavalierski on 2006-07-28
> **pelgrim said:**
> ok, thanx a lot for your help
I appreciate it.

So, final question,
how to avoid defining everything in web.xml

This was not needed on my mandrake server,
also running tomcat5 ...
Like said before,
this is mainly a development environment,
defining everything in web.xml in the future will
be very anoying and time consuming ...

Hi, pelgrim:p 

Good to hear. It's almost done.
Until Tomcat3 it is ok to use /servlet/ folder to deploy servlet. However after Tomcat4 because of the security issue, we use web.xml to specify the servlet.

It is still possible even Tomcat5 to use /servlet/ if you don't really care about the security.

```
sudo vim /usr/share/tomcat5/conf/web.xml
--
<!--Comment out the following-->
<servlet-mapping>
   <servlet-name>invoker</servlet-name>
   <url-pattern>/servlet/*</url-pattern>
</servlet-mapping>
--

```

Then restart the servers :D

---

### Post by pelgrim on 2006-07-29
sudo vim /usr/share/tomcat5/conf/web.xml
--
<!--Comment out the following-->
<servlet-mapping>
   <servlet-name>invoker</servlet-name>
   <url-pattern>/servlet/*</url-pattern>
</servlet-mapping>
--

this doesn't work,
not putting this in the old web.xml I had in win XP / apache5,
not in a copy I took from the servlets-examples

Anyway, I started to list all needed servlets in the list,
after all, security will become an issue in near future anyway.

Next problem I have now:
I have servlets reading directory content from subdirectories
in my "worker" html root directory.
Again, this worked in Mandrake, not not anymore.

this is the error output from the servlet:
```
java.security.AccessControlException: access denied (java.util.PropertyPermission catalina.home read)
	java.security.AccessControlContext.checkPermission(AccessControlContext.java:264)
	java.security.AccessController.checkPermission(AccessController.java:427)
	java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
	java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:1285)
	java.lang.System.getProperty(System.java:627)
```

The problem is simple: security issue.
Solving the problem is another case for me,
I'm rather new to linux

While I'm asking:
apache port is set at 8080,
and now my servlets run at port 8180.
Where to tell tomcat I want them also at port 8080

---

### Post by goanookie on 2006-07-29
The config files are good, as far as I can see, but still the servlet keeps throwing errors, like the one below. 
Anybody care to enlighten this error?

Greetz
Peter

```

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

javax.servlet.ServletException
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:290)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

root cause

java.lang.NoClassDefFoundError
	ODBC.PostgreSQL.listClass.<init>(listClass.java:39)
	JavaClassDigger.data.ListModule.<init>(ListModule.java:13)
	JavaClassDigger.XML.moduleindex.doGet(moduleindex.java:68)
	JavaClassDigger.XML.moduleindex.doPost(moduleindex.java:94)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:709)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	JavaClassDigger.HTML.index.doGet(index.java:31)
	JavaClassDigger.HTML.index.doPost(index.java:49)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:709)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	JavaClassDigger.XML.moduleindex.doGet(moduleindex.java:86)
	JavaClassDigger.XML.moduleindex.doPost(moduleindex.java:94)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:709)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)


```

---

### Post by pelgrim on 2006-07-29
is there any way I can get rid of this security settings.

making the entries
<servlet>
  <servlet-name>"invoker" ...

<servlet-mapping>
  <servlet-name>"invoker" ...

active didn't help,
deleting all security engris in web.xml als didn't help.

ok, finally I figured it out ...

/etc/init.d/tomcat5

there is the option to put security off ...

One final problem remains that I can't figure out:
I installed apache and tomcat with synaptics,
but tomcat doesn't seem to work until I manually
stop apache and start tomcat an apache myself.

I want this to be done at boot ofcourse ...

doing this in rc.local doens't help ...

---

### Post by thor918 on 2006-08-10
what apt-sources do one need to get these packages?

I think I found it now:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse


seems to be working now.
by the way I got this error first:
root@urk:~# /etc/init.d/tomcat5 start
Could not start Tomcat 5 servlet engine because no Java Development Kit
(JDK) was found. Please download and install JDK 1.3 or higher and set
JAVA_HOME in /etc/default/tomcat5 to the JDK's installation directory.

so I just added this line to that file:
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun

after that it started working.
:D

---

### Post by TheThirdWheel on 2006-10-09
I followed the instructions given in the beginning of this post, but for some reason when I go to [http://localhost/jsp-examples](http://localhost/jsp-examples) I get the following error:

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 Server at 127.0.1.1 Port 80

Any help or guidance would be more than welcome.

---

### Post by pelgrim on 2006-10-09
It looks like Tomcat is not running.

I had a simalar problem here.
When I checked Apache was running automatic as a service at boot,
but tomcat not.
Try to shut down Apache and Tomcat,
and restart them.
Apache needs to start first.

---

### Post by MidNight(tomcat) on 2006-11-08
Hi !! I followed all instructions, start tomcat(1st) and apache(2nd) but i have a probem: my apache server([http://localhost](http://localhost)) is ranning good but my tomcat server([http://localhost:8080](http://localhost:8080)) dosn`t opened(Enabled to connect to the server!).Help me:confused:

---

### Post by ess on 2007-01-16
Hello there

I have followed the instructions and managed to install Tomcat5 with an already configured LAMP solution on my home server. 

I would like to know if there is a way to allow JSP pages to be served from within users **public_html folder**

I have added the following line to jk.load file, but tomcat reports 404 errors when i try to view the page. 

```
JkMount /*.jsp worker1
```

Is there a way that I can do this. 

Regards,
Ess

---

### Post by mitjab on 2007-01-17
where i can find administration for tomcat?

thx

---

### Post by mitjab on 2007-01-17
anyone?

---

### Post by mohammadrizki on 2007-06-26
> **mitjab said:**
> where i can find administration for tomcat?

thx

I usually use the web-based one at [http://localhost:8180/admin](http://localhost:8180/admin).

---

### Post by _sluimers_ on 2009-05-09
I followed the tutorial, but nothing happened. I still get to see 403 forbidden

---

