---
title: "How to find and run file boot-repair from u14.04 live disk"
date: 2014-10-22
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-10-22
I was running Software Center on my installed U14.04.1 and attempting to install Wine; while Wine was installing I attempted to install other programs. None of the programs finished installing including Wine. I shutdown and rebooted my computer [acer-one-inspire-500]. I got only a blank screen. I then booted the live USB and attempted to find and run boot-repair. I was not successful. How do I find/locate and run boot-repair from the live usb?

I opened Software Center and successfully downloaded RedNotebook. I was unable to run it and got the message no disk space . I ran df -h and it showed / on the live usb was full. How do I install programs to my u14.04 hard drive from the live usb? On the harddrive /dev/sda , sda2 is /  [60GB] and sda3 is/home [40G] with very low disk usage.

---

### Post by slickymaster on 2014-10-22
Have a read at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Redalien0304 on 2014-10-22
Boot-Repair is out of Date for Ubuntu 14.04. I have tried to use it on my Ubuntu 14.04 system has Failed. It is not Updated for  Grub 2.02 beta 9 which is the current version Grub. Boot-Repair has not been updated since 2013. Use at Your Own Risk. If i am wrong then let me know

---

### Post by oldfred on 2014-10-22
You actually install the older version of Boot-Repair and it still works. 

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Note that there is an additional install line to convert trusty to saucy just for the Boot-Repair ppa.
Most of what Boot-Repair does is from your install, it just is running the commands/scripts for you, so most of it does not depend on version.

---

### Post by Redalien0304 on 2014-10-22
yep i saw that oldfred thanks. but need an updated version of Boot-Reapir live cd-usb version

---

### Post by grahammechanical on 2014-10-22
@nu2u904

Wine uses Microsoft TrueType core fonts. So, when we install Wine we also need to agree to the Microsoft End User Licence otherwise the installation of Wine cannot proceed. It is possible that the dialog box asking for your agreement to the Microsoft EULA was hidden behind the Software Centre application windows. I have had that happen to me. Unless we click "Agree" or Cancel" the install process just waits for our user interaction. The OS was not frozen. It was just in a waiting for user state.

Boot Repair is not included in the Ubuntu live/install image. We have to run the Ubuntu live session, connect to the internet and install Boot Repair or download and burn the Linux Secure Remix image, which is Ubuntu with Boot Repair and OS-Remover already installed. There are plenty of posts on this forum from users using Boot Repair.

But there is some thing many do not understand. Boot Repair is designed to fix boot loader problems. It is not designed to fix OS loading problems that occur after the boot loader has done its job.

So, do you get the Grub boot menu? If you do you can open the Advance Options for Ubuntu sub-menu and select Recovery mode. At the Recovery menu you can take either or both of two choices.

a) Select Resume and see if that loads to a working desktop using an fall back open source video driver and proceed from there. Or

b) select Network. That will establish an internet connection and put the file system into read/write mode. Then select Root and run these to commands.

```
apt-get update
apt-get upgrade
```

and note any error messages. Then type exit and then select Resume.

We need to separate problems. So, what is the problem? Not able to load the OS? Or disk is full? So, please describe how far the OS loading process gets before you get that black screen. We need to identify if the problem is the boot loader not finding the Linux Kernel or the loading of Ubuntu that is breaking at some point.

Regards

---

### Post by nu2u904 on 2014-10-22
> **slickymaster said:**
> Have a read at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you slickymaster. I did visit that site and when I get home I will follow it. In the meantime could you or another moderator answer the rest of my question. How do I redirect program installs from my 'filled' live disk pseudo root to my installed u14.04 real root. How do I do a df -h of my hard drive ?

Donald

---

### Post by nu2u904 on 2014-10-22
Thank you for your response. I get the blank screen immediately after the acer computer splash screen. I tried Crl-t to try to get a terminal window to no avail same for Crl-Alt- F2. 

The problems are linked but I'll only respond to your question in this post.

Regards,

---

