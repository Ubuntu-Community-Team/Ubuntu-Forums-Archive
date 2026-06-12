---
title: "Install ubuntu 12.10 with wubi and keep old ubuntu 11.10 wubi installation"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by RookieGui on 2013-06-08
Hello everyone!
[you may have seen this question on askubuntu, I'm posting this problem here as well because I hope on getting a faster and more complete reply]

         I'd like you to help me, if you may! 

  I need to install ubuntu 12.10 on my notebook, which has Windows 7 as  default OS, and I prefer to install it through wubi just to get the  least problems in terms of warranty
(therefore, freeing space to create an empty partition and putting a full install on it is not an answer in my case)

  My Hard Disk Drive current setup is the following:
  
[LIST]
[*]100 MB NTFS - Windows System - Primary Partition 
[*](C: ) 270 GB NTFS - Windows 7 OS - Primary Partition 
[*](D: ) 400 GB NTFS - Logical Partition 
[*]24 GB - Recovery Stuff - Primary Partition 
[/LIST]
  
I already installed ubuntu 11.10 using wubi ( in D: ), and I NEED to  keep that installation because I will be working on that setup in the  future
  (upgrading isn't an option either, i need 11.10 as it is)

  I already backed up 11.10 folder, and let's say I renamed "D:\ubuntu" to "D:\ubuntuOld"

1) Is there a way to install ubuntu 12.10 ( again, in D: ) with wubi in a  separate folder (with separate root.disk)? can you explain me how?

  2) It would be best if I could choose which version to boot between 12.10 and 11.10 ... but swapping root.disk files when I need the other ubuntu version, would do the trick for me, if that can be done.

Either way I'd like you to explain me what I should do in order to get those results.
  
I searched for an answer but I wasn't completely sure of the  procedures to apply in order to get exactly what I wanted, without  screwing up everything!
Looks like I need to be guided step by step, so please help me!

---

### Post by oldfred on 2013-06-08
There are only one or two here that know wubi well enough to answer your question. I know one also answers questions in askubuntu. I would think you can swap root.disks as I have seen that as a way to restore an old version that was backed up. You cannot dual boot wubi as I understand it. Note that wubi is being phased out. It does not work with gpt partitioned drives and all the new systems are UEFI with gpt partitioned drives.

Most of the rest of us suggest once you like Ubuntu that you convert to a full partitioned install. But alternatives do exist if you do not want to partition. Since you already have a logical partition adding a new / (root) partition is not much different than adding a new root.disk and does give more flexibility and reliability. With wubi you rely on the Windows boot loader and the NTFS file system.

I have a full install in 16GB flash drive. While USB is a bit slower once booted it runs well. You can use a flash drive or an external hard drive with your notebook for full installs and then could have several versions on one large flash drive or external hard drive.

While more a proof of concept, you can have your root.disk on an external drive and just boot with grub without Windows.
 See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

---

### Post by RookieGui on 2013-06-09
First of all, thanks for taking the time to reply!

> **oldfred said:**
> There are only one or two here that know wubi well enough to answer your question. I know one also answers questions in askubuntu. I would think you can swap root.disks as I have seen that as a way to restore an old version that was backed up. You cannot dual boot wubi as I understand it. Note that wubi is being phased out. It does not work with gpt partitioned drives and all the new systems are UEFI with gpt partitioned drives.
I think that switching root.disk is still the best option for me
I hope there's someone that can answer my first concern...

I just want to know if this could work:
 rename "D:\ubuntu" where 11.10 is installed to "D:\ubuntuOld"
reinstall wubi with 12.10 ( will the new install overwrite important files? like the  *wubildr* & *wubildr*.mbr in C:\ ? )
at this point, if I put again my 11.10 from "D:\ubuntuOld" to "D:\ubuntu" ( and back up the new install into "D:\ubuntuNew" ) will my 11.10 boot without flaws?

are there any other things to change/set up?
I mean... all the filenames and path should be identical when comparing "D:\ubuntuOld" and "D:\ubuntuNew" ... that should work without doing anything else as long as wubi 12.10 operates as the one I used to install 11.10
  
> **oldfred said:**
> Most of the rest of us suggest once you like Ubuntu that you convert to a full partitioned install. But alternatives do exist if you do not want to partition. Since you already have a logical partition adding a new / (root) partition is not much different than adding a new root.disk and does give more flexibility and reliability. With wubi you rely on the Windows boot loader and the NTFS file system.

I have a full install in 16GB flash drive. While USB is a bit slower once booted it runs well. You can use a flash drive or an external hard drive with your notebook for full installs and then could have several versions on one large flash drive or external hard drive.

While more a proof of concept, you can have your root.disk on an external drive and just boot with grub without Windows.
 See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)
