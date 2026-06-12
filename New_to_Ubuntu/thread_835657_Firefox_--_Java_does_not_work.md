---
title: "Firefox -- Java does not work"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by zaphod_fl on 2008-06-20
Using Hardy Heron AMD64 on Core2Duo with 4GB memory (first time trying 64 bit edition...)

Nothing Java works.  I fear I have really screwed it up now as I have been all over trying many different things.  Even installed Sun's version of Java.  

When I go to [http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3) I get "Start:applet not initialized." in the lower left corner.  Nothing java works in the browser.  

Any thoughts?

---

### Post by avtolle on 2008-06-20
From the 64 bit user's forum: [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)
The problem is that for the Sun Java, there is not yet a 64 bit plugin for FF, e.g., so to use 64 bit, one needs to use the open-source java as outlined in the link (which was f/k/a "iced tea").

EDIT: If using Sun Java is highly important to you, you would need to install the 32 bit 8.04 on your system, and proceed accordingly.

---

### Post by dmedell on 2008-06-22
I was having similar issues. My wife couldn't play her online games that she oh so loves.....

any way I was d-loading everything and apt-get updating everything with no positive results.

I happened across this link on mozilla's help for java section
[http://javatester.org/version.html]("http://javatester.org/version.html")

any way I d-loaded what it suggested and it works.

Try it out and post if it worked for you.:cool:

---

### Post by tinny on 2008-06-22
What is the output of...

```

java -version

```

---

### Post by dmedell on 2008-06-24
~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

---

### Post by tinny on 2008-06-24
The games / java stuff you are all talking about are Java Applets right?

Make sure you have java enabled in firefox.

Tools > Options > Content > Enable Java (make sure its checked)

Also, what is the text displayed to you when you open Tools > Java Console.

Should look something like this:

```

Java Plug-in 1.6.0_05
Using JRE version 1.6.0_05 Java HotSpot(TM) Client VM
User home directory = <HOME DIR>


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

en_US: /res/dldir_en.res


```

---

