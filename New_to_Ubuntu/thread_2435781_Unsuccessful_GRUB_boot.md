---
title: "Unsuccessful GRUB boot"
date: 2020-01-25
forum: New to Ubuntu
---

### Post by paultb70 on 2020-01-25
After accidentally closing the terminal during a get update command, I tried to use the GRUB boot recovery mode l and ran it without any root modifications. Now I can’t get back to the GRUB window even when I restart my computer to try some of the root commands I’ve found on this forum. When I initially did the boot I let my computer run for over 4 hours and it’s still showing a blinking cursor with an otherwise completely black screen. Is there any option I can use in BIOS to get this back? I haven’t been able to access anything but the Strtup menu when I hit shif/excel before Ubuntu appears.

---

### Post by Bashing-om on 2020-01-25
paultb70; Yukkie :(

But A Welcome to the forum :)

Let's have a look at the hard drive so we know what we are working with.

Boot up the liveDVD/USB that you used to install ubuntu in the "try ubuntu" mode.
Activate a terminal in this live mode and post back the result of terminal command:
```

sudo fdisk -lu

```

and we look and see about the boot code.

[INDENT][INDENT]gots to start somewhere
[/INDENT][/INDENT]

---

### Post by paultb70 on 2020-01-25
Thank you for the reply!

Unfortunately, I've had Ubuntu for a couple years now and I can't quite remember how I installed it originally (I think it was a virtual USB). I've tried all the boot options from the startup menu and none have led to any success (I of course can try to let them run longer).

---

### Post by Bashing-om on 2020-01-25
paultb70; Still yukkie :(

If the system does not boot in a matter of seconds, there is a problem.
If you can not boot to the grub boot menu - there is a problem.

And, the only way I know forward in such a case is to boot up a live environment. From this live environment we can have a looksee. If you no longer have the installer on hand, then you will need to makeup a liveDVD/USB of the installed version.

We must have access to the installed system in order to see what the root of the issue may be, and that my friend is the role of the live environment.

[INDENT]with a liveUSB
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT]

---

### Post by paultb70 on 2020-01-25
So are you saying I need to get a physical USB drive? I&#8217;d so what do I need to put on it and how do I configure the startup to use it. Thanks again!

---

### Post by oldfred on 2020-01-25
Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

If not Ubuntu, but one of its flavors:
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

You only need a 4GB flash drive, and it will be erased with most of the ways the installer is created.
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by paultb70 on 2020-01-26
[IMG]https://imgur.com/92EPrjc[/IMG]I did a live USB boot and am able to access a terminal window. Where do I go from here? I ran the command you suggested but I didn't see anything out of the ordinary. I did the standard update commands as well but I doubt that did anything since the issue is not on the usb's version of ubuntu. I also did a disk check and found no errors. 

When I was rebooting, I got this error message for a few seconds that has been flickering on my screen previously if it's any help. [IMG]https://imgur.com/92EPrjc[/IMG][ATTACH=CONFIG]284907[/ATTACH]

