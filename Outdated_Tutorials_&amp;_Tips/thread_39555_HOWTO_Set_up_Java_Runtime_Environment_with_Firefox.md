---
title: "HOWTO: Set up Java Runtime Environment with Firefox autopackage"
date: 2005-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by rykel on 2005-06-05
Title: How to set up Java Runtime Environment (JRE) with Firefox autopackage in Ubuntu Hoary

Adapted from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)


Hi there,

If you had removed the Ubuntu Firefox 1.0.3 and installed the Firefox 1.0.4 autopackage, you will inevitably wonder how you can get your Java, Flash and MPlayer plugins to work with your spanking new browser.

This HOWTO is designed to show you how simple it is to do precisely that.

Thanks to Chua at the Unofficial Ubuntu Guide for his original instructions.


The JRE you might have installed earlier following instructions from the Unofficial Ubuntu Guide cannot be used with the Firefox autopackage, but the reason is basic. The Ubuntu Firefox resides in the "/usr/lib/mozilla-firefox" folder, while the Firefox autopackage stays in "/usr/lib/firefox" folder.

You can download the LATEST Firefox autopackage here and install it, if you have not done so already. Thanks to Taj Morton for making the autopackage available.

Firefox autopackages:
[http://www.wildgardenseed.com/Taj/autopackage](http://www.wildgardenseed.com/Taj/autopackage)


HOW TO SETUP JRE AFTER INSTALLING FIREFOX AUTOPACKAGE:

Download the Java Manual Installer from java.com. (jre-1_5_0_02-linux-i586.bin)

Save to your Desktop.

Open up a terminal and issue the following commands:
_________________________________________________________________

cd ~/Desktop

sudo ./jre-1_5_0_02-linux-i586.bin

sudo mkdir /usr/java

sudo mv jre1.5.0_02/ /usr/java/

sudo chown -R root:root /usr/java/jre1.5.0_02/

sudo ln -fs /usr/java/jre1.5.0_02/bin/java /usr/bin/java

sudo ln -fs /usr/java/jre1.5.0_02/bin/java_vm /usr/bin/java_vm

sudo ln -fs /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/

sudo ln -fs /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/

java -version
_________________________________________________________________

Instructions for Flash and MPlayer are similar, but a really FAST way to do it, is to simply copy the files in the "/usr/lib/mozilla-firefox/plugins" folder to "/usr/lib/firefox/plugins".

I hope that soon, even Flash and MPlayer will come as autopackages, and that way, they will install their plugins automatically into the correct and relevant folders when they "check for Firefox plugin folder".



Best Regards,

Rykel
Singapore

---

### Post by sloopjc on 2007-01-31
Here's a note for anyone who upgraded their Firefox browser on Ubuntu Dapper and found that their Java Runtime Environment didn't work. Do you have the Mozilla browser? Does JRE work OK? If so, copy: "libjavaplugin.so" from folder: "/usr/lib/mozilla/plugins" and paste in folder: "/usr/share/firefox/plugins".

---

### Post by rykel on 2007-02-01
Hi,

It is amazing how fast the world of Linux moves!

Anyway, here is an updated and even simpler way of installing Java Runtime Environment in the official Firefox (autopackage) on Dapper... other than Step 2, all the rest can be done in GNOME.

[INDENT]1.   Install Firefox as User, not Root.

2.   Download and unpack the latest Java Runtime Environment in your Home directory. (No need for Root password - simply unzip the file in a Terminal.)

3.   Go to the Java Plugins folder (~/jre1.5.0_10/plugin/i386/ns7) that has been created and using GNOME, right-click and "Make Link" to "libjavaplugin_oji.so".

4.   Drag and drop the newly created Link to "~/.mozilla/plugins".[/INDENT]

I have tested on Java.com and DBS.com... it works!

Hope that helps.

---

### Post by johncw on 2007-02-03
Why do you associate the Mozilla plugins directory with the Firefox browser? They're separate browsers on Ubuntu Dapper, with their own plugins folders. Creating a link to the **usr/share/firefox/plugins** folder was how I got my updated Firefox browser working with Java Runtime Environment.

---

### Post by rykel on 2007-02-04
> **johncw said:**
> Why do you associate the Mozilla plugins directory with the Firefox browser? They're separate browsers on Ubuntu Dapper, with their own plugins folders. Creating a link to the **usr/share/firefox/plugins** folder was how I got my updated Firefox browser working with Java Runtime Environment.

I am not sure why it works either way too... whatever the case, I guess the fact that the JRE works could be attributed to the reality that it is independent of the browser. ie. it does not matter which plugins folder of whichever browser (it possible can even be an Opera plugins folder) the JRE is linked, it will work nonetheless.

Most important of all, IT JUST WORKS (tm).

:guitar:

---

### Post by johncw on 2007-02-04
> **rykel said:**
> ...it does not matter which plugins folder of whichever browser the JRE is linked, it will work nonetheless.


That's not a very clear statement. It suggests that a link in one browser plugin folder might work for a different browser that doesn't have a link to JRE in its own specific plugins folder. To say, "*it will work nonetheless*" is inspiring though.

---

### Post by rykel on 2007-02-04
> **johncw said:**
> That's not a very clear statement. It suggests that a link in one browser plugin folder might work for a different browser that doesn't have a link to JRE in its own specific plugins folder. To say, "*it will work nonetheless*" is inspiring though.

I see where my statement is ambiguous... thanks for pointing it out!

For the ones who are still scratching their heads while reading this thread, what I was trying to say was that, it seems like if you make a link from Firefox plugins folder to the JRE located in the Mozilla plugins folder, or possibly even the Opera plugins folder, the JRE will still work.

And yeah, if that is the case, then it is really awesome indeed.   =)

---

### Post by jkapellen on 2007-03-07
Thank you very much for posting this. It worked perfectly for me.

Ubuntu 6.10
Firefox 2.0.0.2
jre-1_5_0_11-linux-i586 - downloaded from Sun.

---

### Post by rykel on 2007-03-24
You are welcome. Linux is all about sharing and contributing what you have received in the first place.   : )

---

