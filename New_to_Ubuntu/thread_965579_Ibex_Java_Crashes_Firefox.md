---
title: "Ibex Java Crashes Firefox"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jasonhaley on 2008-10-31
Hi, I had Ibex working well for a few days (I had the RC) and then all of a sudden Firefox started crashing on almost every page. I  tried re-installing mozilla, flash, and even Java and Iceweasel and nothing worked. I'm now surfing the web with NetSurf, since they don't allow Java..and so don't crash.

 This is killing my Ibex experience. Should I just downgrade to Hardy?

---

### Post by phidia on 2008-10-31
You can look at your logfiles (System > Admin > Log files) but perhaps the best way to troubleshoot this is to open ff from the terminal and when it crashes there should  be output there to work with.

Have you filed or looked at bug reports?

---

### Post by stephanvaningen on 2008-10-31
Do you have standard 32bit install of Ibex?

---

### Post by jasonhaley on 2008-10-31
I went through numerous bug reports and tried suggestions but nothing worked. I'd figure a complete reinstall of java/flash and firefox would have fixed it but it didn't. I even temporarily threw my entire home folder in the Trash but still nothing happened. I'm using 32bit..I'll try to see if the terminal outputs anything.

---

### Post by jasonhaley on 2008-10-31
I got these messages in my terminal:
ICEDTEAPLUGIN_DEBUG = (NULL)

Everything works fine but then if I go to a certain page it will hang, dim and close. Leaving this message:

BUS ERROR

The odd thing is that it only happens on certain pages, like Lifehacker.com always crashes it. On Wordarc.com I can view a few pages but it will crash on certain ones.

---

### Post by phidia on 2008-10-31
It's probably not a solution you'll like but you could try another browser until some updates come through. Opera is often recommended, some like epiphany.

---

### Post by Axos on 2008-10-31
I have the latest version of Adobe Flash (10,0,12,36 from adobe.com, not Ubuntu repositories) and Java (6u10 from sun.com, not Ubuntu repositories) installed and I've clicked around lifehacker.com without any crashes.

Roughly 0.000000000000000000000001% of web sites use client-side Java (not to hurt Sun's feelings but it's true) so my hunch is something besides Java is causing the crash. Have you tried disabling all your Firefox add-ons? The only add-on I use is Adblock Plus.

This page will tell you what version of Adobe Flash you have installed:

[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

This page will tell you what version of Java you have installed:

[http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

---

### Post by jasonhaley on 2008-10-31
I tried Opera, Epiphany, Midori and none worked. They all crash just like Firefox. That's why I'm convinced it's a JAVA issue because NetSurf (that doesn't use JAVA) is the only browser that works for me right now ..but I'd like some java capabilities since even this site uses it.

---

### Post by jasonhaley on 2008-10-31
Not only did I get rid of all my plugins. I got tried re-installing it completely. I even deleted my home folder, and made a new user account but still the same problems arise.

How do I install the latest adobe? I'm so desperate for a solution I'll even do that.

---

### Post by stephanvaningen on 2008-10-31
Reading the debug-msg I assume you use the open-source IcedTea i.o. Sun's Java? You can see if there's a difference when you install the Sun's JVM/JRE?

---

### Post by jasonhaley on 2008-10-31
That was my original set-up. I had them both running..but I can uninstall icedtea and try again with only Sun JVM.JRE...

---

### Post by jasonhaley on 2008-10-31
Didn't work.

I do just get the BUS error in the terminal.

---

### Post by jasonhaley on 2008-10-31
Maybe it's a virus? Before the crashes started happening, I did download Dragon Naturally Speaking from the Pirate Bay and couldn't get it working through Wine. But I uninstalled it and even uninstalled Wine..but it still crashes.

---

### Post by poldie on 2008-10-31
> **jasonhaley said:**
> Maybe it's a virus? Before the crashes started happening, I did download Dragon Naturally Speaking from the Pirate Bay and couldn't get it working through Wine. But I uninstalled it and even uninstalled Wine..but it still crashes.

I don't see where you posted the results of which version of java you have installed.

---

### Post by jasonhaley on 2008-11-01
Sorry, when I went to the link Axos provided it said I had the latest version of Java for my distribution.
"Version 6 Update 10"

---

### Post by gandaran on 2008-11-01
> **jasonhaley said:**
> Sorry, when I went to the link Axos provided it said I had the latest version of Java for my distribution.
"Version 6 Update 10"
how did you install this version, synaptic or sun java website?
you could go to firefox»tools»addons»plugins disable flash or java just to find out which one is causing the crashes

---

### Post by kansasnoob on 2008-11-01
I believe the "icedtea" stuff is just wrong for 32 bit (1386).

I'm using all sun-java6-*** (except sun-java6-doc and -source) with 8.10's Flash 10 + flashblock and no probs here!

You know each time you make changes you need to quit Firefox: file > Quit, then restart:)

---

### Post by TransitMan on 2008-11-01
> **jasonhaley said:**
> I got these messages in my terminal:
ICEDTEAPLUGIN_DEBUG = (NULL)

Everything works fine but then if I go to a certain page it will hang, dim and close. Leaving this message:

