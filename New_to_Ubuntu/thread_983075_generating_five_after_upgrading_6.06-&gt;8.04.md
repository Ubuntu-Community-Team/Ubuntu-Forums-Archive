---
title: "generating five after upgrading 6.06-&gt;8.04"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by igor1102828 on 2008-11-15
Hello, everyone.
I am trying to upgrade Ubuntu Dapper to Ubuntu Hardy.
Th version Dapper worked properly. After one of updates via Synaptic Manager
I decided to use its suggestion to upgrade till Hardy the system internet, 
have clicked, and agreed with all suggestions. When I tried to reboot to new system,
I failed in two places: 1) I was forced to add "noapic" mode, then booting went further, 
and 2) every 5 seconds in screen appeared the cipher "5" both in safe mode and in normal,
so, I am not able even to login!!: whatever I am trying to write, in-between the cipher 5
is generated (like "ubu5nt5u55555 .."). 
Then I've read that it is better to use Alternate CD, I've downloaded it and tried to repair the system with it.
Well, I can reach the shell with the Alternate 8.04 CD, but where the problem comes from, I have no idea.
(I have 3-boot system, Vista/XP/Ubuntu, both Windows parts work properly, no changes are seen).
How to handle it? Any ideas?
Any help is appreciated!

---

### Post by igor1102828 on 2008-11-15
pardon

---

### Post by Steve1961 on 2008-11-15
As far as I know you can't upgrade directly from dapper to hardy, you would have to do it in small stages.  That would take so long you would be better off backing up your data and doing a clean install.

If you have actually tried to upgrade in stages you potentially face all sorts of issues along the way.  So unless you really know what you're doing just do a clean install.

---

### Post by igor1102828 on 2008-11-15
Thanks, Steve, but the problem is not in data only, - I have too many programs installed therein. I'd prefer in this case to get back to Dapper, but, I am afraid, this would be dificult. Is it possible?
Nevetheless, i'd like to try to understand, where this strange print-on-screen every 5 seconds can come from, which programs in the system are responsible for that and, possibly, to handle the problem.

---

### Post by Steve1961 on 2008-11-15
> **igor1102828 said:**
> Thanks, Steve, but the problem is not in data only, - I have too many programs installed therein. I'd prefer in this case to get back to Dapper, but, I am afraid, this would be dificult. Is it possible?

Well it's technically possible if you use something called apt-pinning.  I tried it once a few years ago and ended up in a huge mess, so I really wouldn't recommend it.  there's some links on this thread from yesterday about the possibility:

