---
title: "Installed updates, Cinnamon crashes..."
date: 2015-09-23
forum: New to Ubuntu
---

### Post by shelley2 on 2015-09-23
*This is not my personal computer. It is a work computer. I have admin privileges, but I can't do whatever I want.
*I am not a total noob, but I am no wizard. Keep it simple.

I inherited a computer from a person that left our lab. Before he left, he reinstalled Ubuntu so I would have a fresh installation, and he added me as a user. After he was done, some key programs I needed weren't working (Coot, CCP4i, some other crystallography programs). While trying to fix the programs I needed, he did something (I really don't know what, I wasn't here), and the screen went black except for the cursor. All I know is that Unity crashed. He worked on it for two days, and his fix involved installing Cinnamon. 

It was working just fine until I installed some updates today, and now Cinnamon crashes every time I reboot. I keep getting this error message: Xlib:  extension "GLX" missing on display ":0.0".modprobe: FATAL: Module nvidia not found. 

This is my history from today:
Start-Date: 2015-09-23  10:17:22
Commandline: aptdaemon role='role-commit-packages' sender=':1.347'
Upgrade: e2fslibs:amd64 (1.42.9-3ubuntu1.2, 1.42.9-3ubuntu1.3), e2fsprogs:amd64 (1.42.9-3ubuntu1.2, 1.42.9-3ubuntu1.3), libicu52:amd64 (52.1-3ubuntu0.3, 52.1-3ubuntu0.4), libcomerr2:amd64 (1.42.9-3ubuntu1.2, 1.42.9-3ubuntu1.3), mount:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7), libss2:amd64 (1.42.9-3ubuntu1.2, 1.42.9-3ubuntu1.3), libuuid1:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7), libmount1:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7), libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8.1, 2.4.31-1+nmu2ubuntu8.2), bsdutils:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7), uuid-runtime:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7), unity-settings-daemon:amd64 (14.04.0+14.04.20140606-0ubuntu3, 14.04.0+14.04.20150825-0ubuntu2), libblkid1:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7), util-linux:amd64 (2.20.1-5.1ubuntu20.6, 2.20.1-5.1ubuntu20.7)
End-Date: 2015-09-23  10:17:34


Start-Date: 2015-09-23  10:19:03
Commandline: aptdaemon role='role-commit-packages' sender=':1.347'
Upgrade: xul-ext-ubufox:amd64 (3.1-0ubuntu0.14.04.1, 3.2-0ubuntu0.14.04.1), firefox:amd64 (40.0.3+build1-0ubuntu0.14.04.1, 41.0+build3-0ubuntu0.14.04.1), chromium-codecs-ffmpeg-extra:amd64 (44.0.2403.89-0ubuntu0.14.04.1.1095, 45.0.2454.85-0ubuntu0.14.04.1.1097), chromium-browser-l10n:amd64 (44.0.2403.89-0ubuntu0.14.04.1.1095, 45.0.2454.85-0ubuntu0.14.04.1.1097), ubufox:amd64 (3.1-0ubuntu0.14.04.1, 3.2-0ubuntu0.14.04.1), chromium-browser:amd64 (44.0.2403.89-0ubuntu0.14.04.1.1095, 45.0.2454.85-0ubuntu0.14.04.1.1097)
End-Date: 2015-09-23  10:19:13



As far as I can tell, there's no reason that any of these updates would have done anything to Cinnamon. I asked IT dude for help, he suggested updating the BIOS (um...? WTH does that have to do with anything?).

Ideas?

---

### Post by v3.xx on 2015-09-24
Its difficult to get help with cinnamon here.  You have posted in official flavors, but it is not.  There is good support for the flavors both here and at "Ask Ubuntu".  Maybe Unity is not a good fit for your box; whats the specs?

[http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours)

---

### Post by buzzingrobot on 2015-09-24
Well, this:


> **shelley2 said:**
> Xlib:  extension "GLX" missing on display ":0.0".modprobe: FATAL: Module nvidia not found. 

