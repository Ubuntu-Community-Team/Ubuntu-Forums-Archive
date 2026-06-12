---
title: "Ubuntu won't boot after kernel 3.0.0-13-generic update"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by thom# on 2011-11-24
Last night I installed updates on my computer and today I noticed that it won't start.

When it reaches the purple screen, the following text is displayed:

[B]loading Linux 3.0.0-13-generic
loading initial ramdisk[/B]

A few more processes seem to run and I'm left in the terminal (I can copy the output if required.)

I used *'startx'* to run the GUI and tried to continue installing updates. However this didn't fix the issue.

Below is the output of *'cat /var/log/dpkg.log | egrep 'install |upgrade '*

I'm quite new to ubuntu, so please excuse my lack of knowledge. I'm just taking a wild guess - but is this something to do with the Linux headers that were installed?

Any help would be appreciated. :confused:

> 2011-11-23 19:54:27 upgrade libcups2 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:29 upgrade libcups2:i386 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:31 upgrade libcupscgi1 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:34 upgrade libcupsdriver1 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:37 upgrade libcupsimage2 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:40 upgrade libcupsimage2:i386 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:42 upgrade libcupsmime1 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:44 upgrade libcupsppdc1 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:54:46 install linux-image-3.0.0-13-generic <none> 3.0.0-13.22
2011-11-23 19:55:18 upgrade banshee 2.2.0-1ubuntu2 2.2.1-1ubuntu1
2011-11-23 19:55:37 upgrade banshee-extension-soundmenu 2.2.0-1ubuntu2 2.2.1-1ubuntu1
2011-11-23 19:55:41 upgrade banshee-extension-ubuntuonemusicstore 2.2.0-1ubuntu2 2.2.1-1ubuntu1
2011-11-23 19:55:43 upgrade compiz-gnome 1:0.9.6+bzr20110929-0ubuntu5 1:0.9.6+bzr20110929-0ubuntu6
2011-11-23 19:55:47 upgrade compiz-plugins 1:0.9.6+bzr20110929-0ubuntu5 1:0.9.6+bzr20110929-0ubuntu6
2011-11-23 19:55:49 upgrade compiz-plugins-default 1:0.9.6+bzr20110929-0ubuntu5 1:0.9.6+bzr20110929-0ubuntu6
2011-11-23 19:55:53 upgrade libdecoration0 1:0.9.6+bzr20110929-0ubuntu5 1:0.9.6+bzr20110929-0ubuntu6
2011-11-23 19:55:55 upgrade compiz-core 1:0.9.6+bzr20110929-0ubuntu5 1:0.9.6+bzr20110929-0ubuntu6
2011-11-23 19:56:00 upgrade compiz 1:0.9.6+bzr20110929-0ubuntu5 1:0.9.6+bzr20110929-0ubuntu6
2011-11-23 19:56:03 upgrade cups-common 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:56:07 upgrade cups-bsd 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:56:14 upgrade cups-client 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:56:16 upgrade cups-ppdc 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:56:19 upgrade cups 1.5.0-8ubuntu4 1.5.0-8ubuntu5
2011-11-23 19:56:43 upgrade libgnome-desktop-3-2 3.2.0-0ubuntu4.1 3.2.1-0ubuntu1.1
2011-11-23 19:56:45 upgrade gnome-desktop3-data 3.2.0-0ubuntu4.1 3.2.1-0ubuntu1.1
2011-11-23 19:56:50 upgrade libnautilus-extension1 1:3.2.1-0ubuntu2 1:3.2.1-0ubuntu3.1
2011-11-23 19:56:55 upgrade linux-generic 3.0.0.12.14 3.0.0.13.15
2011-11-23 19:57:03 upgrade linux-image-generic 3.0.0.12.14 3.0.0.13.15[B]
2011-11-23 19:57:07 install linux-headers-3.0.0-13 <none> 3.0.0-13.22
2011-11-23 20:08:13 install linux-headers-3.0.0-13-generic <none> 3.0.0-13.22[/B]
2011-11-23 20:08:21 upgrade linux-headers-generic 3.0.0.12.14 3.0.0.13.15
2011-11-23 20:08:22 upgrade linux-libc-dev 3.0.0-12.20 3.0.0-13.22
2011-11-23 20:08:26 upgrade nautilus-data 1:3.2.1-0ubuntu2 1:3.2.1-0ubuntu3.1
2011-11-23 20:08:32 upgrade nautilus 1:3.2.1-0ubuntu2 1:3.2.1-0ubuntu3.1
2011-11-23 20:08:36 upgrade onboard 0.95.1-0ubuntu4 0.96.1-0ubuntu0.1
2011-11-23 20:08:42 upgrade simple-scan 3.2.0-0ubuntu1 3.2.1-0ubuntu1~oneiric1
2011-11-23 20:08:46 upgrade software-center 5.0.2 5.0.2ubuntu0.1
2011-11-23 20:08:52 upgrade xserver-xorg-video-intel 2:2.15.901-1ubuntu2 2:2.15.901-1ubuntu2.1
2011-11-24 20:27:39 upgrade libv4l-0 0.8.5-3ubuntu1 0.8.5-3ubuntu2
2011-11-24 20:27:41 upgrade appmenu-qt 0.2.2-0ubuntu1 0.2.2-0ubuntu1.1
2011-11-24 20:27:43 upgrade firefox-globalmenu 7.0.1+build1+nobinonly-0ubuntu2 8.0+build1-0ubuntu0.11.10.3
2011-11-24 20:27:45 upgrade firefox 7.0.1+build1+nobinonly-0ubuntu2 8.0+build1-0ubuntu0.11.10.3
2011-11-24 20:27:52 upgrade firefox-locale-en 7.0.1+build1+nobinonly-0ubuntu2 8.0+build1-0ubuntu0.11.10.3
2011-11-24 20:27:54 upgrade firefox-locale-ja 7.0.1+build1+nobinonly-0ubuntu2 8.0+build1-0ubuntu0.11.10.3
2011-11-24 20:27:55 upgrade firefox-locale-ko 7.0.1+build1+nobinonly-0ubuntu2 8.0+build1-0ubuntu0.11.10.3
2011-11-24 20:27:57 upgrade libgs9-common 9.04~dfsg-0ubuntu11 9.04~dfsg-0ubuntu11.1
2011-11-24 20:28:00 upgrade ghostscript-x 9.04~dfsg-0ubuntu11 9.04~dfsg-0ubuntu11.1
2011-11-24 20:28:02 upgrade ghostscript 9.04~dfsg-0ubuntu11 9.04~dfsg-0ubuntu11.1
2011-11-24 20:28:04 upgrade libgs9 9.04~dfsg-0ubuntu11 9.04~dfsg-0ubuntu11.1
2011-11-24 20:28:07 upgrade ghostscript-cups 9.04~dfsg-0ubuntu11 9.04~dfsg-0ubuntu11.1
2011-11-24 20:28:09 upgrade libgnome-control-center1 1:3.2.1-0ubuntu1 1:3.2.2-0ubuntu1
2011-11-24 20:28:11 upgrade gnome-control-center-data 1:3.2.1-0ubuntu1 1:3.2.2-0ubuntu1
2011-11-24 20:28:16 upgrade gnome-control-center 1:3.2.1-0ubuntu1 1:3.2.2-0ubuntu1
2011-11-24 20:28:19 upgrade gwibber 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:23 upgrade gwibber-service 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:27 upgrade libgwibber2 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:28 upgrade libgwibber-gtk2 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:30 upgrade gwibber-service-facebook 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:31 upgrade gwibber-service-identica 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:33 upgrade gwibber-service-twitter 3.2.1-0ubuntu1.2 3.2.1-0ubuntu1.3
2011-11-24 20:28:35 upgrade libnotify0.4-cil 0.4.0~r3032-3build1 0.4.0~r3032-4~ubuntu0.1
2011-11-24 20:28:37 upgrade ure 3.4.3-3ubuntu2 3.4.4-0ubuntu1
2011-11-24 20:28:40 upgrade uno-libs3 3.4.3-3ubuntu2 3.4.4-0ubuntu1
2011-11-24 20:28:43 upgrade libreoffice-calc 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:28:49 upgrade libreoffice-impress 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:28:52 upgrade libreoffice-draw 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:28:56 upgrade libreoffice-gtk 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:28:58 upgrade libreoffice-gnome 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:00 upgrade python-uno 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:02 upgrade ttf-opensymbol 2:2.4.3+LibO3.4.3-3ubuntu2 2:2.4.3+LibO3.4.4-0ubuntu1
2011-11-24 20:29:04 upgrade libreoffice-math 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:09 upgrade libreoffice-style-human 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:12 upgrade libreoffice-common 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:22 upgrade libreoffice-writer 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:29 upgrade libreoffice-base-core 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:31 upgrade libreoffice-core 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:44 upgrade libreoffice-emailmerge 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:46 upgrade libreoffice-l10n-common 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:29:48 upgrade libreoffice-l10n-en-gb 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:29:51 upgrade libreoffice-help-en-gb 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:29:55 upgrade libreoffice-help-en-us 1:3.4.3-3ubuntu2 1:3.4.4-0ubuntu1
2011-11-24 20:29:59 upgrade libreoffice-l10n-ja 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:30:01 upgrade libreoffice-help-ja 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:30:06 upgrade libreoffice-l10n-ko 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:30:08 upgrade libreoffice-help-ko 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:30:12 upgrade libreoffice-l10n-en-za 1:3.4.3-1ubuntu1 1:3.4.4-0ubuntu1
2011-11-24 20:30:14 upgrade python-papyon 0.5.5-1ubuntu3.1 0.5.5-1ubuntu3.2
2011-11-24 20:30:18 upgrade seahorse 3.2.1-0ubuntu1 3.2.2-0ubuntu0.1
2011-11-24 20:30:23 upgrade xul-ext-ubufox 1.0-0ubuntu2 1.0-0ubuntu2.1
2011-11-24 20:30:25 upgrade libbrlapi0.5 4.2-8ubuntu5 4.2-8ubuntu5.1
2011-11-24 20:30:27 upgrade brltty-x11 4.2-8ubuntu5 4.2-8ubuntu5.1
2011-11-24 20:30:30 upgrade brltty 4.2-8ubuntu5 4.2-8ubuntu5.1
2011-11-24 20:30:34 upgrade python-brlapi 4.2-8ubuntu5 4.2-8ubuntu5.1

