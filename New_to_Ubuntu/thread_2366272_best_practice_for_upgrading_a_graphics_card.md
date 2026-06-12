---
title: "best practice for upgrading a graphics card"
date: 2017-07-15
forum: New to Ubuntu
---

### Post by gazzawazza on 2017-07-15
hi all

I've done some research on how to approach changing my graphics card. However, I'm still somewhat unclear on best practice.

I'm very strong in the Windows environment, so understand about need to get the driver situation right.

My crude, bumbling investigation on lubuntu might point to me not having any graphics card drivers installed (certainly not proprietary).

The only thing listed under additional drivers in software & updates refers to AMD microcode, which I know is CPU related (as I have an athlon XP 1800+).

I've run sudo ubuntu-drivers devices and it just returns:

"== cpu-microcode.py ==
driver   : amd64-microcode - distro non-free"

My current card (VGA controller) is reported as an **nvidia NV11 geforce2 MX400**.

I'm looking to try an ATI 3d prophet 9800 pro (since it's in theory more powerful and is just lying around). So, particularly as I'm switching GPU manufacturers, I was particularly aware of needing to think about clean driver installs, etc.

My current "display vendor" (i'm guessing this is the VGA driver provider?) is X.ORG, so presumably this is the open VGA driver?

Or does it mean that my GPU is so antiquated, I'm not getting any hardware assisted graphics tasks (and it's all on the CPU)?

I've found that "xserver-xorg-video-nouveau X.Org X server -- Nouveau display driver  1:1.0.12-1build2" is installed so I guess that's my VGA driver.

I've read about open source ATI and nouveau drivers or I can resort to nvidia, which I swear i read somewhere does not play happily with nouveau.

Due to the age of my nvidia card, I'm struggling to find ubuntu nvidia  drivers for it, so can't test whether they're an improvement on nouveau.  Whereas, i have confirmed on the ubuntu radeondriver help page that the  9800 pro is supported.

So, what would people recommend? What's a good procedure to follow in linux for removing drivers and installing new ones, etc?

Thanks for any help.

Btw, I'm running 16.04.2 LTS lubuntu





Regards,

Gary

PS I genuinely have been reading round the topic (i found, amongst others, the ubuntu help pages on radeon - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) - and nvidia - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) - to be good) but would like to pick peoples' brains because I'm so new and inept with linux :)

---

### Post by deadflowr on 2017-07-15
Both cards are old and best to try the open-source drivers for them, either way you slice it.
(There are no closed-source drivers for the ati card and I don't think the nvidia card has drivers available for it on Ubuntu anymore anyway)


> I've read about open source ATI and nouveau drivers or I can resort to nvidia, which I swear i read somewhere does not play happily with nouveau.
Somewhat confusing, but in terms of nouveau versus nvidia driver, they are two different driver that would be the driver for the same thing, and you cannot have one device using two different drivers.
(Nividia gets around this by defaulting a blacklist of the nouveau driver)


At the end of the day, though, since you do not have any closed-source drivers installed, if you wanted to switch out the nvidia card for the ati card, it should not be any problem.
Since you more than likely would have the open-source radeon driver installed and ready to be used.

(the radeon and nouveau drivers do not conflict with one another like the nvidia and nouveau do.)

Is any of that not confusing?
(or was I always the confused one here?)

---

### Post by vocx on 2017-07-15
> **gazzawazza said:**
> hi all

I've done some research on how to approach changing my graphics card. However, I'm still somewhat unclear on best practice.

I'm very strong in the Windows environment, so understand about need to get the driver situation right.

My crude, bumbling investigation on lubuntu might point to me not having any graphics card drivers installed (certainly not proprietary).


Anyway, basically the "drivers" in the Linux world are included in the Linux kernel. If you check your system you will find many subdirectories under "/lib/modules/[version]/kernel/". The many directories are there by vendor, brand, type, model, or so on. And it's for many different types of devices such as mice, keyboard, video card, ethernet card, wifi card, usb, etc. All the ".ko" files are the "kernel objects", that is, the kernel modules, or drivers which actually interface with your hardware. **So you do have many many drivers installed**, even if you did not manually install them. Whenever you plug in a device, hard drive, mouse, video card or so, the kernel detects this and "plugs" the correct module. When you see people running the "lsmod" command, it is to show all the kernel modules currently in use.

Occasionally you need to run
```

modprobe -i [module]
modprobe -r [module]

```
to load a module or unload a module from use. But if the kernel detects everything right, you don't need to do this at all.

> 
...

My current card (VGA controller) is reported as an **nvidia NV11 geforce2 MX400**.

I'm looking to try an ATI 3d prophet 9800 pro (since it's in theory more powerful and is just lying around). So, particularly as I'm switching GPU manufacturers, I was particularly aware of needing to think about clean driver installs, etc.

