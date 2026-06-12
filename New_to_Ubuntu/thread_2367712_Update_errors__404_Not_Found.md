---
title: "Update errors:  404 Not Found"
date: 2017-08-02
forum: New to Ubuntu
---

### Post by iblueflash on 2017-08-02
[ATTACH=CONFIG]276232[/ATTACH][ATTACH=CONFIG]276233[/ATTACH][ATTACH=CONFIG]276231[/ATTACH]
I have a clean installation of Ubuntu 17.04 from the official site.
When I want to update I see that tow errors(I have network connection).

```
iblueflash@iblueflash-X556UQK:~$ sudo apt update && sudo apt upgade
[sudo] password for iblueflash: 
Sorry, try again.
[sudo] password for iblueflash: 
Ign:1 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) zesty InRelease
Err:2 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) zesty Release
  404  Not Found
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease [89,2 kB]
Hit:4 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease   
Hit:6 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) zesty InRelease
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:8 [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) zesty-updates InRelease              
Reading package lists... Done                     
E: The repository 'http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
iblueflash@iblueflash-X556UQK:~$
```

---

### Post by #&amp;thj^% on 2017-08-02
I seem to be missing something Here. /home/iblueflash/Pictures/Imp_1.png /home/iblueflash/Pictures/Imp_2.png
Open the terminal and run this and copy the text inside and paste it back here.
```
sudo apt update
```
Pictures are not always helpful.

---

