---
title: "Can't Install Java - Please Help"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-07-15
Hey there!

First off, I want to say I am impressed - very - by Ubuntu. I have only been using the Live CD for a few days and it's so easy and such a pleasure to use!

However, I have a problem install sun-java5 and 6-jre and sun-java 5/6-bin both using the Terminal and Synaptic Package Interface. The packages both have errors and I suck at Terminal type apps except Lynx.

I type in sudo get-apt sun-java5-jre.bin and there's an error. With downloaded software it's impossible, I can't understand it at all. Should I download program in folder where I install it? I don't know. I tried googling how to install ubuntu apps and the directions confused me. *sigh*

So if someone help me could I would be SO grateful.

ALSO - I can't get videos in VLC. Codecs, I did download but no luck! Same with the default. So what should I do?

Thank you so much!
-bobby
P.S. -  I am sorry if my English is bad. I am oral Deaf and my English gets bad when I'm tired. ;)

ETA: It's now just the jre bin that not work.

ETA 2 - got everything figured out, just want to find out what happened with bin?

And how to install a new game thats not on the database like hearts or something? folder which?

---

### Post by Yoke &amp; Chung on 2008-07-15
Welcome to Ubuntu :-)

You do not need to tyep the ".bin" extension if you are using app-get command in the terminal.

Type this in your terminal:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

It should do the trick.

Installing Ubuntu applications is different from Windows, you do occasionally download ".deb" extension file and double click it like in Windows for the installation, but most of the time you will probably do it via Synaptics or apt-get.

Using Synaptics and apt-get will install the files automatically, and you will not see a installer program for the application as in Windows.

Try to stick to Synaptics/ apt-get and ".deb" installation method for now, as you progress and learn more about Linux, you will be more confident to tackle ".bin", ".rpm", or compiling from source.

---

### Post by hyper_ch on 2008-07-15
```

sudo get-apt sun-java5-jre.bin

```
Well, that's not the name of the package....

search for the proper name:
```

apt-cache search sun-java5

```

---

### Post by ForksHolder on 2008-07-15
For the Java thing, Try to download it from [here]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=23103") and if you will go to the bottom of the page, there will be [instractions]("http://www.java.com/en/download/help/5000010500.xml#selfextracting") there.

For the video thing, I would recogmend on Mplayer.
See this to install with all the codecs:
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)


Good luck. =]

---

### Post by hyper_ch on 2008-07-15
why do you point to another site for downloading it when it's in the repos?

---

### Post by tinny on 2008-07-15
> **hyper_ch said:**
> why do you point to another site for downloading it when it's in the repos?

Yeah, go with the repos.

Use the Sun version of Java and not the OpenJDK (its really not ready yet).

I use Sun Java 6 and its just fine.

Go to Add / Remove applications, select "Show: All available applications", then search for "sun". You should then get "Sun Java 6 Runtime" near the top of the search results list. Select it and install.

(No command line required :) )

As for the Java browser plug in. If you navigate to a website that uses Java the browser will prompt you to install the plugin.

Like this one.
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

Just remember to restart the browser after the plug in install

---

### Post by iaskedalice09 on 2008-07-15
I'm still stuck on how to install apps that are downloads. What should I do?

---

### Post by iaskedalice09 on 2008-07-15
Oh, and thanks so much for all your help!

---

### Post by RomeReactor on 2008-07-15
Hi. Is there a particular reason you want Java 5 instead of 6? Do you have Ubuntu 32 bit, or 64? What error messages do you get? Try:
```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

If you get errors, please post them.

---

### Post by avtolle on 2008-07-15
Clarification, please; you posted that you had been running from the Live CD for a few days. Are you still running from the Live CD, or have you installed the o/s on your HDD? If running from the Live CD, any downloaded application will be in the RAM only, and once the computer is shut down/restarted, it will not be there.

---

### Post by alzie on 2008-07-15
I'm agreeing with **avtolle**,  we need to know if you have installed ubuntu or are just trying it out with the live cd at this point.  

If you are unsure about changing operating systems you should consider a Wubi install or dual booting so that you still have your old operating system available

---

### Post by stchman on 2008-07-15
Here is how to install Java 1.6 on 32 bit.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```

This will install the browser plugin as well.

To install Java in 64 bit with browser plugin use Icedtea.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

If you do not care about Java enabled websites when using 64 bit you can use the 32 bit code but just omit the plugin package.

SUN Java 6 works fine in 64 bit EXCEPT the plugin.

---

### Post by iaskedalice09 on 2008-07-15
I'm running it Live. I got Java up and running with 5. I will install Ubuntu dual boot within a few days...I just need to defrag..and have a friend who KNOWS Ubuntu on the other line...I'm gonna call him when he's free. :)

---

