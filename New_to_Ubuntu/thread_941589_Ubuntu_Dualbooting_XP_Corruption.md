---
title: "Ubuntu Dualbooting XP Corruption"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by pobri19 on 2008-10-08
Hi guys, so I wanted to try out Ubuntu. I'm new to Linux, and I want to learn some new things, so I thought this distro would be a good starting point. Anyways I have a Windows XP hard drive, and a spare 160gigabyte data hard drive. I booted into the Ubuntu live CD (The latest one) and performed the install.

During the install process I ran into a few troubles, when it got to the part where it asks which partition you would like to use, or if you would like to create one, the list was completely blank, and it wasn't detecting either of my two hard drives. I went into BIOS and disabled the 'ACPI' (I think that's what it was called) after doing a bit of googling to try and fix that problem. After doing that both my hard drives were detectable by Ubuntu, so I proceeded to use the whole of my 2nd hard drive for Ubuntu, performed a format/partition on it, etc. The install went smoothly, until I restarted my computer and tried to get into Windows...

Every time I restart my computer and select windows from the Grub boot loader it would take me to the Windows loading logo, then after about 1-2 seconds it would flash up a blue screen of death for about 1 second, then restart my computer. This happens every single time I restart. I also tried disabling ACPI, but if I do that then Grub causes an error (error 21 if I recall correctly) when I start my computer, and won't let me into Windows OR Ubuntu. My XP install has all of my data on it, and I can mount it and access that data inside of Ubuntu, but I can't boot into Windows without it causing a BSOD.

Any help would be greatly appreciated! Thanks a lot.

---

### Post by caljohnsmith on 2008-10-08
So you can boot into Ubuntu OK but just not Windows? Please first post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can go from there.

---

### Post by pobri19 on 2008-10-08
Sure thing caljohnsmith, here you go:

android@android-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9acd9ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b238b23

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   300431564   150215751   83  Linux
/dev/sdb2       300431565   312576704     6072570    5  Extended
/dev/sdb5       300431628   312576704     6072538+  82  Linux swap / Solaris
android@android-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a4e231e8-6ef3-4175-b698-f5e9e8c484e5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4e231e8-6ef3-4175-b698-f5e9e8c484e5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4e231e8-6ef3-4175-b698-f5e9e8c484e5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-10-08
Your Windows entry in your Grub's menu.lst should work based on your setup. Right now though you have Grub installed to the MBR (Master Boot Record) of your Windows drive, and then Grub's files (menu.lst, etc) are on your Ubuntu drive; that isn't too ideal, because if anything happens with your Ubuntu drive, you won't be able to boot your Windows drive (assuming Windows even works).

Can you change the HDD boot order in BIOS? If so, I would make your 160 GB Ubuntu drive first in the boot order, and then we can install Grub to its MBR (Master Boot Record) so you can boot the Ubuntu drive OK. Then you can reinstall a Windows boot loader to the MBR of your Windows drive, and see if Windows boots. I think it is highly likely though that Windows won't boot, because it sounds like you may have a Windows problem at this point. I've seen some rare cases in the forums here where Windows won't boot with Grub (despite using the correct Grub syntax), but Windows will boot with a Windows boot loader. 

So if you can change BIOS to boot the Ubuntu drive first, let me know and we can go about getting your MBRs straightened out. Or if you can't boot the Ubuntu drive first, let me know and we can still work from there.

---

### Post by Cpuboye11 on 2008-10-08
Just asking... But did you tell it to not install over windows???? 

Like
Explain how you installed it..

Can you see your windws drive in ubuntu?? Can you write to it.. or what??

---

### Post by pobri19 on 2008-10-08
OK caljohnsmith, I just changed the BIOS boot options so that my Ubuntu drive is the first to boot. I took the Windows drive out of the choices too, and I'm still getting the same error when I try and boot into windows (Which is probably what you expected :-D) but it let me get into Ubuntu just fine. I've got to go now, but I'll be back tommorow (around 6 hours or so I'd say) so I'll read up on the forums first thing in the morning. Thanks for helping me out tonight, and if you need any more info just let me know!

edit: yes and yes Cpuboye11, I can see it and I can add files to it. The installation process was just routine, I formatted the secondary spare drive and installed Ubuntu on it. I didn't purposely touch the windows drive, nor did I write over it purposely.

---

