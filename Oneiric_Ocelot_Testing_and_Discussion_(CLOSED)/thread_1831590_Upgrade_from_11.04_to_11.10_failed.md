---
title: "Upgrade from 11.04 to 11.10 failed"
date: 2011-08-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by TakisX on 2011-08-23
I upgraded from 11.04 to 11.10 and after i rebooted no gui 
The lcd flashes and dies
I have ati 5770 card and i had installed the closed drivers in 11.04 
Any help ?

---

### Post by sikander3786 on 2011-08-23
You mean to say no gui or no display at all?

If you are able to boot to the command line, you can try removing your graphics drivers and the older xorg.conf from /etc/X11 directory and then re-installing the drivers.

---

### Post by Yumi on 2011-08-23
My upgrade from 11.04 to 11.10 also failed initially. One error I remember is that it "failed to install desktop". Waiting a long time I got the loging page and was able to log into "ubuntu classic". Got some sort of desktop but without the System Menu on top. 

Through the terminal I did a further upgrade -d which executed overnight. Now I did a "gksudo update-manager". Get "Package operation failed" in front of my eyes. Details say "installArchives() failed.

Hope you are able to get into 11.10

Michael

---

### Post by Rasa1111 on 2011-08-23
why would anyone "upgrade" to 11.10 already?
that's just asking for trouble.

---

### Post by Yumi on 2011-08-23
I always upgraded around Alpha3. We do not expect a fully trouble free experience and the feedback helps developers. Somebody has to find the problems. If you can not accept this, wait until the final version is out.

This discussion is not to complain but to discuss existing problems!

Michael

---

### Post by Rasa1111 on 2011-08-23
Complain? lol  what? 
I asked a simple question is all.

---

### Post by sir.sargento on 2011-08-24
Not trying to hi-jack this thread just hoping to help get it solved. But I to have had this problem today. Used Alt+F2 'update-manager -d' and everything went well until about the last part of the upgrade and it tells me it installed the upgrade but had problems. 

So I reboot and after I login all I have is a black screen, cant see anything. I can use the desktop like the unity sidebar etc by guessing where my icons were. Anyways I go into synaptic and it tells me that I have a broken package which was 'ubuntu-desktop' I reinstalled the package and it says its fine now but still just have a black screen.

Hope this helps at all and hopefully somebody can help us.

Thanks

---

### Post by Yumi on 2011-08-24
Sargento, as I wrote, same experience here. I can only login by selecting "Gnome Classic (no effects)" below the login.

Then I got a number of errors relating to packages. Once sortet out, it now runs somewhat stable.

Michael

---

### Post by TakisX on 2011-08-24
No display at all
.How i unistall the closed drivers of ati card ?
How i install then the open drivers ?

---

### Post by sir.sargento on 2011-08-24
Fixed the problem. Saw a solution in another thread hopped into terminal and it worked for me. Hope this helps at all.

sudo apt-get update
sudo apt-get upgrade 
#or 
sudo apt-get dist-upgrade
reboot

---

### Post by coffeecat on 2011-08-24
> **TakisX said:**
> No display at all
.How i unistall the closed drivers of ati card ?
How i install then the open drivers ?

Boot into recovery mode and choose "drop to root shell". At the root (#) prompt, run these commands:

```
apt-get purge fglrx*
rm /etc/X11/xorg.conf
```

The open source driver is already installed and will be activated when you reboot. If you still can't boot into the GUI, post back.

> **sir.sargento said:**
> Fixed the problem. Saw a solution in another thread hopped into terminal and it worked for me. Hope this helps at all.

sudo apt-get update
sudo apt-get upgrade 
#or 
sudo apt-get dist-upgrade
reboot

@sir.sargento, the OP's problem is almost certainly down to the proprietary fglrx driver which gave me a similar problem with an ATI Radeon 5*** card. What graphics card do you have? A simple update/upgrade will almost certainly not help with what seems to be a broken fglrx driver.

---

### Post by meborc on 2011-08-24
> **Yumi said:**
> I always upgraded around Alpha3. We do not expect a fully trouble free experience and the feedback helps developers. Somebody has to find the problems. If you can not accept this, wait until the final version is out.

This discussion is not to complain but to discuss existing problems!

Michael

I must say i disagree a bit here. The success or failure of an upgrade to a DEVELOPMENT version of an operating system depends on so many variables. At least during alpha status when so many big chunks are still changing. Giving the developers notice that an upgrade failed just because there was "partial upgrade state" or dependency hell in the mirrors adds nothing as by next day this issue has already been fixed or new problems have arisen.

Upgrade patch testing is a separate issue and should be tested in beta or RC state when no major breakage is expected. Everyone with an ATI card (me included) should know what kind of mess the fglrx situation is every development cycle and act accordingly.

Just my take on things :)