---

### Post by BC59 on 2011-11-24
From the logoon screen choose to boot with the older kernel 3.0.0-12.

---

### Post by thom# on 2011-11-24
Thank you. :)

I was able to access the GRUB menu, by holding shift, and select the previous kernel 3.0.0-12-generic.

However, I'm unsure how to undo the installation of the latest kernel. *Is this risky?* :confused: Should I just continue accessing the old kernel through the GRUB menu?

Thank you for assistance.

---

### Post by sdd on 2011-11-25
I have a similar issue. 3.0.0-13 wont boot. I get two flashing lights, caps lock and one next to it, a couple of seconds after selection in grub!

It was working fine last night!

I can get in using the previous version 3.0.0-12. That works fine.

Does any one know how to re-install, repair etc.

---

### Post by Sealbhach on 2011-11-25
> **thom# said:**
> 
However, I'm unsure how to undo the installation of the latest kernel. *Is this risky?* :confused: 

You can remove that latest kernel you installed using the Software Centre or Synaptic Package Manager, just like you would remove any other software. It's not dangerous and the package manager will run update-grub so your Grub menu will be back the way it was.

It's only dangerous if you try to remove the kernel you are actually running, but it will give you plenty of warning that the thing you're about to do is really REALLY not a good idea.

It's possible that the graphics driver or some other driver module was not recompiled properly when you installed the new kernel, that should happen automatically through the DKMS service. 

In the meantime, it's possible to lock the current version of the linux kernel so you won't keep getting nagged about updates. I would wait a while and see if there's some problem with that kernel update that they haven't fixed yet.

Hope this helps.


.

---

### Post by bluexrider on 2011-11-25
sudo apt-get --purge remove [B]linux-headers-3.0.0-13-generic


[/B]

---

### Post by lolpenguin on 2011-11-25
As long you have other kernels installed, you can remove any other ones without damaging your system. But remember, everytime you change your kernel you have to recompile third-party dkms (such as virtualbox-dkms)

---

