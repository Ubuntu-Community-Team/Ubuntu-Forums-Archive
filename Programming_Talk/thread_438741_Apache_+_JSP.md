---
title: "Apache + JSP"
date: 2007-05-10
forum: Programming Talk
---

### Post by rem on 2007-05-10
Hi,

I followed the first part of [this post]("http://ubuntuforums.org/showthread.php?t=301897&highlight=apache+jsp") and installed Tomcat 5.5 with all the JAVA stuff.
I never worked with JSP before so even Tomcat is starting with no errors, I still can't see any JSP page on [http://localhost:8180](http://localhost:8180) could you explain me in just a few lines what should I do to actually have the parsed JSP pages?

Thanks a mil!

---

### Post by Skardal on 2007-05-10
You aren't able to see any of the examples either? Or even the tomcat welcome screen?

---

### Post by rem on 2007-05-10
> **Skardal said:**
> You aren't able to see any of the examples either? Or even the tomcat welcome screen?

neither one of these 2 just:

Unable to connect
Firefox can't establish a connection to the server at localhost:8180 (also tried with 8080)

---

### Post by Skardal on 2007-05-10
Hva you checked that it really is running?

```
ps ax | grep tomcat
```

..and you can check what port that's used in /etc/tomcat5/server.xml :)

---

### Post by rem on 2007-05-10
I run the command

ps ax | grep tomcat

and got some really scary stuff I attached in a file here
I don't have anything in /etc/tomcat5/server.xml :)

Thanks for your help, I really appreciate it...

---

### Post by cknoblock on 2007-05-10
What's in your catalina.out file under the tomcat directory under the logs folder?  This should show you step by step what tomcat is doing on startup. 

-c

---

### Post by rem on 2007-05-11
> **cknoblock said:**
> What's in your catalina.out file under the tomcat directory under the logs folder?  This should show you step by step what tomcat is doing on startup. 

-c

This is very funny because I can't see anything in the browser when point it to [http://localhost:8180](http://localhost:8180) even though Tomcat is started. If I start Tomcat, then run this command **cat /var/lib/tomcat5.5/logs/catalina.out** it is! I will attach here the generated log.

---

### Post by wieman01 on 2007-05-11
What about...
> [http://localhost](http://localhost)

HOWTO: [http://www.jajakarta.org/tomcat/tomcat3.2-4.0/tomcat-3.2.3/doc/tomcat-apache-howto.html]("http://www.jajakarta.org/tomcat/tomcat3.2-4.0/tomcat-3.2.3/doc/tomcat-apache-howto.html")

---

### Post by rem on 2007-05-11
I am a PHP developer so on [http://localhost](http://localhost) there's Apache running with my stuff.
I just need to integrated some JSP code pages into some templates and this should be just a few hours work...

I copied my files to /tomcat-docs/test but can't run any file... what I get is just a bunch of errors. This is not my expertise anyway, so I'm thinking to give up on it. I thought it is a matter of just a few configuration just like Apache has for PHP then toss a folder into the root path and there you go... It's not the case here, so there's no point in wasting your and my time anymore. Thanks  a lot for being so kind and offering to help and really sorry for keeping your attention so long with this matter.

My best!

---

### Post by AZzKikR on 2007-05-11
What I did to make Tomcat working under Ubuntu was simply **not** using installation from repository. It may be a little bit unconventional, but it worked. Configuration and logging will all remain under one root directory, which may you consider better, or not.

I started by downloading the binaires from [tomcat.apache.org]("http://apache.proserve.nl/tomcat/tomcat-5/v5.5.23/bin/apache-tomcat-5.5.23.tar.gz"). I unpackaged them under the folder
```
/usr/share/tomcat
``` 
Then I started the server using
```
sudo /usr/share/tomcat/bin/startup.sh
```

That was all it took. The server ran on [http://localhost:8080]("http://localhost:8080").

Your result from the grep command also told me that you had like 12 Tomcats running? Analyse your logfiles to check for any exceptions or errors.

---

### Post by rem on 2007-05-11
thanks a lot AZzKikR, i really appreciate it... i used the repository files of course.
it's good to know for future need :)

have a great one!

---

### Post by bedfordd on 2007-05-11
After I first installed Tomcat5, I hit it with my browser and connected but the page was blank (nothing when show source). You can then install the Tomcat example package with lots of examples to use. Sorry, I'm not in front of my machine so I don't know the package name.

---