[http://ubuntuforums.org/showthread.php?t=979842](http://ubuntuforums.org/showthread.php?t=979842)

However, I'm sorry to tell you that you'll probably have to bite the bullet and do a clean install

---

### Post by igor1102828 on 2008-11-15
Thanks, I've read the suggestions in the link you've given me. Both ways, clean install and downgrade, therefore, look highly pessimistic for me. It really makes sense for me to make an attempt to understand, **[COLOR="Red"]where from this strange command for print-on-screen  comes from every 5 seconds[/COLOR]**, which programs in the system are responsible for that and, possibly, to handle the problem. Just in order to be able to get into normal mode.

---

### Post by Steve1961 on 2008-11-15
> **igor1102828 said:**
> Thanks, I've read the suggestions in the link you've given me. Both ways, clean install and downgrade, therefore, look highly pessimistic for me. It really makes sense for me to make an attempt to understand, **[COLOR="Red"]where from this strange command for print-on-screen  comes from every 5 seconds[/COLOR]**, which programs in the system are responsible for that and, possibly, to handle the problem. Just in order to be able to get into normal mode.


Have you tried a simple sudo apt-get -f install followed by sudo apt-get update and sudo apt-get dist-upgrade just to see if the upgrade you've attempted is fixable?

If you can't log in you could always use a live ubuntu cd to chroot into the installed system and run those commands

---

### Post by NullHead on 2008-11-15
Well it sounds like an issue with your video drivers. I'd try re-doing your xorg.conf with this command. Can you type in a f1 terminal? Try pressing Ctrl + Alt + f2 and login and put in your password and type this in: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then restart your system from the command line like so: ```
sudo shutdown -r now
```

That would be what I would do if I had that issues, but there's no telling if that will fix your problem.

---

### Post by kansasnoob on 2008-11-15
> **NullHead said:**
> Well it sounds like an issue with your video drivers. I'd try re-doing your xorg.conf with this command. Can you type in a f1 terminal? Try pressing Ctrl + Alt + f2 and login and put in your password and type this in: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then restart your system from the command line like so: ```
sudo shutdown -r now
```

That would be what I would do if I had that issues, but there's no telling if that will fix your problem.

+1. I was going to suggest reconfiguring the works:

```
sudo dpkg-reconfigure -phigh -a
```

---

### Post by igor1102828 on 2008-11-15
The situation is as follows.
I've tried Steve's suggestion: got into system via Alternate 8.04 CD,
 selected *Rescue a broken system*, 
then again *noapic* via *F6* key 
and have performed all these commands. Indeed, some packages have been loaded and some replaced. Then I tried to reboot via 1st hard disk, the ***5-problem***  stopped me at the stage of login (I can write the username, but cannot password within 5-second interval!). The same situation in f1 screen.
Then I've checked, if the situation will change if I boot from Live 8.04 CD. The answer is NO,
the "5-problem" remains. Then I've got back to the Alternate 8.04 CD, again went into system via 
the "Rescue a Broken System" option and got to the shell, and tried to perform the NullHead's suggestion.
The answer was 
[COLOR="DarkSlateBlue"]FATAL: could not load /lib/modules/2.6.24-19-generic/modules.dep
[/COLOR]
I've looked at the /lib/modules/. There are 2.6.24-21-386 and 2.6.24-21-generic.
However, if boot via Live 6.06 CD and mount the Ubuntu disk to the created directory /oldroot, I've got 
the following:

[COLOR="Indigo"]ubuntu@ubuntu:/$ sudo chroot /oldroot

root@ubuntu:/# ls
bin    etc         initrd.img.old  media   output  skype.tmp  usr
boot   home        lib             mnt     proc    srv        var
cdrom  initrd      lib64           MyLibs  root    sys        vmlinuz
dev    initrd.img  lost+found      opt     sbin    tmp        vmlinuz.old
root@ubuntu:/# ls lib/modules
2.6.15-51-386  2.6.15-51-k7      2.6.15-51-server-bigiron  2.6.24-21-386
2.6.15-51-686  2.6.15-51-server  2.6.15-52-386             2.6.24-21-generic
root@ubuntu:/# sudo dpkg-reconfigure -phigh xserver-xorg
sudo: unable to resolve host ubuntu
grep: /proc/cmdline: No such file or directory
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081115225621[/COLOR]
[COLOR="Navy"]FATAL: Could not load /lib/modules/2.6.15-26-386/modules.dep:[/COLOR] [COLOR="Indigo"]No such file or directory
grep: /proc/cpuinfo: No such file or directory
rm: cannot remove `/tmp/dexconf-tmp-9281/Header': Function not implemented
rm: cannot remove `/tmp/dexconf-tmp-9281/InputDeviceKeyboard': Function not impl emented
rm: cannot remove `/tmp/dexconf-tmp-9281/InputDeviceMouse': Function not impleme nted
rm: cannot remove `/tmp/dexconf-tmp-9281/Device': Function not implemented
rm: cannot remove `/tmp/dexconf-tmp-9281/Monitor': Function not implemented
rm: cannot remove `/tmp/dexconf-tmp-9281/Screen': Function not implemented
rm: cannot remove `/tmp/dexconf-tmp-9281/ServerLayout': Function not implemented
rm: cannot remove `/tmp/dexconf-tmp-9281/dexconf-out': Function not implemented
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
root@ubuntu:/#
[/COLOR]
As seen, it requires now other 2.6.15-26-386 thing. Does it mean that it tries reconfigure from CD? I thought that it seeks in repositaria. 
The comment "[COLOR="DarkRed"]sudo: unable to resolve host ubuntu[/COLOR]" is also strange. Anyway, it is still not clear, what should I do. Should I try to find somewhere this required module [COLOR="DarkRed"]2.6.24-19-generic[/COLOR]? 
And why everything works perfectly under 6.06 Live CD, while under BOTH Alternate and Live 8.04 everything is broken? He-e-e-e-lp!!!

---

### Post by igor1102828 on 2008-11-15
If it does not find the module, reconfiguring the works, probably, will not help?
Does it mean that this is simply a bug in the 8.04 distro?

---

### Post by Zill on 2008-11-15
> **Steve1961 said:**
> As far as I know you can't upgrade directly from dapper to hardy, you would have to do it in small stages...
[You can directly upgrade to Ubuntu 8.04 LTS ("Hardy Heron") from Ubuntu 7.10 ("Gutsy Gibbon") or from Ubuntu 6.06 LTS ("Dapper Drake").]("https://help.ubuntu.com/community/HardyUpgrades")

AIUI, it is possible to upgrade directly from one LTS release to another LTS release.  However, if an "interim" release is installed then it is necessary to install all others sequentially.

---

### Post by igor1102828 on 2008-11-16
> **Zill said:**
> [You can directly upgrade to Ubuntu 8.04 LTS ("Hardy Heron") from Ubuntu 7.10 ("Gutsy Gibbon") or from Ubuntu 6.06 LTS ("Dapper Drake").]("https://help.ubuntu.com/community/HardyUpgrades")

AIUI, it is possible to upgrade directly from one LTS release to another LTS release.  However, if an "interim" release is installed then it is necessary to install all others sequentially.

That is exactly what I did: I had Ubuntu 6.06 LTS and upgraded to Ubuntu 8.04 LTS (I followed instructions from Ubuntu [https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS](https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS) 
). The fact which calls for an explanation is that [COLOR="Red"]I have the same "5-second" problem even if I load Ubuntu 8.04 LTS simply from its Live CD[/COLOR] (!), ***whereas if I load Ubuntu 6.06 LTS from Live CD, this problem is absent.*** However, if it was a bug, other people would experience the same problems. Should I conclude from this fact that this particular version somehow does not have a module which fits to my hardware and I have to re-install some of earlier versions? At the moment I have only two ways to communicate with the system: Either via Alternate 8.04 LTS CD in rescue mode, where it gives shell without "5-secods" problem!), but some problems arise with [COLOR="Navy"]root password[/COLOR] (about this -below), or via Live 6.06 LTS CD, via mounting root part. 
II. [COLOR="Navy"]Root password[/COLOR]
[COLOR="Navy"]In the file /etc/hosts in Laptop with Ubuntu 6.06 LTS I have[/COLOR]
[COLOR="DarkRed"]127.0.0.1       localhost
127.0.1.1       MyName-laptop[/COLOR]
[COLOR="Navy"]and in desktop with the same Ubuntu 6.06 LTS I had[/COLOR]
[COLOR="DarkRed"]127.0.0.1       localhost
127.0.1.1       MyName-desktop.[/COLOR]
[COLOR="Navy"]Now, on the way to shell from Alternate Ubuntu 8.04 LTS CD it asks me computer's name. If I give "MyName", it generates [/COLOR]
[COLOR="DarkRed"]127.0.0.1       localhost MyName-desktop
127.0.1.1       MyName-desktop [/COLOR]
and after that I have problems. Is t some bug?
Any more sugestions?

---

### Post by Zill on 2008-11-16
igor1102828:  It looks like you have two PCs - a desktop and a laptop.  Do you get the same problem with your Live CD on *both* PCs?

If so then it is likely that this is corrupted.  I suggest you download the ISO again, ensure the md5 sum is correct and then burn a new CD.  From the initial menu, check the new disk for errors.

When you have verified that this is a good disk, reboot the PC with the new CD and run Ubuntu from the live CD - do not try to install it at this stage.  Accept all the defaults when booting and see if Ubuntu starts up correctly.

If it does, and you can type without the mysterious "5" problem, then you can reinstall the system by clicking on the desktop icon.  Note that this will overwrite (delete) your existing programs and data unless you have used a separate /home partition and ensured that it is *not* reformatted.

If the live CD still produces the "5" problem then it looks to me like either a hardware keyboard and/or video fault or an incompatibility with the software.  I don't know what language/regional settings you are using but if it is not English then it may also be worth selecting this for test purposes.

Regarding the /etc/hosts file, I am slightly mystified by your reference to "root password" as /etc/hosts does not contain the password but rather the PC name.  Ubuntu does not even have a "root password" by default, instead relying on the user password and then using sudo for root access when required.

---

### Post by igor1102828 on 2008-11-16
Thanks, Zill, for good idea to check CD. I was sure that it is OK because after downloading I have checked [COLOR="Navy"]MD5SUM[/COLOR]. It was and it is OK indeed, since now I am writing from Live 8.04 LTS CD with which I've booted laptop. On the laptop this misterious five does not arise. The assumption about video or keyboard fault also does not explain the things, since the same desktop with the same keyboard and video card works properly a) under Windows XP b)under Windows Vista c) under Live Ubuntu 6.06 LTS CD. 
The language I am using all the time is English (tried both US and UK). 
As regards /etc/hosts, I beg your pardon, I've described the situation inaccurately, I remember that shell refused to do sudo writing me that I don't have rights or smth like that. When I meet this problem again, I'll describe it with details (for me it is difficult to do this from the shell; probably, I had to write it to a separate file, then mount usb flash and copy it therein, but I don't know how to get all this convesation with SHELL into file). 
So, the conclusion is that the **[COLOR="DarkRed"]Live CD 8.04 is OK[/COLOR]**. [COLOR="Navy"]md5sum[/COLOR] for Alternate disk also was OK...
[COLOR="DarkRed"]**Is it possible indeed that some of my hardware (keyboard or video) are incompatible with 8.04 LTS whereas compatible with 6.06 LTS ?!**[/COLOR]

---

### Post by Zill on 2008-11-16
igor1102828:  Even though the md5 sum is correct, this does not verify the CD burn.  With the live CD in the drive, when you boot up a menu appears which has an option to "verify disk" (or similar - I can't remember the exact wording!)  I suggest you run this first to ensure the disk is good.

Then reboot this good live CD again, in the desktop PC, and see how far it gets.  No password is required for this so there should be no need to *type* anything.  Does the PC boot correctly and does the Ubuntu desktop appear?

If so, what happens if you then open an application like gedit or terminal and then type.  Does the text you type appear correctly?

If any error messages appear at any stage please describe them as accurately as possible.

---

### Post by igor1102828 on 2008-11-17
> **Zill said:**
> igor1102828:  Even though the md5 sum is correct, this does not verify the CD burn.  With the live CD in the drive, when you boot up a menu appears which has an option to "verify disk" (or similar - I can't remember the exact wording!)  I suggest you run this first to ensure the disk is good.

Then reboot this good live CD again, in the desktop PC, and see how far it gets.  No password is required for this so there should be no need to *type* anything.  Does the PC boot correctly and does the Ubuntu desktop appear?

If so, what happens if you then open an application like gedit or terminal and then type.  Does the text you type appear correctly?

If any error messages appear at any stage please describe them as accurately as possible.

1. I have veryfied both, Live and Alternative 8.04 LTS CDs, - no errors.
2. Both can boot only with "noapic" option [COLOR="DarkRed"](even in the "Check integrity of the disk" option)[/COLOR].
3. I have rebooted good live CD again, in the desktop PC, "fives" are still generating in both, black screen (safe mode) and, if I manage to make [COLOR="Navy"]cntrl-D[/COLOR] after deleting all "5-s", it goes to the normal mode. The screen with this nice bird appears. When I open terminal, 5-s immediately start appear therein. When I open, say, vi, they are generated only in insert mode, not in the command mode. Nevertheless, it was difficult even to perform the command [COLOR="DarkRed"]wq![/COLOR] because it is transformed to [COLOR="DarkRed"]wq5!5[/COLOR] , etc.. In the text editors the text, consisting of 5-s (55555555) starts to appear even before I start typing.

There no any error messages on he way!
4. Booting Aternate 8.04 LTS.
a. "noapic" option is nesessary.
b. verification does not show any errors.
c. I enter the "Rescue mode" to my /dev/sdb1
(I have two disks, on all sda are Vista and XP)
d. Execute a shell in /dev/sdb
[COLOR="Red"]There is no this "5-problem " in the shell mode.[/COLOR]
It brings me to the root directory **[COLOR="Navy"]/[/COLOR]**.
Just in case I played again 
```
dpkg --configure -a
exit
```
and selected to reboot system.
**Nothing has changed.** The problem is, that there are no any error messages...
Any other suggestions?

---

### Post by Zill on 2008-11-17
igor1102828:  As the Ubuntu 8.04 live CD does not run correctly I can only assume there is a hardware compatibility problem.  However, I doubt it is lack of resources if the same PC can run Vista!

I suggest you download the ISO for Xubuntu 8.04 and see if this live CD runs OK.  This should require fewer resources which *may* help.
[URL="http://www.xubuntu.org/get"]
http://www.xubuntu.org/get[/URL]

ps.  Please post your PC specifications.

---

### Post by igor1102828 on 2008-11-17
> **Zill said:**
> igor1102828:  As the Ubuntu 8.04 live CD does not run correctly I can only assume there is a hardware compatibility problem.  However, I doubt it is lack of resources if the same PC can run Vista!

I suggest you download the ISO for Xubuntu 8.04 and see if this live CD runs OK.  This should require fewer resources which *may* help.
[URL="http://www.xubuntu.org/get"]
http://www.xubuntu.org/get[/URL]

ps.  Please post your PC specifications.

[COLOR="Indigo"]**Answers**.
1) I am not restricted in resources. 
***Here is Specification of my PC***.
[/COLOR]
AMD Athlon(tm) Dual Core Processor 4200+ 2.20 Ghz
(ACPI x86-based PC)
Memory RAM 2047 Mb
System type 32-bit Operating system
Display adaptors - NVIDIA GeForce 7500 LE
IDE ATA/ATAPI controllers:
  IDE channel
  IDE channel
  NVIDIA nForce serial ATA Controller
  NVIDIA nForce serial ATA Controller
  Standard Dual Channel PCIIDE Controller
IEEE 1394 Bus host controllers:
  AGERE OHCI Compliant IEEE 1394 Host Controller
Keyboard: HID Kyboard device
Monitor: LG L1960TR(Analog)
Network adapters:
  Fujitsu Siemens Computers WLAN 802.11b/g (SiS163u)
  NVIDIA nForce Networking controller
Processors:
  AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
  AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
Sound, video and Game controllers
  Pinnacle PCTV 310i Capture Device
  RealTek High Definition Audio
Storage controllers
  Adaptec AIC-7870 PCI SCSI Controller (Emulated)
  Microsoft iSCSI Initiator
System devices (long list - what specifically cn be of interest?)
-------------------------
[COLOR="DarkRed"]2) I've downloaded Xubuntu 8.04.1 (md5 OK, burned CD), booted, the same story! In both terminal and text editor it prints 55555...This is extremely strange: Ubuntu 6.06 worked and works from Live CD perfectly,[/COLOR] [COLOR="Red"]what is changed? [/COLOR]

---

### Post by NullHead on 2008-11-17
Try a different keyboard.

---

### Post by igor1102828 on 2008-11-17
> **NullHead said:**
> Try a different keyboard.
May be it's a good idea - tomorrow I'll buy anoher one and try. Thanks.

---

### Post by Zill on 2008-11-17
> **igor1102828 said:**
> May be it's a good idea - tomorrow I'll buy anoher one and try. Thanks.
...and consider adding a new PC to your shopping list...

Half-joking but I am right out of ideas! :-(

---

### Post by igor1102828 on 2008-11-18
> **NullHead said:**
> Try a different keyboard.
Thanks again, people, for you time! Unfortunately, the telega still does not want to move:
I've made the test with other keyboard (actually, this is the keyboard, which has come
 in the package together with the computer and is produced  (as the computer itself) by Fujitsu Siemens). So, [COLOR="DarkRed"]everything works perfectly 
1) Under Vista
2) Under Windows XP
3) Under Ubuntu 6.06 LTS (booted from Live CD).[/COLOR]

So, since everything works under other systems, it would be nice to get help first in two quite concrete questions: 
[COLOR="Red"][B][I]which programs in the system can be responsible for

a) generating time sequence with the period T=5 s 
b) provide response to this signal in the form print-on-screen.
[/I][/B][/COLOR]
**Any more suggestions?**

---

### Post by NullHead on 2008-11-18
File a bug report here: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
And re-install 6.04LTS. I have no idea why the new versions are doing this other than it tells me that something changed recently doesn't agree with your keyboard\motherboard settings.

---

### Post by igor1102828 on 2008-11-18
> **NullHead said:**
> File a bug report here: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
And re-install 6.04LTS. I have no idea why the new versions are doing this other than it tells me that something changed recently doesn't agree with your  keyboard\motherboard settings.

I've placed the bug report. I am not sure, that this is keyboard involved:
I do not even touch keyboard when it starts inserting 5-s.  
One of reasons why I've made an attempt to upgrade from 6.06 LTS to 8.04 LTS was annoying suggestion of almmost every website to refresh/install new version of Flash player, and Ubuntu 6.06 LTS has some libraries which are inconsistent with requirements of Flash installer. So, in spite of my love to Ubuntu I don't want to move back. If Ubuntu, Xubuntu, etc., do not work for my PC, I'll be forced to install some other Linux system. Alas..

---

### Post by igor1102828 on 2008-11-20
Little addition to symptoms. I've switched off ALL external hardware including the keyboard and mouse. The computer automatically has booted into Ubuntu 8.04 LTS and started to print in any place where the input mode is assumed: 5555... And when I've plugged in the USB connector for the wireless keyboad and mouse, nothing has changed.
This, probably, means that some of inner Fujitsu-Siemens PC devices is in a conflict with new Ubuntu...

---