EDIT: and by the way, fresh install of 11.10 has also problems. in any case some ATI card users have to add radeon.nomodeset=1 to their boot line, read more from - [http://ubuntuforums.org/showthread.php?t=1773851](http://ubuntuforums.org/showthread.php?t=1773851)

---

### Post by TakisX on 2011-08-24
apt-get purge fglrx*
rm /etc/X11/xorg.conf
I run them and it booted with gui but everything is broken , i can not even rebbot

---

### Post by coffeecat on 2011-08-24
> **TakisX said:**
> apt-get purge fglrx*
rm /etc/X11/xorg.conf
I run them and it booted with gui but everything is broken , i can not even rebbot

You can reboot with ctrl-alt-F1 to get a virtual console, log in and:

```
sudo reboot
```

Let's see if we can get the open source driver working by re-installing it and associated packages.

Boot into recovery console again and this time choose "drop to root shell with networking". You need to use a wired ethernet connection. Now:

```
apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
reboot
```

Does that help?

---

### Post by TakisX on 2011-08-24
You are magician man , it worked  !!( with the second reboot )

---

### Post by coffeecat on 2011-08-24
> **TakisX said:**
> You are magician man , it worked  !!( with the second reboot )

I'm glad it worked. You might want to avoid the fglrx driver until after Oneiric goes final, bearing in mind what meborc says (quite rightly) about fglrx during the development cycle. Actually, you might want to avoid the fglrx driver **after** release, but that's another matter! :wink:

In the meantime, you might find a slightly distracting lagginess about some aspects of the Unity desktop in 11.10 with the ATI open source driver, as discussed here:

[http://ubuntuforums.org/showthread.php?t=1831441](http://ubuntuforums.org/showthread.php?t=1831441)

You'll see from posts #13 and #14 that if you install compizconfig-settings-manager and change the Dash Blur value under the experimental tab in the Unity plugin to "no blur" or "static blur", this solves this issue.

Good luck with testing Oneiric!

---

### Post by TakisX on 2011-08-24
I instaled compizcongig-settings-manager but i cant find it in order to check no blur

---

### Post by coffeecat on 2011-08-24
Compizcongig-settings-manager -> Desktop -> Ubuntu Unity Plugin -> Experimental tab -> Dash Blur.

---

### Post by TakisX on 2011-08-24
I cant find this : Compizcongig-settings-manager

---

### Post by coffeecat on 2011-08-24
> **TakisX said:**
> I cant find this : Compizcongig-settings-manager

This is true! :p You made a typo in post #17 and I copied and pasted that into my post #18 without noticing. I need to eat more carrots. Try compizcon[SIZE="4"]f[/SIZE]ig-settings-manager and you should be OK.

---

### Post by TakisX on 2011-08-24
Dont mind the typo i installed it corectly
The problem is that in 11.10 i cant find how i start a program
In ubuntu software center you see the installed programs but no way to run them
The new version totaly broken
I cant start any program exept the ones in the dock in the left

---

### Post by mc4man on 2011-08-24
While the dash is still semi-broken it can work a bit - 
open dash, type in ccsm, it should show up
or
Alt+f2 > ccsm
or browse to /usr/share/applications, d. click on the icon

---

### Post by TakisX on 2011-08-24
I run ccsm it opened and crashed after 5 seconds and everything disappeard from desktop
I rebooted 
How i run the other programs ?
I will make a clean installation the system is broken , you cannot upgrade at the moment from 11.04 to 11.10

---

### Post by coffeecat on 2011-08-24
> **TakisX said:**
> 
I will make a clean installation the system is broken , you cannot upgrade at the moment from 11.04 to 11.10

Is this your only installation of Ubuntu? If so, I suggest you reinstall Natty and delay upgrading until Oneiric is released. General advice is to run an alpha only on a spare partition or spare machine - not to rely on it for day-to-day use. Breakage is to be expected at this stage of development.

---

### Post by TakisX on 2011-08-24
Its the only instalation but i have Arch also
I follow your advise

---

### Post by TakisX on 2011-08-25
I made a clean installation with the latest iso and worked fine with 3007 kernel
Then i run sudo apt-get upgrade and upgraded to 3009 
After reboot everything broke , no launcher bar , ony a an empty desktop
Something is seriously wrong with this release 
After the installation i touched nothing , a virgin installation and it broke down after the first update , who is thid posible ?

---

### Post by meborc on 2011-08-25
> **TakisX said:**
> I made a clean installation with the latest iso and worked fine with 3007 kernel
Then i run sudo apt-get upgrade and upgraded to 3009 
After reboot everything broke , no launcher bar , ony a an empty desktop
Something is seriously wrong with this release 
After the installation i touched nothing , a virgin installation and it broke down after the first update , who is thid posible ?

maybe you should be using 11.04 (stable)

there is a reason why 11.10 is not recommended to be used on production machines. stuff breaks :)

---

### Post by TakisX on 2011-08-25
Yes stuff breaks of course , but after first update ?
You cant use at all in order to test it
I will wait the beta version 
Thanks all of you

---

### Post by meborc on 2011-08-25
> **TakisX said:**
> Yes stuff breaks of course , but after first update ?
You cant use at all in order to test it
I will wait the beta version 
Thanks all of you

It depends WHEN you are doing the first upgrade :) for you it happened to the first, to another guy it might have been the last

unstable development cycle is like that sometimes. I was not able to install a 11.10 from 2-days ago even if I really tried. I got so messed up in fglrx and did not have the time or skill to fix it :D

just try again a few weeks from now. Things will be different (might not be better though)

---

### Post by TakisX on 2011-08-25
Here is my desk top
[ATTACH]200782[/ATTACH]

---

### Post by TakisX on 2011-08-25
Here it is 
In orde to begin firefox i check report a problem and firefox srarts
[ATTACH]200785[/ATTACH]

---

### Post by jerrylamos on 2011-08-25
On un-stable linux's I use multiple partitions.

One partition for what works, the 11.04 or whatever.

Carve out 10 GB partition and install the 11.10 onto it.

That way you can multi-boot whichever one you want to.

If the new linux it works, then gradually set it up & get programs running in it like they are on your existing install.

There are those who claim all you have to do is upgrade.  My experience from time to time upgrades break, so I wind up doing an install every so often especially at Alpha & Beta time.

One of my test pc's might have a Lucid Lynx, a Meerkat, a Natty Narwhal, and a Oneiric Ocelot.  Well, that's likely more than I need, but at least Narwhal and the test Oneiric.

On this pc I've got Narwhal and a couple Oneiric's.

Good luck,

Jerry

---

### Post by TakisX on 2011-08-25
Good luck in a forum about computers xa xa ,,,

---