I think that going through USB the cons would exceed the pros... I need that for programming and as long as I won't be doing any performance hungry computation soon, I might be in the near future... wubi was an acceptable compromise for me 
(I'm starting to think about getting a full install and hope everything goes well)

ok, newbie question time again:
if, out of frustration, I end up creating a logical partition to put a full install (provided that the resize of windows partition ( C: ) from Win7 integrated utility has gone well, without errors)
is that a way to keep windows boot loader as the first loader? from what I understood, it is possible if you install grub on the logical partition, leaving the MBR as it is, with it's original WBL ... but is there an option during ubuntu install that let me choose where to install grub?

( in case that's not possible, and I MUST have grub on MBR, is that possibile that windows get messed up? )

---

### Post by Karlchen on 2013-06-09
Hello, RookieGUI.

_Preface:_
When oldfred mentioned that there were only two people in this forum that were Wubi experts, I assume that one of the persons whom he had in mind was user **bcbc**. I am not sure who the second person is. sorry, my ignorance. ;)
Though I am *not an officially certified Wubi expert*, I have performed and have been using several Wubi installations during the past 3.5 years.
On one machine, I had a dual Wubi system - Ubuntu 10.04 and Linxu Mint 13 (Ubuntu 12.04) - living on a Windows 7 machine and used both Wubi installations for my office work without any hassle for almost 12 months.

[U]Summary:
[/U]By design, it is not possible to have more than 1 Wubi installation living on a given Windows system. But there is a way of achieving the goal nonetheless.

_Details of How I Did It: _

[LIST]
[*]The initial Wubi installation present on the Windows 7 machine, of course, was Ubuntu 10.04 (Lucid Lynx). It lived in the folder D:\Ubuntu. 
[*]Before starting to add Linux Mint 13 "Maya" (Ubuntu 12.04) as a second Wubi installation the following preparatory steps were taken:
+ The Lucid boot files C:\wubildr, C:\wubildr.cfg were backed up as C:\wubildr.lucid , C:\wubildr.cfg.lucid
+ The Windows Uninstall information for "Ubuntu" were exported from the registry to a .reg-file.
+ The Windows Uninstall information for "Ubuntu" were removed from the registry.
+ The Windows boot manager configuration was saved to a file with the help of EasyBCD. 
[*]Linux Mint 13 "Maya" (Ubuntu 12.04) was installed through mint4win (Mint name of Wubi). The default target folder D:\linuxmint was used.
_Note:_
Because Mint suggests the path \linuxmint for its Wubi installations and Ubuntu suggests the path \ubuntu for its Wubi installations, there was no naming conflict in my scenario. 
You should allow your Ubuntu 11.10 to stay in D:\Ubuntu and install Ubuntu 12.10 in D:\Ubuntu12 e.g. thus avoiding a naming conflict. 
[*]Mint4win rebooted the machine and the genuine Linux installation was performed running from the harddisk. 
[*]After the Linux Mint 13 installation had been finished, too, the machine was rebooted again. 
[*]The genuine Windows boot manager was still in control of the booting process.
To my amazement it offered two Linux installations:
+ Linux Mint
+ Ubuntu
No matter which of the two I selected, it was always Linux Mint which would be started. (Selecting to boot Windows would boot into Windows correctly.)

[U]The reason was pretty simple:
[/U]The boot files used by Linux Mint 13 had exactly the same names as the ones used by Ubuntu 10.04: C:\wubildr, C:\wubildr.cfg 
[*][U]How to switch between Ubuntu 10.04 and Linux Mint 13 nonetheless:
[/U]From inside the running Windows 7 these steps had to be executed:

If Mint 13 had been active last:
+ rename C:\wubildr to C:\wubildr.maya
+ rename C:\wubildr.lucid to C:\wubildr
+ (swapping the C:\wubildr.cfg files was not necessary, I found out)
+ reboot
+ select "Linux Mint" or "Ubuntu" from the Windows boot manager menu
+ Ubuntu 10.04 would come up

If Ubuntu 10.04 had been active last:
+ rename C:\wubildr to C:\wubildr.lucid
+ rename C:\wubildr.maya to C:\wubildr
+ (swapping the C:\wubildr.cfg files was not necessary, I found out)
+ reboot
+ select "Linux Mint" or "Ubuntu" from the Windows boot manager menu
+ Linux Mint 13 would come up

[U]Note:
[/U]Swapping the C:\wubildr files was possible from inside the running Ubuntu or Mint Wubi installation, too. - I used Nautilus in order to do so. 
[*]_Automating the switch:_
After having swapped the bootable Wubi installations Ubuntu 10.04 and Linux Mint 13 several times manually, it was decided to create a small Windows batch script. This script, launched in elevated mode, would simply activate the appropriate C:\wublidr file, after having performed a few minimal sanity checks.
Rebooting had to be done manually afterwards. 
[/LIST]

So, let me repeat:
Although what you want to do exceeds the original design of what Wubi can do, there are ways of achieving your goal.
Basically all you have to do is to follow the same steps that have been explained above.

Kind regards,
Karl

---

### Post by RookieGui on 2013-06-10
Thanks Karl, you were of great help!

So, first of all, I did what u suggested

> **Karlchen said:**
> 
+ The Lucid boot files C:\wubildr, C:\wubildr.cfg were backed up as C:\wubildr.lucid , C:\wubildr.cfg.lucid
+ The Windows Uninstall information for "Ubuntu" were exported from the registry to a .reg-file.
+ The Windows Uninstall information for "Ubuntu" were removed from the registry.
+ The Windows boot manager configuration was saved to a file with the help of EasyBCD.


By the time you answered I had already shrinked my Win7 partition, and thus took out 100 GB of space from the end of C:

Since Ubuntu's wubi default path is in "SELECTED_DRIVE_LETTER:\ubuntu\" and I didn't know if there was a command to change that, I decided to partition that unused space into a logical NTFS partition and I labelled it as E:
( I know many out here will get shivers, but I don't wanna mess the boot loader, and for now I'll stick with wubi... I'll see if I'll need a full install in the future )
I started wubi (wubi.exe and 64bit ubuntu desktop iso file must be in the same dir) and installed 12.10 into E: ... thus eliminating the possible conflict with the previous wubi installation in "D:\ubuntu"

when I did a reboot, in order to complete 12.10 install, the system auto-selected ubuntu 11.10

so I restarted once more and this time Windows boot Loader had 3 options, the last 2 being named as "ubuntu"
I booted into windows to see through EasyBCD which of the two were the 12.10
I renamed the entries into EasyBCD to reflect which one was 11 and which was 12

my current Windows boot loader shows the following entries:

Windows 7
Ubuntu11
Ubuntu12

but I was able to boot into 12.10 only renaming "D:\ubuntu" ( to something else... I renamed to "D:\ubuntu11" )

obviously, as long as I don't rename back to "D:\ubuntu", ubuntu 11 can't start

I see that in EasyBCD the two ubuntu entries have the same BCD ID

I don't know how to resolve this issue... I tried to find info about BCD IDs but had no luck

---

### Post by mastablasta on 2013-06-10
if you have enough power and RAM it might be easier to just use virtual box. no reboot necessary... can install multiple OS easilly side by side. you can make snapshots of the system so even no boot is necessary.

i run Xubutnu on single core CPU with 2GB ram.

not sure why changing disk partition would void warranty....

---

### Post by bcbc on 2013-06-10
Wubi boots like this:

Windows boot manager calls GRUB4DOS (wubildr.mbr)
Wubildr.mbr looks for the first wubildr it can find (on the root of any partition)
wubildr looks for the first /ubuntu/disks/root.disk it can find (on any partition).

This is why you can't have D:\ubuntu\disks\root.disk and E:\ubuntu\disks\root.disk and hope to boot them from the Windows boot manager. The wubildr can be configured to boot a different root.disk, or to boot a different folder, but it's a pain (you can't choose at boot time, instead you have to remember to switch the wubildr files before rebooting). As Karlchen pointed out, you can switch over the wubildr and then it will go to the different target (this works with Mint, but won't work if both installs are looking for /ubuntu/disks/root.disk as it will always find the first one).

Luckily Wubi uses Grub2 (that's built into the wubildr), so you have all the power of a modern bootloader/manager. You can just tell it about the other install, and then select between them. So... where to begin?

Scenario: you have 11.10 on D: and 12.10 on E:. Currently only the 11.10 install is booting. So you boot Ubuntu and add a Grub menu entry to boot the 12.10 entry by editing the file:
```
gksudo gedit /etc/grub.d/40_custom
```

And make it look like this - well, not quite like this - you need to know your partition corresponding to E: (bolded):
```
#!/bin/shexec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu 12.10 on E:' {
        insmod ntfs
        set root='(**hd0,msdos3**)'
        loopback loop1 /ubuntu/disks/root.disk
        set root=(loop1)
        linux /vmlinuz root=**/dev/sda3** loop=/ubuntu/disks/root.disk ro quiet splash
        initrd /initrd.img
```

That's not the end of it unfortunately, because the **wubildr** will be periodically updated when you get grub updates, and you don't want the 12.10 Grub trying to load the 11.10 grub.cfg. These are not compatible between versions.

So you would boot the 12.10 install and make sure it doesn't try to update the wubildr by editing the grub-mkimage file included with lupin (the thing that's required to allow grub to loop mount wubi installs):

The following is a ***diff*** of my /usr/share/lupin-support/grub-mkimage from some version or other of grub. You'll need to add a line "***exit 0***" somewhere to stop it generating the wubildr. 
```
--- /mnt/usr/share/lupin-support/grub-mkimage 2011-09-20 03:44:44.000000000 -0700
+++ /usr/share/lupin-support/grub-mkimage 2012-10-29 22:02:55.784517389 -0700
@@ -112,7 +112,7 @@
         exit 1
     fi
 fi
-
+exit 0 # for raring test install, bypass creation of wubildr
 wubildr_partitions="$(find_wubildr)"
 
 if [ ! -f "$target" ] && [ -z "$wubildr_partitions" ]; then

```

This is a lot of work... it's doable, but it's not really what Wubi was intended for. I'll help you get it setup if you want, but you need to understand that it requires a bit of hacking.

---

### Post by bcbc on 2013-06-11
I forgot to mention you need to update grub.cfg after editing /etc/grub.d/40_custom 
```
sudo update grub
```

---

