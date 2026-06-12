---
title: "nVidia drivers won't install."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Vondurr on 2008-10-05
Hey :)

I'm trying to install Ubuntu on my Asus laptop, but I've hit a roadblock with getting the nVidia drivers working. I'm not sure what information is relevant here, but the laptop is about a year old, it has an nVidia GeForce 8400 256mb graphics card. Until now it's been running on Vista and I haven't had any problems with the card, so I doubt there's anything wrong with it.

I've been trying to fix this for a while now, googling relentlessly to find someone with a similar problem, but no matter what I try it doesn't seem to work.

The automatic hardware driver installer gives me this error:

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

I tried EnvyNG, but it told me to run nvidia-xconfig and then restart, which I did, but it had no effect. All it did was to give me a prompt when I start the computer saying I'm running in low graphics mode and should choose my monitor/graphics card from a list to be able to change resolution. After trying virtually every combination on that list I gave up and searched for other options.

I found some guides on various forums, but nothing worked. So, I'm thinking this is my only option at this point.

Anyone have a clue on how to fix this? If you need more information just ask. I'll reply as soon as possible.

P.S. I've reinstalled Ubuntu, so I'll be starting with a clean slate.

---

### Post by BDNiner on 2008-10-05
Try running
```

sudo dpkg-reconfigure xserver-xorg

```
and follow the prompts and tell us what happened.

---

### Post by Vondurr on 2008-10-05
sudo dpkg-reconfigure xserver-xorg

--

Use kernel framebuffer device interface?  
Yes.

Autodetect keyboard layout?
Yes.

Keyboard Layout:
se

XKB rule set to use:
xorg

Keyboard model:
pc105

Keyboard variant?
(blank)

Keyboard options:
(blank)

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081005210455

---

### Post by BDNiner on 2008-10-05
Is your video display back to normal?

---

### Post by falkTX on 2008-10-05
I always installed the NVIDIA drivers manually
(by changing to a shell, kill the GDM, and install it)

Never had problem with it

---

### Post by Vondurr on 2008-10-05
Well, it's stuck in 800x600 and can't go higher due to the lack of drivers. It's been like that since I installed. The default system works like it should, I just can't get the drivers in so I can change my resolution

---

### Post by falkTX on 2008-10-05
I find out!

Run in a terminal:
"sudo gedit /etc/default/linux*"
(if you don't have "gedit" installed, change it to "nano")

And at the bottom add "nv nv_new", like this:

DISABLED_MODULES:"nv nv_new"


Keep others if there's any.

I'm not sure how it works, but it solved my problem some time ago before I changed to SUSE

---

### Post by BDNiner on 2008-10-05
How are you trying to change the resolution? are you using the built in ubuntu GUI, manually editing the xorg.conf from the command line or running the nvidia-settings tool? the nvidia-settings tool needs to be run as root to work. That is how i normally change my resolution. it is in the respositories so you should be able to install it if you don't have it.

---

### Post by Vondurr on 2008-10-05
I'm trying to change it through the Ubuntu GUI (System -> Preferences -> Screen Resolution). I can choose either 800x600 or 640x480. The video card is capable of a lot better than that. I can't actually install the drivers so I can't run any configs there. How can I get it from the repositories?

---

### Post by falkTX on 2008-10-05
Here's what you have got to do:

1. Run the "sudo gedit /etc..." like I mencioned before;
2. Install the NVIDIA drivers manually (using sudo sh NVIDIA-xxx...)
3. When the NVIDIA setup is almost finished, click yes when it prompts to modify the xorg.conf file
4. Reboot

You're done

This always worked for my NV-7400

EDIT:
If you still have low resolutions, just edit the /etc/X11/xorg.conf manually, but be careful

---

### Post by Vondurr on 2008-10-05
> sudo sh NVIDIA-Linux-x86-173.14.12.pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.14.12.pkg1.run

Do I download it and place it somewhere before running it, or does this get it from a repository?

---

### Post by BDNiner on 2008-10-05
can you post the output of your /etc/apt/sources.list? I think that there could be an issue with the repositories you have listed.

---

### Post by Vondurr on 2008-10-05
/etc/app/source.list comes up as empty, surely that's not right? It's just a text file with nothing in it.

---

### Post by BDNiner on 2008-10-05
it is /etc/apt/sources.list

make sure you spell it correctly.

---

### Post by Vondurr on 2008-10-05
> #deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

read it as "app", when it gave me a text file I took that as positive feedback, nvm :p

---

### Post by BDNiner on 2008-10-05
Ok we need to edit that file.

gksudo gedit /etc/apt/source.list

See these last lines.
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

change them to look like this
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security multiverse

Then save the changes

Then in a terminal
sudo apt-get update && sudo apt-get upgrade
Then try and install the hardware drivers again.

---

### Post by Vondurr on 2008-10-05
after the updates the hardware drivers manager is now empty, but still can't change my resolution. 

off to bed for tonight, thanks for all the help so far :)

---

### Post by BDNiner on 2008-10-18
It has been about a week since you last posted. how is your resolution? did you change the repositories back to security from the archives and try to install the drivers again?

---

### Post by christianvaldes on 2008-10-21
I have an 8800 GT Nvidia Video Card.

The Ubuntu Drivers worked at one point for me but I found they did not work as well as the drivers on the Nvidia website.

You should download that package of there website.

[http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)

While your in X...

Get to a command prompt.

<CTRL><ALT><F1>

Then login from there and do a....
(make sure your in the right directory where you have downloaded the installation package from the Nvidia site)
sudo NVIDIA-Linux-x86-177.80.pkg1.run

Follow the installation instructions.

Please let me know if this gets your driver up and running for your video card.  I spent lots of time getting mine going and these steps have worked everytime I needed to install the driver after updates.

---

### Post by artsci2 on 2008-10-25
I'm stuggling through the monitors issues too. One problem I found in searching is that the proprietary drivers are not ready for Ubuntu 8.10. Did you upgrade to 8.10?

---