### Post by caljohnsmith on 2008-10-08
OK, so if you have a Windows Install CD, boot that, go to the "Recovery Console", and then run:
```
fixmbr
```
That should put a Windows MBR in your Windows drive. And while you are in the Windows command line, go ahead and run:
```
chkdsk /r

```
And let me know if chkdsk finds any problems with your Windows partition. 

Next boot your Live CD and do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit

```
That will install Grub to the MBR of your Ubuntu drive. Then do:
```
sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use "root (hd0,0)" instead of using (hd1,0); also change the line that says "#groot=(hd1,0)" to use (hd0,0) instead. At the end of that file, change your Windows entry to:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Now your Ubuntu drive should be fully set to boot. Let me know if you get this far or if you run into problems.

---

### Post by SunnyRabbiera on 2008-10-08
well one thing you might have messed up on is if you didnt defrag windows before installing Ubuntu then its no wonder why you have issues.
I had a simular issue to yours once and I found out I had to defrag windows before even attempting a dual boot as if you shrink a windows drive without defragging it will give you hell later.

---

### Post by pobri19 on 2008-10-08
caljohnsmith: When I try to access the recovery console it says something along the lines of 'no hard drives detected'. And won't let me get to the prompt. I also tried changing it back to the Windows drive for boot order first, still the same problem, could this be caused by ACPI running? (I never originally had that running, but I activated it so Ubuntu could detect my drives). So yeah, I can't access Recovery Console :(

SunnyRabbiera: Why would I have needed to defrag my Windows drive when I wasn't installing on it? I didn't want the Ubuntu install to touch the Windows drive at all! :(

---

### Post by caljohnsmith on 2008-10-08
> **pobri19 said:**
> caljohnsmith: When I try to access the recovery console it says something along the lines of 'no hard drives detected'. And won't let me get to the prompt. I also tried changing it back to the Windows drive for boot order first, still the same problem, could this be caused by ACPI running? (I never originally had that running, but I activated it so Ubuntu could detect my drives). So yeah, I can't access Recovery Console :(

I would go ahead and toggle your ACPI setting in BIOS temporarily so you can hopefully get your Windows CD to recognize the drive. If that doesn't work, I've seen cases where the Windows Install CD does not recognize the HDD because the the HDD's partition table is corrupt; I doubt that is your case, because you haven't touched your Windows HDD as far as repartitioning, right? Anyway, let me know if changing ACPI in BIOS will at least allow you to use your Windows CD.

---

### Post by bumanie on 2008-10-08
Can you go to Places --> Computer  and then double click on your windows drive and post a screenshot of what windows files are shown.

---

### Post by pobri19 on 2008-10-08
Bumanie: The windows folder seems to be intact, and the drive itself seems to be intact as well as far as I can tell. Nothing appears to be missing, there's still the Windows folder with all the necessary Windows files (from what I can see) and my user accounts, program files, etc etc. It's all there. I'll try disabling ACPI now and booting with the Windows CD.

Bumanie: did you want a screenshot of INSIDE the windows folder? It's pretty large.. It won't all fit on 1 screenshot.

---

### Post by pobri19 on 2008-10-08
*Accidental repost sorry.*

---

### Post by bumanie on 2008-10-09
Just wanted to check that you had the necessary xp boot files - but you can look. The important ones are ntldr; boot.ini; ntdetect.com - check that those three are there. If they are, the best thing to try is what have posted above. I think caljonsmith is on the right track re getting into xp's console and do a fixmbr and fixboot. If you can get windows to boot, grub can be fixed later via the live ubuntu cd or super grub disk. Concentrate on trying to get xp working at present. However as caljonsmith says there are occasions where /boot/grub/menu.lst is correct but the computer doesn't do what it should. I think that is an issue peculiar to some bios' - I once had a computer that wouldn't boot into ubuntu other than with super grub disk, but the /boot/grub/menu.lst was correct. Some bios firmware from about 5 years ago seemed to have this issue.

---

### Post by pobri19 on 2008-10-09
Hey so here's what went down, I disabled Sata AHCI (It's AHCI not AHPI I just realised) and booted into the XP cd. Ran the fixmbr which said 'the computer appears to have a non-standard or invalid master boot record', and fixmbr worked according to the output. Then I did a chkdsk /r and it detected something (and it fixed it, it didn't say what exactly it detected). I rebooted, and Windows loaded. The thing is though, now I don't get a grub prompt. Before if I disabled AHCI when Windows wasn't working, grub would return a error 21. Now if I reboot without AHCI it just automatically boots into Windows with no grub prompt (even know the Ubuntu hard drive is the first priority device to boot). If I enable AHCI now it still gives no grub prompt, and automatically goes into Windows, but it causes the crash again. So here's the thing:

AHCI On -> Doesn't prompt for grub anymore so I can't choose Ubuntu to boot into. Automatically starts windows then instantly crashes.

AHCI Off -> Automatically runs Windows, with Windows working. Doesn't return a grub error anymore. But also doesn't give me a grub boot loader, so I can't boot into Ubuntu.

EDIT: So... Windows doesn't work with AHCI Enabled. It is what's causing the crash. The only way I can think of a way around this is if it was possible to install grub on the Windows drive? That way it would detect the Windows drive at startup, then prompt to boot into Ubuntu or Windows (And not rely on AHCI to detect the Ubuntu drive, instead it would rely on the Windows drive's grub to point to the drive). Just an idea if there's no way to fix this stupid crap. Gah this is so frustrating.

Ok thanks.

---

### Post by bumanie on 2008-10-09
OK, xp is working. What you have done in console mode overwrites the mbr, including grub. Grub can be reinstalled via the live ubuntu cd. I am assuming youhave not altered any partitions if not do this; boot live cd and follow this [guide]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by pobri19 on 2008-10-09
bumanie: If I do that, it'll bring me back to the exact same spot I was at before. The thing is, XP doesn't work with AHCI Enabled, and grub causes an error with it disabled (which causes nothing to boot, and me having to restart).

So, I have 3 options from what I can see, here I go:

#1 Somehow make Windows XP run when AHCI is Enabled, that way when I start my computer, it will take me to a grub prompt (after I reinstall it) and when I choose Windows the crash will no longer happen.

#2 Somehow make it so that when AHCI is Disabled, grub no longer shows an error message, and it automatically boots into Windows XP (Instead of stopping and showing an error message: 21, and causing me to restart, therefore the only way I can get into my system is with AHCI enabled).

#3 Possibly install grub on Windows XP, and leave AHCI disabled, that way when I start my computer, it will detect the XP drive, and the grub loader will start, and it will ask me whether I want to boot into Ubuntu or XP (Not sure if this option is possible).

I'd like some recommendations on which would be best and how to overcome this :) I can't reinstall grub till I've done one of those options (or something similar that fixes the same problem) or I'll be back at where I started.

Thanks a lot!

---

### Post by bumanie on 2008-10-09
> #3 Possibly install grub on Windows XP, and leave AHCI disabled, that way when I start my computer, it will detect the XP drive, and the grub loader will start, and it will ask me whether I want to boot into Ubuntu or XP (Not sure if this option is possible).
Must admit I don't know much about acpi, but the thread that describes reinstalling grub has the aim of grub getting installed so you will be given a choice of booting ubuntu or xp - that is how most dual boot systems work. What happens at grub stage 1.5 is that grub has recognized there is more than one OS, so gives you choice of which to boot into. If you choose ubuntu, grub boots ubuntu, if you choose xp, grub hands over the job of booting xp to xp's bootloader 

If I were you I'd try the thread and see what happens. Now that the xp bootsector has been repaired, it may work correctly. Not quite sure what else to suggest other than trying super grub disk - a live cd that often fixes grub/booting issues - it could be worth a try. Could also look [here]("http://users.bigpond.net.au/hermanzone/p15.htm"), there is heaps of info. on grub.

---

### Post by pobri19 on 2008-10-09
The problem wasn't actually the MBR, all it is is that Windows XP won't boot with AHCI Enabled. But if I disable it then grub has an error 21, so I can't boot into Windows XP anyways. With AHCI enabled grub gives me the choice of booting into XP or Ubuntu, but since AHCI is enabled... XP will just instantly crash if I choose it. Ubuntu will work though. That's the whole problem.

---

### Post by bumanie on 2008-10-09
As you have two hard drives it is possible (though a bit painful) to A) Get windows working, then unplug the hdd it is on
B) Connect the second hdd and install ubuntu
C) Connect both hdd's back up to the computer
D) Boot via choosing first boot device option in bios. ie want to boot xp, go into bios and have that drive as the first boot device. Alternatively, want to use ubuntu, enter bios and change that drive to the first boot device. 
Some people set their computers up this way specifically so windows and linux don't have any clashes ( although most users don't have hassles). 
Of course you can hang around and someone who knows more about the acpi issue will come along at some stage. Sorry I can't help further. Choosing the boot device from bios is an option.

