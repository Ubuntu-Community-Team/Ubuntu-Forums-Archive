---
title: "No option for full screen in Ubuntu"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2013-02-21
I have Ubuntu & Windows XP Dual booting.

When in XP, i can play any flash games in Facebook, and i get a box to play in full screen if i wish.

Sadly, when using Ubuntu, i don’t get this option, so i am stuck in normal screen size.

I am guessing this is a flash player or driver issue.

If so is there anything i can do to get it working in Ubuntu ???

Many Thanks for any help :D

---

### Post by Mark Phelps on 2013-02-21
To see if its a video driver issue, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA" -- that will list out the make and model video chipset you're using.

Post that information back here.

---

### Post by MadMonkey1966 on 2013-02-21
> **Mark Phelps said:**
> To see if its a video driver issue, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA" -- that will list out the make and model video chipset you're using.

Post that information back here.

Thanks for the quick reply Mark. I done what you said and just have the one line with VGA on it. Hope this helps ;)

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

---

### Post by MadMonkey1966 on 2013-02-21
Just to add , it only seems certain Flash games as well , if that's any help. Some will go into full screen ??

---

### Post by MadMonkey1966 on 2013-02-22
I have searched on Google for 

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

and this seems to be a problem...but i cant seem to find an answer......

---

### Post by Mark Phelps on 2013-02-22
Intel video drivers are installed by default -- and are supposed to work without problems.

You could try going to the link below and seeing if there is any newer version of the driver:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng")

---

### Post by MadMonkey1966 on 2013-02-23
> **Mark Phelps said:**
> Intel video drivers are installed by default -- and are supposed to work without problems.

You could try going to the link below and seeing if there is any newer version of the driver:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng)

hmmmm that seems to only deal with Wifi drivers...unless i am missing something.

---

### Post by MadMonkey1966 on 2013-02-24
I kept searching and found some more on the subject. When i followed this i still dont get full screen in some games in Ubuntu, but now i get an error when Update Manager is trying to install one particular thing (attached)

The installation or removal of a software package failed.
installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 224696 files and directories currently installed.) 
Preparing to replace libdrm-nouveau1a 2.4.39-0ubuntu1 (using .../libdrm-nouveau1a_2.4.42~precise~ppa1_i386.deb) ... 
Unpacking replacement libdrm-nouveau1a ... 
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau1a_2.4.42~precise~ppa1_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libdrm-nouveau1a_2.4.42~precise~ppa1_i386.deb 
Error in function: 