In actuality there are basically three types of video card: integrated into the motherboard with the CPU, such as Intel cards, and discrete cards, either Nvidia or ATI. A few years ago, ATI was acquired by AMD, so now the branding of their cards is AMD/ATI, or just AMD.

For the longest time, Linux did not work properly with Nvidia and ATI/AMD cards because they are mostly high performance, expensive cards, intended for running video games in Windows. Therefore, the Linux community had problems making them work right. Realize that Nvidia and ATI/AMD are hardware manufacturers of integrated circuits. Making an integrated circuit is a secretive task as it constitutes highly valued intellectual property. Therefore, these vendors did not release enough information about their devices to make them work correctly under Linux. I believe over the last 10 years they have released better drivers, so support for Linux has improved.

So, in the Linux world there was always the question whether to use open source drivers, such as "nouveau" and "radeon", developed by the community, or the proprietary drivers, like "nvidia" and "fglrx", released by Nvidia and ATI/AMD. Occasionally, the open source driver would be better, or the other way around. Nowadays, I believe the closed source drivers actually work quite well.

My best recommendation before buying a new video card is browsing online for forum posts, blogs, and other information for users' experience with that particular card under Linux. They will usually mention whether it works outside of the box, or whether you need to do something special for it, or get a new driver.

> 
My current "display vendor" (i'm guessing this is the VGA driver provider?) is X.ORG, so presumably this is the open VGA driver?

Or does it mean that my GPU is so antiquated, I'm not getting any hardware assisted graphics tasks (and it's all on the CPU)?

Forget about X.Org. This refers to the X11 Window System, which is a complicated thing to explain. It is basically a framework that allows you to see things on screen. It has existed since the early 1990s and it's basically standard for all Linux systems today.

> 
I've found that "xserver-xorg-video-nouveau X.Org X server -- Nouveau display driver  1:1.0.12-1build2" is installed so I guess that's my VGA driver.

You are using the "nouveau" driver for your Nvidia card.

> 
I've read about open source ATI and nouveau drivers or I can resort to nvidia, which I swear i read somewhere does not play happily with nouveau.

Nvidia and ATI/AMD are two different brands, so their cards need each their respective driver.

For Nvidia cards, you can use either "nvidia" or "nouveau", you cannot use both drivers at the same time. As "nouveau" is open source, it is already installed in your system. If you install the "nvidia" driver, what happens is the "nouveau" driver is blacklisted, so it cannot interfere with "nvidia".

> 
Due to the age of my nvidia card, I'm struggling to find ubuntu nvidia  drivers for it, so can't test whether they're an improvement on nouveau.  Whereas, i have confirmed on the ubuntu radeondriver help page that the  9800 pro is supported.

Basically, you cannot use the new "nvidia" driver for your old card. Your card is only supported by the old "nouveau" driver. Trying to use the newer driver will not work.

On the other hand, if you confirmed that the ATI/AMD card that you wish to buy works with the "radeon" driver, then sure, go with that.

> 
So, what would people recommend? What's a good procedure to follow in linux for removing drivers and installing new ones, etc?

Thanks for any help.

Btw, I'm running 16.04.2 LTS lubuntu





Regards,

Gary

PS I genuinely have been reading round the topic (i found, amongst others, the ubuntu help pages on radeon - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) - and nvidia - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) - to be good) but would like to pick peoples' brains because I'm so new and inept with linux :)

Read about the other people's experience with the card you want to buy, before you buy. My recommendation would be to not buy a very new card. Don't buy something that came out this year, as the drivers for it are probably not working correctly at this moment, and you may have bugs. I would buy something that is a few years in the market and that threads online say is well supported and just works. But I'm not a gamer, so actually I cannot give suggestions about performance.

