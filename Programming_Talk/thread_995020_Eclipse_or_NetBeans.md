---
title: "Eclipse or NetBeans?"
date: 2008-11-27
forum: Programming Talk
---

### Post by JimTDI on 2008-11-27
Hi Everyone!

I'm a beginning Java developer - worked with Java 1.4 and a simple text editor a little bit a few years back, but now I want get serious about learning Java, and more specifically J2EE to develop a web application.  So I will be needing to have an IDE.  I know the Java developers at my shop all seem to like Eclipse (but they all program on Windows, not Linux) - but a few talk about NetBeans.  I have read about both of them, and I wanted to know which would be a better IDE for me to learn Java and J2EE on.  Unless there is a compelling reason to learn either IDE on Windows, I'd prefer to use Ubuntu Linux.

One last question please, is it better to install Java, Eclipse, Netbeans, GlassFish, Tomcat, etc. from the Ubuntu packages, or go grab the versions directly.  I see in the case of NetBeans, that the Ubuntu package is older than what's on the NetBeans web site.

Thank you for any insight or thoughts you'd care to share!

---

### Post by abbec on 2008-11-27
In my opinion eclipse is way better :).

---

### Post by jespdj on 2008-11-27
Eclipse and NetBeans are both very good and popular IDEs. One is not clearly better than the other. It comes down to personal preference.

For both Eclipse and NetBeans, I'd recommend downloading them from the Eclipse and NetBeans websites, and not installing them from the Ubuntu repository. The versions in the repository are old, and installing the directly downloaded versions is easy: with Eclipse, you only have to unpack the downloaded file in a directory and you're done, and NetBeans comes with an easy installation wizard.

If your goal is to get started with Java EE, then download "Eclipse IDE for Java EE Developers", or with NetBeans one of the packages that contains Java EE support.

If you specifically want to work with GlassFish and Tomcat, then NetBeans might be easier, because those are included with NetBeans and automatically set up for use with the IDE for you.

---

### Post by jimi_hendrix on 2008-11-27
first do

sudo apt-get install eclipse netbeans

then decide which you like then do

sudo apt-get remove eclispe netbeans

then go get the one you liked best from the site

---

### Post by trojatra on 2008-11-28
I like NetBeans itself, but it crashes/takes forever to load every time that I run it and Python support is only in the beta version I believe (not an issue for you maybe, but for me it is), so I was going to go back to Eclipse, but that also takes a while to load. Anjuta is very fast to load for me, but the Java and Python support are kinda lame. Geany it is, on my end.
Geany has support for tons of languages (programming, scripting, and markup) and is very fast.

---

### Post by Sorivenul on 2008-11-28
I agree that this comes down to personal preference.

Personally, I prefer NetBeans whenever I work with Java.  If you want GlassFish and Tomcat, it is definitely the easier route.  Should you choose to branch into other Languages, Eclipse is more easily extensible. Try both, and pick what is best for you.  

Good luck.

---