---

### Post by pobri19 on 2008-10-09
Alright well thanks for trying bumanie, I think I'll just hang around and see if anyone else has some suggestions. Maybe caljohnsmith will have an idea when he gets around to reading this. Thanks again.

---

### Post by pobri19 on 2008-10-09
I found a guide online to make windows XP run with AHCI Enabled even if it wasn't installed with it enabled. No success. Still open to ideas. I think the installing of grub onto windows (if possible) would still be a good idea (if it would work and do what I'm after).

---

### Post by caljohnsmith on 2008-10-09
Hi pobri19, I see you've made at least some progress, and I'm glad Bumanie stepped in and helped out while I was away. So have you tried installing Grub to your second Ubuntu drive, and booting from that? Or when you say you reinstalled Grub, did you install it to your Windows drive again? Did you follow the Grub steps in post #7 to install Grub to your Ubuntu drive? Then you can add the Windows entry from that post to try and boot Windows. Sounds like your AHCI problem might prevent Windows from booting, but see if you can at least get as far booting your Ubuntu drive with Grub and using that Windows Grub entry from post #7 to boot Windows. If that doesn't work we can try a different strategy. :)

---

### Post by pobri19 on 2008-10-09
Alright caljohnsmith, I was actually waiting for you to try that :) But I'll try that now.