In general, you do not need to bother about "removing drivers and installing new ones", or having a "clean" install. As when you have a new card, your system will immediately try to use another driver for it. All the drivers in the "/lib/modules/" directory are "installed" but they don't interfere with your current system, because they are only loaded when the specific device for it is plugged into your system.

Basically, you have only five options
[LIST]
[*]Integrated Intel video. It uses the standard intel drivers, "i915", and works out of the box without problems. 
[*]Nvidia card, old. It uses the "nouveau" drivers. 
[*]Nvidia card, new. It uses the "nvidia" driver (proprietary). 
[*]ATI/AMD card, old. It uses the "radeon" driver. 
[*]ATI/AMD card, new. It uses the "flgrx" (proprietary). 
[/LIST]

Your system will try to use the correct one for your card. If the card you have refuses to work properly with one of those drivers, then really, at this moment your card may be incompatible with Linux.

---

### Post by gazzawazza on 2017-07-15
> **deadflowr said:**
> Both cards are old and best to try the open-source drivers for them, either way you slice it.
(There are no closed-source drivers for the ati card and I don't think the nvidia card has drivers available for it on Ubuntu anymore anyway)



Somewhat confusing, but in terms of nouveau versus nvidia driver, they are two different driver that would be the driver for the same thing, and you cannot have one device using two different drivers.
(Nividia gets around this by defaulting a blacklist of the nouveau driver)


At the end of the day, though, since you do not have any closed-source drivers installed, if you wanted to switch out the nvidia card for the ati card, it should not be any problem.
Since you more than likely would have the open-source radeon driver installed and ready to be used.

(the radeon and nouveau drivers do not conflict with one another like the nvidia and nouveau do.)

Is any of that not confusing?
(or was I always the confused one here?)

not at all confusing

Basically I'd have an potential driver conflict to manage/avoid if i went from nouveau to nvidia but that's not a problem because of a lack of nvidia drivers (I'd come to the same conclusion - i couldn't find any nvidia drivers, so there aren't any on ubuntu) but things should be fine jumping between Radeon and Nouveau.

Cheers deadflowr :)

---

### Post by gazzawazza on 2017-07-15
> **vocx said:**
> Anyway, basically the "drivers" in the Linux world are included in the Linux kernel. If you check your system you will find many subdirectories under "/lib/modules/[version]/kernel/". The many directories are there by vendor, brand, type, model, or so on. And it's for many different types of devices such as mice, keyboard, video card, ethernet card, wifi card, usb, etc. All the ".ko" files are the "kernel objects", that is, the kernel modules, or drivers which actually interface with your hardware. **So you do have many many drivers installed**, even if you did not manually install them. Whenever you plug in a device, hard drive, mouse, video card or so, the kernel detects this and "plugs" the correct module. When you see people running the "lsmod" command, it is to show all the kernel modules currently in use.

Occasionally you need to run
```

modprobe -i [module]
modprobe -r [module]

```
to load a module or unload a module from use. But if the kernel detects everything right, you don't need to do this at all.


In actuality there are basically three types of video card: integrated into the motherboard with the CPU, such as Intel cards, and discrete cards, either Nvidia or ATI. A few years ago, ATI was acquired by AMD, so now the branding of their cards is AMD/ATI, or just AMD.

For the longest time, Linux did not work properly with Nvidia and ATI/AMD cards because they are mostly high performance, expensive cards, intended for running video games in Windows. Therefore, the Linux community had problems making them work right. Realize that Nvidia and ATI/AMD are hardware manufacturers of integrated circuits. Making an integrated circuit is a secretive task as it constitutes highly valued intellectual property. Therefore, these vendors did not release enough information about their devices to make them work correctly under Linux. I believe over the last 10 years they have released better drivers, so support for Linux has improved.

So, in the Linux world there was always the question whether to use open source drivers, such as "nouveau" and "radeon", developed by the community, or the proprietary drivers, like "nvidia" and "fglrx", released by Nvidia and ATI/AMD. Occasionally, the open source driver would be better, or the other way around. Nowadays, I believe the closed source drivers actually work quite well.

My best recommendation before buying a new video card is browsing online for forum posts, blogs, and other information for users' experience with that particular card under Linux. They will usually mention whether it works outside of the box, or whether you need to do something special for it, or get a new driver.


Forget about X.Org. This refers to the X11 Window System, which is a complicated thing to explain. It is basically a framework that allows you to see things on screen. It has existed since the early 1990s and it's basically standard for all Linux systems today.


You are using the "nouveau" driver for your Nvidia card.


Nvidia and ATI/AMD are two different brands, so their cards need each their respective driver.

For Nvidia cards, you can use either "nvidia" or "nouveau", you cannot use both drivers at the same time. As "nouveau" is open source, it is already installed in your system. If you install the "nvidia" driver, what happens is the "nouveau" driver is blacklisted, so it cannot interfere with "nvidia".


Basically, you cannot use the new "nvidia" driver for your old card. Your card is only supported by the old "nouveau" driver. Trying to use the newer driver will not work.

On the other hand, if you confirmed that the ATI/AMD card that you wish to buy works with the "radeon" driver, then sure, go with that.



Read about the other people's experience with the card you want to buy, before you buy. My recommendation would be to not buy a very new card. Don't buy something that came out this year, as the drivers for it are probably not working correctly at this moment, and you may have bugs. I would buy something that is a few years in the market and that threads online say is well supported and just works. But I'm not a gamer, so actually I cannot give suggestions about performance.

In general, you do not need to bother about "removing drivers and installing new ones", or having a "clean" install. As when you have a new card, your system will immediately try to use another driver for it. All the drivers in the "/lib/modules/" directory are "installed" but they don't interfere with your current system, because they are only loaded when the specific device for it is plugged into your system.

Basically, you have only five options
[LIST]
[*]Integrated Intel video. It uses the standard intel drivers, "i915", and works out of the box without problems. 
[*]Nvidia card, old. It uses the "nouveau" drivers. 
[*]Nvidia card, new. It uses the "nvidia" driver (proprietary). 
[*]ATI/AMD card, old. It uses the "radeon" driver. 
[*]ATI/AMD card, new. It uses the "flgrx" (proprietary). 
[/LIST]

Your system will try to use the correct one for your card. If the card you have refuses to work properly with one of those drivers, then really, at this moment your card may be incompatible with Linux.

Thanks for the epic and very usefully detailed reply Vocx.

I see you removed your comment about windows experts. To be fair, I'm such a noob on linux i'd not taken offence. I didn't say i was an expert - perhaps i should have said strongly familiar. I have longitudinal experience with a lot of Windows OSs (from DOS onwards to win 10 and server 2012). My experience has been as a user, power-user (i guess), techie and certed IT admin / 1st line tech (but not reading from a script - I've got foundation knowledge in networking, file and folder permissions, drivers, printers, VMs, a wee bit of powershell (for cloud services batch user management), web admin (bit of joomla), etc, etc, but still have quite some way to go before I'd consider myself a competent 2nd line engineer). I build my PCs and therefore have to troubleshoot them. I've done a bit of clumsy programming (Excel and Access VBA) but at no point would i call myself a coder.

I think the thing i like already about linux is that I sense I'll get a much better overview of how systems operate and interact using it, since while the desktop environment works ok, i feel the bare bones are very very close to the surface. It's just a steep learning curve, since I've only used windows (so don't have any transferable skills from, say, UNIX), and I'm having to learn how to do tasks i took for granted/was very familiar with, in Windows.