### Post by aszxcv on 2008-11-28
[http://www.javaworld.com/javaworld/jw-03-2008/jw-03-java-ides0308.html](http://www.javaworld.com/javaworld/jw-03-2008/jw-03-java-ides0308.html)

i found this

---

### Post by jespdj on 2008-11-28
> **jimi_hendrix said:**
> first do

sudo apt-get install eclipse netbeans
...

No, it is better to download from the Eclipse and NetBeans websites than install old versions from the Ubuntu repository, as I explained.

> **trojatra said:**
> I like NetBeans itself, but it crashes/takes forever to load every time that I run it and Python support is only in the beta version I believe (not an issue for you maybe, but for me it is), so I was going to go back to Eclipse, but that also takes a while to load. Anjuta is very fast to load for me, but the Java and Python support are kinda lame. Geany it is, on my end.
Geany has support for tons of languages (programming, scripting, and markup) and is very fast.

Which version of NetBeans are you using, and how much memory does your computer have? NetBeans 6.5 has just been released and it works great. It doesn't take really long to load on my computer, but my computer has 4 GB RAM. Both Eclipse and NetBeans do need a lot of memory (NetBeans even more than Eclipse), I'd recommend installing at least 2 GB in your machine.

Geany is a nice, light weight IDE, but the question was about Eclipse vs. NetBeans.

---

### Post by Kilon on 2008-11-28
> **JimTDI said:**
> Hi Everyone!

I'm a beginning Java developer - worked with Java 1.4 and a simple text editor a little bit a few years back, but now I want get serious about learning Java, and more specifically J2EE to develop a web application.  So I will be needing to have an IDE.  I know the Java developers at my shop all seem to like Eclipse (but they all program on Windows, not Linux) - but a few talk about NetBeans.  I have read about both of them, and I wanted to know which would be a better IDE for me to learn Java and J2EE on.  Unless there is a compelling reason to learn either IDE on Windows, I'd prefer to use Ubuntu Linux.

One last question please, is it better to install Java, Eclipse, Netbeans, GlassFish, Tomcat, etc. from the Ubuntu packages, or go grab the versions directly.  I see in the case of NetBeans, that the Ubuntu package is older than what's on the NetBeans web site.

Thank you for any insight or thoughts you'd care to share!

At GUI , deleting comnponents was a nightmare in BETBEANS. Eclipse behaves the way I epxect to . I am newcomer to both. 

From a general look Netbeans looks like a cutdown version of Eclipse. I dont find NETBEANS easier either. So but I would not recommend NETBEANS over Eclipse.

---

### Post by Majorix on 2008-11-28
I use NetBeans because the Visual Editor plugin for Eclipse hasn't been made available for the latest releases of Eclipse.

---

### Post by Kilon on 2008-11-28
> **Majorix said:**
> I use NetBeans because the Visual Editor plugin for Eclipse hasn't been made available for the latest releases of Eclipse.

I use jigloo recommended by a friend here. It is quite good. 

And unlike NETBEANS does not complicate the code  , it keeps code simple, readable and editable.

For further info look here

[http://ubuntuforums.org/showthread.php?t=987002](http://ubuntuforums.org/showthread.php?t=987002)

---

### Post by tinny on 2008-11-28
> **jespdj said:**
> Eclipse and NetBeans are both very good and popular IDEs. One is not clearly better than the other. It comes down to personal preference.

For both Eclipse and NetBeans, I'd recommend downloading them from the Eclipse and NetBeans websites, and not installing them from the Ubuntu repository. The versions in the repository are old, and installing the directly downloaded versions is easy: with Eclipse, you only have to unpack the downloaded file in a directory and you're done, and NetBeans comes with an easy installation wizard.

If your goal is to get started with Java EE, then download "Eclipse IDE for Java EE Developers", or with NetBeans one of the packages that contains Java EE support.

If you specifically want to work with GlassFish and Tomcat, then NetBeans might be easier, because those are included with NetBeans and automatically set up for use with the IDE for you.

jespdj, you are bang on with your comments here. I hope the OP takes your advice.

Both are great IDE's and at the end of the day to be a professional Java developer you should have experience with both (OP should also have a play with Intellij one day...).

Personally I have a slight preference for Eclipse mainly because it is liter on RAM and for me has tended to be a little more responsive. However Netbeans does give the best out of the box experience which I think the OP will enjoy (Eclipse can sometimes require a little bit of config to get setup correctly for enterprise development). Also Netbeans has some very good learning trails on their website, these trails are executed using the Netbeans IDE which may also help get you up and running quickly with the fundamentals.

But have a play with both :-)

FYI:

[http://www.netbeans.org/kb/trails/java-ee.html](http://www.netbeans.org/kb/trails/java-ee.html)
[http://www.netbeans.org/kb/60/javaee/ejb30.html](http://www.netbeans.org/kb/60/javaee/ejb30.html)
[http://www.netbeans.org/kb/61/web/quickstart-webapps-spring.html](http://www.netbeans.org/kb/61/web/quickstart-webapps-spring.html)
[http://www.netbeans.org/kb/61/web/quickstart-webapps-struts.html](http://www.netbeans.org/kb/61/web/quickstart-webapps-struts.html)
[http://www.netbeans.org/kb/60/web/quickstart-webapps-wicket.html](http://www.netbeans.org/kb/60/web/quickstart-webapps-wicket.html)

---

### Post by Shin_Gouki2501 on 2008-11-28
I think if you are going for Java EE and need an App Server running Netbeans should be easy.

---

### Post by Majorix on 2008-11-28
> **Kilon said:**
> I use jigloo recommended by a friend here. It is quite good.

To quote them on their mainpage:

> Features and Requirements
Eclipse: 	2.1.*, 3.0*, 3.1*, 3.2*, 3.3
Java: 	1.3, 1.4, 5 or 6
Platforms: 	

Windows, Linux (gtk) and Mac OSX. It has not been tested on other platforms, but may perform successfully on them

It obviously is not for me because I have Eclipse 3.4 :)

---

### Post by jespdj on 2008-11-28
> **Majorix said:**
> It obviously is not for me because I have Eclipse 3.4 :)
Well, does it really not work on 3.4, or have they just not updated their website yet? I've never used Jigloo, but heard the name often, I get the impression that it's popular, and I would be surprised if it doesn't work on Eclipse 3.4. Maybe you should just try it out.

---

### Post by L815 on 2008-11-28
I am a huge fan of Eclipse, but when Netbeans 6.5 was in RC I became hooked. 6.5 has been fully released and it is really really nice. Still feels a bit slower in terms of response time when doing things via the UI compared to Eclipse, but Netbeans really shines when writing code.

---

### Post by Kilon on 2008-11-29
> **Majorix said:**
> To quote them on their mainpage:



It obviously is not for me because I have Eclipse 3.4 :)


Have you actually downloaded and tested it ? How can you be certain that it does not work for you if you have not done so ?

I have tested all the basic functionality of jigloo in version of Eclipse 3.4.1 ,which as far as I know is the latest version,  for both Windows and MACOSX and it works like a charm. It is logical to assume that you should not experience with it any problems in UBUNTU. 

Try it , it does not look as much as the NETBEANS editor but it really is very easy to use and it keeps your code very simple. I think it is ideal for a beginner who loves to understand what he is programming or what Eclipse programms for him.  I will report if I find any problem with it.

---

### Post by shafi on 2008-11-29
Eclipse is the best,
its more powerful than netbeans.its not only fo beginners but you can do really advance projects with eclipse,
many thins are possible that you can not have them instantly in netbeans.
most software engineers use this IDE for their tasks,
regarding the j2ee you have many facilities you can generate codes very easild ,you can do hibernating ,  the JSF section is very cool and you can do lots of things by mouse drags and drops.
you can Google for some j2ee tutorials using eclipse then you will see how cool is eclipse ;)

---

### Post by rlzyoner on 2008-11-29
I'm running eclipse 3.5.1 i think and the jigloo plugin works fine for me.
I'm not too sure if its still maintained but it definately works fine.
And to agree with one of the guys up there, the output code from the gui, is a lot cleaner than the netbeans code.

---

### Post by JimTDI on 2008-11-30
Thanks everyone for your answers to my question.  For starting out in my endeavor to learn Java and J2EE I have decided to use NetBeans, and a book from Deitel called "Java - How To Program - Sixth Edition".  I'm sure once I get a little further down the Java road - I can switch IDEs, but learning some of the Java basics are the most important to me right now.  (Does anyone either recommend this book, or NOT recommend this book?)

Now, I just need to sort out which version(s) of Java are on my Ubuntu box.  I know I have Sun Java, and Open Java.  I'm wanting to use Sun's version, so I'm playing around with which version NetBeans sees and uses to compile, etc.

I very much appreciate the links and suggestions you all have provided!  This Ubuntu community is the best!!

---

### Post by tinny on 2008-11-30
> **JimTDI said:**
> Thanks everyone for your answers to my question.  For starting out in my endeavor to learn Java and J2EE I have decided to use NetBeans, and a book from Deitel called "Java - How To Program - Sixth Edition".  I'm sure once I get a little further down the Java road - I can switch IDEs, but learning some of the Java basics are the most important to me right now.  (Does anyone either recommend this book, or NOT recommend this book?)

Now, I just need to sort out which version(s) of Java are on my Ubuntu box.  I know I have Sun Java, and Open Java.  I'm wanting to use Sun's version, so I'm playing around with which version NetBeans sees and uses to compile, etc.

I very much appreciate the links and suggestions you all have provided!  This Ubuntu community is the best!!

Tip, to check your Java setup

```

> java -version
> javac -version

```

---

### Post by jespdj on 2008-12-01
To select which Java is used by default on your system, use:
```
sudo update-alternatives --config java
```
You'll get a menu that lets you select which Java to use.

---

### Post by JimTDI on 2008-12-03
> **jespdj said:**
> To select which Java is used by default on your system, use:
```
sudo update-alternatives --config java
```
You'll get a menu that lets you select which Java to use.

Thank you for this!  Do I need to install the Java package first, and then this lets me choose from the Java versions installed on my box?

---

### Post by jamesstansell on 2008-12-03
> **JimTDI said:**
> Thank you for this!  Do I need to install the Java package first, and then this lets me choose from the Java versions installed on my box?

Yes, this switches which version is the default, pointed to from /usr/bin/java, usr/bin/javac, etc.

All the other versions are still usable by referencing them directly, as in

```
$ /usr/lib/jvm/java-6-sun/bin/java -version
```

---

### Post by JimTDI on 2008-12-04
> **jamesstansell said:**
> Yes, this switches which version is the default, pointed to from /usr/bin/java, usr/bin/javac, etc.

All the other versions are still usable by referencing them directly, as in

```
$ /usr/lib/jvm/java-6-sun/bin/java -version
```

May I ask if in your opinion it's better to load Sun Java 6 from the Ubuntu Repositories, or to download it directly from Sun's web site.  I think I'm gonna (re)install NetBeans right from Sun's site so I get the new version.  I say reinstall because I went from Ibex back to Heron due to screen resolution isues I was having.  Thanks for your input.  You and the other folks here are what make Ubuntu such a joy to run!

---

### Post by jamesstansell on 2008-12-04
> **JimTDI said:**
> May I ask if in your opinion it's better to load Sun Java 6 from the Ubuntu Repositories, or to download it directly from Sun's web site.  I think I'm gonna (re)install NetBeans right from Sun's site so I get the new version.  I say reinstall because I went from Ibex back to Heron due to screen resolution isues I was having.  Thanks for your input.  You and the other folks here are what make Ubuntu such a joy to run!

I generally prefer to use the ubuntu packages for sun-java.  The binaries are the same, but the packages are generally easier to manage.  (I also appreciate having the permissions automatically set so I don't accidentally modify the JDK installation.)

Last night I downloaded the 6u11 packages from jaunty and installed them on my hardy box.  Didn't run anything but applets, but they worked just fine.

---

### Post by JimTDI on 2008-12-05
> **jamesstansell said:**
> I generally prefer to use the ubuntu packages for sun-java.  The binaries are the same, but the packages are generally easier to manage.  (I also appreciate having the permissions automatically set so I don't accidentally modify the JDK installation.)

Last night I downloaded the 6u11 packages from jaunty and installed them on my hardy box.  Didn't run anything but applets, but they worked just fine.

Thanks!  I went ahead and installed the JDK 1.6 from the Ubuntu repos.  I wasn't sure what you meant "jaunty" but after a little searching, it appears that's the name of the next Ubuntu - so I'm thinking you were saying you used their repos, yes?  Thanks again!!

---

