---
title: "XAMPP/LAMPP like stack for java and python"
date: 2013-02-24
forum: Programming Talk
---

### Post by vikkyhacks on 2013-02-24
I used to create web applications with XAMPP ([www.apachefriends.org/en/xampp-linux.html](www.apachefriends.org/en/xampp-linux.html)) which has a simple whole collection of mysql, php, apache which i cam turn on/off with just simple ```
/lampp/bin/lampp <args>
``` without installing anything on my whole native machine ... If i end up messing with mysql DB or some config error I just remote the whole lampp directory and reinstall by just unzipping the installer i downloaded...

**[SIZE="3"] IS THERE ANY SUCH XAMPP STACK FOR JAVA AND PYTHON[/SIZE]**

please help me ... I really need one like XAMPP

---

### Post by greenpeace on 2013-02-24
Hi!

I don't think there's any direct equivalent, but for Java you can have a look at the tomcat[1] webserver, and which is in the repositories[2] and simple to set up and administer[3].  Once you have something ready, installing your webapps is easy too[4].

For Python, you can work with Apache too, in a similar way to PHP [5], and it's not overly complicated if you're already familiar with PHP and Apache.

Good luck!
gp

[1] [http://tomcat.apache.org/](http://tomcat.apache.org/)
[2] [https://help.ubuntu.com/12.04/serverguide/tomcat.html](https://help.ubuntu.com/12.04/serverguide/tomcat.html)
[3] [https://help.ubuntu.com/12.04/serverguide/tomcat.html#tomcat-webapps](https://help.ubuntu.com/12.04/serverguide/tomcat.html#tomcat-webapps)
[4] [http://www.vogella.com/articles/ApacheTomcat/article.html#tomcat_deploy](http://www.vogella.com/articles/ApacheTomcat/article.html#tomcat_deploy)
[5] [http://docs.python.org/2/howto/webservers.html](http://docs.python.org/2/howto/webservers.html)

---

### Post by vikkyhacks on 2013-02-24
Well thanks for the reply, I have used PHP with apache for a long time, surprisingly never took the pain of configuring it myself because I was introduced to it with XAMPP, Its easy to work without touching my native os. I found this Bitnami, a bit similar to XAMPP where i can remove the whole bundle if there is some crappy configurations. I am looking for something which 

  [B]1. Can be copied simply to /opt/ directory with no need to install 
  2. Previously configured with python/java so that I can kick start my programming
[/B]
(I also have to mention that i am a beginner with jsp/python CGI)

Reference:
This is a bundle but not 100% configured (not sure if its preconfigured)
```
http://bitnami.org/stack/lamp
```

---

### Post by vikkyhacks on 2013-02-24
Never mind, Found it myself, Bitnami's stack are preconfigured. I was trying to mess with django(without knowing about it) I just had to put my python files inside cgi-bin to et it working. The python part is fine for me, but I will leave the thread open for Java.

---

### Post by greenpeace on 2013-02-24
Hi, 

Not sure what's wrong with tomcat... Once it is installed (and you can see how easy that is on the links I sent) you need to do absolutely no configuration on it to have a working java servlet container.  

I haven't had to mess with the configurations on my server since installing, and uninstalling is just as simple; using apt-get.

Then, once you have a java app written (which could be anything from your "hello world" and upwards) it's as easy as exporting a .war from your IDE, and copying that into the webapps directory (/var/lib/tomcat6/webapps/ here)... you don't need to change your "native os" beyond installing the tomcat server itself.

There are a million tutorials online to help you kickstart your programming, and some excellent ones on the tomcat project pages themselves [1].

Have a look at it... I'm not sure you'll find anything simpler :)

Cheers
gp

[1] [http://tomcat.apache.org/tomcat-6.0-doc/appdev/index.html](http://tomcat.apache.org/tomcat-6.0-doc/appdev/index.html)

---

### Post by cybergalvez on 2013-02-24
for python I would look at web2py, it is 100% self contained. You can get fancy and add a real db like mysql or run it behind apache, but if you're just developing apps you really don't need anything else

---

### Post by vikkyhacks on 2013-02-25
> **greenpeace said:**
> Not sure what's wrong with tomcat... Once it is installed (and you can see how easy that is on the links I sent) you need to do absolutely no configuration on it to have a working java servlet container.


   Tomcat is perfectly fine, but it does not come with an database ...  I need to have separate stack, I work with jsp,php and python. I make some simple optimization with the database depending on the application server. That is why i need a self contained php,jsp and python appserver with its own database.

---

### Post by vikkyhacks on 2013-02-25
................

---

### Post by vikkyhacks on 2013-02-25
> **cybergalvez said:**
> for python I would look at web2py, it is 100% self contained. You can ..

do we have it for Linux (Ubuntu)

---

### Post by greenpeace on 2013-02-25
> **vikkyhacks said:**
> I make some simple optimization with the database depending on the application server. That is why i need a self contained php,jsp and python appserver with its own database.

Ok, understand now, though I'm not aware of anything along those lines.

What optimisations are you making to the DB that means you can't use MySQL or Postgresql with it?

Cheers,
Gp

---

### Post by memilanuk on 2013-02-25
> **vikkyhacks said:**
> do we have it for Linux (Ubuntu)

You just download it into your user directory, unpack it and run it.  By default it uses a simple http server (Rocket) and sqlite.

You can modify the settings to use other databases as needed, or to use another web server if desired.  But 'getting off the ground' with it is *very* easy.

---

### Post by sandyd on 2013-02-25
You can also take a look at uwsgi, though be careful of [https://bugs.launchpad.net/ubuntu/+source/uwsgi/+bug/1131314](https://bugs.launchpad.net/ubuntu/+source/uwsgi/+bug/1131314)

---

