---
title: "Replaced NVIDIA 4mx with FX 5500 but it won't work correctly, help!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by jocose on 2008-06-29
Hi friends,

I uninstalled the NVIDIA driver I had installed for my NVIDIA 4 MX card and replaced that card with an NVIDIA FX 5500, and when I started up Ubuntu Hardy again, and installed the restricted driver from the repos "nvidia-glx-new" and rebooted, it came up to a desktop saying it was starting in low resolution, now my desktop in Ubuntu Hardy is 600x480 or 600x400, one of those choices and the NVIDIA driver isn't being used!

I've tried just about everything, google google google and sudo dpkg-reconfigure xserver-xorg, sudo nvidia-xconfigure (or nvidia-xconfig whatever it was I'm too exhausted to remember, but I've tried it several times and that didn't work either), and the command which some have suggested here which they say is sudo nvidia-glx-config enable but the file does not exist.

I've also tried sudo X :1 -scanpci and adding the BusID into the Device Section of xorg.conf, yes it says nvidia there for the driver, it doesn't matter what I try it just will not work! I've rebooted more times than I want to remember, and I had to boot into my WinXP partition just to get a decent resolution to post this in because in Ubuntu it's still low resolution with NVIDIA driver not working! It works fine in Windows, why not in Ubuntu? It has also frozen my system in Ubuntu and I've had to do a hard reboot which I don't like to do.

I've also tried purging and reinstalling nvidia-glx-new nvidia-glx-new-dev nvidia-kernel-common but this does not work either!

Please help me get this card working, I've read a lot of problems with this card in Linux, but I've also read about people say it works.

Please, I'm setting this up for my family today and I really need help finishing the job! Please!! If I cannot get it working I'll have to pull the card and revert my family back to the Geforce 4 MX card which I don't want to do!! :confused:

---

### Post by forger on 2008-06-29
1) Did you by any chance choose envy or downloaded nvidia drivers from nvidia.com website?
If so, I hope that you did uninstall the driver properly using **nvidia-install --uninstall**
If not, then that's the problem, I kind of forgot the files installed by the nvidia installer, but try to reinstall the nvidia from the nvidia website and uninstall it with the command above 

2) FX 5500 is supported by the nvidia-glx-new driver :)

Ok, go to Applications > Accessories > Terminal
```
sudo apt-get install --reinstall nvidia-glx-new nvidia-settings
```

after that do
```
gksudo nvidia-settings
```

click x server display configuration > detect displays > choose your resolution and the refresh rate your want > click "save to X configuration file" > Quit

Log out and log back in, you should be able to use the nvidia drivers

---

### Post by jocose on 2008-06-29
> **forger said:**
> 1) Did you by any chance choose envy or downloaded nvidia drivers from nvidia.com website?

No, I haven't tried envy or the nvidia.com driver, and neither installs were on this drive, the previous driver for the old card was from the official repos.

> 2) FX 5500 is supported by the nvidia-glx-new driver :)


This is nice to hear, but it is not working for me when I try to install it!!

I tried as you instructed and after I installed nvidia-glx-new and went to nvidia-settings it said the drivers weren't installed or enabled and I had to run a command with sudo, which I did and it wanted me to restart X, so I logged out and when I did it flashed a black screen three times with the last line mentioning something about rc. boot scripts or something and then it went to a low resolution box which I had to click to continue past to get to the login screen....

so then I logged in again and the screen froze after a few seconds and locked everything up, I had to do a hard reboot because I couldn't even login in a text terminal f1-f6 no keys pressed would work!

I rebooted and once again the flashing black screen with text and low resolution message... AND ANOTHER FREEZE!

so I hard reboot again....

Same thing happened with a freeze again once I logged into gnome...

Here I am typing this message in Windows XP again... and now I cannot go into Ubuntu desktop without it freezing on me.. if I am quick I can go to terminal #f1 and stop gdm and purge the nvidia-glx-new driver but it still freezes randomly ever since I installed this nvidia fx 5500 pci card, and it is DRIVING ME MAD!!

Why is this not working please help me I am going INSANE! Nothing I try works, I've tried so many things and nothing works! This card works in Windows but apparently not Ubuntu! Why.. WHy.. Whyy... please help me get it working somebody! :confused:

---

### Post by jocose on 2008-06-29
i'm going to try envy and if this doesn't work I will give up on trying to get this card to work on Ubuntu, it's not worth the trouble.

---

### Post by forger on 2008-06-29
FX 5500 is a good card, I think it's worth a shot :)
Can you post back with the contents of **/etc/X11/xorg.conf** file?

Another thing you could do is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
log out and log in
```
sudo nvidia-xconfig
```
log out and log in again

Let's hope this makes it work.
Post **/etc/X11/xorg.conf** again  after this

---

### Post by jocose on 2008-06-29
thank you for following up and the offer for extra help, but I spent four hours or so on it today and I've given up, extracted the foul card from my computer and replaced it with the old one.

so future posters please disregard this thread, I'm going to try another card out instead at a later date.

---

### Post by nowshining on 2008-06-29
it should work - so u gave up - ugh-

---

### Post by jocose on 2008-06-30
> **nowshining said:**
> it should work - so u gave up - ugh-

Hello nowshining,