### Post by oldfred on 2014-10-22
Is now the issue you cannot boot live installer?

You should just be able to run df -H in terminal in live installer. It is one of the many commands that Boot-Repair runs in its summary report.

Did you configure live installer with persistence? That would allow you to save some data. 
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
       [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
    
You could only directly update your install by chrooting into your install from the live installer. Chroot is CHange ROOT or booting with kernel from live installer, but then switching to use rest of system that you mount.

Couple of examples of chroot to reinstall grub. But once in your chroot you can do just about anything.
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by nu2u904 on 2014-10-24
Thank you oldfred. I have read all your references. I have no problem booting and running live USB; the  same one I used to install successfully install u14.04.1.  I was happy wd] even after I enabledih the install until I at5tempteuniverse d to install Wine from the software  center. Wine appeared to be installing ok so I iniated the install of 32 other programs. Then I noticed that Wine was stuck 1/2 way. All the other programs were waiting for install. I subsequently learned that Wine was waiting for my acceptance of Microsoft fonts. This window was hidden to me. I thought something was wrong and restarted the computer. Thats when I got the blank screen immediately after the Acer splash screen and my difficulties began. I tried to fin d  boot repair.  [sudo apt-get boot-repair; file not found] even after i enabled the  universe repositiry.  [sudo fdisk  -l ] only displayed my usb disk. Is there something simple I can do.I

---

### Post by oldfred on 2014-10-24
Your drive is probably corrupted. But fsck should fix it.
Best never to force shutdown but remember the Elephants first.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)

You probably need to run fsck from live installer.
      
 Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

   #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by nu2u904 on 2014-10-24
What is the package name for boot-repair? apt-get doesn't like boot-repair, Boot-Repair, Boot Repair ?  How do I find a package name?

---

### Post by oldfred on 2014-10-24
Boot-Repair is not in the repository, you have to add a ppa. And there is not a trusty version, but have to use saucy which will work.
Instructions to install are here:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nu2u904 on 2014-10-27
tHANK YOU OLDFRED. i WAS SUCCESSFUL INSTALLING bOOT rEPAIR HAD NO PROBLEM EVEN THOUGH sOFTWARE uPDATE WOULD NOT ALLOW ME TO CHECK THE OTHER REPOSITORIES; KEPT UNCHECKING MY CHECKS. tHE PPA HAD NO PROBLEM DOWNLOADING PACKAGES  FROM UNIVERSE AND MULTIVERSE REPOSITORIES. i THEN RAN bOOT rEPAIR AND RESPONDED TO THE REPAIR OPTION. bOOT rEPAIR THEN MOSTED THE MESSAGE: please go to the repository containing grub2 and then try again. How do I find this repository? Can I use the terminal and what should the command be. I posted the paste.ubuntu.com [Create  Bootinfo summary report].
The post was autosaved twice. I was unable to find it. I was told to go to the last place you posted to and it would be just below the text input area. I accidentaly hit cap lock I apologize.

---

### Post by oldfred on 2014-10-27
Is Internet working?

Updating syste, posting and updating the summary report needs working Internet. Best to always use wired Ethernet until fully updated.

You can just run another summary report and post link it gives.

---

### Post by nu2u904 on 2014-10-27
Thank you oldfred.  I found my partial autosaved post  at the bottom of the Feedback forum as a blue label that I then clicked and here is what was saved

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     8693999     4346968+   b  W95 FAT32
/dev/sda2   *     8694000   329859071   160582536    7  HPFS/NTFS/exFAT
/dev/sda3       371180941   390715919     9767489+   5  Extended
/dev/sda4       329859072   371179519    20660224   83  Linux
/dev/sda5       371180943   389778479     9298768+  83  Linux
/dev/sda6       389778543   390715919      468688+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
What repository is it and how do I enable it?

 [/code]

I will post again the Create Bootinfo report as soon as get home and to a ubuntu computer. 

