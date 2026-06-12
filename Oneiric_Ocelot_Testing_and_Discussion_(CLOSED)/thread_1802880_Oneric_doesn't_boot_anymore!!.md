---
title: "Oneric doesn't boot anymore!!"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ZamekM on 2011-07-12
Hi everyone,

Today, after an upgrade (of gnome-shell and others stuff) i can't boot back on Ubuntu.
I'm stuck at : Checking battery state...

I tried to re-install plymouth ; restart and switch between lightdm and gdm ; make all type of upgrades ... but without success!

Please help me to go back on ubuntu! 
Thanks


ps: sorry for my english.

---

### Post by fjgaude on 2011-07-12
What's wrong with waiting a day or two and re-installing the Alpha 2 and then updating, upgrading?

---

### Post by ZamekM on 2011-07-12
Nothing, ... if you have time. I really want to avoid a complete re-installation. I'm full of exams and others stuff, so if can avoid it ... better.

---

### Post by cgroza on 2011-07-12
> **ZamekM said:**
> Nothing, ... if you have time. I really want to avoid a complete re-installation. I'm full of exams and others stuff, so if can avoid it ... better.
You use an Alpha2 release as a production machine? I suggest you do a dual boot with a stable release. Just resize your partition to make room for it.
Be sure Oneiric will break quite often so don't count on it.

---

