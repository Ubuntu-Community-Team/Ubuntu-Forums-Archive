---
title: "Four problems"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by juanfran27 on 2008-09-08
After a couple failed tries, I installed Hardy Heron over Vista. So far I like it very much and it is working fine. However I have, like the title suggests, four problems:

**1.** The built-in microphone of my laptop is not working.

**2.** When I turn on the built-in webcam, the images freezes after ~30 seconds.

**3.** Following [[COLOR="Blue"]this procedure[/COLOR]]("https://help.ubuntu.com/community/VirtualBox?highlight=(virtualbox)"), I tried to install Virtualbox to run Windows only applications. But right after the first step I get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages

**4.** This may sound geeky, but I sometimes play Guild Wars and Battlefield2. I downloaded and installed WINE. Surprisingly, it was very simple to install the first game. When I started it, it ran almost well -it runs a bit slow- but suddenly, without a warning, it exits. With this result, I have not tried for the latter game.

I also use Adobe Photoshop CS2 *a lot*, does this run well on WINE or would it be better to use the Virtualbox? How about CS3? I know I can use Gimp, but that is not an option for me.

Any ideas?

So, there it is. If you are willing to guide a new Ubuntu user, I would greatly appreciate it.

Thanks to all in advance.

Cheers.

---

### Post by juanfran27 on 2008-09-08
I almost forgot. I'm running Ubuntu 8.04 on a Dell 1520, nVidia 8600M, 2GB memory, Intel Core 2 Duo (I believe).

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by Threbus5 on 2008-09-09
Check sound settings. Some of the newer machines, particularly laptops, input audio require either low level reconfiguration or simply fail to work. You should search for the model of computer and audio settings.

regarding the nvidia, lots of people seem to be discussing that. Again, recommend a search for that topic.

try this thread for some similar problems:

[http://ubuntuforums.org/showthread.php?t=765792&highlight=dell+laptop+microphone](http://ubuntuforums.org/showthread.php?t=765792&highlight=dell+laptop+microphone)

or this one

[http://ubuntuforums.org/showthread.php?t=798064&highlight=dell+laptop+microphone](http://ubuntuforums.org/showthread.php?t=798064&highlight=dell+laptop+microphone)

A proper virtual box install should work. It seemed to handle normal Windows apps on my system. But, I did not try games.

---

### Post by dioltas on 2008-09-09
Here are the wine application database entries for guild wars and Battlefield2, the comments usually have tips on getting the programs running. The [application database]("http://appdb.winehq.org/") is always a good place to look if you are having trouble getting a wine application working.
[Guild Wars]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194")
[Battlefield2]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438")

Click through the different user reviews aswell,

Ratings mean:  (i think)
Platinum means game worked perfectly first time
Gold means game worked after a bit of setting up
Silver means game works with some minor annoyances
Bronze - some major annoyances affecting gameplay
Garbage - rubbish, didnt work

Expect some glitches and things, although you might get a game running almost perfectly, it may still crash unexpectedly from time to time. If you know what makes it crash try avoiding doing that if possible, and maybe post a rating on the wine app database including the bug and maybe someone will sort it out.

---

### Post by jemate18 on 2008-09-09
> **juanfran27 said:**
> After a couple failed tries, I installed Hardy Heron over Vista. So far I like it very much and it is working fine. However I have, like the title suggests, four problems:

**1.** The built-in microphone of my laptop is not working.

**2.** When I turn on the built-in webcam, the images freezes after ~30 seconds.

**3.** Following [[COLOR="Blue"]this procedure[/COLOR]]("https://help.ubuntu.com/community/VirtualBox?highlight=(virtualbox)"), I tried to install Virtualbox to run Windows only applications. But right after the first step I get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages

**4.** This may sound geeky, but I sometimes play Guild Wars and Battlefield2. I downloaded and installed WINE. Surprisingly, it was very simple to install the first game. When I started it, it ran almost well -it runs a bit slow- but suddenly, without a warning, it exits. With this result, I have not tried for the latter game.

I also use Adobe Photoshop CS2 *a lot*, does this run well on WINE or would it be better to use the Virtualbox? How about CS3? I know I can use Gimp, but that is not an option for me.

Any ideas?

So, there it is. If you are willing to guide a new Ubuntu user, I would greatly appreciate it.

Thanks to all in advance.

Cheers.

for your wine applications. check this list.. this contains tested applications
> [http://appdb.winehq.org/](http://appdb.winehq.org/)
Some works.. and others don't try to search for ratings platinum, gold.

---

### Post by Vadi on 2008-09-16
In regards to the webcam, try lowering the resolution in preferences. That helped speed up the image for me.

---

### Post by markbuntu on 2008-09-16
SInce you have not specified your hardware, I can only guess that you have a HDA sound card. If so, this thread might help you to get your microphone working:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Also, you can read the first part of my guide to see if it is anything simple you may have overlooked:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

