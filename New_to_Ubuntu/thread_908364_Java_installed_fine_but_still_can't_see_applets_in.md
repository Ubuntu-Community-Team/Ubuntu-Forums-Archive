---
title: "Java installed fine but still can't see applets in Firefox"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by nathanscottdaniels on 2008-09-02
I am so sick of stuff not working in this OS!  ](*,)I have 
[I]sun-java6-bin
sun-java6-jre
sun-java6-doc
sun-java6-demo
sun-java6-jdk
and sun-java6-source[/I]
packages installed (which are every package with the work java6 in the title!) and I can compile and run Java programs with ease but I still can't see applets in Firefox.  They all say I need Java installed and turned on (it is both!).  I know in Vista if this happens all you have to do is copy a file to FF's plugin folder, and indeed many Ubuntu users have done the same thing, but that isn't the case here as I don't have such a file in my java directory.

What am I doing wrong?:confused:

---

### Post by aloshbennett on 2008-09-02
My! So many packages installed and you missed sun-java6-plugin!

I am not sure if this will fix your problem, but is worth giving a try. In the older versions we had to copy a lib.so into the plugins folder, but those days are gone.

You can test using this site:
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

(infact, it would install the plugin if you follow the link)

---

### Post by nathanscottdaniels on 2008-09-02
> **aloshbennett said:**
> My! So many packages installed and you missed sun-java6-plugin!

I am not sure if this will fix your problem, but is worth giving a try. In the older versions we had to copy a lib.so into the plugins folder, but those days are gone.

You can test using this site:
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

(infact, it would install the plugin if you follow the link)


This is what I get when I try to install the package:

```
nathan@nathan-laptop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
nathan@nathan-laptop:~$ 

```

Going to the page aforementioned, a bar appeared in FF saying I needed to install a plugin but it failed to do it for me and instead just sent me to java.com.

---

### Post by aloshbennett on 2008-09-03
> alosh@zion:~$ apt-cache show sun-java6-plugin
Package: sun-java6-plugin
Priority: optional
Section: multiverse/web


This is a problem with repositories then. Do you have multiverse enabled? Are you on ubuntu 32 bit or 64 bit?

---

### Post by nathanscottdaniels on 2008-09-03
Uni- and Multiverse are enabled.  I am running 64-Bit.

---

### Post by philinux on 2008-09-03
For 64 bit Install the icedtea-gcjwebplugin

---

### Post by gandaran on 2008-09-03
maybe it's better you remove all sun-java6 packages (there is no sun-java 64-bits plugin for firefox) and install the open-java and icedtea plugin for firefox

---

### Post by nathanscottdaniels on 2008-09-04
Open JDK sucks.  It has no benefits over Sun's original version and it doesn't support compilation via the Tools.jar file which I need for Dr. Java.

Icedtea made the top 4 clocks on this page work (sporadically) but not the bottom 4.
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)
What does that mean?  Is that the limited nature of homemade plugins?

Being a CS student specializing in programing, it is important that I am able to test my applets on my laptop!

---

### Post by philinux on 2008-09-04
> **nathanscottdaniels said:**
> Open JDK sucks.  It has no benefits over Sun's original version and it doesn't support compilation via the Tools.jar file which I need for Dr. Java.

Icedtea made the top 4 clocks on this page work (sporadically) but not the bottom 4.
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)
What does that mean?  Is that the limited nature of homemade plugins?

Being a CS student specializing in programing, it is important that I am able to test my applets on my laptop!

I get same result. So if your specialising in programming have a look at the the above links page source. Maybe a clue to why icedtea not displaying bottom 4 applets.

---

### Post by speck1966 on 2008-09-04
I had the same problem as I am new to ubuntu. What I did was to go to the search box in my firefox browser and type in jre for ubuntu. It took me to a page where they told me how to download and install jre6. Also they said in order for it to work after it is installed, you must reboot your ubuntu system. I hope this helps.

---

### Post by philinux on 2008-09-04
you can install jre 6 from synaptic. However on 64bit there is no jre6 browser plugin.

---

