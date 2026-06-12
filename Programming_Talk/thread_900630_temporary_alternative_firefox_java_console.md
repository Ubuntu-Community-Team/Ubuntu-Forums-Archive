---
title: "temporary alternative firefox java console?"
date: 2008-08-25
forum: Programming Talk
---

### Post by bodselecta on 2008-08-25
I'm doing a small applet prototype at the moment using JApplet and also using J3D and everything works fine in eclipse's applet viewer, but the J3D code in the firefox applet plugin won't display

There's no exceptions thrown and I have no way of telling if anything else has gone wrong because there's no java console for firefox 3. (I've seen threads that say they can get it to work)
Now I've read allot of threads regarding applet problems with firefox 3, but applets work in firefox and j3d applets from other sites also work).

I have suns 1.5 jre installed (also 1.6 but my java path is set to 1.5).
about : plugins says I'm using the IceTea plugin.

I suspect that I should be using 1.6 for j3d, but the j3d panel runs fine in eclipse.

Is there any other way to see the IcedTea plugin's console output?

It's really annoying me that there's no console. I like using ubuntu but I sometimes spend too much time tinkering with things you should take as standard

---

### Post by Zugzwang on 2008-08-26
I might be wrong, but doesn't IcedTea belong to the OpenJDK? So it might be not the Sun JRE that is being used. Dunno how it works here, but I remember that in Windows, you can open up a console for a running applet by clicking on the Java Icon that appeared in the Task bar when running an applet.

---

### Post by tinny on 2008-08-26
> **bodselecta said:**
> I'm doing a small applet prototype at the moment using JApplet and also using J3D and everything works fine in eclipse's applet viewer, but the J3D code in the firefox applet plugin won't display

There's no exceptions thrown and I have no way of telling if anything else has gone wrong because there's no java console for firefox 3. (I've seen threads that say they can get it to work)
Now I've read allot of threads regarding applet problems with firefox 3, but applets work in firefox and j3d applets from other sites also work).

I have suns 1.5 jre installed (also 1.6 but my java path is set to 1.5).
about : plugins says I'm using the IceTea plugin.

I suspect that I should be using 1.6 for j3d, but the j3d panel runs fine in eclipse.

Is there any other way to see the IcedTea plugin's console output?

It's really annoying me that there's no console. I like using ubuntu but I sometimes spend too much time tinkering with things you should take as standard

IcedTea is part of OpenJDK.

There may be a few things going on here. First off, are you using a 64bit version of Ubuntu?

If you have a 32bit version, have you installed sun-java6-plugin ????

```

sudo apt-get install sun-java6-plugin

```

Whats the output of:
```

java -version
javac -version

```

---

### Post by bodselecta on 2008-08-26
This is where I'm getting slightly lost re the IcedTea plugin and firefox.
I'd thought it was the most likely problem, but I can't work out how to change the plugin to a sun java 5 jre in firefox.
I've got java 5 installed in java home as I'm developing mainly in java 5.
```

java -version
java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Server VM (build 1.5.0_15-b04, mixed mode)


javac -version
javac 1.5.0_15


```
 

And it's 32-bit hardy heron installed.

I'd googled a few pages and some said to remove the icedtea plugin from firefox, but replace it with what? I've disabled the plugin in firefox but am I able to point firefox to the right plugin?
Or will I have to apt-get java 5 again and will that install the plugin location in firefox?
(I've also got the j3d jars on my system classpath, and LD_LIBRARY for j3d. It might just be classfile incompatibility between j3d and open jdk, but without the console I can't tell!!)

Thanks for the help....






> **tinny said:**
> IcedTea is part of OpenJDK.

There may be a few things going on here. First off, are you using a 64bit version of Ubuntu?

If you have a 32bit version, have you installed sun-java6-plugin ????

```

sudo apt-get install sun-java6-plugin

```

Whats the output of:
```

java -version
javac -version

```

---

### Post by bodselecta on 2008-08-26
I found something on launchpad that might be something similar
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/173966](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/173966)

I've tried adding the symlinks and updating the libjavaplugin in about:config in firefox, but not much luck.

But there's so many comments, allot of them probably don't apply.

e.g. ~/.mozilla/plugins doesn't exist

I didn't think it'd be so difficult (and annoying) to change the java plugin!

---

### Post by tinny on 2008-08-26
This is what id try if I where you (brute force!).

Remove ALL java installs!

To check that every thing is uninstalled
```

sudo update-alternatives --config java

```

Now install Sun Java (You really only need this on 32 bit Ubuntu, dont install OpenJDK, it sucks right now)

Install all of Java 5
```

sudo apt-get sun-java5*

```

And cross your fingers :)

---

### Post by bodselecta on 2008-08-26
this'll be the last of my tinkering for a few days, but just noticed that java 1.5.0_15-b04 is now showing up in firefox addons, and about: plugins has the correct libjavaplugin_oji.so
But couldn't disable IcedTea without disabling java 5. 

So I apt-get removed IcedTea and now suns java 5 and 6 are showing. The J3D applet isn't showing yet but other jpanels in my applet works.
No console yet either though I followed the instructions on [http://www.java.com/en/download/help/5000010500.xml](http://www.java.com/en/download/help/5000010500.xml) and unzipped the ffjcext.zip.
'java console' is now showing as a menu item in firefox>tools but it's greyed out..

Time out !!

---

### Post by tinny on 2008-08-26
> **bodselecta said:**
> this'll be the last of my tinkering for a few days, but just noticed that java 1.5.0_15-b04 is now showing up in firefox addons, and about: plugins has the correct libjavaplugin_oji.so
But couldn't disable IcedTea without disabling java 5. 

So I apt-get removed IcedTea and now suns java 5 and 6 are showing. The J3D applet isn't showing yet but other jpanels in my applet works.
No console yet either though I followed the instructions on [http://www.java.com/en/download/help/5000010500.xml](http://www.java.com/en/download/help/5000010500.xml) and unzipped the ffjcext.zip.
'java console' is now showing as a menu item in firefox>tools but it's greyed out..

Time out !!

I have the Java console in Application>System Tools>Sun Java 6 Console (something like that)

Im running Sun Java 6

---

### Post by bodselecta on 2008-08-28
Managed to get this working eventually, thanks tinny for the replies.

I did a few things, probably some unnecessary...
When I work out what the right ones were, I'll post an update.

Java3D is working fine in the browser now too, the console menu items in firefox sometimes disable though the console runs fine.
Thanks

---

