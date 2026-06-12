---
title: "proper permissions for apache tomcat folder"
date: 2010-08-07
forum: Programming Talk
---

### Post by badperson on 2010-08-07
Hi,
I'm trying to get apache working on my ubuntu 10.04 machine (64bit)

I had the default installation of tomcat 6. I tried to drop a .war file into the webapps folder, but when I entered the url 

```
http://localhost:8080/AppName/ServletName
```

I got a 404, and the webapp .war file hadn't expanded into a folder.

so I did a chmod 777 in the webapps folder, same result.

I stopped the server, tried to start a server within eclipse and wasn't able to start a tomcat 6 folder. So I downloaded tomcat 7. Eclipse allowed me to create a tomcat 7 server, but I couldn't start it because of a permission error. So I did chmod 777 on the apache tomcat folder, but then eclipse wouldn't let me create a tomcat 7 server....


All of which is a long way of asking what the proper permissions are so I can drop a .war file and have eclipse create an instance of the server...

permissions for tomcat 6 folder:
> drwxrwxrwx 2 root root 4096 2010-07-19 08:15 bin
drwxrwxrwx 2 root root 4096 2010-07-19 08:15 lib
drwxrwxrwx 3 root root 4096 2010-08-07 07:52 webapps


for tomcat 7

> drwsrwsrwx 2 root root  4096 2010-08-07 08:13 bin
drwsrwsrwx 3 root root  4096 2010-08-07 08:18 conf
drwsrwsrwx 2 root root  4096 2010-08-07 08:13 lib
-rwxrwxrwx 1 root root 56802 2010-06-13 10:54 LICENSE
drwsrwsrwx 2 root root  4096 2010-08-07 08:18 logs
-rwxrwxrwx 1 root root  1193 2010-06-13 10:54 NOTICE
-rwxrwxrwx 1 root root  8785 2010-06-13 10:54 RELEASE-NOTES
-rwxrwxrwx 1 root root  6665 2010-06-13 10:54 RUNNING.txt
drwsrwsrwx 2 root root  4096 2010-08-07 08:18 temp
drwsrwsrwx 7 root root  4096 2010-06-13 10:53 webapps
drwsrwsrwx 3 root root  4096 2010-08-07 08:18 work



thanks!
bp

---

### Post by badperson on 2010-08-07
I deleted and re-installed tomcat 7, and the problem still persists. In eclipse, when I try to select "tomcat 7" (or "tomcat 6"), the "next button is greyed out. 

if I select "tomcat 5" (which isn't installed) it allows me to hit next...uugghhh.....anyone?
bp

---

### Post by badperson on 2010-08-07
okay, 
found a solution [here:]("http://stackoverflow.com/questions/447289/problem-creating-a-tomcat-6-server-in-eclipse-form-ubuntu")

but now I need to know how to stop tomcat 6 from being generated at startup...

---