BUS ERROR

The odd thing is that it only happens on certain pages, like Lifehacker.com always crashes it. On Wordarc.com I can view a few pages but it will crash on certain ones.

You need to open Synaptic and then search for ICEDTEAJAVAPLUGIN. When you find them, remove them all.
Then install SunJava and Adobe Flash, restart the computer, and you should be good to go.

---

### Post by jasonhaley on 2008-11-01
> **TransitMan said:**
> You need to open Synaptic and then search for ICEDTEAJAVAPLUGIN. When you find them, remove them all.
Then install SunJava and Adobe Flash, restart the computer, and you should be good to go.

-Deleted all Icedtea packages
-Re-installed Suna java and Adobe Flash
-Re-started computer

...Problem persists, nothing has changed in either Opera or Firefox.

---

### Post by dreikin on 2008-11-01
Do this in Firefox:

* Click Tools >> Add-ons
* Make sure you're on the "Plugins" tab
* Tell us ALL the java plugins listed (eg, mine shows GCJ Web Browser Plugin 0.96.1)

(Note that I have the same problem on goproblems.com when I try to play a problem - but I'm on 64bit and trying to get it to work without 32bit firefox)

---

### Post by dreikin on 2008-11-01
Update:
I've got my problem site running with the following plugins enabled in firefox:

* GCJ Web Browser Plugin 0.96.1
* IcedTea Web Browser Plugin

BOTH are enabled, as IcedTea appears to depend on GCJ.

GCJ was installed by default, and the second appeared after doing:

* sudo apt-get install icedtea6-plugin

---

### Post by jasonhaley on 2008-11-01
> **dreikin said:**
> Update:
I've got my problem site running with the following plugins enabled in firefox:

* GCJ Web Browser Plugin 0.96.1
* IcedTea Web Browser Plugin

BOTH are enabled, as IcedTea appears to depend on GCJ.

GCJ was installed by default, and the second appeared after doing:

* sudo apt-get install icedtea6-plugin

Well I had all plugins disabled and it still didn't work. I also gave IcedTea a chance and it didn't work. GCJ is always installed when I try it.

---

### Post by jasonhaley on 2008-11-02
> **dreikin said:**
> Do this in Firefox:

* Click Tools >> Add-ons
* Make sure you're on the "Plugins" tab
* Tell us ALL the java plugins listed (eg, mine shows GCJ Web Browser Plugin 0.96.1)

(Note that I have the same problem on goproblems.com when I try to play a problem - but I'm on 64bit and trying to get it to work without 32bit firefox)

Well I disabled all the plugins in both Firefox and Opera so I don't think it's a plugin issue.

---

### Post by jasonhaley on 2008-11-02
Update: I installed Google Chrome through Chromium and it still doesn't work.

A page such as wordarc.com will work but if I click on what of its navigation links like wordarc.com/alishahnovin/2008/10/31 Gmail_Labs_-_The_Shotgun_Approach_to_Innovation it stalls ....the same goes for a lot of other sites, like lifehacker.com

---

### Post by jasonhaley on 2008-11-03
Looks like everyone is out of solutions. Ok, I'm going to re install Ibex from scratch... if that doesn't work, then I'm just going back to Hardy Heron and may wait for the next Jackalope.

---

### Post by WSiaB on 2008-11-03
I am having the same problem since upgrading to Ibex from Hardy.  This is on multiple machines.  Everything else worked great, so I upgraded all the machines before this problem was discovered.  I have tried all the suggestions and am still having the same problem.  Let's not give up, if you have a suggestion I would LOVE to hear it.

In our case the only Java plugin is Java(TM) Plug-in 1.6.0_10-b33.  I am fairly certain the problem is with Java and not Firefox though.  I have completely removed and reinstalled Java from the Sun site on one machine and from the repositories on another to the same effect.

---

### Post by WSiaB on 2008-11-03
[COLOR="DarkRed"]I have gotten Java to work on the upgraded machines[/COLOR] by:
Completely removing Java from the upgraded machines. Restarting and reinstalling Java per the instructions at [www.java.com](www.java.com) for the self extracting version. Restarting Firefox, "Get Add-ons", find Java Console 6.0 and install it.  Restarting Firefox and Java should be working!  This bug should be passed on for documentation or correction with an upcoming update. This bug occurs on fresh installs in addition to upgrades.

---

### Post by ShelJ on 2008-11-06
I found the following on the Reslease Notes page ([http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)).  I don't know if you tried this yet, but I did and it still didn't work for me in FF, but it may solve this issue in other browsers.

[HTML]Access to Java Runtime Environment

To use Java programs, you need to install the openjdk-6-jre package whch contains the Java Runtime Environment. If you want to develop Java programs, then install the openjdk-6-jdk package. To work with Java applets in the Firefox browser and compatible browsers on x86 architectures, you need to install the icedtea6-plugin package by hand. 

The JRE and the Java applet plugin are installed by default in the live session on the Ubuntu DVD, but are not currently installed elsewhere due to space constraints. However, a missing feature in the installer means that these packages will not be installed when installing using the graphical installer on the DVD, so you will need to install them afterwards.[/HTML]

Hope this helps.

---

### Post by jamesstansell on 2008-11-09
> **dreikin said:**
> Update:
I've got my problem site running with the following plugins enabled in firefox:

* GCJ Web Browser Plugin 0.96.1
* IcedTea Web Browser Plugin

BOTH are enabled, as IcedTea appears to depend on GCJ.

GCJ was installed by default, and the second appeared after doing:

* sudo apt-get install icedtea6-plugin

Because of the "braindead" special treatment firefox gives to java you can't have more than one plugin installed, but only enable one.  Enabling or disabling one also takes the same action on all the others.

Only one of them, though, will ever be used.  There doesn't seem to be a way to tell which one the browser will use either.  (I _think_ I've seen it switch back and forth.)

I don't believe the icedtea6-plugin depends on the gcj plugin.  You should be able to remove the latter.

---

### Post by jamesstansell on 2008-11-09
> **WSiaB said:**
> [COLOR="DarkRed"]I have gotten Java to work on the upgraded machines[/COLOR] by:
Completely removing Java from the upgraded machines. Restarting and reinstalling Java per the instructions at [www.java.com](www.java.com) for the self extracting version. Restarting Firefox, "Get Add-ons", find Java Console 6.0 and install it.  Restarting Firefox and Java should be working!  This bug should be passed on for documentation or correction with an upcoming update. This bug occurs on fresh installs in addition to upgrades.

I've seen some reports of a regression in the sun-java6-plugin 6u10 version.  Sounds like you might have run into that.

One known work-around is to use the "plugin2" implementation (libnpjp2.so) that was added to 6u10.  There aren't easy instructions yet for switching to it.

Another suggestion has been that the regression only happens with the sun-java6-jdk package installed, which isn't needed for the plugin.  (the jdk package has developer-oriented tools)  I don't know though if anyone has fixed the regression by removing it.

Sounds like you solution here may be a possible 3rd option.  Or possibly a variation of the 2nd option, since java.com wouldn't have included instructions for the JDK.

---

### Post by WSiaB on 2008-11-10
We haven't had the problem due to the regression (yet) but we do have a repository active that upgraded Firefox to 3.0.4 which again broke Java.

We don't use the JDK on these machines since they are not development machines.  Ironically our development machines are still running Hardy with no plans of upgrading :).  These were upgraded due to end users pestering us after they saw our kiosk running it (looks are everything to EUs).

I am just starting on the "rebroken" Java problem now, will update this post if it is related.

---

### Post by jasonhaley on 2008-11-22
Ok i tried EVERYTHING here..and NOTHING worked for me... I had re-installed firefox completely about 4 times and java... but nothing would work..but now I found the solution!!!

Ubuntu FTW .... only after so much stress
 ..i don't know why it would crash.. I just kept upgrading ubuntu and adding new programs ...never bothering to do fresh installs....and then firefox would always crash ..so I went to my add/remove programs and got rid of all the most unpopular programs on ubuntu.... including my games.... and it worked. I have no idea how or why ....it could have been some obscure flash program or something to... I don't know.. but my games weren't working too well either..so I got rid of the ones that didn't work..and it worked.. lifehacker.com kept crashing the browser but something like youtube or gmail would work... I tried opera and a bunch of other browsers and they didn't work either. My guess was I may have downloaded some weird virus on a game that would use my browser? I don't know.. it works now after 3 weeks of trying to fix the thing. It couldn't be a firefox plugin ...because none of the browsers worked. I bet it was a virus or a bug .... that I somehow disabled by removing the program.. it's probably dormant in some unknown folder. I also remove Microsoft Fonts from ubuntu... unfortunately I just removed all the least popular programs..so I'm not sure which one did it to me. There was a macromedia flash plugin that I removed too.. but I think I remember already trying to remove that solely and it didn't work initially... not sure if that was the culprit.. but that would have been the most likely one...although lifehacker.com doesn't really use flash..and not a lot of java.

Its funny..because I trained my brain not to click on any links in firefox that I didn't know... and now that I'm testing it, my heart skips a beat every time a page loads slowly.. out of fear that it may still crash. The only problem I have now is that the quick-reply box on the ubuntu forums doesn't work..but that's a small sacrifice compared to the nightmare i had before.

---

### Post by jasonhaley on 2008-11-22
Fixed everything is working pretty well now.

---

### Post by dgbearcat on 2008-12-02
I wish you knew what it was that fixed this, as I am having the same problem: Java crashes Firefox, but only on a few sites in particular. I'll try the fix earlier on the thread when I get home.

---

### Post by kenn e on 2009-04-08
are you confusing Java (From Sun) with Javascript? they are two very different things.
This site uses Javascript (quite heavily) but does not use Java that i am aware of.

A page that does use Java, the facebook photo uploader, can crash, if you aren't patient enough - my experience is that the browser dim's then comes back as the application loads, and if you try and click on images or scroll down too quickly after it comes up, the browser will crash.

I am using the latest Sun JRE from the update manager.

[try uninstalling only Java, see if your experience changes -- you will get a "plugin required" thing if you do need Java.]

ken.

---