Guess i am going to have to stick with XP for games..... :(

---

### Post by audiomick on 2013-02-25
regarding this

> **MadMonkey1966 said:**
> 
Preparing to replace libdrm-nouveau1a 2.4.39-0ubuntu1 (using .../libdrm-nouveau1a_2.4.42~precise~ppa1_i386.deb) ... 
Unpacking replacement libdrm-nouveau1a ... 
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau1a_2.4.42~precise~ppa1_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libdrm-nouveau1a_2.4.42~precise~ppa1_i386.deb 
Error in function: 

Guess i am going to have to stick with XP for games..... :(

Look very carefully at the ouput you posted here
[http://ubuntuforums.org/showpost.php?p=12529242&postcount=5]("http://ubuntuforums.org/showpost.php?p=12529242&postcount=5")

I reckon that package went through when you did the apt-get upgrade there.


Edit: I can only agree with what Mark Phelps said: Intel graphics shouldn't be giving you any trouble. I don't really know, but I suspect your problem is more likely flash related.

Have you got the ubuntu-restricted-extras installed? That includes the installer for the adobe flash plugin for firefox. That might work better, if you haven't already got it.

This is only a guess, mind you. I don't play games, and am not a facebook user, so I can't check to see if the games there work for me.

---

### Post by MadMonkey1966 on 2013-02-25
Hi again Mick :P

I am lost when it comes to these package things. I understand drivers etc....which is why i can not understand why on a dual boot pc, i get full screen on XP, but not on Ubuntu.

It gives me full screen in some things, but not others. i am thinking it may have something to do with Flash Player maybe.

I guess my graphics card and monitor must be ok as they work fine on XP, BUT i am so trying to get off of using Windows (any version, but XP is the best), but i do like my games to relax.

How do i Instal that ubuntu-restricted-extras??

---

### Post by audiomick on 2013-02-25
> **MadMonkey1966 said:**
> 
How do i Instal that ubuntu-restricted-extras??

It should be in the software centre. I don't have a 12.04 or 12.10 install yet, but it was in there on 11.10. You may have to go to the package sources and tick the box for "universe" and "multiverse" before it will show up.

---

### Post by MadMonkey1966 on 2013-02-25
> **audiomick said:**
> It should be in the software centre. I don't have a 12.04 or 12.10 install yet, but it was in there on 11.10. You may have to go to the package sources and tick the box for "universe" and "multiverse" before it will show up.

Thanks Mick, i installed ubuntu-restricted-extras but nothing has changed.

Still no full screen...

---

### Post by MadMonkey1966 on 2013-02-25
I found this on a page while looking everywhere to find the solution to the full screen problem.

> Web browsers, including the default Firefox browser in Ubuntu, often  have problems calling the proper library to view Flash in fullscreen  mode. To fix this problem, load the library before loading the browser.  In your Preferences menu, select "Internet." Choose your browser and  select "Preferences." In the Command field, you will see the command  that Ubuntu uses to launch your browser. Before that command, add "env  LD_PRELOAD=/usr/lib/libGL.so.1." Close the Preferences menu and try  Flash in fullscreen mode again.Is that worth trying in 12.04...if so how do i do it ?

(though, there is so much written in the various forums about full screen not working, i dont think there is an answer at the moment :( )

---

### Post by MadMonkey1966 on 2013-02-25
Just for interest i went through a few other flash games on Facebook.

The one i play with my sister Farmville 2 is th eonly one i can find that will not play in full screen in Ubuntu. All others seems to be fine.

I am wondering if it is because the game is sort of 3D though as i say it is fine in Windows XP. 

Maybe this is something to do with not using Unity......

---

### Post by uc50_ic4more on 2013-02-25
If you have just now installed the ubuntu-restricted-extras package, then I don't think you have even had Flash installed; and may not even be using it now:

I think Ubuntu may come with "Gnash" (or nothing at all) which aims to provide some of the functionality that the (proper) Flash plugin would give you. You will NOT, however, get the same experience as with the real Flash player. I don't think this is a driver issue or anything remotely that complicated. I think you just need to use the Flash plugin and not the unofficial, semi-complete work-a-like. In Firefox, click Tools -> Add-ons, then click Plugins on the left of the Add-ons Manager tab. You should see "Shockwave Flash" listed and version 11.2 or so (as of this writing). Make sure it isn't disabled. Re-install ubuntu-restricted-extras if you have to; either through the Software Centre or via a command in a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

A "package" is simply the installation file(s) for an application. When you download a Windows program, and it is called "setup.exe" or setup.msi" that is the equivalent to a package in Ubuntu for the most part. A terrific advantage Ubuntu has over Windows is that there are thousands of packages available from one source: The Ubuntu Software Centre. In Windows you have to go to different sites and get different "setup.exe" or other installation media and install them all manually and separately. In Ubuntu you simply choose applications you want from the Software Centre and click "Install".

---

### Post by MadMonkey1966 on 2013-02-25
Hi uc50_ic4more

This is my conclusion after another day of trying to sort this.

Flash is installed as when i right click in any Flash game, it shows me about Adobe Flash player etc.... APART from this one game that WONT go full screen. I can not even right click in the game. Interesting that this is written under the game.

You are playing FarmVille 2 without graphics acceleration. 		Some of the graphics are not as sharp as they could be and the game may run slower. 		Want better graphics? 		[ 			Make sure you have the latest version of flash 		]("https://fb1.farm2.zynga.com/clean_redirect.php?url=http://get.adobe.com/flashplayer/") 	[CENTER] [/CENTER]
    	 		Having trouble seeing FarmVille 2?
		[Please update your flash player by clicking HERE.]("https://fb1.farm2.zynga.com/clean_redirect.php?url=http://get.adobe.com/flashplayer/")
		Powered by Flare3D Engine. Copyright © 2012

The line that draws my attention is the bottom one ( 		Powered by Flare3D Engine. Copyright © 2012) mentioning the 3D Engine. This is the only game that mentions it.

I tried as you suggested anyway:

sudo apt-get install ubuntu-restricted-extras
But as i say, it is already there.

So i think conclusion in that it is a 3D problem i think.

---

### Post by uc50_ic4more on 2013-02-25
> **MadMonkey1966 said:**
> So i think conclusion in that it is a 3D problem i think.

Yes, and it seems as though I may have spoken too soon and with too much assurance. 

I have some intermediate experience in Flash (although none in Flash games) and know nothing of this (seemingly) third-party 3D engine. It is difficult to say what this 3D engine wants to see in terms of 3D capabilities from your drivers and hardware; and somewhat strange that you Intel graphics do not meet these standards, especially since Windows seems to work well with it. I wonder if the culprit is the Linux version of the Flash player, and/or it's relationship to this 3D engine, and/ or their relationship to Ubuntu's graphics stack.

Either way, sadly, it seems like you might be suffering one of the handful of drawbacks to using an OS with a ~1% user base: Developers and manufacturers often regard us as an afterthought at best. I can only suggest that you investigate this in whatever forums or support that the makers of this 3D engine offer; and report back here if you uncover anything of substance.

---

### Post by MadMonkey1966 on 2013-02-25
Yes, i think i will mention it on the Zynga Forums as they are the ones who make all the Flash games for Facebook.

This is there first upgrade into the world of 3D Flash games, so i doubt they have even thought about it.

I will close the thread and just have to play that one game when in Windows XP

Many thanks for your help.

---