---

### Post by pobri19 on 2008-10-09
OK so that semi fixed it. Here's what happens now: I boot with AHCI enabled, it takes me to grub, I can then boot into ubuntu, but XP won't work because it doesn't want to run with AHCI enabled.

Now if I disable AHCI then xp will boot without causing a grub error 21 and stopping it from automatically using XP (like it did before). The only bad thing about this is that I can't get to XP through the grub menu, so I have to manually set AHCI off every time I want to boot into XP, and turn it on every time I want to boot into Ubuntu. Preferably I would love it if Ubuntu didn't even need AHCI enabled, but I don't think that's possible. So yeah, thoughts caljohnsmith?

---

### Post by pobri19 on 2008-10-09
Another thing, I just discovered that not only will I need to disable AHCI if I want to get into the XP install, but if I want to get into Ubuntu after doing that, I also have to set the ubuntu drive as #1 again, because when XP boots it automatically switches it to #1 in the bios settings, so therefore if I don't change it back, grub won't load again. Which is just really annoying ;p

---

### Post by caljohnsmith on 2008-10-09
Another boot loader option that might help solve your problem is "Grub4DOS", which is basically Grub inside of Windows. If you go this route, Grub4DOS will add an extra entry in your Windows boot loader, so that on start up, you would see two menu choices: Windows or Grub4DOS. If you then select Grub4DOS, you will get a Grub menu which you can configure to (hopefully) boot your Ubuntu on the 2nd drive. So even if it does work, the small disadvantage would be having to go through two menus on start up to get to Ubuntu, but that seems like a minor nuisance compared to changing your BIOS settings all the time, would you agree? :)

Anyway, if you're feeling adventurous and want to give it a shot, first begin by downloading Grub4DOS from:

