---
title: "Dell - Inspiron 7000 Series - 7567 - Ubuntu Nvidia Driver Installation Issues &amp; Steam"
date: 2018-12-09
forum: New to Ubuntu
---

### Post by turpsicon on 2018-12-09
Hi All,

I hope this isn't a repost but i'm getting desperate now.

Its been a while (6 days+) since i've been trying to change from Windows 10 (64bit) to Ubuntu 16.04 or even 18.04 and i feel like I'm having countless problems.
I wanted to move to ubuntu to learn the OS and got sick of so much maintenance work needed to be done on the Windows environment.

The experience hasn't been great so far and I've been doing so many re-installs I'm now here hoping someone will help me.
I've done all the possible research I could and haven't found any answers as yet, or maybe i'm not a good googler.

Initial Problems:

Freezing: This i manage to sort out myself by editing the grub using - acpi_osi=! and acpi_osi='Windows 2009'

Biggest Problem:

NVidia Driver Installation - It seems whenever I get to this process it never goes well. I first attempted on 16.04, got it working miraculously but then I moved to 18.04 (by format re-install) realized afterwards, this isn't working because I can't get primus to run discretely (see: [https://support.steampowered.com/kb_article.php?ref=6316-GJKC-7437](https://support.steampowered.com/kb_article.php?ref=6316-GJKC-7437)) when using steam.

CURRENTLY: 

When checking on the nvidia website, it shows 410 is what I should get, so I always attempt installing the recommended proprietary drivers ([COLOR=#333333]ppa:graphics-drivers/ppa), go to my additional drivers select 410 however before i reboot I install bumblebee, bumblebee-nvidia and primus using the Synaptic Package Manager and afterwards rebooting.
Big mistake, once i reboot, I can't get back into ubuntu as it freezes again, no mouse, can't even enter the account I've created. I can't get into terminal just before the login screen of the gui (by using CTRL+ALT+F1) and if I take too long it will freeze there too. So I'm forced to use the recovery method, attempt to fix it, which is where i'm always getting stuck.
I have no idea what else to do, I've tried nomodeset  in the grub, that hasn't worked. So I really dont know what to do.

STEP-by-STEP (current):

USB installation of Ubuntu (16.04.5 AMD64)
Hit-e (for installation) add - acpi_osi=! acpi_osi='Windows 2009' [after splash]
gui installation process - Logon to Wireless
3rd Party for Graphics,Wireless,etc. selected (no download of updates selected)
3 Partitions created (sda1 - UEFI part boot, sda2 - ubuntu [ext4], sda3 - 32GB swap)
[Installation Done] - REBOOT
apt-get update
Install Synaptic Package Manager
Perform updates - REBOOT

add properietary ([/COLOR][COLOR=#333333]ppa:graphics-drivers/ppa)
[/COLOR][COLOR=#333333]Select 410 drivers, 
[/COLOR][COLOR=#333333]install bumblebee, bumblebee-nvidia and primus as well as bbswitch using the Synaptic Package Manager, REBOOT

[/COLOR][COLOR=#333333]GUI FREEZE

I think its got something to do with xorg, but im not sure... Like i said, i've run out of ideas.

Machine Specs:

[/COLOR]Brand    DellSeries    Inspiron 7000 Series
Model    7567
Graphics     NVIDIA GeForce GTX 1050 Ti 4GB GDDR5
Previous OS Windows 10 Home 64-bit

Can someone please help me.
[COLOR=#333333]
[/COLOR]

---

### Post by turpsicon on 2018-12-09
My apologies for placing this here, I wasn't sure where to post this.

So if any of the moderators can move this post to the appropriate area, I'd appreciate it.

Either : Installation & Upgrades or General Help or Hardware (As I said, I have no idea where this should go)

---

### Post by oldrocker99 on 2018-12-09
The Ubuntu method of installing nVidia drivers for you is this:
```
sudo apt purge nvidia*
sudo add-apt repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-driver-415
reboot
```

That will get your apparently hosed nVidia installation, and give you a repository, so that the driver will be upgraded if it has a new version automagically.

Good luck!

---

### Post by oldfred on 2018-12-09
You should not now be installing bumblebee and need to also purge all of that.
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

Note page not updated since 2015
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
With 16.04
[https://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u](https://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u)
Some of issues of getting kernel, drivers & support software all working together with 16.04 and some of the later versions.
[https://ubuntuforums.org/showthread.php?t=2329171](https://ubuntuforums.org/showthread.php?t=2329171)

But you really should be installing 18.04 as Dell does many updates and they eventually get included in kernel, support software & drivers that are in a distribution. Than can take a while, but older version installs will not have any of the updates.

---

### Post by turpsicon on 2018-12-09
@oldrocker99 - Thanks for the advice, i'm gonna try the below suggestion.

@oldfred 

Ok, Let me go and format-reinstall with 18.04 LTS (again) and see. I'll give feedback about this once I'm done installing just backing up some stuff.

---

### Post by oldfred on 2018-12-09
Some other Dell 7000 series & issues they had.

       DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

---

### Post by turpsicon on 2018-12-10
Well, I did as you guys suggested.
Reformatted. Ubuntu 18.04 installed.
I've added the necessary boot parameters in grub for this as well.
acpi_osi=! acpi=_osi='Windows 2009'

I was though a bit too scared to do the installation manually, so instead I've added the ppa-graphics, updated then in terminal decided to run the following.

ubuntu-drivers devices [then]
ubuntu-drivers autoinstall [reboot via gui / sudo reboot]

Installation of drivers went smoothly, no freezing, nothing. The only thing that bothers me now, is attempting to run my games using the gfx card (discretely) via steam.

As I said before, I saw a link for steam using primusrun %command% inserted under launch options.
Having to switch using primus-select (logoff and on) is slightly annoying.

I wonder if anyone has queried this on the forums lately.

---

### Post by turpsicon on 2018-12-10
> **oldfred said:**
> Some other Dell 7000 series & issues they had.

       DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

Thanks for the additional info... will look at it right now.

---

