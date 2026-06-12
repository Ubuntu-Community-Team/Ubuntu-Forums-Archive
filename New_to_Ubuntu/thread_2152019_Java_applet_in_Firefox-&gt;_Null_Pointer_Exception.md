---
title: "Java applet in Firefox-&gt; Null Pointer Exception"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by churka on 2013-06-06
The issue is certain java applets would not load on Ubuntu but on  Windows- on the same computer, with the same browsers, and the same  oracle jdk/JRE 7u21. I have dual boot ubuntu/winxp.

I have tried and tested OpenJDK-java6/7, Oracle JRE Java-7 (update 21). All of these together, and when didnt work, seperately each of them, in Firefox/Opera/Chrom/ium .

One sample applets is Security/stock chart Applet at the bottom of the page at url---
[http://indiabulls.com/securities/research/techanalysis/tech_analysis.aspx](http://indiabulls.com/securities/research/techanalysis/tech_analysis.aspx)

Applet here loads smoothly on windows but not in ubuntu.
I have also tried few other applets on web- some of them gave the same error, some didnt.

I have tried everything from clearing cache to reinstalling whole system but it doesnt disappear. So I believe there is error in applet code. I also read so here -> [http://www.javacoffeebreak.com/articles/greyboxapplets/](http://www.javacoffeebreak.com/articles/greyboxapplets/)  

But how could it be so as I am using same version of JavaJRE on windows /ubuntu, on  a dual boot computer and on a dual boot netbook. 

It has been just 2 weeks that I have been on Ubuntu and am planning to use Ubuntu 90% of the time.It is difficult for me to solve this issue on my own.
Is there any work around ? What can I do to sort it out?

---

### Post by slickymaster on 2013-06-06
After installing Java, did you enabled it in your browser?

If not, that could be the issue. To configure the Java Plugin follow these steps:
[LIST=1]
[*]Exit Firefox browser if it is already running.
[*]Uninstall any previous installations of Java Plugin.
[*]Create a symbolic link to the libnpjp2.so file in the browser plugins directory
[/LIST]
[INDENT]Go to the plugins sub-directory under the Firefox installation directory```
cd Firefox_installation_directory/plugins
```[/INDENT]
[INDENT]Create the symbolic link```
ln -s Java_installation_directory/lib/i386/libnpjp2.so
```[/INDENT]

---

### Post by churka on 2013-06-06
Thanks for quick reply!;)
Java was enabled. Ceated symbolic link but the error pesists. Will it help if i install icedtea-7-plugin with existing oracle-java-7-u21?
There is no other version of java or java plugin at the moment on my computer. only oracle-7-u21/plugin

PS: Makes me wonder why "platform independent" java is woking on windows-xp but not in Ubuntu. I am using dual boot computers - AcerAspire1 /CompaqHP AMD Athlon2+ Ghz

---

### Post by slickymaster on 2013-06-07
> **churka said:**
> ... Will it help if i install icedtea-7-plugin with existing oracle-java-7-u21?
There is no other version of java or java plugin at the moment on my computer. only oracle-7-u21/plugin...

Well, you could try it, but don't hold too many expectations.

Eventually you may be faced with interference between that plugin and Oracle Java.

---

### Post by churka on 2013-06-07
thanks for advice!
This particular applet  runs on windows but on ubuntu - so i will assume that linux JRE is different than windows JRE.

Many other applets are running smoothly with oracle-java-7u21. 

May be RPM based linux distro will run this particular applet. i will wait for that.):P

---

### Post by slickymaster on 2013-06-07
> **churka said:**
> ... This particular applet  runs on windows but on ubuntu - so i will assume that linux JRE is different than windows JRE.

Many other applets are running smoothly with oracle-java-7u21. ...

IMO the problem you're facing relies more in the applet itself than on the JRE.

---

### Post by churka on 2013-06-08
> **slickymaster said:**
> IMO the problem you're facing relies more in the applet itself than on the JRE.

Couldnt agree more. Thats what I have concluded and going to write to those guys providing that applet for use. 

In the mean time I will try one of rpm-based linux distro to see if applet error is handled by them as oracle-JRE on windows does.

ubuntu (debian), OpenSuse (rpm) and Windows xp- each of these 3 have sepeartely available JRE. 
rpm base oracle JRE might work for that faulty applet :)

---

### Post by slickymaster on 2013-06-08
> **churka said:**
> ... In the mean time I will try one of rpm-based linux distro to see if applet error is handled by them as oracle-JRE on windows does.

ubuntu (debian), OpenSuse (rpm) and Windows xp- each of these 3 have sepeartely available JRE. 
rpm base oracle JRE might work for that faulty applet :)

Since you're intending to go rpm, I would advise you CentOS, I've tried the minimal install of 6.4 version and and I was very impressed with it. I strongly recommend it.

---

### Post by churka on 2013-06-13
> **slickymaster said:**
> Since you're intending to go rpm, I would  advise you CentOS, I've tried the minimal install of 6.4 version and and  I was very impressed with it. I strongly recommend it.

Tried CentOS 6.4. really neat . no fuss. no tantrums. works smooth. On top of everything, its Enterprise Edition and FREE. Its in my * list now!

that java applet wouldnt run here in this rpm linux/centOS either. certainly a faulty applet. have already written to applet-guys, they hav to fix their applet class/java file.

Thanks again!

---

### Post by 1clue on 2013-06-13
> **churka said:**
> Thanks for quick reply!;)
Java was enabled. Ceated symbolic link but the error pesists. Will it help if i install icedtea-7-plugin with existing oracle-java-7-u21?
There is no other version of java or java plugin at the moment on my computer. only oracle-7-u21/plugin

PS: Makes me wonder why "platform independent" java is woking on windows-xp but not in Ubuntu. I am using dual boot computers - AcerAspire1 /CompaqHP AMD Athlon2+ Ghz

Don't blame Java or Ubuntu.  I'm running fine with oracle Java on xubuntu.  I agree with other posters -- this is a problem with the specific applet.

---

### Post by churka on 2013-06-20
> **1clue said:**
> Don't blame Java or Ubuntu.  I'm running fine with oracle Java on xubuntu.  I agree with other posters -- this is a problem with the specific applet.

Now I am in contact with folks maintaining that applet in order to get it rectified. They are working on it now!

I love Ubuntu Community and Ubuntu!!! Every problem is heard here and taken care of, given advice to. Its awesome!!!

Thanks for the comment :)

---