[http://sourceforge.net/projects/grub4dos](http://sourceforge.net/projects/grub4dos)

And let me know so we can go from there.

---

### Post by pobri19 on 2008-10-09
Yes I definitely would agree. I've downloaded it and am awaiting your instructions boss ^_^ Oh and by the way will it be possible to set Ubuntu as the default boot device? :D

---

### Post by caljohnsmith on 2008-10-09
OK, the following instructions are going to assume you've downloaded the grub4dos-0.4.3.zip package to your Ubuntu desktop:
```
cd ~/Desktop
unzip grub*.zip
cd grub*
gedit menu.lst

```
That last command should pull up the menu.lst file, so if it does, replace the contents of that with:
```
# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color black/cyan yellow/cyan
timeout 30
default /default

title Grub on 2nd drive
root (hd1,0)
configfile /boot/grub/menu.lst
```
Next do:
```
sudo umount /dev/sda1
```
Don't worry about an error, that's just to make sure sda1 is not mounted some where else. Continue with:
```
sudo mount /dev/sda1 /mnt
sudo cp grldr menu.lst /mnt/.
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
gksudo gedit /mnt/boot.ini
```
That should pull up your Windows boot.ini file, and just add the last line as shown:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
[COLOR="Blue"]C:\grldr="Grub4DOS menu"[/COLOR]
```
Save, and you're done. Make sure AHCI is disabled and that you boot from your first drive, not the Ubuntu drive. Let me know what happens. :)

---

### Post by pobri19 on 2008-10-09
I followed your instructions word for word, unfortunately when I restart I don't see a Grub4DOS menu :( Any idea what is going on?

---

### Post by caljohnsmith on 2008-10-09
OK, so what do you see on start up? And are you sure you are booting your Windows drive again? I need as much info as possible if you want me to help troubleshoot. :)

---

### Post by pobri19 on 2008-10-09
I got the Grub4DOS menu to show. Apparently in linux, when I edited the boot.ini, the new line character was different from the one used on Windows, and Windows didn't detect it as a new line, so I just edited the boot.ini in Windows to have that line on a seperate line. Anyways now there's a new freaking problem... It loads up, I go linux, it says "Error: Unable to detect disk" or something along the lines of that. Wow, this is insane...

So yeah, Grub4DOS loaded, I went to the second choice (I don't remember what it was, the one other than Windows), then I selected the only one in the list, which is ofcourse Ubuntu. It said Error 26? (I think it was 26) Unable to detect disk or something like that. Which is why I had to enable AHCI to install Ubuntu in the first place. This is nuts.

EDIT: I Googled Error 26, apparently the message was "Disk Read Error" which means the same thing, but I just wanted to let you know ;)

---

### Post by pobri19 on 2008-10-09
Oh another thing, just to let you know, my second hard drive doesn't even get detected in BIOS unless I enable AHCI, then restart, and allow it to do the AHCI scan. This hard drive is fairly old, which probably has something to do with it. I think it's about 4 years old, 160gig.

---

### Post by caljohnsmith on 2008-10-09
> **pobri19 said:**
> I got the Grub4DOS menu to show. Apparently in linux, when I edited the boot.ini, the new line character was different from the one used on Windows, and Windows didn't detect it as a new line, so I just edited the boot.ini in Windows to have that line on a seperate line. Anyways now there's a new freaking problem... It loads up, I go linux, it says "Error: Unable to detect disk" or something along the lines of that. Wow, this is insane...
It looks like Grub4DOS has the same problem as Grub, which is not surprising since it's obvious now that your 2nd drive is not recognized at all by BIOS on start up. Given that, I'm not sure any different boot loader is going to help, because I think they all have to work within the limitations of BIOS on start up (I could be wrong though). If you really want to try another boot loader, I could suggest one, but I don't think it's going to help. Probably having an older drive that doesn't work with AHCI is the root of the problem, like you say.

---

### Post by pobri19 on 2008-10-09
Yeah I'm inclined to agree... Well that's a major pain in :P. Alright well at this point I'm just going to give up and manually switch it in the BIOS if I need Windows. Although I probably will just avoid using Windows now, so hopefully I won't need to do that too often. Alright well mate, all I can say is you've been awesome! Thanks a lot for all the help you've given me, was great. Thanks again, and hopefully I can return the favor one day ;) (Although I doubt that lol, you seem to know your stuff VERY well). OK thanks again! Night.

---

### Post by caljohnsmith on 2008-10-09
> **pobri19 said:**
> Yeah I'm inclined to agree... Well that's a major pain in :P. Alright well at this point I'm just going to give up and manually switch it in the BIOS if I need Windows. Although I probably will just avoid using Windows now, so hopefully I won't need to do that too often. Alright well mate, all I can say is you've been awesome! Thanks a lot for all the help you've given me, was great. Thanks again, and hopefully I can return the favor one day ;) (Although I doubt that lol, you seem to know your stuff VERY well). OK thanks again! Night.
Well at least you have a workaround, even though it is a nuisance to change BIOS around to just boot Windows; that's better than not being able to boot it at all at this point. And you're certainly welcome, it's too bad we couldn't find a better solution. Cheers, and hope to see you around in the forums in the future. :)

---

