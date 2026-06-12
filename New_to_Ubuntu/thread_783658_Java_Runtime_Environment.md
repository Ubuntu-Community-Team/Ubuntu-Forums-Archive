---
title: "Java Runtime Environment"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by spacefreak86 on 2008-05-05
So while trying to use some Java-based chat rooms online, they each spit back on Firefox that I need to download and install Java Runtime Environment, yet Synaptic and Add/Remove both claim that I have JRE and all of its plugins installed. Is there a way to get Firefox to see that they are in fact, installed?

---

### Post by glennric on 2008-05-05
Try typing
```
sudo update-alternatives --config java
```
in a terminal and make sure that there is a * by the java-6-sun version.

---

### Post by c4v3m4n on 2008-05-05
This link helped me get it installed and running.  Hope it helps you!

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/")

---

### Post by spacefreak86 on 2008-05-06
This is what I am getting:

```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-4.2
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java

```

Yet it still won't load in firefox.

---

### Post by spacefreak86 on 2008-05-08
After reformatting and re-installing Hardy, and JRE 1.6.0, I am still having this problem. Currently, the above code that someone gave me gives me this:

```
sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

I am also still having a problem with Wikipedia playing any form of media file. I suspect that it is the same problem.

Help?

---

### Post by spacefreak86 on 2008-05-08
> **c4v3m4n said:**
> This link helped me get it installed and running.  Hope it helps you!

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/")

I'm confused around the point where it says:

```
$ vi $HOME/.bash_profile
```

Append the following line:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin
```

How do I go about this one, it won't open. And unlike the previous line, I can't find this in the home folder as its a hidden file (and I don't know how to make those hidden files visible)..

---

### Post by jamesstansell on 2008-05-08
Instead of vi try gedit or kate

---

### Post by jamesstansell on 2008-05-08
> **spacefreak86 said:**
> So while trying to use some Java-based chat rooms online, they each spit back on Firefox that I need to download and install Java Runtime Environment, yet Synaptic and Add/Remove both claim that I have JRE and all of its plugins installed. Is there a way to get Firefox to see that they are in fact, installed?

Is Firefox still saying that the Java plugin is not installed?

Which version of Firefox is it?

---

### Post by jamesstansell on 2008-05-08
The JAVA_HOME variable is rarely needed, and never needed by Firefox.

---

### Post by spacefreak86 on 2008-05-08
Followed the instructions, using Firefox 2.0.0.14, still having problems. I tried the Java Verification site[http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp") and Firefox is STILL prompting me to say that JRE is not installed.

---

### Post by NathanB on 2008-05-08
From a (command line) terminal, type:
```
cd ~
sudo gedit .bashrc
```

Add the lines, then SAVE.

---

### Post by spacefreak86 on 2008-05-08
Done, only with Kate. And still no effect.

---

### Post by jamesstansell on 2008-05-08
> **spacefreak86 said:**
> Followed the instructions, using Firefox 2.0.0.14, still having problems. I tried the Java Verification site[http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp") and Firefox is STILL prompting me to say that JRE is not installed.

I think you're experiencing the Firefox 2 plugin registration bug

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309)

The instructions at [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309/comments/11](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309/comments/11) (about dpkg-reconfigure) may work for you.  Or, if you're not comfortable with them (I'm not completely comfortable myself) then a "ln -s" command may well work.

```
$ mkdir ~/.mozilla/plugins
$ ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins

```
Be sure that you have the sun-java6-jre package installed.

If the mkdir command gives you an error that the directory exists, you can just ignore it.  (But if it was me I'd want to know if there was anything else in that directory.)

The "ln -s" command links the .so file for the java plugin from your personal mozilla plugins directory.  There may be some point in the future where you want to remove that link, so don't forget that you put it there!

---

### Post by spacefreak86 on 2008-05-08
Awesome, I got the wikipedia bug fixed now! And I think the Java error is fixed.

How did you figure out what it was so that I can try to start figuring out these bugs on my own?

---

### Post by Trab on 2008-05-08
> **spacefreak86 said:**
> 
How did you figure out what it was so that I can try to start figuring out these bugs on my own?

I had the same bug going on. Its actually a really old bug, that appears to have resurfaced. (or rather, the fix for it resurfaced, the bug itself is new, as before it was just lack of a feature, now its a broken feature).

He knew (probably from past experience) that firefox was having trouble locating java, and thats why it would ask you to install it even when it was installed, so the fix is to point it to the correct file.

---

### Post by stchman on 2008-05-08
> **spacefreak86 said:**
> So while trying to use some Java-based chat rooms online, they each spit back on Firefox that I need to download and install Java Runtime Environment, yet Synaptic and Add/Remove both claim that I have JRE and all of its plugins installed. Is there a way to get Firefox to see that they are in fact, installed?

If you are running 32 bit Ubuntu and want to have 1.6 Java use the following.

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

The plugin package is for web browsers.

I have not figured out how to get Sun Java plugin to work with 64 bit.

---

### Post by jamesstansell on 2008-05-08
> **stchman said:**
> I have not figured out how to get Sun Java plugin to work with 64 bit.

Sun does not provide a 64bit browser plugin.  If you look at their bug parade they plan to release one in the first half of 2009.

You should try the icedtea-gcjwebplugin package, but be aware that there are many applets that it can't run.

(Although when I tried Runescape it seemed to be just fine, and I'm sure many other applets will also run perfectly well with it.)

You might also visit the 64-bit users forum for more suggestions.

---