### Post by ajgreeny on 2017-08-02
Sorry, but your query does not actually ask a question, and those two lines do not appear to be errors.
Open a terminal and show us the output you get from these commands run one after the other```
sudo apt update
sudo apt upgrade
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by iblueflash on 2017-08-02
/home/iblueflash/Pictures/Imp_03.png
This is what I get.

---

### Post by deadflowr on 2017-08-02
> **iblueflash said:**
> /home/iblueflash/Pictures/Imp_1.png
/home/iblueflash/Pictures/Imp_2.png
I have a clean installation of Ubuntu 17.04 from the official site.
When I want to update I see that tow errors(I have network connection).

To post your screenshot you will need to open a new post with Reply to Thread.
(Or click on the Edit Post button in the bottom of your previous thread and then click on the Go Advanced button in the edit window.) 
Then the editor's toolbar will have a paperclip icon, click on it to upload an image or two as an attachment(s).

(Image attachments, unlike file attachments, are viewable by simply clicking on them.)
We prefer this method of posting images because it helps keep page loading bandwidth down, which helps other users who do not have fast internet access.

---

### Post by QIII on 2017-08-02
Would you also please edit the title of your original post to provide meaningful information about your issue.  "Help me" titles are often passed by.  It can be safely assumed that you need help based solely on the fact that you started a thread in a support sub-forum.

---

### Post by oldos2er on 2017-08-02
> **iblueflash said:**
> /home/iblueflash/Pictures/Imp_03.png
This is what I get.

If you're posting terminal output please copy and paste the text into your post here.

---

### Post by deadflowr on 2017-08-02
Okay.
So the codeblocks ppa has no version for zesty, unfortunately.
This means you need to remove that.
Two methods to do that are

1) open the program Software and Updates
go to Other Software > find the damien-moore (or codeblocks) entry and uncheck it (or highlight it and click remove/delete)
Then closing will auto run the apt-get update command.

2) run this command
```
sudo add-apt-repository -r ppa:damien-moore/codeblocks-stable
```
this reverses the add command and makes it remove instead.
Then run
```
sudo apt-get update
```

---

### Post by QIII on 2017-08-02
Please note the change to the title of your thread.  That is what I meant by "meaningful".

---

### Post by cariboo on 2017-08-02
You could also change the ppa release back to to Xenial by opening Software & updates, click the Other Software tab highlight the ppa and click Edit.

---

### Post by iblueflash on 2017-08-03
Thanks for help , now is working. :)

It sound stupit but I dont know how to post again!

---

### Post by deadflowr on 2017-08-04
> **iblueflash said:**
> It sound stupit but I dont know how to post again!

?
Post what?

---

### Post by iblueflash on 2017-08-04
```
iblueflash@iblueflash-X556UQK:~$ sudo apt update && sudo apt upgrade
[sudo] password for iblueflash: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates InRelease [89,2 kB]
Hit:3 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security InRelease [89,2 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata [51,9 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons [23,9 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata [78,0 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons [86,7 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata [5.840 B]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata [11,7 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata [14,4 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons [31,0 kB]
Ign:13 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease         
Hit:14 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) xenial InRelease
Hit:15 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Fetched 482 kB in 5s (81,1 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gamin guile-2.0-libs i965-va-driver liba52-0.7.4 libaacs0 libass5
  libavcodec57 libavutil55 libbasicusageenvironment1 libbdplus0 libbluray2
  libcddb2 libchromaprint1 libcrystalhd3 libdc1394-22 libdca0
  libdirectfb-1.2-9 libdvbpsi10 libdvdnav4 libdvdread4 libebml4v5
  libedataserverui-1.2-1 libfaad2 libgamin0 libgc1c2 libgme0
  libgnome-games-support-1-2 libgnome-games-support-common libgroupsock8
  libgsm1 libiso9660-8 libkate1 liblivemedia57 liblua5.2-0 libmad0
  libmatroska6v5 libmp3lame0 libmpcdec6 libmpeg2-4 libmpg123-0 libopenjp2-7
  libopenmpt-modplug1 libopenmpt0 libproxy-tools libqqwing2v5
  libresid-builder0c2a libsdl-image1.2 libshine3 libsidplay2v5 libsndio6.1
  libsoxr0 libssh-gcrypt-4 libssh2-1 libswresample2 libtwolame0 libupnp6
  libusageenvironment3 libva-drm1 libva-x11-1 libva1 libvcdinfo0 libvlc-bin
  libvlc5 libvlccore8 libwxsmithlib0 libx264-148 libx265-110 libxcb-xv0
  libxvidcore4 libzvbi-common libzvbi0 linux-headers-4.10.0-19
  linux-headers-4.10.0-19-generic linux-image-4.10.0-19-generic
  linux-image-extra-4.10.0-19-generic mesa-va-drivers va-driver-all valgrind
  vlc-bin vlc-data vlc-l10n vlc-plugin-base vlc-plugin-notify vlc-plugin-qt
  vlc-plugin-samba vlc-plugin-skins2 vlc-plugin-video-output
  vlc-plugin-video-splitter vlc-plugin-visualization
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.10.0-30 linux-headers-4.10.0-30-generic
  linux-image-4.10.0-30-generic linux-image-extra-4.10.0-30-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
4 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 62,4 MB of archives.
After this operation, 308 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-image-4.10.0-30-generic amd64 4.10.0-30.34 [20,2 MB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-image-extra-4.10.0-30-generic amd64 4.10.0-30.34 [30,0 MB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-generic amd64 4.10.0.30.31 [1.784 B]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-image-generic amd64 4.10.0.30.31 [2.312 B]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-headers-4.10.0-30 all 4.10.0-30.34 [10,6 MB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-headers-4.10.0-30-generic amd64 4.10.0-30.34 [688 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-headers-generic amd64 4.10.0.30.31 [2.282 B]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-libc-dev amd64 4.10.0-30.34 [914 kB]
Fetched 62,4 MB in 1min 13s (853 kB/s)                                         
Selecting previously unselected package linux-image-4.10.0-30-generic.
(Reading database ... 245778 files and directories currently installed.)
Preparing to unpack .../0-linux-image-4.10.0-30-generic_4.10.0-30.34_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Done.
Unpacking linux-image-4.10.0-30-generic (4.10.0-30.34) ...
Selecting previously unselected package linux-image-extra-4.10.0-30-generic.
Preparing to unpack .../1-linux-image-extra-4.10.0-30-generic_4.10.0-30.34_amd64.deb ...
Unpacking linux-image-extra-4.10.0-30-generic (4.10.0-30.34) ...
Preparing to unpack .../2-linux-generic_4.10.0.30.31_amd64.deb ...
Unpacking linux-generic (4.10.0.30.31) over (4.10.0.29.30) ...
Preparing to unpack .../3-linux-image-generic_4.10.0.30.31_amd64.deb ...
Unpacking linux-image-generic (4.10.0.30.31) over (4.10.0.29.30) ...
Selecting previously unselected package linux-headers-4.10.0-30.
Preparing to unpack .../4-linux-headers-4.10.0-30_4.10.0-30.34_all.deb ...
Unpacking linux-headers-4.10.0-30 (4.10.0-30.34) ...
Selecting previously unselected package linux-headers-4.10.0-30-generic.
Preparing to unpack .../5-linux-headers-4.10.0-30-generic_4.10.0-30.34_amd64.deb ...
Unpacking linux-headers-4.10.0-30-generic (4.10.0-30.34) ...
Preparing to unpack .../6-linux-headers-generic_4.10.0.30.31_amd64.deb ...
Unpacking linux-headers-generic (4.10.0.30.31) over (4.10.0.29.30) ...
Preparing to unpack .../7-linux-libc-dev_4.10.0-30.34_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.10.0-30.34) over (4.10.0-29.33) ...
Setting up linux-image-4.10.0-30-generic (4.10.0-30.34) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.10.0-30-generic
Found initrd image: /boot/initrd.img-4.10.0-30-generic
Found linux image: /boot/vmlinuz-4.10.0-29-generic
Found initrd image: /boot/initrd.img-4.10.0-29-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found linux image: /boot/vmlinuz-4.10.0-19-generic
Found initrd image: /boot/initrd.img-4.10.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-libc-dev:amd64 (4.10.0-30.34) ...
Setting up linux-headers-4.10.0-30 (4.10.0-30.34) ...
Setting up linux-image-extra-4.10.0-30-generic (4.10.0-30.34) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.10.0-30-generic
Found initrd image: /boot/initrd.img-4.10.0-30-generic
Found linux image: /boot/vmlinuz-4.10.0-29-generic
Found initrd image: /boot/initrd.img-4.10.0-29-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found linux image: /boot/vmlinuz-4.10.0-19-generic
Found initrd image: /boot/initrd.img-4.10.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-headers-4.10.0-30-generic (4.10.0-30.34) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Setting up linux-image-generic (4.10.0.30.31) ...
Setting up linux-headers-generic (4.10.0.30.31) ...
Setting up linux-generic (4.10.0.30.31) ...
```

This is good or not?

---

### Post by deadflowr on 2017-08-04
Looks good.
No errors.
Only thing about it is you have quite a few packages the system now deems obsolete.
That's most likely because you removed a package (or 2 or 3) which those packages listed in the can be removed section were installed with.
So now the system thinks those leftover packages are no longer needed.
Whether or not you want any of the listed packages is up to you.

Also do not worry about the Warning:
```
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
```
it's just a warning, if you heed it's advice and did not change the GRUB_TIMEOUT settings in /etc/default/grub then you can simply ignore it.

---

