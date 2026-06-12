---
title: "Hardy Heron 64bit Java &amp; Flash issues"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by trekguy on 2008-04-30
This is my first try at a Linux OS.  It is installed on a brand new AMD64 build.  It came with Firefox 3B5.

**Java**___ At first, no Java at all. After doing some reading, I installed some icedtea things.  Now, at a Java test page, I get animation, and it tells me that my version is old, and should be updated.  It didn't look like they had anything for me at the Java site.  And, should ALL software be installed from the repositories, and not directly??  Anyway, so it appears that I have some kind of Java working... but when I go to Yahoo/Geocities to work on a website that I've built... I can't get into Page Builder, as it says I don't have Java.  ??????????

**Flash**___ Somehow I did get Flash working... but the animations do not start automatically.  There is a gray box with a "play" arrow on it... when I click on it... it will go.

**Random question #1**: When I install something from Synaptic, will it automatically uninstall what it is replacing, or what it doesn't need anymore???  If it does not, is it important to manually uninstall before??

**Random question #2:**  Seems as though the problems that I am having are due to the 64 bit thing.  IF I were to install Firefox 2, would that solve my Java and Flash problems???  Will it automatically replace FF3B5?  Will my bookmarks go away then?  Will I have to redo the email again??

---

### Post by garyedwardjohnston on 2008-04-30
> **trekguy said:**
> This is my first try at a Linux OS.  It is installed on a brand new AMD64 build.  It came with Firefox 3B5.

[COLOR="Red"]WELCOME TO OUR WORLD!!![/COLOR]

**Java**___ At first, no Java at all. After doing some reading, I installed some icedtea things.  Now, at a Java test page, I get animation, and it tells me that my version is old, and should be updated.  It didn't look like they had anything for me at the Java site.  And, should ALL software be installed from the repositories, and not directly??  Anyway, so it appears that I have some kind of Java working... but when I go to Yahoo/Geocities to work on a website that I've built... I can't get into Page Builder, as it says I don't have Java.  ??????????

**Flash**___ Somehow I did get Flash working... but the animations do not start automatically.  There is a gray box with a "play" arrow on it... when I click on it... it will go.

[COLOR="Red"]I strongly recommend to reinstall Hardy then the very first thing you do is get your hardware drivers set up correctly (they may be just fine out of the box), SECONDLY install "Ubuntu Restricted Extras".  This package is the only one I've found that works well.  It installs Java, Flash, and a bunch of other necessary things.[/COLOR]

**Random question #1**: When I install something from Synaptic, will it automatically uninstall what it is replacing, or what it doesn't need anymore???  If it does not, is it important to manually uninstall before??

[COLOR="Red"]Do a complete removal, restart, then reinstall.[/COLOR]

**Random question #2:**  Seems as though the problems that I am having are due to the 64 bit thing.  IF I were to install Firefox 2, would that solve my Java and Flash problems???  Will it automatically replace FF3B5?  Will my bookmarks go away then?  Will I have to redo the email again??

[COLOR="Red"]NO, stay with the Ubuntu default.  To fix these problems remember Ubuntu Restricted Extras.[/COLOR]

---

### Post by jimv on 2008-04-30
For the java issue, open a terminal and type:

sudo apt-get install sun-java6-jre sun-java6-plugin

---

### Post by QCompson on 2008-04-30
While I had no problems with java/flash on 64-bit Gutsy, Hardy has been driving me crazy.  Can anyone view the videos on comedycentral.com with 64 Hardy?  This isn't my only java/flash issue (some java applets refuse to load), but is the most vexing one at the moment.

I have flashplugin-nonfree installed.  I have ubuntu-restricted-extras installed.  I have the icedtea-gcjwebplugin installed.

Thanks.

---

### Post by trekguy on 2008-04-30
> **jimv said:**
> For the java issue, open a terminal and type:

sudo apt-get install sun-java6-jre sun-java6-plugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by trekguy on 2008-04-30
> **garyedwardjohnston said:**
> [COLOR="Red"]NO, stay with the Ubuntu default.  To fix these problems remember Ubuntu Restricted Extras.[/COLOR]

I did install the Ubuntu Restricted Extras.  Do I need to uninstall something?

You want me to completely reinstall HH?  Won't I lose everything that I've set up, like bookmarks, email, address book???

Everything else besides Java (and Flash-sort of) works great. Sound, printer, all good.

Sorry for the ignorance... me is Linux n00b.  :)

---

### Post by QCompson on 2008-04-30
> **trekguy said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

Trekguy,

Try opening synaptic (System -->Administration --> Synaptic Package Manager), and then in the synaptic menu, go to Settings-->Repositories.  Make sure the check box next to "Software restricted by copyright or legal issues (multiverse)" is checked.  Then hit "close", and "Reload", and try to install sun-java6-plugin again.

---

### Post by borisattva on 2008-04-30
> **QCompson said:**
> Trekguy,

Try opening synaptic (System -->Administration --> Synaptic Package Manager), and then in the synaptic menu, go to Settings-->Repositories.  Make sure the check box next to "Software restricted by copyright or legal issues (multiverse)" is checked.  Then hit "close", and "Reload", and try to install sun-java6-plugin again.

just wanted to +1. i have multiverse (and everything else for that matter) enabled and i get the same output as OP reported above.

---

### Post by trekguy on 2008-04-30
> **QCompson said:**
> Trekguy,

Try opening synaptic (System -->Administration --> Synaptic Package Manager), and then in the synaptic menu, go to Settings-->Repositories.  Make sure the check box next to "Software restricted by copyright or legal issues (multiverse)" is checked.  Then hit "close", and "Reload", and try to install sun-java6-plugin again.

Did it, reloaded, tried with the terminal...same result.