In regard to your excellent post, basically i was just tidying up this morning and threw away some very old GPU cards, only to realise they were compatible with my current linux box (which resulted in some comic bin rummaging and recovery mins later), so I've already got the ATI card I referred to. I'm just trying to breath some life into a WinXP box and also properly dabble with Linux, to expand my knowledge and understanding. I'm about to buy a Pi 3 too, to have a play with Pi-Hole (rather excited by this actually).

Thanks for the info about how drivers are managed (kernel-wise), the difficulties in developing linux GPU drivers and the breakdown of appropriate drivers depending on age and GPU. All very useful and informative. You must have spent some time too on your post - i appreciate it.



Regards,

Gary

---

### Post by vocx on 2017-07-15
> **gazzawazza said:**
> Thanks for the epic and very usefully detailed reply Vocx.

I see you removed your comment about windows experts. To be fair, I'm such a noob on linux i'd not taken offence. I didn't say i was an expert - perhaps i should have said strongly familiar. I have longitudinal experience with a lot of Windows OSs (from DOS onwards to win 10 and server 2012). My experience has been as a user, power-user (i guess), techie and certed IT admin / 1st line tech (but not reading from a script - I've got foundation knowledge in networking, file and folder permissions, drivers, printers, VMs, a wee bit of powershell (for cloud services batch user management), web admin (bit of joomla), etc, etc, but still have quite some way to go before I'd consider myself a competent 2nd line engineer). I build my PCs and therefore have to troubleshoot them. I've done a bit of clumsy programming (Excel and Access VBA) but at no point would i call myself a coder.