Yes, I hate to give up, especially with such fine help here, but I had not slept for many, many hours, and the computer had locked up hard requiring a complete manual reboot so many times I often didn't have a chance to do anything at the command line or in a GUI I would have to reboot the computer as pressing no key would do anything! Also, when booting the information the NVIDIA card should show during boot before you enter your BIOS password was a flash of strange text leading me to suspect something was going wrong, even though it worked in WindowsXP, I didn't like what I saw.

I replaced the old card and it should be working but I can't get it working again, it wants to give me resolution errors now so I had to revert to the "nv" driver.

I have a new problem now, I have to reinstall Ubuntu again because I cannot get my old card working now, it flashes at black screen with boot information with some rc. boot message being the final line on the screen and tells me I have to have a low resolution now just like the error with the newer card I tried.

So now my system is hosed, I think, is it possible to reconfigure my old NVIDIA card again *without* having to reinstall Ubuntu? I'm thinking it may take less time to reinstall than it would to try and sort this out again, I sure messed something up..... I think I ruined everything when I followed someone's advice somewhere to start reinstalling the kernel with restricted modules and other modules and now I'm lost trying to get the original NVIDIA card (the nvidia 4 mx) working again!

Edit: I'll do a fresh re-install so please ignore this thread, sorry to waste anybody's time, I was so tired (still am only got a few hours sleep between not having any for a few days) and shouldn't have posted since I didn't have enough power to stay awake, alert, and receptive. I'll know better before I initiate posts from now on!

**Conclusion: I'm reinstalling Ubuntu to fix my hosed nvidia issues** I'm just glad I'm doing this and not my Windows-minded Linux-ignorant family members who wouldn't know anything about the command line. While the card /should/ work as many have said (the fx 5500) it has given me no end of problems and I became so angry at it, and normally I can spend hours hammering away at an issue but when it comes to something so simple as a graphics card there comes a point when you just say enough. It was very frustrating to just uninstall an old driver and reinstall a new one in WindowsXP and have the card *just work* but to be faced with such headaches in Linux. The situation was much worse years ago before the NVIDIA driver became much easier to work with in Linux, so I had assumed it would've been something simple. But now that I can't get my original NVIDIA card working again my only quick option is a complete reinstall, something I was not prepared to do until 2010, as HH is LTS. I can't understand why swapping a gfx card out, especially when I've backed up and regenerated the xorg.conf file and purged old drivers before installing new, would give me issues to the point of causing HARD SYSTEM LOCKS?! I even had the experience of, when switching to the NV driver, trying google earth and being thrown back to the gnome login from simply attempting to run an application! That is wild.

If only NVIDIA would [change](http://news.cnet.com/8301-10784_3-9975720-7.html) their minds about open sourcing the driver (shakes fist at proprietary NVIDIA drivers with disgust).

---

### Post by nowshining on 2008-06-30
ctrl + allt + f2, f3, etc..

ur username

ur pw

ur pw won't show as you type:

a reinstall isn't necessary, and ur system wasn't hosed - u just had to re-install the nvidia drivers and re-configure your xorg.conf file in /etc/X11 or let NVidia do that:

it's quite easy to re-install the nvidia driver esp. the one from the nvidia site.

By the way - the Nvidia driver from the ubuntu repos is not the latest - remove that one and install the one from the nvidia site. That and the opensource ones suck on 3D performance, etc..

---

### Post by jocose on 2008-07-06
> **nowshining said:**
> ctrl + allt + f2, f3, etc..

ur username

ur pw

ur pw won't show as you type:

a reinstall isn't necessary, and ur system wasn't hosed - u just had to re-install the nvidia drivers and re-configure your xorg.conf file in /etc/X11 or let NVidia do that:

it's quite easy to re-install the nvidia driver esp. the one from the nvidia site.

By the way - the Nvidia driver from the ubuntu repos is not the latest - remove that one and install the one from the nvidia site. That and the opensource ones suck on 3D performance, etc..

Yes, thank you for your help nowshining. I know a reinstall shouldn't have been necessary, but it was and I did. I tried everything I could think of and find on any website discussing Linux, Ubuntu, and Nvidia cards, especially this problem, and nothing helped, nothing. I'm not going to go over the many attempts I made to get the card working, or the attempts I made to get the old card working when I replaced it and the same problems existed. My system was locking up hard after the system started, **nothing** I tried could fix that. After a complete reinstall, everything is working fine as it was before I tried to swap Nvidia cards.

I tried the drivers in the repos, I tried envy, I tried the drivers from Nvidia's site, I tried *everything*. I appreciate the desire to help, but this is over and done with, and nothing is going to be resolved or helped by posts continuing to say, "You didn't have to reinstall" or something else, it's **over**. Would I have stretched this issue out for a few more days, it's possible I could've solved it, but I have many other people using this computer, many who kept saying, "Why isn't it simple like in Windows?" and it was trivial to reinstall vs. fighting this problem any further. I've worked with Linux for many years, and I've swapped cards and hardware all of the time without a problem, perhaps this was a BIOS issue, or some other problem specific to this particular system, I don't know, but it's over and done with.

I deeply appreciate the people who were gracious enough to help and encourage me to stick with it and fix it without a reinstall. Had I stuck with it, I may have learned something new, but when you have flapping mouths around you by the computer wondering why something simple isn't being resolved in Linux, which they don't understand, the tension builds until you just decide to reinstall to appease the noise makers.

---