This code is from the command: sudo fdisk -l.
As i posted Boot Repair stopped and queried me to enable the repository containing  grub2 and its packages. Then try again. How do I  find the repository that contains grub2 and how do I enable it. I was connected to the internet by ethernet. As I said ppa had no problem accessing univeerse and multiverse repositories.

Why did Software Update not allow me to check for the other repositories? Are you saying connection to the internet is the issue even though I wasconnected. I left the comper running so I would not lose  Boot R%epair. Where does live disk store the files if it doesn't write to the hard drive. How can I tell live disk to save to a 32GB USB device?

---

### Post by oldfred on 2014-10-27
Grub should be in default Ubuntu repository. Nothing extra should be required.
Usually if not working, the Internet is not working. 
Did you change from default repository. I do use a local one for better update speed, but it has all the Ubuntu updates, just may be a day later.

Live Disk is just saving into RAM. If you create live installer on flash drive that is a bit larger you can enable persistence which gives you a little room to save things. But you cannot update installer as it just the image as originally released.

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

You can also save to anther flash drive or any drive that you can mount. If Linux formatted you may have permission & ownership issues to work around.

---

### Post by nu2u904 on 2014-10-28
Thank you oldfred. Again I thought I was home free oon my Acer Aspire one D255. I followed your directi ons obtaqined and ran Boot Repair. No problem selected summary and then reran install line and selected boot repair. That ra, removed the live n and then requested  chroot which I then ran without error. I shut down the system normallyusb and rebooted, brief Acer splash screen and then blinking cursor in upper left corner, nothing else3. I ried Alt-Sysrq reisub without effect. That told me the system did not boot. I repeated th  e boot process, same result.