Ha ha. I didn't remove it. The moderators did. I guess they thought I was being unnecessarily sarcastic. But it was just a joke. My intention was to poke fun at the situation of changing environments. It is a matter of fact that even if you are very good at something you may have to learn more things when you are outside your element. Just look at Michael Jordan. The guy won three NBA championships, being the most dominant player ever. Then he retired to play baseball, and unsurprisingly, he was not good at it. He returned to play professional basketball after 18 months, and he continued dominating basketball, and won three more championships! That's just unbelievable.

> 
I think the thing i like already about linux is that I sense I'll get a much better overview of how systems operate and interact using it, since while the desktop environment works ok, i feel the bare bones are very very close to the surface. It's just a steep learning curve, since I've only used windows (so don't have any transferable skills from, say, UNIX), and I'm having to learn how to do tasks i took for granted/was very familiar with, in Windows.

I think the learning curve depends on your previous knowledge. Twenty years ago, graphical interfaces were not so developed, so even if you learned computing in Windows you would learn a bit about the command line, and stuff like that. Nowadays it's more about the interfaces.

> 
In regard to your excellent post, basically i was just tidying up this morning and threw away some very old GPU cards, only to realise they were compatible with my current linux box (which resulted in some comic bin rummaging and recovery mins later), so I've already got the ATI card I referred to. I'm just trying to breath some life into a WinXP box and also properly dabble with Linux, to expand my knowledge and understanding. I'm about to buy a Pi 3 too, to have a play with Pi-Hole (rather excited by this actually).

Yes, I realized that you already have the card. My point is, for anybody looking to buy a new card, the same advice stands. Don't just buy it. Do your research to see if it is supported by the new drivers, or by the old drivers, or if it's not supported at all. Unfortunately I feel some people jump into Linux without doing their homework and become disillusioned and upset, so it's better to know what to expect.

> 
Thanks for the info about how drivers are managed (kernel-wise), the difficulties in developing linux GPU drivers and the breakdown of appropriate drivers depending on age and GPU. All very useful and informative. You must have spent some time too on your post - i appreciate it.



Regards,

Gary
Yes, I spent like a whole 30 minutes! That's a whole lot of milliseconds. Imagine all the CPU cycles I could have used for something else. I even went to lunch 20 minutes late.

---

### Post by gazzawazza on 2017-07-23
Just to update and close the thread, replacement GPU card is working fine, though gets rather warm. ATI 9800 pro (instead of a passively cooled geforce2 mx400). I can run glmark2 now because I've got openGL2. Wouldn't before because of paltry openGL1.2. Hasn't made any difference to day-to-day use but the glmark2 demos are pretty :D

Put a bit of cooling in the  case (it's sole exhaust fan was through the PSU), so it's now got a massive 60mm case fan lol (yes that was the case cut-out available - shows how old the case is) and a neat little system blower. I've managed to move the HDs to a suspended cage too and have knocked 6 degrees off their operating temp.

And I've got a raspberry Pi3 running lubuntu 16.04.2 and pi-hole.

Probably time to go an do some Windows Cert exam revision and stop fiddling with linux.

EDIT: it's not that I'm done with linux. Just that I need to stop getting consumed and distracted by a new OS and learning about that, when I need to stuff my head with Windows nonsense to pass an exam :)

Thanks for everyone's help.



Cheers,

Gary

---

### Post by Yellow Pasque on 2017-07-24
Please mark the thread solved (thread tools menu above first post).

---

