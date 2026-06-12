---
title: "Huge Eclipse (Java) problem while writing code"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by m.pleines on 2014-01-08
Hello Guys!

During my course of studies I came to a point where I have to use an Ubuntu Server 32bit setup.

On my clean setup I just installed the Ubuntu-Desktop, the JDK:

```
[COLOR=#666666][/COLOR][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get install**[/COLOR] openjdk-[COLOR=#000000]7[/COLOR]-jdk
```

and Eclipse:

```
sudo apt-get install eclipse
```

Starting Eclipse works just fine. When it comes to write a java class in Eclipse nearly every single line of my code gets an Error mark to the left.
Especially the regular class definition at the head of the class is marked as wrong.

I reinstalled Ubuntu and the same issues remain.

Since my program won't run on an applet anywhere, I have to use Eclipse to run the code for getting credit points.



I'm thankful for any help!!

---

### Post by hoopia on 2014-01-08
Can you post the exact errors here? Which java version gets returned when you run *java -version* in Terminal?

---

### Post by m.pleines on 2014-01-08
I will return to the Ubuntu Server PC tomorrow, I will post some Screenshots then.

As far as I know, the system was able to run Java applets online.

---

### Post by tgalati4 on 2014-01-08
I'm confused.  You installed Ubuntu server and then installed the desktop?  Perhaps you are missing some pieces.  Why don't you perform a clean desktop install and then install java and eclipse?

There's also a lot of pieces to the JDK:

```
apt-cache search jdk
```

---