Here is the summary:    [http://paste.ubuntu.com/8724377](http://paste.ubuntu.com/8724377)

```

sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda2" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda2" apt-get install -y --force-yes lvm2
sudo chroot "/mnt/boot-sav/sda2" apt-get purge -y --force-yes grub*


sudo chroot "/mnt/boot-sav/sda2" apt-get purge -y --force-yes grub*


http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,170 kB in 2s (436 kB/s)                 
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra gawk gksu glade2script libgksu2-0 libsigsegv2
  pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
0 upgraded, 9 newly installed, 0 to remove and 443 not upgraded.
Need to get 1,520 kB of archives.
After this operation, 5,715 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 i386 2.10-2 [14.8 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk i386 1:4.0.1+dfsg-2.1ubuntu2 [730 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 i386 2.0.13~pre1-6ubuntu4 [71.4 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu i386 2.0.2-6ubuntu2 [27.5 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main boot-sav all 3.199~ppa40~saucy [430 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main boot-repair all 3.199~ppa40~saucy [47.2 kB]
Get:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main boot-sav-extra all 3.199~ppa40~saucy [142 kB]
Fetched 1,520 kB in 1s (1,198 kB/s)     
Selecting previously unselected package libsigsegv2:i386.
(Reading database ... 173688 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_i386.deb ...
Unpacking libsigsegv2:i386 (2.10-2) ...
Setting up libsigsegv2:i386 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 173696 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_i386.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_3.199~ppa40~saucy_all.deb ...
Unpacking boot-sav (3.199~ppa40~saucy) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_3.199~ppa40~saucy_all.deb ...
Unpacking boot-repair (3.199~ppa40~saucy) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_3.199~ppa40~saucy_all.deb ...
Unpacking boot-sav-extra (3.199~ppa40~saucy) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_i386.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_i386.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (3.199~ppa40~saucy) ...
Setting up boot-repair (3.199~ppa40~saucy) ...
Setting up boot-sav-extra (3.199~ppa40~saucy) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:8917): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
boot-repair is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 443 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda2" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
1 not fully installed or removed.
Need to get 0 B/27.8 kB of archives.
After this operation, 134 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 197729 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) over (3.4+nmu1ubuntu1) ...
Processing triggers for update-notifier-common (0.154.1) ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /tmp/tmp2XwIiv.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /tmp/tmpnZiPqw.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpSnGHE9.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpQlpsxI.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpuXv0iK.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpgMvplA.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpFgw3SG.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmpieqsgF.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /tmp/tmp7YOcA4.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmp_rc0Rf.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /tmp/tmp2_cHnm.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda2" apt-get install -y --force-yes lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda2" apt-get purge -y --force-yes grub*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'sabily-grub-artwork' for regex 'grub*'
Note, selecting 'grub-ieee1275-bin' for regex 'grub*'
Note, selecting 'grub-pc-dbg' for regex 'grub*'
Note, selecting 'grub-efi-ia32-bin' for regex 'grub*'
Note, selecting 'grub-imageboot' for regex 'grub*'
Note, selecting 'grub-legacy-doc' for regex 'grub*'
Note, selecting 'grub-emu-dbg' for regex 'grub*'
Note, selecting 'grub-disk' for regex 'grub*'
Note, selecting 'grub-theme-starfield' for regex 'grub*'
Note, selecting 'grub-coreboot-dbg' for regex 'grub*'
Note, selecting 'grub2-splashimages' for regex 'grub*'
Note, selecting 'grub-gfxpayload-lists' for regex 'grub*'
Note, selecting 'grub-common' for regex 'grub*'
Note, selecting 'ruby-rspec-longrun' for regex 'grub*'
Note, selecting 'grub-ipxe' for regex 'grub*'
Note, selecting 'grub-invaders' for regex 'grub*'
Note, selecting 'grub-xen-bin' for regex 'grub*'
Note, selecting 'grub-pc' for regex 'grub*'
Note, selecting 'grub-efi' for regex 'grub*'
Note, selecting 'wmlongrun' for regex 'grub*'
Note, selecting 'grub-rescue-pc' for regex 'grub*'
Note, selecting 'congruity' for regex 'grub*'
Note, selecting 'grub-efi-amd64' for regex 'grub*'
Note, selecting 'grub-ieee1275-dbg' for regex 'grub*'
Note, selecting 'grub-splashimages' for regex 'grub*'
Note, selecting 'grub-efi-amd64-bin' for regex 'grub*'
Note, selecting 'grub-emu' for regex 'grub*'
Note, selecting 'pv-grub-menu' for regex 'grub*'
Note, selecting 'kde-config-grub2' for regex 'grub*'
Note, selecting 'grub-efi-ia32-dbg' for regex 'grub*'
Note, selecting 'ruby-gruff' for regex 'grub*'
Note, selecting 'grub-xen' for regex 'grub*'
Note, selecting 'grub-legacy' for regex 'grub*'
Note, selecting 'grub-linuxbios' for regex 'grub*'
Note, selecting 'grub' for regex 'grub*'
Note, selecting 'grun' for regex 'grub*'
Note, selecting 'grub2-common' for regex 'grub*'
Note, selecting 'grub-pc-bin' for regex 'grub*'
Note, selecting 'grub2' for regex 'grub*'
Note, selecting 'grub-legacy-ec2' for regex 'grub*'
Note, selecting 'grub-coreboot-bin' for regex 'grub*'
Note, selecting 'grub-ieee1275' for regex 'grub*'
Note, selecting 'grub-efi-ia32' for regex 'grub*'
Note, selecting 'grub-doc' for regex 'grub*'
Note, selecting 'longrun' for regex 'grub*'
Note, selecting 'grub-yeeloong' for regex 'grub*'
Note, selecting 'fgrun' for regex 'grub*'
Note, selecting 'grub-efi-ia64' for regex 'grub*'
Note, selecting 'grub-xen-dbg' for regex 'grub*'
Note, selecting 'grub-coreboot' for regex 'grub*'
Note, selecting 'espresso-grub' for regex 'grub*'
Note, selecting 'grub-firmware-qemu' for regex 'grub*'
Note, selecting 'grub-efi-i386' for regex 'grub*'
Note, selecting 'grub-efi-amd64-dbg' for regex 'grub*'
Package 'grub-efi-ia64' is not installed, so not removed
Package 'grub-yeeloong' is not installed, so not removed
Package 'grub-legacy' is not installed, so not removed
Package 'espresso-grub' is not installed, so not removed
Package 'grub-efi-i386' is not installed, so not removed
Package 'grub' is not installed, so not removed
Package 'grub-doc' is not installed, so not removed
Package 'grub-ipxe' is not installed, so not removed
Package 'grub-legacy-doc' is not installed, so not removed
Package 'congruity' is not installed, so not removed
Package 'fgrun' is not installed, so not removed
Package 'grub-disk' is not installed, so not removed
Package 'grub-imageboot' is not installed, so not removed
Package 'grub-invaders' is not installed, so not removed
Package 'grub-splashimages' is not installed, so not removed
Package 'grub2-splashimages' is not installed, so not removed
Package 'grun' is not installed, so not removed
Package 'kde-config-grub2' is not installed, so not removed
Package 'longrun' is not installed, so not removed
Package 'pv-grub-menu' is not installed, so not removed
Package 'ruby-gruff' is not installed, so not removed
Package 'ruby-rspec-longrun' is not installed, so not removed
Package 'sabily-grub-artwork' is not installed, so not removed
Package 'wmlongrun' is not installed, so not removed
Package 'grub-efi' is not installed, so not removed
Package 'grub-efi-amd64' is not installed, so not removed
Package 'grub-efi-amd64-bin' is not installed, so not removed
Package 'grub-efi-amd64-dbg' is not installed, so not removed
Package 'grub-efi-ia32' is not installed, so not removed
Package 'grub-efi-ia32-bin' is not installed, so not removed
Package 'grub-efi-ia32-dbg' is not installed, so not removed
Package 'grub-ieee1275' is not installed, so not removed
Package 'grub-ieee1275-bin' is not installed, so not removed
Package 'grub-ieee1275-dbg' is not installed, so not removed
Package 'grub-legacy-ec2' is not installed, so not removed
Package 'grub-pc-dbg' is not installed, so not removed
Package 'grub-xen' is not installed, so not removed
Package 'grub-xen-bin' is not installed, so not removed
Package 'grub-xen-dbg' is not installed, so not removed
Package 'grub-coreboot' is not installed, so not removed
Package 'grub-coreboot-bin' is not installed, so not removed
Package 'grub-coreboot-dbg' is not installed, so not removed
Package 'grub-emu' is not installed, so not removed
Package 'grub-emu-dbg' is not installed, so not removed
Package 'grub-firmware-qemu' is not installed, so not removed
Package 'grub-linuxbios' is not installed, so not removed
Package 'grub-rescue-pc' is not installed, so not removed
Package 'grub-theme-starfield' is not installed, so not removed
Package 'grub2' is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*
0 upgraded, 0 newly installed, 5 to remove and 37 not upgraded.
After this operation, 16.8 MB disk space will be freed.
(Reading database ... 197737 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.6) ...
Removing grub-pc (2.02~beta2-9ubuntu1) ...
Purging configuration files for grub-pc (2.02~beta2-9ubuntu1) ...
Removing grub2-common (2.02~beta2-9ubuntu1) ...
Removing grub-pc-bin (2.02~beta2-9ubuntu1) ...
Removing grub-common (2.02~beta2-9ubuntu1) ...
Purging configuration files for grub-common (2.02~beta2-9ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
ubuntu@ubuntu:~


```

I selected the option do not remove grub2 as it was highlighted.

I'am at loss what to do now.

---

### Post by oldfred on 2014-10-28
It looks like you may have the issue with Microsoft fonts locking the update.
You have to accept the install of the fonts, and that accept box is often hidden behind other pop-up boxes.
It is not gui, so you have to use tab, spacebar and enter to accept the fonts.
Then the rest of the updates should run.

---

### Post by nu2u904 on 2014-10-29
Thank you oldfred. While doing boot repair I accepted the displayed microsoft true fonts message. It was suggested that I should change the BIOS order for the hard drive to be first and since there is no usb drive present I don't see that as an  issue since I need usb first in order to run this live session.

---