[https://imgur.com/a/GICww8W](https://imgur.com/a/GICww8W)

---

### Post by oldfred on 2020-01-26
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Most of the warnings you can ignore.
The one on db list is often related to UEFI settings for Secure boot or version of grub.
Did you change to/from UEFI Secure Boot. Or are you also booting Windows which with an update may have changed it?
Or do you have multiple installs or an old install's boot loader and system is trying to boot that?
Report should clarify some of those issues, but does not show UEFI settings, so you need to review those.

---

### Post by paultb70 on 2020-01-26
I'm not running any of that; I did a clean install when I originally got ubuntu. I was just attempting a recovery boot after getting directed to the grub window and now I can't do anything. 

[http://paste.ubuntu.com/p/b7ksNNyWX2/](http://paste.ubuntu.com/p/b7ksNNyWX2/)

That's the report I ran on the session with the USB boot. It proposes a fix which seems hopeful.

---

### Post by oldfred on 2020-01-26
The suggested is a total reinstall of grub.

I might do that but also install newest kernel which in advance mode you can select both.
Choose your install & drive to install boot loader into, it should default to your NVMe drive.
Advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by paultb70 on 2020-01-26
I tried to add those options but got the following error. 

Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 19.04 (nvme0n1p2). Then try again.

I am going to try to restart again and see what happens. I may need to boot out of 19.04 because that's what I was trying to change to initially. Here are the steps I was in the middle of and the error codes I just now got when I reran the steps 

[https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-18-04-to-ubuntu-19-04-directly-from-command-line](https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-18-04-to-ubuntu-19-04-directly-from-command-line)

dpkg: error processing archive /var/cache/apt/archives/locales_2.29-0ubuntu2_all.deb (--unpack):
 unable to make backup link of './usr/sbin/validlocale' before installing new version: Input/output error
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../libc6-dbg_2.29-0ubuntu2_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.29-0ubuntu2) over (2.27-3ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dbg_2.29-0ubuntu2_amd64.deb (--unpack):
 unable to make backup link of './usr/lib/debug/lib/x86_64-linux-gnu/libSegFault.so' before installing new version: Input/output error
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
dpkg: considering deconfiguration of locales, which would be broken by installation of libc6:amd64 ...
dpkg: yes, will deconfigure locales (broken by libc6:amd64)
Preparing to unpack .../libc6_2.29-0ubuntu2_amd64.deb ...
De-configuring locales (2.27-3ubuntu1) ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...FAILED! (2)

Unpacking libc6:amd64 (2.29-0ubuntu2) over (2.27-3ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libc6_2.29-0ubuntu2_amd64.deb (--unpack):
 unable to make backup link of './usr/lib/x86_64-linux-gnu/gconv/ANSI_X3.110.so' before installing new version: Input/output error
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.29-0ubuntu2_all.deb
 /var/cache/apt/archives/libc6-dbg_2.29-0ubuntu2_amd64.deb
 /var/cache/apt/archives/libc6_2.29-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

############ (seperate set of errors)

/tmp/locales.config.g0KUD3: 545: /tmp/locales.config.g0KUD3: tr: Input/output error
/tmp/locales.config.g0KUD3: 553: /tmp/locales.config.g0KUD3: tr: Input/output error
/tmp/ca-certificates.config.8NGJ7k: 69: /tmp/ca-certificates.config.8NGJ7k: tr: Input/output error
/tmp/ca-certificates.config.8NGJ7k: 35: /tmp/ca-certificates.config.8NGJ7k: tr: Input/output error
dpkg: error: reading package info file '/var/lib/dpkg/available': Input/output error
E: Sub-process dpkg --set-selections returned an error code (2)
E: Couldn't record the approved state changes as dpkg selection states

---

### Post by oldfred on 2020-01-26
The issue is that 19.04 has expired, so repository closed. You have to use a current version.
Ubuntu 19.04 support ends on January 23, 2020.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by paultb70 on 2020-01-27
I've tried a lot since I last posted and thank you for sticking with me. Right off the bat, I'll say I tried a boot to 19.10 but I couldn't install boot-repair. 

On the other versions of Ubuntu boots and the boot repair disk, they all wanted me to run some sudo chmod commands to patch up something called dynare-matlab which is a program I was trying to install that led me to try to update to 19.04 in the first place. It never seemed to be installed correctly. The commands it gave me to run never actually worked, so I tried to purge the program myself but I couldn't get it to work even after assuming root access. 

Thankfully, the boot repair disk was able to circumvent the problematic package and install GRUB, but the new grub window is not like the original one. It's completely black and does not give me the option to do a recovery boot. 

Do you have any further advice about how I should wipe out the program (I'm fine removing anything with "dynare" in it) or next steps in general?

---

### Post by oldfred on 2020-01-27
Boot-Repair has an advanced mode where you can do a total reinstall of grub and add the latest kernel.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
And you may be able to run other fixes while in its chroot.

Otherwise a full chroot from a live installer to run commands on your install.
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by paultb70 on 2020-02-01
Well after several days of trial and error I finally was able to fix my boot and log in normally. For anyone in a similar situation who's found this:

I removed the problematic package using sudo chroot "youroriginalubunutdirectory". After that I was able to run boot repair normally. I then used chroot to run apt update/upgrade/dist-upgrade etc to try to complete the normal update process. I also ran some checks on the mounting of my drive but unfortunately I ran those lines in a usb session so I cannot retrieve the link. The first command was mount "youroriginalubuntudirectory" /mnt. Eventually when I rebooted I was able to to do repair mode where I ran the package/file repair stuff and root commands of sudo apt update/upgrade etc. Then when I continued the boot I booted into my original 19.04 that I was in the middle of updating when this all started. I then was able to complete the update to 19.10 by fixing the errors in my sudo apt update command. The trick is to do sudo nano /etc/apt/sources change all the firmware stuff to mirror from [http://archieve.ubuntu.com/ubuntu](http://archieve.ubuntu.com/ubuntu) (if it's not already) and if that doesn't fix it edit the file again and places a # in front of any problematic repository. From there, you should be able to complete the update to 19.10/whatever distribution you need to move on to. I now boot normally into a login screen instead of GRUB or system options. 

Thank you so much oldfred for sticking with me.

---