Did a search in Synaptic for sun-java6-plugin... not there.

Oh yeah, it was already checked.  ;-)

---

### Post by trekguy on 2008-04-30
> **QCompson said:**
> While I had no problems with java/flash on 64-bit Gutsy, Hardy has been driving me crazy.  Can anyone view the videos on comedycentral.com with 64 Hardy?  This isn't my only java/flash issue (some java applets refuse to load), but is the most vexing one at the moment.

[B]I have flashplugin-nonfree installed.  I have ubuntu-restricted-extras installed.  I have the icedtea-gcjwebplugin installed.
[/B]
Thanks.

That's what I did, as well.

I'm trying a com-central vid right now... I've got a black screen that says "loading".

---

### Post by QCompson on 2008-04-30
> **trekguy said:**
> Did it, reloaded, tried with the terminal...same result.

Did a search in Synaptic for sun-java6-plugin... not there.

Oh yeah, it was already checked.  ;-)

Try searching in Synaptic for sun-java

---

### Post by trekguy on 2008-04-30
> **QCompson said:**
> Try searching in Synaptic for sun-java

Yep, there's a whole pile of Java in there.  Java5, Java6, and JavaDB...

Some have said that Java isn't really going to work in HH64 til Java 7 comes out... do you think that may be the case??

---

### Post by QCompson on 2008-04-30
> **trekguy said:**
> Yep, there's a whole pile of Java in there.  Java5, Java6, and JavaDB...

Some have said that Java isn't really going to work in HH64 til Java 7 comes out... do you think that may be the case??

I have no idea about that.  I was under the impression that java 6 is relatively new.  

For me, youtube works fine, and some javascript based stuff works fine, but some java-applets don't work for me (java-based chat rooms and such).  I also experience the same issue with comedycentral that you do; endless loading-screen.

Everything java and flash related worked ok for me in Gutsy (also 64 bit).

---

### Post by redbob on 2008-04-30
I installed Gutsy 64bit... Java issue, flash issue... so much braining to make my machine work equal as it ran with 32bit... rounding and googling, I read a phrase that turned me back to 32bit. Someone told: "I prefer that My machine works for me than I would work for my machine." So I waited for 8.04 and I made a fresh install 32bit. Alive and kicking again!!

---

### Post by trekguy on 2008-04-30
> **QCompson said:**
> I have no idea about that.  I was under the impression that java 6 is relatively new.  

For me, youtube works fine, and some javascript based stuff works fine, but some java-applets don't work for me (java-based chat rooms and such).  I also experience the same issue with comedycentral that you do; endless loading-screen.

Everything java and flash related worked ok for me in Gutsy (also 64 bit).

I just checked, and YouTube works for me, too.  I don't know the difference between javascript and java-based.  ???  All I really need is for Yahoo Page Builder to work.

---

### Post by Moop on 2008-04-30
I'm using Hardy 64bit and have no issues with java or flash. I just used restricted-extras and enabled the medibuntu repository for codecs etc. 

Take a look at this sticky. It's full of great info.
 [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by QCompson on 2008-04-30
> **Moop said:**
> I'm using Hardy 64bit and have no issues with java or flash. I just used restricted-extras and enabled the medibuntu repository for codecs etc. 

Take a look at this sticky. It's full of great info.
 [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Just curious, Moop... can you view the videos on [comedycentral.com]("http://comedycentral.com")?

I just get an endless loading screen, but they work in XP under virtualbox.

---

### Post by doorknob60 on 2008-04-30
It seems like many of you are ignoring the fact this this is 64-bit!! For Java, see here [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins) (It gives instructions for Flash too, but there's a better way to use Flash in a 64 bit browser instead of using a 32 bit one). For Flash, try this: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) If it doesn't work, do the flash instructions in the first link.

---

### Post by Moop on 2008-04-30
> **QCompson said:**
> Just curious, Moop... can you view the videos on [comedycentral.com]("http://comedycentral.com")?

I just get an endless loading screen, but they work in XP under virtualbox.

I'm getting the endless loading screen too. I'm not sure what that's about. :confused:

---

### Post by trekguy on 2008-05-01
Flash issue solved... found this in another thread.  I think the swfdec auto-installed when I hit my first flash website.  I later had installed flash plugin non-free.  But, apparently the removal step of swfdec is important.  Here's what I did... works great now!


> Originally posted by tjwoosta

 **Re: Flash on Hardy 64bit**
if you see grey boxes that you have to click on to make them play, it is because you have the swfdec player instead of the prefered flashplugin-nonfree

to remove the swfdec player do this
Code:

**sudo apt-get purge swfdec-mozilla**

then install the working flashplayer like this
Code:

**sudo apt-get install flashplugin-nonfree**

this works on hardy 64 bit fine, no need to install any 32 bit java or librarys or anything


Now, Java!

---

### Post by trekguy on 2008-05-06
Still looking for a Java solution.  I will say that I am extremely happy with my first try with Linux/Ubuntu... except for one thing... Yahoo PageBuilder doesn't work.  I have now read a hundred different ways to try to fix it... but I'm hesitant to start changing too much because I really do think that the rest of it is working so well... I don't want to mess it up.

OK, as of right now, I have Java-common, and some icedtea stuff.  I can go to a Java test site, and it will tell me that I have Java 1.6 installed, and the test animation will work.  But, when I go to use Yahoo PageBuilder, it says that my browser does not support Java. Is there anyone out there running Page Builder with Hardy Heron 64?  Is there an install from the depositories that WILL work?  Do I need to uninstall the current Java/icedtea stuff before I attempt another install, or will Synaptic do that automatically?  If it turns out that it isn't going to work til the next java version, that's fine too... I would just like to know one way or another.

---

### Post by trekguy on 2008-05-07
Bump. :)

---

