---
title: "java not reconizing path to desktop"
date: 2011-07-27
forum: Programming Talk
---

### Post by &lt;(-.-)&gt; on 2011-07-27
im writing a program to move files in java from the desktop to another .jar file.  When i use /home/user/Desktop as my path it doesn't recognize the path, but when i use my own system username it works just fine.  How can i fix this?

---

### Post by ziekfiguur on 2011-07-27
you can use System.getenv() to find the username that you have to use, or you can replace /home/user by a ~

---

### Post by stchman on 2011-07-27
A way to get to your Desktop in Java:

```

String userDesktop = System.getProperty( "user.home" ) + File.separator + "Desktop";

```

This will display only the currently logged in users desktop.

---

### Post by &lt;(-.-)&gt; on 2011-07-29
stchman does your method of finding the desktop also work on windows and mac because i need this program to be cross platform

---

### Post by stchman on 2011-07-30
> **<(-.-)> said:**
> stchman does your method of finding the desktop also work on windows and mac because i need this program to be cross platform

AFAIK.

Desktop is the name of the desktop on my Windows(XP and Vista) and Linux machines.  If Desktop is used in OS X, then it is golden.

---

### Post by Wim Sturkenboom on 2011-07-30
You can always try to find the OS and version. Never tried it in java, but in Tcl it's possible. Set the correct path based on the result.

---

### Post by &lt;(-.-)&gt; on 2011-07-30
Thanks pretty much I'm just trying to get the current username out of this code so I can input it into a couple of paths not really trying to go to the desktop with final product. And finding the os you look for the index of win, nux, ect. In the name.os file

---

### Post by stchman on 2011-08-02
> **<(-.-)> said:**
> Thanks pretty much I'm just trying to get the current username out of this code so I can input it into a couple of paths not really trying to go to the desktop with final product. And finding the os you look for the index of win, nux, ect. In the name.os file

If you wanted the users name easy:

```

String userName = System.getProperty( "user.name" );

```

Visit the System portion of the Java API.

[http://download.oracle.com/javase/6/docs/api/java/lang/System.html](http://download.oracle.com/javase/6/docs/api/java/lang/System.html)

---