### Post by ZamekM on 2011-07-12
Yes i know, it was stupid to update to oneiric on my main partition. I did it to enjoy as much as possible gnome shell on ubuntu (i couldn't use to fedora). That why if i really have to re-install everything i'm not going to use oneiric (perhaps gnatty). But if i can avoid it...

---

### Post by sgage on 2011-07-12
> **ZamekM said:**
> Yes i know, it was stupid to update to oneiric on my main partition. I did it to enjoy as much as possible gnome shell on ubuntu (i couldn't use to fedora). That why if i really have to re-install everything i'm not going to use oneiric (perhaps gnatty). But if i can avoid it...

Try doing an apt-get update ... apt-get upgrade from a command prompt.

If you can't boot even to a terminal, boot the LiveCD and chroot to your system, and do the apt-get.

---

### Post by ZamekM on 2011-07-12
I can access to command prompt when it's stuck to Checking battery state. So i did it (cf post 1) several times (last 5 min ago) and install everything ... without changes. (i did it in recovery mod too)

---

### Post by Harry33 on 2011-07-12
> **ZamekM said:**
> Hi everyone,
Today, after an upgrade (of gnome-shell and others stuff) i can't boot back on Ubuntu.
I'm stuck at : Checking battery state...
...


Could you print here all the updates after this happened.
Gnome-shell has not been updated for a while. Where did you get that (a PPA maybe)?

---

### Post by ZamekM on 2011-07-12
I don't know where i can find it.
 
For gnome-shell perhaps it was a mistake (... but i was quite sure ...) because the changelog don't show anything after the end of june... 
I haven't a lot of other ppa, i think i still have gnome3-team/gnome3 and ubuntugnometeam/ppa-gen but no more ricotz's ppa and nothing else strange.

---

### Post by ZamekM on 2011-07-12
I fund it!
Here is my /apt/term.log
(sorry it's in french; i'm going to do something for an easier understanding)
EDIT: translation done.

```
Log started: 2011-07-12  11:18:11
(Reading database... 
(Reading database... 5%
(Reading database... 10%
(Reading database... 15%
(Reading database... 20%
(Reading database... 25%
(Reading database... 30%
(Reading database... 35%
(Reading database... 40%
(Reading database... 45%
(Reading database... 50%
(Reading database... 55%
(Reading database... 60%
(Reading database... 65%
(Reading database... 70%
(Reading database... 75%
(Reading database... 80%
(Reading database... 85%
(Reading database... 90%
(Reading database... 95%
(Reading database... 100%
(Reading database... 382932 files and directories currently installed.)
Removing gnome-applets ...
Removing gnome-session-fallback ...
Removing gnome-panel ...
Removing gnome-shell-extensions-user-theme ...
Removing gnome-shell-extensions-common ...
Removing gnome-tweak-tool ...
Removing gnome-shell ...
Removing indicator-datetime ...
Processing triggers for «*man-db*»...
Processing triggers for «*gconf2*»...
Processing triggers for «*gnome-menus*»...
Processing triggers for «*bamfdaemon*»...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for «*desktop-file-utils*»...
Processing triggers for «*libglib2.0-0*»...
Processing triggers for «*libc-bin*»...
ldconfig deferred processing now taking place
(Reading database... 
(Reading database... 5%
(Reading database... 10%
(Reading database... 15%
(Reading database... 20%
(Reading database... 25%
(Reading database... 30%
(Reading database... 35%
(Reading database... 40%
(Reading database... 45%
(Reading database... 50%
(Reading database... 55%
(Reading database... 60%
(Reading database... 65%
(Reading database... 70%
(Reading database... 75%
(Reading database... 80%
(Reading database... 85%
(Reading database... 90%
(Reading database... 95%
(Reading database... 100%
(Reading database... 382505 files and directories currently installed.)
Preparing to replace libedataserver1.2-14 3.1.2-0ubuntu1 (using .../libedataserver1.2-14_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libedataserver1.2-14 ...
Selecting previously deselected libcamel-1.2-28 .
Unpacking libcamel-1.2-28 (à partir de .../libcamel-1.2-28_3.1.3.1-0ubuntu1_amd64.deb) ...
Preparing to replace libebook1.2-11 3.1.2-0ubuntu1 (using .../libebook1.2-11_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libebook1.2-11 ...
Preparing to replace libecal1.2-9 3.1.2-0ubuntu1 (using .../libecal1.2-9_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libecal1.2-9 ...
Preparing to replace libebackend-1.2-1 3.1.2-0ubuntu1 (using .../libebackend-1.2-1_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libebackend-1.2-1 ...
Preparing to replace libedata-book-1.2-10 3.1.2-0ubuntu1 (using .../libedata-book-1.2-10_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libedata-book-1.2-10 ...
Preparing to replace libedata-cal-1.2-12 3.1.2-0ubuntu1 (using .../libedata-cal-1.2-12_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libedata-cal-1.2-12 ...
Preparing to replace evolution-data-server 3.1.2-0ubuntu1 (using .../evolution-data-server_3.1.3.1-0ubuntu1_amd64.deb) ...
Unpacking replacement evolution-data-server ...
Preparing to replace libevolution 3.1.2-0ubuntu2 (using .../libevolution_3.1.3-0ubuntu1_amd64.deb) ...
Unpacking replacement libevolution ...
Preparing to replace evolution-plugins 3.1.2-0ubuntu2 (using .../evolution-plugins_3.1.3-0ubuntu1_amd64.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace evolution 3.1.2-0ubuntu2 (using .../evolution_3.1.3-0ubuntu1_amd64.deb) ...
Unpacking replacement evolution ...
Processing triggers for «*man-db*»...
Processing triggers for «*gnome-menus*»...
Processing triggers for «*bamfdaemon*»...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for «*desktop-file-utils*»...
Processing triggers for «*gconf2*»...
(Reading database... 
(Reading database... 5%
(Reading database... 10%
(Reading database... 15%
(Reading database... 20%
(Reading database... 25%
(Reading database... 30%
(Reading database... 35%
(Reading database... 40%
(Reading database... 45%
(Reading database... 50%
(Reading database... 55%
(Reading database... 60%
(Reading database... 65%
(Reading database... 70%
(Reading database... 75%
(Reading database... 80%
(Reading database... 85%
(Reading database... 90%
(Reading database... 95%
(Reading database... 100%
(Reading database... 382514 files and directories currently installed.)
Removing libedataserverui-3.0-0 ...
Processing triggers for «*libc-bin*»...
ldconfig deferred processing now taking place
(Reading database... 
(Reading database... 5%
(Reading database... 10%
(Reading database... 15%
(Reading database... 20%
(Reading database... 25%
(Reading database... 30%
(Reading database... 35%
(Reading database... 40%
(Reading database... 45%
(Reading database... 50%
(Reading database... 55%
(Reading database... 60%
(Reading database... 65%
(Reading database... 70%
(Reading database... 75%
(Reading database... 80%
(Reading database... 85%
(Reading database... 90%
(Reading database... 95%
(Reading database... 100%
(Reading database... 382507 files and directories currently installed.)
Preparing to replace evolution-data-server-common 3.1.2-0ubuntu1 (using .../evolution-data-server-common_3.1.3.1-0ubuntu1_all.deb) ...
Unpacking replacement evolution-data-server-common ...
Selecting previously deselected libedataserverui-3.0-1 .
Unpacking libedataserverui-3.0-1 (à partir de .../libedataserverui-3.0-1_3.1.3.1-0ubuntu1_amd64.deb) ...
Preparing to replace evolution-common 3.1.2-0ubuntu2 (using .../evolution-common_3.1.3-0ubuntu1_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace libffi6 3.0.10~rc8-5 (using .../libffi6_3.0.10~rc8-6_amd64.deb) ...
Unpacking replacement libffi6 ...
Preparing to replace libudev0 172-0ubuntu1 (using .../libudev0_172-0ubuntu2_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libgudev-1.0-0 1:172-0ubuntu1 (using .../libgudev-1.0-0_1%3a172-0ubuntu2_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace initramfs-tools 0.98.8ubuntu4 (using .../initramfs-tools_0.99ubuntu1_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace initramfs-tools-bin 0.98.8ubuntu4 (using .../initramfs-tools-bin_0.99ubuntu1_amd64.deb) ...
Unpacking replacement initramfs-tools-bin ...
Preparing to replace udev 172-0ubuntu1 (using .../udev_172-0ubuntu2_amd64.deb) ...
Ajout de «*détournement de /sbin/udevadm en*/sbin/udevadm.upgrade par fake-udev*»
Unpacking replacement udev ...
Preparing to replace libibus2 1.3.9-1ubuntu1 (using .../libibus2_1.3.9-2ubuntu1_amd64.deb) ...
Unpacking replacement libibus2 ...
Preparing to replace ibus 1.3.9-1ubuntu1 (using .../ibus_1.3.9-2ubuntu1_amd64.deb) ...
Unpacking replacement ibus ...
Preparing to replace python-ibus 1.3.9-1ubuntu1 (using .../python-ibus_1.3.9-2ubuntu1_all.deb) ...
Unpacking replacement python-ibus ...
Preparing to replace ibus-gtk 1.3.9-1ubuntu1 (using .../ibus-gtk_1.3.9-2ubuntu1_amd64.deb) ...
Unpacking replacement ibus-gtk ...
Preparing to replace libglib2.0-cil 2.12.10-1ubuntu1 (using .../libglib2.0-cil_2.12.10-2ubuntu1_amd64.deb) ...
Removing libglib2.0-cil from Mono
Unpacking replacement libglib2.0-cil ...
Preparing to replace libart2.0-cil 2.24.2-0ubuntu1 (using .../libart2.0-cil_2.24.2-1_all.deb) ...
Removing libart2.0-cil from Mono
Unpacking replacement libart2.0-cil ...
Preparing to replace libgconf2.0-cil 2.24.2-0ubuntu1 (using .../libgconf2.0-cil_2.24.2-1_all.deb) ...
Removing libgconf2.0-cil from Mono
Unpacking replacement libgconf2.0-cil ...
Preparing to replace libgtk2.0-cil 2.12.10-1ubuntu1 (using .../libgtk2.0-cil_2.12.10-2ubuntu1_amd64.deb) ...
Removing libgtk2.0-cil from Mono
Unpacking replacement libgtk2.0-cil ...
Preparing to replace libglade2.0-cil 2.12.10-1ubuntu1 (using .../libglade2.0-cil_2.12.10-2ubuntu1_amd64.deb) ...
Removing libglade2.0-cil from Mono
Unpacking replacement libglade2.0-cil ...
Preparing to replace libgnome-vfs2.0-cil 2.24.2-0ubuntu1 (using .../libgnome-vfs2.0-cil_2.24.2-1_all.deb) ...
Removing libgnome-vfs2.0-cil from Mono
Unpacking replacement libgnome-vfs2.0-cil ...
Preparing to replace libgnome2.24-cil 2.24.2-0ubuntu1 (using .../libgnome2.24-cil_2.24.2-1_amd64.deb) ...
Removing libgnome2.24-cil from Mono
Unpacking replacement libgnome2.24-cil ...
Preparing to replace libgtk-sharp-beans-cil 2.14.1-2 (using .../libgtk-sharp-beans-cil_2.14.1-2build1_all.deb) ...
Unpacking replacement libgtk-sharp-beans-cil ...
Preparing to replace telepathy-haze 0.4.0-1ubuntu (using .../telepathy-haze_0.5.0-1_amd64.deb) ...
Unpacking replacement telepathy-haze ...
Processing triggers for «*hicolor-icon-theme*»...
Processing triggers for «*doc-base*»...
Processing 1 changed doc-base file...
Enregistrement des documents avec scrollkeeper...
Processing triggers for «*man-db*»...
Processing triggers for «*ureadahead*»...
ureadahead will be reprofiled on next reboot
Processing triggers for «*gnome-menus*»...
Processing triggers for «*bamfdaemon*»...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for «*desktop-file-utils*»...
Processing triggers for «*gconf2*»...
Processing triggers for «*python-support*»...
Processing triggers for «*libgtk2.0-0*»...
Setting up libedataserver1.2-14 (3.1.3.1-0ubuntu1) ...
Setting up libcamel-1.2-28 (3.1.3.1-0ubuntu1) ...
Setting up libebook1.2-11 (3.1.3.1-0ubuntu1) ...
Setting up libecal1.2-9 (3.1.3.1-0ubuntu1) ...
Setting up libebackend-1.2-1 (3.1.3.1-0ubuntu1) ...
Setting up libedata-book-1.2-10 (3.1.3.1-0ubuntu1) ...
Setting up libedata-cal-1.2-12 (3.1.3.1-0ubuntu1) ...
Setting up evolution-data-server-common (3.1.3.1-0ubuntu1) ...
Setting up evolution-data-server (3.1.3.1-0ubuntu1) ...
Setting up libedataserverui-3.0-1 (3.1.3.1-0ubuntu1) ...
Setting up libevolution (3.1.3-0ubuntu1) ...
Setting up evolution-common (3.1.3-0ubuntu1) ...
Setting up evolution (3.1.3-0ubuntu1) ...
Setting up evolution-plugins (3.1.3-0ubuntu1) ...
Setting up libffi6 (3.0.10~rc8-6) ...
Setting up libudev0 (172-0ubuntu2) ...
Setting up libgudev-1.0-0 (1:172-0ubuntu2) ...
Setting up initramfs-tools-bin (0.99ubuntu1) ...
Setting up libibus2 (1.3.9-2ubuntu1) ...
Setting up python-ibus (1.3.9-2ubuntu1) ...
Setting up ibus (1.3.9-2ubuntu1) ...
Installing new version of config file /etc/X11/xinit/xinput.d/ibus ...
update-alternatives: utilisation de «*/etc/X11/xinit/xinput.d/ibus*» pour fournir «*/etc/X11/xinit/xinput.d/ja_JP*» (xinput-ja_JP) en mode automatique.
update-alternatives: utilisation de «*/etc/X11/xinit/xinput.d/ibus*» pour fournir «*/etc/X11/xinit/xinput.d/ko_KR*» (xinput-ko_KR) en mode automatique.
update-alternatives: utilisation de «*/etc/X11/xinit/xinput.d/ibus*» pour fournir «*/etc/X11/xinit/xinput.d/zh_CN*» (xinput-zh_CN) en mode automatique.
update-alternatives: utilisation de «*/etc/X11/xinit/xinput.d/ibus*» pour fournir «*/etc/X11/xinit/xinput.d/zh_TW*» (xinput-zh_TW) en mode automatique.
update-alternatives: utilisation de «*/etc/X11/xinit/xinput.d/ibus*» pour fournir «*/etc/X11/xinit/xinput.d/zh_HK*» (xinput-zh_HK) en mode automatique.
update-alternatives: utilisation de «*/etc/X11/xinit/xinput.d/ibus*» pour fournir «*/etc/X11/xinit/xinput.d/zh_SG*» (xinput-zh_SG) en mode automatique.
Setting up ibus-gtk (1.3.9-2ubuntu1) ...
Setting up libglib2.0-cil (2.12.10-2ubuntu1) ...
* Installing 1 assembly from libglib2.0-cil into Mono
Setting up libart2.0-cil (2.24.2-1) ...
* Installing 6 assemblies from libart2.0-cil into Mono
Setting up libgconf2.0-cil (2.24.2-1) ...
* Installing 6 assemblies from libgconf2.0-cil into Mono
Setting up libgtk2.0-cil (2.12.10-2ubuntu1) ...
* Installing 5 assemblies from libgtk2.0-cil into Mono
Setting up libglade2.0-cil (2.12.10-2ubuntu1) ...
* Installing 1 assembly from libglade2.0-cil into Mono
Setting up libgnome-vfs2.0-cil (2.24.2-1) ...
* Installing 6 assemblies from libgnome-vfs2.0-cil into Mono
Setting up libgnome2.24-cil (2.24.2-1) ...
* Installing 2 assemblies from libgnome2.24-cil into Mono
Setting up libgtk-sharp-beans-cil (2.14.1-2build1) ...
Setting up telepathy-haze (0.5.0-1) ...
Setting up udev (172-0ubuntu2) ...
udev start/running, process 6957
Removing «*détournement de /sbin/udevadm en*/sbin/udevadm.upgrade par fake-udev*»
update-initramfs: deferring update (trigger activated)
Setting up initramfs-tools (0.99ubuntu1) ...
Installing new version of config file /etc/initramfs-tools/initramfs.conf ...
Installing new version of config file /etc/kernel/postinst.d/initramfs-tools ...
Installing new version of config file /etc/kernel/postrm.d/initramfs-tools ...
update-initramfs: deferring update (trigger activated)
Processing triggers for «*libc-bin*»...
ldconfig deferred processing now taking place
Processing triggers for «*python-support*»...
Processing triggers for «*initramfs-tools*»...
update-initramfs: Generating /boot/initrd.img-3.0.0-4-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda7
cryptsetup: WARNING: could not determine root device from /etc/fstab
Log ended: 2011-07-12  11:20:48
```

And here my dpkg.log:

```
2011-07-12 11:18:12 startup packages remove
2011-07-12 11:18:12 status installed gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:21 remove gnome-applets 3.1.2-0ubuntu3 <none>
2011-07-12 11:18:21 status half-configured gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status half-installed gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status triggers-pending man-db 2.6.0.2-1
2011-07-12 11:18:22 status half-installed gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status triggers-pending gconf2 2.32.4-1ubuntu3
2011-07-12 11:18:22 status half-installed gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status config-files gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status config-files gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status config-files gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:22 status config-files gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:23 status config-files gnome-applets 3.1.2-0ubuntu3
2011-07-12 11:18:23 status not-installed gnome-applets <none>
2011-07-12 11:18:23 status installed gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:23 remove gnome-session-fallback 3.1.3-0ubuntu2 <none>
2011-07-12 11:18:23 status half-configured gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:23 status half-installed gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:23 status triggers-pending gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:18:23 status half-installed gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:23 status triggers-pending bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:18:23 status half-installed gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:24 status triggers-pending desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:18:24 status half-installed gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:24 status config-files gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:24 status config-files gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:24 status config-files gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:25 status config-files gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:25 status config-files gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:25 status config-files gnome-session-fallback 3.1.3-0ubuntu2
2011-07-12 11:18:25 status not-installed gnome-session-fallback <none>
2011-07-12 11:18:25 status installed gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:25 remove gnome-panel 1:3.0.2-0ubuntu5 <none>
2011-07-12 11:18:25 status half-configured gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:25 status half-installed gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:25 status half-installed gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:25 status half-installed gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:25 status half-installed gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:25 status half-installed gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status config-files gnome-panel 1:3.0.2-0ubuntu5
2011-07-12 11:18:26 status not-installed gnome-panel <none>
2011-07-12 11:18:26 status installed gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:26 remove gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0 <none>
2011-07-12 11:18:26 status half-configured gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:26 status half-installed gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status config-files gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status config-files gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status config-files gnome-shell-extensions-user-theme 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status not-installed gnome-shell-extensions-user-theme <none>
2011-07-12 11:18:27 status installed gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 remove gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0 <none>
2011-07-12 11:18:27 status half-configured gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status half-installed gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status triggers-pending libglib2.0-0 2.29.10-0ubuntu2
2011-07-12 11:18:27 status half-installed gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:27 status config-files gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:28 status config-files gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:28 status config-files gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:28 status config-files gnome-shell-extensions-common 3.0.2-1~~11.04~ricotz0
2011-07-12 11:18:28 status not-installed gnome-shell-extensions-common <none>
2011-07-12 11:18:28 status installed gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:28 remove gnome-tweak-tool 3.0.4-1 <none>
2011-07-12 11:18:28 status half-configured gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status half-installed gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status half-installed gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status half-installed gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status half-installed gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status config-files gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status config-files gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:29 status config-files gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:30 status config-files gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:30 status config-files gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:30 status config-files gnome-tweak-tool 3.0.4-1
2011-07-12 11:18:30 status not-installed gnome-tweak-tool <none>
2011-07-12 11:18:30 status installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 remove gnome-shell 3.0.2-1svn2 <none>
2011-07-12 11:18:30 status half-configured gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:30 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:31 status triggers-pending gconf2 2.32.4-1ubuntu3
2011-07-12 11:18:31 status half-installed gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status config-files gnome-shell 3.0.2-1svn2
2011-07-12 11:18:32 status not-installed gnome-shell <none>
2011-07-12 11:18:33 status installed indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 remove indicator-datetime 0.2.91-0ubuntu1 <none>
2011-07-12 11:18:33 status half-configured indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 status half-installed indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 status half-installed indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 status half-installed indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 status half-installed indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 status half-installed indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:33 status triggers-pending libc-bin 2.13-9ubuntu2
2011-07-12 11:18:34 status config-files indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:34 status config-files indicator-datetime 0.2.91-0ubuntu1
2011-07-12 11:18:34 trigproc man-db 2.6.0.2-1 <none>
2011-07-12 11:18:34 status half-configured man-db 2.6.0.2-1
2011-07-12 11:18:38 status installed man-db 2.6.0.2-1
2011-07-12 11:18:38 trigproc gconf2 2.32.4-1ubuntu3 <none>
2011-07-12 11:18:38 status half-configured gconf2 2.32.4-1ubuntu3
2011-07-12 11:18:44 status installed gconf2 2.32.4-1ubuntu3
2011-07-12 11:18:44 trigproc gnome-menus 3.0.1-0ubuntu3 <none>
2011-07-12 11:18:44 status half-configured gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:18:45 status installed gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:18:45 trigproc bamfdaemon 0.2.92-0ubuntu1 <none>
2011-07-12 11:18:45 status half-configured bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:18:46 status installed bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:18:46 trigproc desktop-file-utils 0.18-0ubuntu5 <none>
2011-07-12 11:18:46 status half-configured desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:18:47 status installed desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:18:47 trigproc libglib2.0-0 2.29.10-0ubuntu2 <none>
2011-07-12 11:18:47 status half-configured libglib2.0-0 2.29.10-0ubuntu2
2011-07-12 11:18:48 status installed libglib2.0-0 2.29.10-0ubuntu2
2011-07-12 11:18:48 trigproc libc-bin 2.13-9ubuntu2 <none>
2011-07-12 11:18:48 status half-configured libc-bin 2.13-9ubuntu2
2011-07-12 11:18:49 status installed libc-bin 2.13-9ubuntu2
2011-07-12 11:18:50 startup archives unpack
2011-07-12 11:18:50 upgrade libedataserver1.2-14 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:50 status half-configured libedataserver1.2-14 3.1.2-0ubuntu1
2011-07-12 11:18:50 status unpacked libedataserver1.2-14 3.1.2-0ubuntu1
2011-07-12 11:18:50 status half-installed libedataserver1.2-14 3.1.2-0ubuntu1
2011-07-12 11:18:50 status half-installed libedataserver1.2-14 3.1.2-0ubuntu1
2011-07-12 11:18:51 status unpacked libedataserver1.2-14 3.1.3.1-0ubuntu1
2011-07-12 11:18:51 status unpacked libedataserver1.2-14 3.1.3.1-0ubuntu1
2011-07-12 11:18:51 install libcamel-1.2-28 <none> 3.1.3.1-0ubuntu1
2011-07-12 11:18:51 status half-installed libcamel-1.2-28 3.1.3.1-0ubuntu1
2011-07-12 11:18:51 status unpacked libcamel-1.2-28 3.1.3.1-0ubuntu1
2011-07-12 11:18:51 status unpacked libcamel-1.2-28 3.1.3.1-0ubuntu1
2011-07-12 11:18:52 upgrade libebook1.2-11 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:52 status half-configured libebook1.2-11 3.1.2-0ubuntu1
2011-07-12 11:18:52 status unpacked libebook1.2-11 3.1.2-0ubuntu1
2011-07-12 11:18:52 status half-installed libebook1.2-11 3.1.2-0ubuntu1
2011-07-12 11:18:53 status half-installed libebook1.2-11 3.1.2-0ubuntu1
2011-07-12 11:18:53 status unpacked libebook1.2-11 3.1.3.1-0ubuntu1
2011-07-12 11:18:53 status unpacked libebook1.2-11 3.1.3.1-0ubuntu1
2011-07-12 11:18:53 upgrade libecal1.2-9 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:53 status half-configured libecal1.2-9 3.1.2-0ubuntu1
2011-07-12 11:18:53 status unpacked libecal1.2-9 3.1.2-0ubuntu1
2011-07-12 11:18:53 status half-installed libecal1.2-9 3.1.2-0ubuntu1
2011-07-12 11:18:53 status half-installed libecal1.2-9 3.1.2-0ubuntu1
2011-07-12 11:18:54 status unpacked libecal1.2-9 3.1.3.1-0ubuntu1
2011-07-12 11:18:54 status unpacked libecal1.2-9 3.1.3.1-0ubuntu1
2011-07-12 11:18:55 upgrade libebackend-1.2-1 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:55 status half-configured libebackend-1.2-1 3.1.2-0ubuntu1
2011-07-12 11:18:55 status unpacked libebackend-1.2-1 3.1.2-0ubuntu1
2011-07-12 11:18:56 status half-installed libebackend-1.2-1 3.1.2-0ubuntu1
2011-07-12 11:18:56 status half-installed libebackend-1.2-1 3.1.2-0ubuntu1
2011-07-12 11:18:56 status unpacked libebackend-1.2-1 3.1.3.1-0ubuntu1
2011-07-12 11:18:56 status unpacked libebackend-1.2-1 3.1.3.1-0ubuntu1
2011-07-12 11:18:56 upgrade libedata-book-1.2-10 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:56 status half-configured libedata-book-1.2-10 3.1.2-0ubuntu1
2011-07-12 11:18:56 status unpacked libedata-book-1.2-10 3.1.2-0ubuntu1
2011-07-12 11:18:56 status half-installed libedata-book-1.2-10 3.1.2-0ubuntu1
2011-07-12 11:18:57 status half-installed libedata-book-1.2-10 3.1.2-0ubuntu1
2011-07-12 11:18:57 status unpacked libedata-book-1.2-10 3.1.3.1-0ubuntu1
2011-07-12 11:18:57 status unpacked libedata-book-1.2-10 3.1.3.1-0ubuntu1
2011-07-12 11:18:57 upgrade libedata-cal-1.2-12 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:57 status half-configured libedata-cal-1.2-12 3.1.2-0ubuntu1
2011-07-12 11:18:57 status unpacked libedata-cal-1.2-12 3.1.2-0ubuntu1
2011-07-12 11:18:57 status half-installed libedata-cal-1.2-12 3.1.2-0ubuntu1
2011-07-12 11:18:57 status half-installed libedata-cal-1.2-12 3.1.2-0ubuntu1
2011-07-12 11:18:58 status unpacked libedata-cal-1.2-12 3.1.3.1-0ubuntu1
2011-07-12 11:18:58 status unpacked libedata-cal-1.2-12 3.1.3.1-0ubuntu1
2011-07-12 11:18:58 upgrade evolution-data-server 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:18:58 status half-configured evolution-data-server 3.1.2-0ubuntu1
2011-07-12 11:18:58 status unpacked evolution-data-server 3.1.2-0ubuntu1
2011-07-12 11:18:58 status half-installed evolution-data-server 3.1.2-0ubuntu1
2011-07-12 11:18:58 status half-installed evolution-data-server 3.1.2-0ubuntu1
2011-07-12 11:18:58 status unpacked evolution-data-server 3.1.3.1-0ubuntu1
2011-07-12 11:18:59 status unpacked evolution-data-server 3.1.3.1-0ubuntu1
2011-07-12 11:18:59 upgrade libevolution 3.1.2-0ubuntu2 3.1.3-0ubuntu1
2011-07-12 11:18:59 status half-configured libevolution 3.1.2-0ubuntu2
2011-07-12 11:18:59 status unpacked libevolution 3.1.2-0ubuntu2
2011-07-12 11:18:59 status half-installed libevolution 3.1.2-0ubuntu2
2011-07-12 11:19:00 status half-installed libevolution 3.1.2-0ubuntu2
2011-07-12 11:19:00 status unpacked libevolution 3.1.3-0ubuntu1
2011-07-12 11:19:00 status unpacked libevolution 3.1.3-0ubuntu1
2011-07-12 11:19:00 upgrade evolution-plugins 3.1.2-0ubuntu2 3.1.3-0ubuntu1
2011-07-12 11:19:00 status half-configured evolution-plugins 3.1.2-0ubuntu2
2011-07-12 11:19:00 status unpacked evolution-plugins 3.1.2-0ubuntu2
2011-07-12 11:19:00 status half-installed evolution-plugins 3.1.2-0ubuntu2
2011-07-12 11:19:00 status half-installed evolution-plugins 3.1.2-0ubuntu2
2011-07-12 11:19:00 status unpacked evolution-plugins 3.1.3-0ubuntu1
2011-07-12 11:19:01 status unpacked evolution-plugins 3.1.3-0ubuntu1
2011-07-12 11:19:01 upgrade evolution 3.1.2-0ubuntu2 3.1.3-0ubuntu1
2011-07-12 11:19:01 status half-configured evolution 3.1.2-0ubuntu2
2011-07-12 11:19:01 status unpacked evolution 3.1.2-0ubuntu2
2011-07-12 11:19:01 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:02 status triggers-pending man-db 2.6.0.2-1
2011-07-12 11:19:02 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:02 status triggers-pending gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:19:02 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:03 status triggers-pending bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:19:03 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:03 status triggers-pending desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:19:03 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:03 status triggers-pending gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:03 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:03 status triggers-pending gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:03 status half-installed evolution 3.1.2-0ubuntu2
2011-07-12 11:19:03 status unpacked evolution 3.1.3-0ubuntu1
2011-07-12 11:19:03 status unpacked evolution 3.1.3-0ubuntu1
2011-07-12 11:19:03 trigproc man-db 2.6.0.2-1 2.6.0.2-1
2011-07-12 11:19:03 status half-configured man-db 2.6.0.2-1
2011-07-12 11:19:05 status installed man-db 2.6.0.2-1
2011-07-12 11:19:05 trigproc gnome-menus 3.0.1-0ubuntu3 3.0.1-0ubuntu3
2011-07-12 11:19:05 status half-configured gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:19:05 status installed gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:19:05 trigproc bamfdaemon 0.2.92-0ubuntu1 0.2.92-0ubuntu1
2011-07-12 11:19:05 status half-configured bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:19:05 status installed bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:19:05 trigproc desktop-file-utils 0.18-0ubuntu5 0.18-0ubuntu5
2011-07-12 11:19:05 status half-configured desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:19:06 status installed desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:19:06 trigproc gconf2 2.32.4-1ubuntu3 2.32.4-1ubuntu3
2011-07-12 11:19:06 status half-configured gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:11 status installed gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:11 startup packages remove
2011-07-12 11:19:11 status installed libedataserverui-3.0-0 3.1.2-0ubuntu1
2011-07-12 11:19:12 remove libedataserverui-3.0-0 3.1.2-0ubuntu1 <none>
2011-07-12 11:19:12 status half-configured libedataserverui-3.0-0 3.1.2-0ubuntu1
2011-07-12 11:19:12 status half-installed libedataserverui-3.0-0 3.1.2-0ubuntu1
2011-07-12 11:19:12 status triggers-pending libc-bin 2.13-9ubuntu2
2011-07-12 11:19:12 status config-files libedataserverui-3.0-0 3.1.2-0ubuntu1
2011-07-12 11:19:12 status config-files libedataserverui-3.0-0 3.1.2-0ubuntu1
2011-07-12 11:19:12 trigproc libc-bin 2.13-9ubuntu2 <none>
2011-07-12 11:19:12 status half-configured libc-bin 2.13-9ubuntu2
2011-07-12 11:19:12 status installed libc-bin 2.13-9ubuntu2
2011-07-12 11:19:13 startup archives unpack
2011-07-12 11:19:14 upgrade evolution-data-server-common 3.1.2-0ubuntu1 3.1.3.1-0ubuntu1
2011-07-12 11:19:14 status half-configured evolution-data-server-common 3.1.2-0ubuntu1
2011-07-12 11:19:14 status unpacked evolution-data-server-common 3.1.2-0ubuntu1
2011-07-12 11:19:14 status half-installed evolution-data-server-common 3.1.2-0ubuntu1
2011-07-12 11:19:14 status half-installed evolution-data-server-common 3.1.2-0ubuntu1
2011-07-12 11:19:14 status unpacked evolution-data-server-common 3.1.3.1-0ubuntu1
2011-07-12 11:19:14 status unpacked evolution-data-server-common 3.1.3.1-0ubuntu1
2011-07-12 11:19:15 install libedataserverui-3.0-1 <none> 3.1.3.1-0ubuntu1
2011-07-12 11:19:15 status half-installed libedataserverui-3.0-1 3.1.3.1-0ubuntu1
2011-07-12 11:19:15 status unpacked libedataserverui-3.0-1 3.1.3.1-0ubuntu1
2011-07-12 11:19:15 status unpacked libedataserverui-3.0-1 3.1.3.1-0ubuntu1
2011-07-12 11:19:15 upgrade evolution-common 3.1.2-0ubuntu2 3.1.3-0ubuntu1
2011-07-12 11:19:15 status half-configured evolution-common 3.1.2-0ubuntu2
2011-07-12 11:19:15 status unpacked evolution-common 3.1.2-0ubuntu2
2011-07-12 11:19:15 status half-installed evolution-common 3.1.2-0ubuntu2
2011-07-12 11:19:16 status triggers-pending hicolor-icon-theme 0.12-1ubuntu1
2011-07-12 11:19:17 status half-installed evolution-common 3.1.2-0ubuntu2
2011-07-12 11:19:18 status half-installed evolution-common 3.1.2-0ubuntu2
2011-07-12 11:19:18 status unpacked evolution-common 3.1.3-0ubuntu1
2011-07-12 11:19:18 status unpacked evolution-common 3.1.3-0ubuntu1
2011-07-12 11:19:19 upgrade libffi6 3.0.10~rc8-5 3.0.10~rc8-6
2011-07-12 11:19:19 status half-configured libffi6 3.0.10~rc8-5
2011-07-12 11:19:19 status unpacked libffi6 3.0.10~rc8-5
2011-07-12 11:19:19 status half-installed libffi6 3.0.10~rc8-5
2011-07-12 11:19:19 status half-installed libffi6 3.0.10~rc8-5
2011-07-12 11:19:19 status unpacked libffi6 3.0.10~rc8-6
2011-07-12 11:19:19 status unpacked libffi6 3.0.10~rc8-6
2011-07-12 11:19:20 upgrade libudev0 172-0ubuntu1 172-0ubuntu2
2011-07-12 11:19:20 status half-configured libudev0 172-0ubuntu1
2011-07-12 11:19:20 status unpacked libudev0 172-0ubuntu1
2011-07-12 11:19:20 status half-installed libudev0 172-0ubuntu1
2011-07-12 11:19:20 status half-installed libudev0 172-0ubuntu1
2011-07-12 11:19:20 status unpacked libudev0 172-0ubuntu2
2011-07-12 11:19:20 status unpacked libudev0 172-0ubuntu2
2011-07-12 11:19:21 upgrade libgudev-1.0-0 1:172-0ubuntu1 1:172-0ubuntu2
2011-07-12 11:19:21 status half-configured libgudev-1.0-0 1:172-0ubuntu1
2011-07-12 11:19:21 status unpacked libgudev-1.0-0 1:172-0ubuntu1
2011-07-12 11:19:21 status half-installed libgudev-1.0-0 1:172-0ubuntu1
2011-07-12 11:19:21 status half-installed libgudev-1.0-0 1:172-0ubuntu1
2011-07-12 11:19:21 status unpacked libgudev-1.0-0 1:172-0ubuntu2
2011-07-12 11:19:21 status unpacked libgudev-1.0-0 1:172-0ubuntu2
2011-07-12 11:19:22 upgrade initramfs-tools 0.98.8ubuntu4 0.99ubuntu1
2011-07-12 11:19:22 status half-configured initramfs-tools 0.98.8ubuntu4
2011-07-12 11:19:22 status unpacked initramfs-tools 0.98.8ubuntu4
2011-07-12 11:19:22 status half-installed initramfs-tools 0.98.8ubuntu4
2011-07-12 11:19:22 status triggers-pending doc-base 0.10.1
2011-07-12 11:19:22 status half-installed initramfs-tools 0.98.8ubuntu4
2011-07-12 11:19:22 status triggers-pending man-db 2.6.0.2-1
2011-07-12 11:19:22 status half-installed initramfs-tools 0.98.8ubuntu4
2011-07-12 11:19:22 status half-installed initramfs-tools 0.98.8ubuntu4
2011-07-12 11:19:23 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:19:23 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:19:23 upgrade initramfs-tools-bin 0.98.8ubuntu4 0.99ubuntu1
2011-07-12 11:19:23 status half-configured initramfs-tools-bin 0.98.8ubuntu4
2011-07-12 11:19:23 status unpacked initramfs-tools-bin 0.98.8ubuntu4
2011-07-12 11:19:23 status half-installed initramfs-tools-bin 0.98.8ubuntu4
2011-07-12 11:19:23 status half-installed initramfs-tools-bin 0.98.8ubuntu4
2011-07-12 11:19:23 status unpacked initramfs-tools-bin 0.99ubuntu1
2011-07-12 11:19:23 status unpacked initramfs-tools-bin 0.99ubuntu1
2011-07-12 11:19:24 upgrade udev 172-0ubuntu1 172-0ubuntu2
2011-07-12 11:19:24 status half-configured udev 172-0ubuntu1
2011-07-12 11:19:24 status unpacked udev 172-0ubuntu1
2011-07-12 11:19:24 status half-installed udev 172-0ubuntu1
2011-07-12 11:19:24 status triggers-pending ureadahead 0.100.0-11
2011-07-12 11:19:24 status half-installed udev 172-0ubuntu1
2011-07-12 11:19:24 status triggers-pending ureadahead 0.100.0-11
2011-07-12 11:19:25 status half-installed udev 172-0ubuntu1
2011-07-12 11:19:26 status half-installed udev 172-0ubuntu1
2011-07-12 11:19:26 status unpacked udev 172-0ubuntu2
2011-07-12 11:19:28 status unpacked udev 172-0ubuntu2
2011-07-12 11:19:28 upgrade libibus2 1.3.9-1ubuntu1 1.3.9-2ubuntu1
2011-07-12 11:19:28 status half-configured libibus2 1.3.9-1ubuntu1
2011-07-12 11:19:28 status unpacked libibus2 1.3.9-1ubuntu1
2011-07-12 11:19:29 status half-installed libibus2 1.3.9-1ubuntu1
2011-07-12 11:19:29 status half-installed libibus2 1.3.9-1ubuntu1
2011-07-12 11:19:29 status unpacked libibus2 1.3.9-2ubuntu1
2011-07-12 11:19:29 status unpacked libibus2 1.3.9-2ubuntu1
2011-07-12 11:19:29 upgrade ibus 1.3.9-1ubuntu1 1.3.9-2ubuntu1
2011-07-12 11:19:29 status half-configured ibus 1.3.9-1ubuntu1
2011-07-12 11:19:30 status unpacked ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status triggers-pending gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status triggers-pending bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status triggers-pending desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:31 status triggers-pending gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:31 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:32 status half-installed ibus 1.3.9-1ubuntu1
2011-07-12 11:19:32 status unpacked ibus 1.3.9-2ubuntu1
2011-07-12 11:19:32 status unpacked ibus 1.3.9-2ubuntu1
2011-07-12 11:19:32 upgrade python-ibus 1.3.9-1ubuntu1 1.3.9-2ubuntu1
2011-07-12 11:19:32 status half-configured python-ibus 1.3.9-1ubuntu1
2011-07-12 11:19:32 status triggers-pending python-support 1.0.13ubuntu1
2011-07-12 11:19:32 status unpacked python-ibus 1.3.9-1ubuntu1
2011-07-12 11:19:33 status half-installed python-ibus 1.3.9-1ubuntu1
2011-07-12 11:19:33 status half-installed python-ibus 1.3.9-1ubuntu1
2011-07-12 11:19:33 status unpacked python-ibus 1.3.9-2ubuntu1
2011-07-12 11:19:33 status unpacked python-ibus 1.3.9-2ubuntu1
2011-07-12 11:19:33 upgrade ibus-gtk 1.3.9-1ubuntu1 1.3.9-2ubuntu1
2011-07-12 11:19:33 status half-configured ibus-gtk 1.3.9-1ubuntu1
2011-07-12 11:19:33 status unpacked ibus-gtk 1.3.9-1ubuntu1
2011-07-12 11:19:33 status half-installed ibus-gtk 1.3.9-1ubuntu1
2011-07-12 11:19:33 status triggers-pending libgtk2.0-0 2.24.5-0ubuntu3
2011-07-12 11:19:33 status half-installed ibus-gtk 1.3.9-1ubuntu1
2011-07-12 11:19:34 status half-installed ibus-gtk 1.3.9-1ubuntu1
2011-07-12 11:19:34 status unpacked ibus-gtk 1.3.9-2ubuntu1
2011-07-12 11:19:34 status unpacked ibus-gtk 1.3.9-2ubuntu1
2011-07-12 11:19:34 upgrade libglib2.0-cil 2.12.10-1ubuntu1 2.12.10-2ubuntu1
2011-07-12 11:19:34 status half-configured libglib2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:35 status unpacked libglib2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:35 status half-installed libglib2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:35 status half-installed libglib2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:36 status unpacked libglib2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:19:36 status unpacked libglib2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:19:36 upgrade libart2.0-cil 2.24.2-0ubuntu1 2.24.2-1
2011-07-12 11:19:36 status half-configured libart2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:37 status unpacked libart2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:37 status half-installed libart2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:37 status half-installed libart2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:37 status unpacked libart2.0-cil 2.24.2-1
2011-07-12 11:19:37 status unpacked libart2.0-cil 2.24.2-1
2011-07-12 11:19:38 upgrade libgconf2.0-cil 2.24.2-0ubuntu1 2.24.2-1
2011-07-12 11:19:38 status half-configured libgconf2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:38 status unpacked libgconf2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:38 status half-installed libgconf2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:38 status half-installed libgconf2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:38 status unpacked libgconf2.0-cil 2.24.2-1
2011-07-12 11:19:39 status unpacked libgconf2.0-cil 2.24.2-1
2011-07-12 11:19:39 upgrade libgtk2.0-cil 2.12.10-1ubuntu1 2.12.10-2ubuntu1
2011-07-12 11:19:39 status half-configured libgtk2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:40 status unpacked libgtk2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:40 status half-installed libgtk2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:40 status half-installed libgtk2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:42 status unpacked libgtk2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:19:42 status unpacked libgtk2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:19:42 upgrade libglade2.0-cil 2.12.10-1ubuntu1 2.12.10-2ubuntu1
2011-07-12 11:19:42 status half-configured libglade2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:43 status unpacked libglade2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:43 status half-installed libglade2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:43 status half-installed libglade2.0-cil 2.12.10-1ubuntu1
2011-07-12 11:19:43 status unpacked libglade2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:19:43 status unpacked libglade2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:19:44 upgrade libgnome-vfs2.0-cil 2.24.2-0ubuntu1 2.24.2-1
2011-07-12 11:19:44 status half-configured libgnome-vfs2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:44 status unpacked libgnome-vfs2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:44 status half-installed libgnome-vfs2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:45 status half-installed libgnome-vfs2.0-cil 2.24.2-0ubuntu1
2011-07-12 11:19:45 status unpacked libgnome-vfs2.0-cil 2.24.2-1
2011-07-12 11:19:45 status unpacked libgnome-vfs2.0-cil 2.24.2-1
2011-07-12 11:19:45 upgrade libgnome2.24-cil 2.24.2-0ubuntu1 2.24.2-1
2011-07-12 11:19:45 status half-configured libgnome2.24-cil 2.24.2-0ubuntu1
2011-07-12 11:19:45 status unpacked libgnome2.24-cil 2.24.2-0ubuntu1
2011-07-12 11:19:46 status half-installed libgnome2.24-cil 2.24.2-0ubuntu1
2011-07-12 11:19:46 status half-installed libgnome2.24-cil 2.24.2-0ubuntu1
2011-07-12 11:19:46 status unpacked libgnome2.24-cil 2.24.2-1
2011-07-12 11:19:46 status unpacked libgnome2.24-cil 2.24.2-1
2011-07-12 11:19:46 upgrade libgtk-sharp-beans-cil 2.14.1-2 2.14.1-2build1
2011-07-12 11:19:46 status half-configured libgtk-sharp-beans-cil 2.14.1-2
2011-07-12 11:19:46 status unpacked libgtk-sharp-beans-cil 2.14.1-2
2011-07-12 11:19:46 status half-installed libgtk-sharp-beans-cil 2.14.1-2
2011-07-12 11:19:46 status half-installed libgtk-sharp-beans-cil 2.14.1-2
2011-07-12 11:19:47 status unpacked libgtk-sharp-beans-cil 2.14.1-2build1
2011-07-12 11:19:47 status unpacked libgtk-sharp-beans-cil 2.14.1-2build1
2011-07-12 11:19:47 upgrade telepathy-haze 0.4.0-1ubuntu 0.5.0-1
2011-07-12 11:19:47 status half-configured telepathy-haze 0.4.0-1ubuntu
2011-07-12 11:19:47 status unpacked telepathy-haze 0.4.0-1ubuntu
2011-07-12 11:19:47 status half-installed telepathy-haze 0.4.0-1ubuntu
2011-07-12 11:19:47 status half-installed telepathy-haze 0.4.0-1ubuntu
2011-07-12 11:19:47 status half-installed telepathy-haze 0.4.0-1ubuntu
2011-07-12 11:19:47 status unpacked telepathy-haze 0.5.0-1
2011-07-12 11:19:47 status unpacked telepathy-haze 0.5.0-1
2011-07-12 11:19:48 trigproc hicolor-icon-theme 0.12-1ubuntu1 0.12-1ubuntu1
2011-07-12 11:19:48 status half-configured hicolor-icon-theme 0.12-1ubuntu1
2011-07-12 11:19:48 status installed hicolor-icon-theme 0.12-1ubuntu1
2011-07-12 11:19:48 trigproc doc-base 0.10.1 0.10.1
2011-07-12 11:19:48 status half-configured doc-base 0.10.1
2011-07-12 11:19:49 status installed doc-base 0.10.1
2011-07-12 11:19:49 trigproc man-db 2.6.0.2-1 2.6.0.2-1
2011-07-12 11:19:49 status half-configured man-db 2.6.0.2-1
2011-07-12 11:19:51 status installed man-db 2.6.0.2-1
2011-07-12 11:19:51 trigproc ureadahead 0.100.0-11 0.100.0-11
2011-07-12 11:19:51 status half-configured ureadahead 0.100.0-11
2011-07-12 11:19:51 status installed ureadahead 0.100.0-11
2011-07-12 11:19:51 trigproc gnome-menus 3.0.1-0ubuntu3 3.0.1-0ubuntu3
2011-07-12 11:19:51 status half-configured gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:19:52 status installed gnome-menus 3.0.1-0ubuntu3
2011-07-12 11:19:52 trigproc bamfdaemon 0.2.92-0ubuntu1 0.2.92-0ubuntu1
2011-07-12 11:19:52 status half-configured bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:19:52 status installed bamfdaemon 0.2.92-0ubuntu1
2011-07-12 11:19:52 trigproc desktop-file-utils 0.18-0ubuntu5 0.18-0ubuntu5
2011-07-12 11:19:52 status half-configured desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:19:52 status installed desktop-file-utils 0.18-0ubuntu5
2011-07-12 11:19:52 trigproc gconf2 2.32.4-1ubuntu3 2.32.4-1ubuntu3
2011-07-12 11:19:52 status half-configured gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:57 status installed gconf2 2.32.4-1ubuntu3
2011-07-12 11:19:57 trigproc python-support 1.0.13ubuntu1 1.0.13ubuntu1
2011-07-12 11:19:57 status half-configured python-support 1.0.13ubuntu1
2011-07-12 11:20:01 status installed python-support 1.0.13ubuntu1
2011-07-12 11:20:01 trigproc libgtk2.0-0 2.24.5-0ubuntu3 2.24.5-0ubuntu3
2011-07-12 11:20:01 status half-configured libgtk2.0-0 2.24.5-0ubuntu3
2011-07-12 11:20:01 status installed libgtk2.0-0 2.24.5-0ubuntu3
2011-07-12 11:20:02 startup packages configure
2011-07-12 11:20:02 configure libedataserver1.2-14 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:02 status unpacked libedataserver1.2-14 3.1.3.1-0ubuntu1
2011-07-12 11:20:02 status half-configured libedataserver1.2-14 3.1.3.1-0ubuntu1
2011-07-12 11:20:03 status installed libedataserver1.2-14 3.1.3.1-0ubuntu1
2011-07-12 11:20:03 status triggers-pending libc-bin 2.13-9ubuntu2
2011-07-12 11:20:03 configure libcamel-1.2-28 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:03 status unpacked libcamel-1.2-28 3.1.3.1-0ubuntu1
2011-07-12 11:20:03 status half-configured libcamel-1.2-28 3.1.3.1-0ubuntu1
2011-07-12 11:20:04 status installed libcamel-1.2-28 3.1.3.1-0ubuntu1
2011-07-12 11:20:04 configure libebook1.2-11 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:04 status unpacked libebook1.2-11 3.1.3.1-0ubuntu1
2011-07-12 11:20:04 status half-configured libebook1.2-11 3.1.3.1-0ubuntu1
2011-07-12 11:20:04 status installed libebook1.2-11 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 configure libecal1.2-9 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:05 status unpacked libecal1.2-9 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 status half-configured libecal1.2-9 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 status installed libecal1.2-9 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 configure libebackend-1.2-1 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:05 status unpacked libebackend-1.2-1 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 status half-configured libebackend-1.2-1 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 status installed libebackend-1.2-1 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 configure libedata-book-1.2-10 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:05 status unpacked libedata-book-1.2-10 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 status half-configured libedata-book-1.2-10 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 status installed libedata-book-1.2-10 3.1.3.1-0ubuntu1
2011-07-12 11:20:05 configure libedata-cal-1.2-12 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:05 status unpacked libedata-cal-1.2-12 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status half-configured libedata-cal-1.2-12 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status installed libedata-cal-1.2-12 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 configure evolution-data-server-common 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:06 status unpacked evolution-data-server-common 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status half-configured evolution-data-server-common 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status installed evolution-data-server-common 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 configure evolution-data-server 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:06 status unpacked evolution-data-server 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status half-configured evolution-data-server 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status installed evolution-data-server 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 configure libedataserverui-3.0-1 3.1.3.1-0ubuntu1 <none>
2011-07-12 11:20:06 status unpacked libedataserverui-3.0-1 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status half-configured libedataserverui-3.0-1 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 status installed libedataserverui-3.0-1 3.1.3.1-0ubuntu1
2011-07-12 11:20:06 configure libevolution 3.1.3-0ubuntu1 <none>
2011-07-12 11:20:06 status unpacked libevolution 3.1.3-0ubuntu1
2011-07-12 11:20:06 status half-configured libevolution 3.1.3-0ubuntu1
2011-07-12 11:20:07 status installed libevolution 3.1.3-0ubuntu1
2011-07-12 11:20:07 configure evolution-common 3.1.3-0ubuntu1 <none>
2011-07-12 11:20:07 status unpacked evolution-common 3.1.3-0ubuntu1
2011-07-12 11:20:07 status half-configured evolution-common 3.1.3-0ubuntu1
2011-07-12 11:20:07 status installed evolution-common 3.1.3-0ubuntu1
2011-07-12 11:20:07 configure evolution 3.1.3-0ubuntu1 <none>
2011-07-12 11:20:07 status unpacked evolution 3.1.3-0ubuntu1
2011-07-12 11:20:07 status unpacked evolution 3.1.3-0ubuntu1
2011-07-12 11:20:07 status half-configured evolution 3.1.3-0ubuntu1
2011-07-12 11:20:07 status installed evolution 3.1.3-0ubuntu1
2011-07-12 11:20:07 configure evolution-plugins 3.1.3-0ubuntu1 <none>
2011-07-12 11:20:07 status unpacked evolution-plugins 3.1.3-0ubuntu1
2011-07-12 11:20:07 status half-configured evolution-plugins 3.1.3-0ubuntu1
2011-07-12 11:20:07 status installed evolution-plugins 3.1.3-0ubuntu1
2011-07-12 11:20:07 configure libffi6 3.0.10~rc8-6 <none>
2011-07-12 11:20:07 status unpacked libffi6 3.0.10~rc8-6
2011-07-12 11:20:07 status half-configured libffi6 3.0.10~rc8-6
2011-07-12 11:20:08 status installed libffi6 3.0.10~rc8-6
2011-07-12 11:20:08 configure libudev0 172-0ubuntu2 <none>
2011-07-12 11:20:08 status unpacked libudev0 172-0ubuntu2
2011-07-12 11:20:08 status half-configured libudev0 172-0ubuntu2
2011-07-12 11:20:08 status installed libudev0 172-0ubuntu2
2011-07-12 11:20:08 configure libgudev-1.0-0 1:172-0ubuntu2 <none>
2011-07-12 11:20:08 status unpacked libgudev-1.0-0 1:172-0ubuntu2
2011-07-12 11:20:08 status half-configured libgudev-1.0-0 1:172-0ubuntu2
2011-07-12 11:20:08 status installed libgudev-1.0-0 1:172-0ubuntu2
2011-07-12 11:20:08 configure initramfs-tools-bin 0.99ubuntu1 <none>
2011-07-12 11:20:08 status unpacked initramfs-tools-bin 0.99ubuntu1
2011-07-12 11:20:08 status half-configured initramfs-tools-bin 0.99ubuntu1
2011-07-12 11:20:08 status installed initramfs-tools-bin 0.99ubuntu1
2011-07-12 11:20:08 configure libibus2 1.3.9-2ubuntu1 <none>
2011-07-12 11:20:08 status unpacked libibus2 1.3.9-2ubuntu1
2011-07-12 11:20:08 status half-configured libibus2 1.3.9-2ubuntu1
2011-07-12 11:20:09 status installed libibus2 1.3.9-2ubuntu1
2011-07-12 11:20:09 configure python-ibus 1.3.9-2ubuntu1 <none>
2011-07-12 11:20:09 status unpacked python-ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 status half-configured python-ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 status installed python-ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 status triggers-pending python-support 1.0.13ubuntu1
2011-07-12 11:20:09 configure ibus 1.3.9-2ubuntu1 <none>
2011-07-12 11:20:09 status unpacked ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 status unpacked ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 status half-configured ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 status installed ibus 1.3.9-2ubuntu1
2011-07-12 11:20:09 configure ibus-gtk 1.3.9-2ubuntu1 <none>
2011-07-12 11:20:09 status unpacked ibus-gtk 1.3.9-2ubuntu1
2011-07-12 11:20:10 status half-configured ibus-gtk 1.3.9-2ubuntu1
2011-07-12 11:20:10 status installed ibus-gtk 1.3.9-2ubuntu1
2011-07-12 11:20:10 configure libglib2.0-cil 2.12.10-2ubuntu1 <none>
2011-07-12 11:20:10 status unpacked libglib2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:10 status half-configured libglib2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:11 status installed libglib2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:11 configure libart2.0-cil 2.24.2-1 <none>
2011-07-12 11:20:11 status unpacked libart2.0-cil 2.24.2-1
2011-07-12 11:20:11 status half-configured libart2.0-cil 2.24.2-1
2011-07-12 11:20:12 status installed libart2.0-cil 2.24.2-1
2011-07-12 11:20:12 configure libgconf2.0-cil 2.24.2-1 <none>
2011-07-12 11:20:12 status unpacked libgconf2.0-cil 2.24.2-1
2011-07-12 11:20:12 status half-configured libgconf2.0-cil 2.24.2-1
2011-07-12 11:20:13 status installed libgconf2.0-cil 2.24.2-1
2011-07-12 11:20:13 configure libgtk2.0-cil 2.12.10-2ubuntu1 <none>
2011-07-12 11:20:13 status unpacked libgtk2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:13 status half-configured libgtk2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:17 status installed libgtk2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:17 configure libglade2.0-cil 2.12.10-2ubuntu1 <none>
2011-07-12 11:20:17 status unpacked libglade2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:18 status half-configured libglade2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:18 status installed libglade2.0-cil 2.12.10-2ubuntu1
2011-07-12 11:20:19 configure libgnome-vfs2.0-cil 2.24.2-1 <none>
2011-07-12 11:20:19 status unpacked libgnome-vfs2.0-cil 2.24.2-1
2011-07-12 11:20:19 status half-configured libgnome-vfs2.0-cil 2.24.2-1
2011-07-12 11:20:20 status installed libgnome-vfs2.0-cil 2.24.2-1
2011-07-12 11:20:20 configure libgnome2.24-cil 2.24.2-1 <none>
2011-07-12 11:20:20 status unpacked libgnome2.24-cil 2.24.2-1
2011-07-12 11:20:20 status half-configured libgnome2.24-cil 2.24.2-1
2011-07-12 11:20:20 status installed libgnome2.24-cil 2.24.2-1
2011-07-12 11:20:20 configure libgtk-sharp-beans-cil 2.14.1-2build1 <none>
2011-07-12 11:20:20 status unpacked libgtk-sharp-beans-cil 2.14.1-2build1
2011-07-12 11:20:20 status half-configured libgtk-sharp-beans-cil 2.14.1-2build1
2011-07-12 11:20:21 status installed libgtk-sharp-beans-cil 2.14.1-2build1
2011-07-12 11:20:21 configure telepathy-haze 0.5.0-1 <none>
2011-07-12 11:20:21 status unpacked telepathy-haze 0.5.0-1
2011-07-12 11:20:21 status half-configured telepathy-haze 0.5.0-1
2011-07-12 11:20:21 status installed telepathy-haze 0.5.0-1
2011-07-12 11:20:21 configure udev 172-0ubuntu2 <none>
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status unpacked udev 172-0ubuntu2
2011-07-12 11:20:21 status half-configured udev 172-0ubuntu2
2011-07-12 11:20:22 status installed udev 172-0ubuntu2
2011-07-12 11:20:22 configure initramfs-tools 0.99ubuntu1 <none>
2011-07-12 11:20:22 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:20:22 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:20:22 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:20:22 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:20:22 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:20:22 status unpacked initramfs-tools 0.99ubuntu1
2011-07-12 11:20:22 status half-configured initramfs-tools 0.99ubuntu1
2011-07-12 11:20:23 status installed initramfs-tools 0.99ubuntu1
2011-07-12 11:20:23 status triggers-pending initramfs-tools 0.99ubuntu1
2011-07-12 11:20:23 trigproc libc-bin 2.13-9ubuntu2 <none>
2011-07-12 11:20:23 status half-configured libc-bin 2.13-9ubuntu2
2011-07-12 11:20:23 status installed libc-bin 2.13-9ubuntu2
2011-07-12 11:20:23 trigproc python-support 1.0.13ubuntu1 <none>
2011-07-12 11:20:23 status half-configured python-support 1.0.13ubuntu1
2011-07-12 11:20:23 status installed python-support 1.0.13ubuntu1
2011-07-12 11:20:23 trigproc initramfs-tools 0.99ubuntu1 <none>
2011-07-12 11:20:23 status half-configured initramfs-tools 0.99ubuntu1
2011-07-12 11:20:47 status installed initramfs-tools 0.99ubuntu1
```

If it can help...

... and there is an installation of gnome-shell!

---

### Post by Harry33 on 2011-07-12
> **ZamekM said:**
> I don't know where i can find it.
 
For gnome-shell perhaps it was a mistake (... but i was quite sure ...) because the changelog don't show anything after the end of june... 
I haven't a lot of other ppa, i think i still have gnome3-team/gnome3 and ubuntugnometeam/ppa-gen but no more ricotz's ppa and nothing else strange.

Those PPA's (gnome3-team/gnome3 and ubuntugnometeam/ppa-gen) is your problem.
They are for Natty, not for Oneiric.
You should only use Ricotz PPA for Oneiric in order to have a recent gnome-shell.
Right now the gnome-panel and gnome-shell in Oneiric's repos does not support the latest evolution-data-server and you have installed that.

---

### Post by ZamekM on 2011-07-13
So i did that:

```
ppa-purge ppa:gnome3-team/gnome3
ppa-purge ppa:ubuntugnometeam/ppa-gen
add-apt-repository ppa:ricotz/testing
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get remove evolution-data-server
```

All with success. I have re-install nvidia's driver (new kernel), remove packages useless after evolution's remove and depending of ugr's ppa.

But ... nothing new, still: Checking battery state...

I have noticed this warning doing : update-initramfs -u

```
update-initramfs: Generating /boot/initrd.img-3.0.0-5-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda7
cryptsetup: WARNING: could not determine root device from etc/fstab
W= Possible missing firmware /lib/firmware/fuc41ad for module nouveau
W= Possible missing firmware /lib/firmware/fuc41ac for module nouveau
W= Possible missing firmware /lib/firmware/fuc409d for module nouveau
W= Possible missing firmware /lib/firmware/fuc409c for module nouveau
W= Possible missing firmware /lib/firmware/nvc4-fuc41ad for module nouveau
W= Possible missing firmware /lib/firmware/nvc4-fuc41ac for module nouveau
W= Possible missing firmware /lib/firmware/nvc4-fuc409d for module nouveau
W= Possible missing firmware /lib/firmware/nvc4-fuc409c for module nouveau
W= Possible missing firmware /lib/firmware/nvc3-fuc41ad for module nouveau
W= Possible missing firmware /lib/firmware/nvc3-fuc41ac for module nouveau
W= Possible missing firmware /lib/firmware/nvc3-fuc409d for module nouveau
W= Possible missing firmware /lib/firmware/nvc3-fuc409c for module nouveau
W= Possible missing firmware /lib/firmware/nvc0-fuc41ad for module nouveau
W= Possible missing firmware /lib/firmware/nvc0-fuc41ac for module nouveau
W= Possible missing firmware /lib/firmware/nvc0-fuc409d for module nouveau
W= Possible missing firmware /lib/firmware/nvc0-fuc409c for module nouveau
```

I don't new if it's related to my problem but ...
I already install nouveau earlier today (yesterday in fact).
sda7 is my linux's partition but every thing is mounted when i use it.

---

### Post by Harry33 on 2011-07-13
You have some problems with initramfs and cryptsetup.
See these:

> 
cryptsetup: WARNING: failed to detect canonical device of /dev/sda7
cryptsetup: WARNING: could not determine root device from etc/fstab


If fstab is not fully recognized, your system will not boot.

---

### Post by dino99 on 2011-07-13
have seen this too:

W= Possible missing firmware /lib/firmware/nvc0-*

---

### Post by ZamekM on 2011-07-13
I have done some reasearch.

> cryptsetup: WARNING: failed to detect canonical device of /dev/sda7
cryptsetup: WARNING: could not determine root device from etc/fstab

For that, i don't realy understand : all seems monted when i use it, i don't use crypto on any of my partitions, and  initramfs allways give this warning. I have read some sites that's wasen't really important....?
Here is my fstab:

```
proc                                       /proc        proc  nodev,noexec,nosuid                 0  0  
/dev/sda7                                  /            ext4  errors=remount-ro,user_xattr        0  1  
UUID=d684dcd7-cff6-44e6-ba5f-757c679aa201  none         swap  sw                                  0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
```

For the other stuff i haven't found a lot of stuff, i'm going to re-install nouveau (but i normally use Nvidia's drivers) but i allready did it yestearday without success.

---

### Post by w3rt on 2011-07-13
Surely a reinstall would be quicker?

---

### Post by ZamekM on 2011-07-13
Ok, ok, sorry. I will re-install everything when i will have time. Someone know something about the stability of gNatty (a Natty with Shell)? (i'know it's not the good place to ask but just if...)

If someone has an idea about my prob untill i re-install, just in case ...

Thank's to everyone

---

