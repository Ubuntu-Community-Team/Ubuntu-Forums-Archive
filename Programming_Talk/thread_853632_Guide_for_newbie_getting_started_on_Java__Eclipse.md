---
title: "Guide for newbie getting started on Java / Eclipse"
date: 2008-07-08
forum: Programming Talk
---

### Post by TonyGould on 2008-07-08
Hi,

I'm an experienced C++ programmer on Windows (and some on NeXT with objective C in the 90s but that's another story!). I've done a Java training course covering Java language + Spring, and want to start developing in Java on Eclipse on Ubuntu. Before I installed 8.04 I had a go at installing Eclipse and didn't do very well, so are there any real-ly sim-ple ins-struct-tions that I could foll-ow? :)

For example, do I go via Synaptic? Do I install a JRE? Anything else?

By the way, it looks like Europa JEE would be the one for me to go for, partly because of Spring, partly because it fits in well with what some people use at work. [http://www.eclipse.org/europa](http://www.eclipse.org/europa). To start off with however I'll probably play around with some simple-as-possible rich client stuff, single-form applications and the like (do people still use swing?), and spring too. Eventually I'd like to be able to try some C++ programming, but that's not important to start with.

I really don't know where to start. Any pointers would be appreciated!

Tony

---

### Post by HotCupOfJava on 2008-07-08
I would use Synaptic. It will automatically pull in all of the related packages you need in addition to the Eclipse packages. It can save you ALOT of headache. It will even set the classpath for you. (I'll say for the record that I use Netbeans instead of Eclipse, though. I don't have a problem with Eclipse, I just haven't used it).

---

### Post by TonyGould on 2008-07-08
> **HotCupOfJava said:**
> I would use Synaptic. It will automatically pull in all of the related packages you need in addition to the Eclipse packages. It can save you ALOT of headache. It will even set the classpath for you. (I'll say for the record that I use Netbeans instead of Eclipse, though. I don't have a problem with Eclipse, I just haven't used it).

thanks, but isn't there a problem in that it uses the Gnu Java Runtime which is v slow? And it looks like the synaptic packages are for Eclipse 3.2, which is 2 years old (it looks like Eclipse releases in June so there is a new version just out)

Tony.

---

### Post by tinny on 2008-07-08
> 
but isn't there a problem in that it uses the Gnu Java Runtime which is v slow?

um... try doesn't work.

> **TonyGould said:**
> thanks, but isn't there a problem in that it uses the Gnu Java Runtime which is v slow? And it looks like the synaptic packages are for Eclipse 3.2, which is 2 years old (it looks like Eclipse releases in June so there is a new version just out)

Tony.

Go for the synaptic package manager version of Eclipse. The chances are that you wont even notice the differences between this version and the latest.

Also, install the Sun JDK first!

```

sudo apt-get install sun-java6-jdk

```

Have you considered using Netbeans? I think it would be a little easier to start with (It comes bundled with everything you need).

CptPicard found this nice Netbeans Spring tutorial the other day.

[http://www.netbeans.org/kb/61/web/quickstart-webapps-spring.html]("http://www.netbeans.org/kb/61/web/quickstart-webapps-spring.html")

---

### Post by HotCupOfJava on 2008-07-08
Well, once Eclipse is installed you should be able to update it easily enough.....

---

### Post by tinny on 2008-07-08
> **HotCupOfJava said:**
> Well, once Eclipse is installed you should be able to update it easily enough.....

True. Good spotting once again :)

Window > Preferences > Java > Installed JRE's

But if you want to run applications outside of Eclipse you will need to be aware of this.

---

### Post by kavon89 on 2008-07-08
I'm gonna go with tinny and say NetBeans is a nice IDE.

---

### Post by TonyGould on 2008-07-09
thanks guys for all that!

I'm going to have to think carefully about what to do, as I really want to learn the IDE at home so that I can be up to speed with Eclipse 3.3 at home.

Tony.

---

### Post by TonyGould on 2008-07-11
> **TonyGould said:**
> I'm going to have to think carefully about what to do, as I really want to learn the IDE at home so that I can be up to speed with Eclipse 3.3 at home.

In the end I decided to get latest eclipse, primarily for compatibility with work. It was pretty straigtforward after finding some helpful posts on people's blogs. In case it helps anyone, this is what I did.

Installed sun-java5-jre, sun-java6-jdk, sun-java6-jre (using Synaptic or "sudo apt-get install"). These get installed under  /usr/lib/jvm. Used "sudo update-alternatives --config java" and added "export JAVA_HOME=/usr/lib/jvm/java-6-sun" to .bashrc to select java6 as default JVM.

Got lastest Eclipse and installed it.
```

wget http://ganymede-mirror1.eclipse.org/technology/epp/downloads/release/ganymede/R/eclipse-jee-ganymede-linux-gtk.tar.gz
tar xvf eclipse-jee-ganymede-linux-gtk.tar.gz
sudo mv eclipse /opt
cd /usr/bin
sudo ln -s /opt/eclipse/eclipse
/opt/eclipse/eclipse -clean

```

The last line sets up eclipse according to this post, [http://www.ubuntued.com/?p=40](http://www.ubuntued.com/?p=40), which also covers how to set up a menu shortcut. I prefer to run eclipse with the Java 5 JRE, as that's what's recommended
```

eclipse -vm /usr/lib/jvm/java-1.5.0-sun/jre/bin

```
so I went into the ubuntu menu editor and added this option. You can then go into the eclipse options and have it build its programs against the Java 6 SDK.

Tony.

---

### Post by arthurven on 2008-07-17
:)Thanks.I followed these steps, it's done!

---

### Post by tinny on 2008-07-17
Those are good instructions TonyGould, well done.

---

