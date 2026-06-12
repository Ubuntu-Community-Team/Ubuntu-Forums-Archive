---
title: "How to: Get Java and Minefield (Firefox 3) playing together."
date: 2007-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by eznet on 2007-11-25
I just wanted to take the time to type up instructions on how I got Minefield and Java to play with each other on my install.  I searched for days trying to find a solution for the issues I was having and could find none, so hopefully this will help others in the same boat as me.  Not everyone will have this problem, only if  you have Java installed outside of /lib/java/ . A bit of system info: I am running Gutsy Gibbon (7.10) x86 .

Obviously, this is at your risk.  Minefield is not the official release of Firefox 3 and may very well have bugs and instabilitity issue.  If you are like me, then you likely do not care that apocalyptic calamity may ensue from your usage of Minefield (aka  future Firefox 3).  Just know that in proceeding, you are accepting full responsibility for your actions.

Obviously in order to follow these instructions you need to have [Minefield]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/") installed and up and running as well as Java.  Java can be installed many ways and so I will not go into that too much here, but if you wish you may install it via synaptic or you can install Java 6 via self-extracting bin available at the [Java Sun website]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80").

Here is what I found to be the easiest way to get things working for me.
[LIST]
[*]-Open up Minefield
[*]-Go into config : In address bar enter “about:config” and click 'I'll be careful, I promise”
[*]-Filter the display to “java” : Enter “java” in the filter blank
[*]-First go to key 'java.default_java_location_others' and change the value from '/usr/java/' to your install directory – for me it is “/usr/lib/jvm”... you can find out your by entering  “sudo update-alternatives --config java” at the console... just make sure you don't mess anything up...  After you enter the location of your java install as the Value press 'ok'
[*]-next change the name of the plugin that Minefield is looking for... by default Minefield looks for “javaplugin_oji” but in my case I needed it to find “libjavaplugin_oji”.  To do this, simply double click the key named “java.java_plugin_library_name” and change its value from “javaplugin_oji” to “libjavaplugin_oji” then click 'ok'
[*]-I am sure that a browser restart is in order here, though it wasn't needed for me... I simply headed over to [Sun]("http://www.java.com/en/download/installed.jsp") to verify the install and all is working great!
[/LIST]
I hope this helps and this it does not further aid in confusing the already confused... If you have any questions of suggestions or find any of this to be flat out wrong or completely offensive then please drop me a line and I will do my best to change it or explain it.  I am but a mere noob and this is my offering.

Matt

---

### Post by Githlar on 2007-12-05
This doesn't seem to work in the Firefox 3.0b1 release. I downloaded the installer from Mozilla and installed it under ~/Firefox3. I changed the values in about:config, but it still doesn't want to run Java applets. I tried using the Java package from the repository and the Sun installer. Neither worked.

---

### Post by Githlar on 2007-12-05
I figured it out. A [page](http://plugindoc.mozdev.org/linux.html#Java) linked in about:plugins says this:
> 
Java Runtime Environment
Version: 1.4.2 or later
SeaMonkey 1.0: Supported
Firefox 2.0: Supported
FAQ: Java FAQ

   1. Install Java Runtime Environment.
   2. Make a symbolic link to libjavaplugin_oji.so in your Mozilla Plugins directory. Use the copy located in the plugin/i386/ns7 directory of JRE 5.0 or later, or plugin/i386/ns610-gcc32 if you are using JRE 1.4.2.

Important! Do not copy the plugin to your plugins directory. If you do, Mozilla will crash any time you attempt to view a page containing a Java applet.
Note: The instructions listed here are for the Sun Java Runtime Environment. Other Java Runtime Environments, such as those available from IBM and the Blackdown project, can also be used.

Here's how I did it. cd over to your Firefox 3.0 directory. cd into the plugins directory and enter this:

> myuser@room:~/firefox/plugins$ ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

---

### Post by reacocard on 2008-02-01
> **Githlar said:**
> I figured it out. A [page](http://plugindoc.mozdev.org/linux.html#Java) linked in about:plugins says this:


Here's how I did it. cd over to your Firefox 3.0 directory. cd into the plugins directory and enter this:

thanks! worked perfectly for me in beta 2.

---

### Post by pingpongboss on 2008-02-02
> **reacocard said:**
> thanks! worked perfectly for me in beta 2.

worked for me too. thanks!

---

### Post by Dencrypt on 2008-02-24
My Firefox 3 Beta 3 just crashes whenever I try to follow this, and load any applet. Can't really figure out what's wrong. I have two different Java versions installed but I am using 1.4 by default.

Could it have something to do with that I am running Kubuntu Hardy Alpha 4? Or x64?

---

### Post by Dencrypt on 2008-02-24
Nevermind. Just updated to java6 and it works fine.

---

### Post by shreg on 2008-04-11
[QUOTE=Githlar]
Here's how I did it. cd over to your Firefox 3.0 directory. cd into the plugins directory and enter this:

Quote:
myuser@room:~/firefox/plugins$ ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so 
[/QUOTE]

This was the way for me on ubuntu 7.10 using Minefield (Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9pre) Gecko/2008041004 Minefield/3.0pre).

If you did try the first way do not forget to but everything back to default. Otherwise it does not work.

You can easily test your java here: [http://www.javatester.org/](http://www.javatester.org/)

Thanks for the tip.

---

### Post by Bootlace on 2008-05-08
Thank you eznet, well written, easy to understand, and it worked for me! I think you saved my sanity, more power to you.

---

### Post by fmouse on 2009-02-16
> **eznet said:**
> I just wanted to take the time to type up instructions on how I got Minefield and Java to play with each other on my install.  I searched for days trying to find a solution for the issues I was having and could find none, so hopefully this will help others in the same boat as me.

Yay!!  Thank you, Matt.  Getting java to play nice with mozilla family browsers is always a hassle, and with Minefield 3.0.5 (Gentoo Linux) it was especially so.  I tried symlinking just about every libjavaplugin_oji.so on my system (and there are almost a dozen of them) into my plugins directory and all I got was either crashes or Java NullPointerException errors telling me it couldn't find the class file which was right there under its nose!

Your solution worked out-of-the-box on this Gentoo desktop system - first time!

Many Thanks :D

Lindsay

---

### Post by khughitt on 2009-12-01
Anyone able to get Java working in Minefield 3.7 on Karmic?

---

### Post by weliot on 2009-12-15
I have got java working in Minefield by soft-linking to the new java plugin libnpjp2.so as detailed in :

[http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825](http://forums.mozillazine.org/viewtopic.php?f=23&t=1576825)

For me, libnpjp2.so is in /usr/java/jre1.6.0_17/lib/i386

This also gets java working in Chromium/Chrome.

---