suggests the machine is running on an Nvidia card and the kernel can't find its driver.   A badly installed/configured Nvidia driver, perhaps? 

If Ubuntu detects that an Nvidia card is active, it will default to using the open source Nvidia driver (Nouveau).  The closed source driver available from Nvidia provides better 3D performance typically, but manual installs (and de-installs) of it are sometimes problematic.

If the machine also has Intel video on the board, you could try setting the BIOS to use that instead of the Nvidia. That could give you a workable display so you can  troubleshoot the other issues.

>   I ask ed IT dude for help, he suggested updating the BIOS (um...? WTH does that have to do with anything?).

Almost certainly nothing.

> Ideas?

Nothing brilliant. It's tough to fix problems you didn't make. If you or IT dude are in a position to cleanly reinstall Ubuntu (or Mint if you like Cinnamon) and also reinstall all the software you need, that might be the simplest approach. If you do need the capabilities of Nvidia's proprietary driver, both Ubuntu ("Additional Drivers") and Mint ("Driver Manager")  have tools to display the driver options appropriate for your hardware, and to install and deinstall them. I really recommend using them.

---

### Post by Bucky Ball on 2015-09-24
> **v3.xx said:**
> Its difficult to get help with cinnamon here.  You have posted in official flavors, but it is not.  There is good support for the flavors both here and at "Ask Ubuntu".  Maybe Unity is not a good fit for your box; whats the specs?

[http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours)

[Cinnamon is a desktop environment]("http://cinnamon.linuxmint.com/"), not a distro. Sounds like the OP is using the Cinnamon DE on a regular install. Nothing wrong with asking about the issues here, but as Cinnamon was developed by the Linux Mint team, which isn't an official flavour, getting help with it is another matter. It is quite possibly not about Cinnamon in any case. :)

@shelley2: You are running Cinnamon as a desktop environment on Ubuntu or one of the official flavours, just to confirm?

---

### Post by shelley2 on 2015-09-25
Yes, It's Cinnamon desktop environment on Ubuntu. 

I went through the list of available drivers. None of them were working until I went back to the Nouveau driver that it was using and rebooted again, and then Cinnamon came back and my X-ray crystallography programs work again. I've rebooted this computer several times with this driver and Cinnamon kept going into fallback mode. I'm pretty convinced that this computer hates me.

Thanks for your suggestions.

---

### Post by Geoffrey_Arndt on 2015-09-25
Why not run the "designed for Ubuntu" desktop  . . Unity?   Doing that, along with installing the nvidia proprietary drivers via "System Settings>Software & Updates>Additional Drivers Tab should provide a more stable and functional desktop.  Was it just the nature of Unity (in that it was an unfamiliar desktop metaphor compared to Cinnamon - - a nicer version of the Windows style desktop)??   Using it for a couple weeks would have taken care of that.

---

### Post by shelley2 on 2015-09-28
Because previous computer owner did something that I can't even begin to explain to Unity. He rendered it (and GNOME) useless somehow, and he told me to leave it alone or risk killing the computer. Given how important this computer is to my lab, I'm just going to leave Unity alone. I've used Unity on my personal laptop since it was released, and it was great once I got over the small learning curve. He had some weird grudge against Unity. 

In another annoying twist of events, it seems that previous owner didn't bother to install the correct Nvidia driver when he switched out the cards. . .I udpated to the correct Nvidia driver, and now everything is fine. Doesn't explain why everything worked with no problems for a month. . .

---

### Post by v3.xx on 2015-09-28
> Doesn't explain why everything worked with no problems for a month. . . 
Maybe you had a kernel upgrade.
Check to see if dkms is installed.
```
apt-cache policy dkms
```

[https://wiki.archlinux.org/index.php/Dynamic_Kernel_Module_Support#Usage](https://wiki.archlinux.org/index.php/Dynamic_Kernel_Module_Support#Usage)

---

