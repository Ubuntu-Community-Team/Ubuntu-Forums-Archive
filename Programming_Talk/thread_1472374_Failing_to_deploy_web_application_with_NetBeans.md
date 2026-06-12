---
title: "Failing to deploy web application with NetBeans"
date: 2010-05-04
forum: Programming Talk
---

### Post by lads on 2010-05-04
Hello everyone,

This thread is coming out of desperation so please forgive me if this is not entirely framed on this forum.

I installed NetBeans 6.7.1 on Ubuntu 9.10 using the Software Center, intending to start developing a few simple web applications. I managed to set Tomcat as the default web server, since it was already installed.

I then went following NetBean's web application tutorial:

[http://netbeans.org/kb/docs/web/quickstart-webapps.html](http://netbeans.org/kb/docs/web/quickstart-webapps.html)

All went well until I had to run the application. When doing so I get the message:

> FAIL - Deployed application at context path /HelloWeb but context failed to start
/media/Hhai/users/lads/Trabalho/Java/HelloWeb/nbproject/build-impl.xml:563: The module has not been deployed.
BUILD FAILED (total time: 0 seconds) 

I tweaked permissions on the application's directory. Tried the same at Tomcat's directories, but that error keeps popping up. After some digging I found someone reporting a similar problem at the NetBeans forum, and left a comment indicating I was struggling with the same:

[http://forums.netbeans.org/viewtopic.php?t=16373](http://forums.netbeans.org/viewtopic.php?t=16373)

That was a week and a half ago and so far no reply showed up. 

I understand this is may not be related to Ubuntu itself, but if anyone could at least point me to some place where I can get help I'd be grateful.

Thank you,

Luís

---

### Post by japsai on 2010-05-04
I don't know NetBeans very well, but did you look at what is at line 563 of that 'build-impl.xml' file?

---

### Post by lads on 2010-05-05
Hello japsai,

These are lines 562 to 564 of the build-imp.xml file:

 ```
<target if="netbeans.home" name="-run-deploy-nb">
        <nbdeploy clientUrlPart="${client.urlPart}" debugmode="false" forceRedeploy="${forceRedeploy}"/>
    </target>
```

I can't say if there's something wrong with that or not.

Thanks.

---

### Post by lads on 2010-05-06
Today I tried something different, I went searching for the web application files under the Project directory to try and run them directly with Tomcat.

Under the project directory there's a build/web directory with all the application files already packed up with META-INF and WEB-INF directories. I copied all this into an HelloWeb directory under webapps:

```

lads@Kohntarkosz:~$ ls -la tomcat/webapps/HelloWeb
total 24
drwxr-xr-x 4 lads lads    4096 2010-05-05 10:54 .
drwxrwxr-x 6 lads tomcat6 4096 2010-05-05 10:53 ..
-rwxrwxrwx 1 lads lads     666 2010-04-23 15:38 index.jsp
drwx------ 2 lads lads    4096 2010-04-23 15:38 META-INF
-rwxrwxrwx 1 lads lads     655 2010-04-23 15:38 response.jsp
drwx------ 3 lads lads    4096 2010-04-23 15:38 WEB-INF

```

With this setting Tomcat does not run the application, returning the error "The requested resource () is not available". I then tried to move all the files into another directory and it runs. Simply changing the directory name from "HelloWeb" to "HelloWeb2" and Tomcat can run it.

I went checking at Tomcat's manager and in fact there already exists a "HelloWeb" application deployed (I believe this was Netbeans work). But this application fails to start and I can't undeploy it (Tomcat says OK but the application remains listed).

I believe NetBeans is having some issue deploying the application to Tomcat, but what can it be?

Thank you.

---

### Post by hellblazer on 2010-11-29
I have the same problem after installing Tomcat6 on it's own (not bundled with Netbeans).

I suspect it might have something to do with the CATALINA_HOME setting in Ubuntu, but I'm not sure.

I will experiment and get reply here with my results.

---

### Post by hellblazer on 2010-11-29
Right, well I feel like a complete idiot. Mainly because I've made this mistake before and obviously didn't learn a thing that time.

My problem has been resolved by stopping the Tomcat server so as to allow Netbeans to run it. If the server is already running when Netbeans tries to deploy an app Netbeans will display the delopy failed message.

Hope that helps you too lads

---

### Post by Porto143 on 2011-07-10
thank you hellblazer, ur solution helped me too :)

---

