---
title: "Howto : GfxBoot (addendum)"
date: 2007-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by 4tro on 2007-06-23
This guide is an addendum to the original guide made by PingunZ:
see this thread here:
```

http://ubuntuforums.org/showthread.php?t=208855

```to keep the howto readable i'll include the complete howto here again.

<deprecation note>
This howto was originaly created for ubuntu 7.04, i cannot guarantee it will work unchanged on the newest ubuntu versions, read the thread for tips on getting it to work on the newest ubuntu.

Or wait another version for Kernel Mode Setting and plymouth.
</deprecation note>

Gfxboot makes grub look nicer but with the same features
In this howto you will install gfxboot and a suse theme for it, soon I'll make an ubuntu one ;) 
Ok, let's start

for x86 based computers:
Download the [grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb")
And the [message.suse ]("http://quasarfreak.googlepages.com/message.suse")

and for x86_64 based computers:
Download [grub-gfxboot_0.97-11_amd64.deb]("http://www.kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb")
And one of the gfxboot themes at the end of this post

Before we start reinstalling the grub we will want to backup our update-grub as the package we're installing has another idea of how update-grub should work.
```
sudo cp /usr/sbin/update-grub /usr/sbin/update-grub.old
```First remove your old grub
```
sudo apt-get remove grub
```Then Install the gfxboot-grub

for the x86 package do:
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```for the x86_64 package do:
```
sudo dpkg -i grub-gfxboot_0.97-11_amd64.deb
```after the installation we can safely copy our update grub back to where it belongs.
```
sudo cp /usr/sbin/update-grub.old /usr/sbin/update-grub
```then we're going to move the message
```
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded 
```Then edit your menu.lst

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced 
```Then do : ```

sudo grub
grub> find /boot/grub/stage1 (not all grubinstallations are in /boot/grub, find yours first if you're unsure)
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```If your gfxboot doesn't show up after this:
find the device name of your root drive and replace the /dev/xxx with the appropriate drive marked by a *.
```
[FONT=monospace]
sudo fdisk -lu
[/FONT]sudo grub-install /dev/xxx

```if the above fails with the following error:
"/dev/sda does not have any corresponding BIOS drive"

do:
```

sudo grub-install --recheck /dev/xxx

```-- Howto make your own theme --

```
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new
```Reboot and enjoy ;)
Thanks to Quasar_freak and kno

here are some themes posted in this thread ;) ( ty :KS  )

Light Green generic theme [message.gobo] | [Link]("http://ubuntuforums.org/showpost.php?p=1214274&postcount=12") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288")
Dark Brown (Dapper look) generic theme [message.new] | [Link]("http://ubuntuforums.org/showpost.php?p=1239724&postcount=55") | [Screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544")
Medium blue kubuntu theme [message.kubuntu] | [Link]("http://ubuntuforums.org/showpost.php?p=1234300&postcount=54") |
Dark grey ubuntu theme [message.ubugrey] | [Link]("http://ubuntuforums.org/showpost.php?p=1251236&postcount=61") | [Screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717")
Medium brown ubuntu theme [message.ububrown] | [Link]("http://ubuntuforums.org/showpost.php?p=1252317&postcount=63") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657")
Light orange ubuntu theme [message.ubu] | [Link]("http://ubuntuforums.org/showpost.php?p=1254642&postcount=64") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852")
Red ubuntu theme [message.new] | [Link]("http://ubuntuforums.org/showpost.php?p=1265601&postcount=65") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852")
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link]("http://ubuntuforums.org/showpost.php?p=1272301&postcount=71") | [Screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746")
White / Grey Snowish generic theme [message.snow] | [Link]("http://ubuntuforums.org/showpost.php?p=1292317&postcount=84") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506")
Linspire-style blue kubuntu theme [message.kubu] | [Link]("http://ubuntuforums.org/showpost.php?p=1294120&postcount=86") |
Old- Grub style dark blue and light blue [message.kubu] | _Who made this one?_ |
Light blue / grey Xubuntu theme [message.xubu] | [Link]("http://ubuntuforums.org/showpost.php?p=1297486&postcount=97") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350")


Grtz PingunZ && Quattro

---

### Post by Neobuntu on 2007-06-29
Nice effort but it does not work for me on this laptop.

I get, "drive not listed in BIOS" or some such error. 

I am well aware what my Linux partition is called and I tried stating it in GRUB nomenclature and in /dev/xxx manner too. Same error. Very frustrating.

---

### Post by clinto on 2007-07-01
I don't mean to bury a post that was made 2 days ago and unanswered since ^, but I have a slight problem. Excuse my noobness, please.

I'd followed Pingunz how-to first, which had me delete grub right off the bat. I didn't even think to back up anything before deleting. So now, when I follow your first step...
```

clinton@koenigdesk:~$ sudo cp /usr/sbin/update-grub /usr/sbin/update-grub.old
Password:
cp: cannot stat `/usr/sbin/update-grub': No such file or directory

```
I'm assuming it went kapoof when I followed Pingunz first step:/

Despite this, I've followed the steps all the way down to...
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

```
... only, when I try to follow this, it says...
```

grub> find /boot/grub/stage1

Error 15: File not found

```

I have little idea what I'm doing at this point. Am I screwed if I try to reboot at this point? Is there something I'm not seeing or am I going to have to reinstall?

---

### Post by 4tro on 2007-07-01
> **clinto said:**
> I don't mean to bury a post that was made 2 days ago and unanswered since ^, but I have a slight problem. Excuse my noobness, please.

I'd followed Pingunz how-to first, which had me delete grub right off the bat. I didn't even think to back up anything before deleting. So now, when I follow your first step...
```

clinton@koenigdesk:~$ sudo cp /usr/sbin/update-grub /usr/sbin/update-grub.old
Password:
cp: cannot stat `/usr/sbin/update-grub': No such file or directory

```I'm assuming it went kapoof when I followed Pingunz first step:/

Despite this, I've followed the steps all the way down to...
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

```... only, when I try to follow this, it says...
```

grub> find /boot/grub/stage1

Error 15: File not found

```I have little idea what I'm doing at this point. Am I screwed if I try to reboot at this point? Is there something I'm not seeing or am I going to have to reinstall?

check where your grub is, because not all grub installs are in /boot/grub, i'll rectify that in the guide.

---

### Post by mcgodx on 2007-12-18
Hi, I just saw this post, I'm not sure if I am doing something wrong or what, but when I try to install gfxboot, I followed the instructions to the T, yet when I boot, there is still GRUB right there.  No themes or anything.

Any ideas?

---

### Post by peitschie on 2007-12-18
mcgodx,

The most likely problem is this part:

> and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced
```


This line MUST be uncommented in your menu.lst file.

---

### Post by clinto on 2007-12-18
Yeah, I haven't messed with mine in a while, or even looked at it, but now when I boot, SOMETIMES it will load the graphic, and other times it won't and will just display the original grub display. Weird.

---

### Post by k-o-x on 2007-12-19
You should know that you will lose the "savedefault" feature when using this package. BTW, anybody knows how to use gfxboot AND savedefault ?

---

### Post by ca2nage on 2008-03-19
> If your gfxboot doesn't show up after this:
find the device name of your root drive and replace the xxx with the appropriate drive. (somebody got an idea to find this one in one terminal command?)

I suppose one could [FONT="Courier New"]sudo fdisk -l[/FONT] before going into the grub commands and locate the device that Linux is associated to.

---

### Post by tattrat on 2008-04-30
> **4tro said:**
> If your gfxboot doesn't show up after this:
find the device name of your root drive and replace the xxx with the appropriate drive. (somebody got an idea to find this one in one terminal command?)

Whatabout:

 ```
sudo fdisk -lu
```

This will output something like:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b733b73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  EFI GPT
/dev/sda2          409640   356925479   178257920   af  Unknown
/dev/sda3   *   356932170   426393639    34730735   83  Linux
/dev/sda4       426393640   488397127    31001744    b  W95 FAT32

```

The one with the '*' in the boot column is the one you are after. Hope this helps.

---

### Post by NeoFax on 2008-05-03
Why use the 0.97-5 version of grub-gfxboot?  Sid is up to 0.97-29.  I even wrote up a howto create your own theme in the sidux forums.

---

### Post by tattrat on 2008-05-04
> **NeoFax said:**
> Why use the 0.97-5 version of grub-gfxboot?  Sid is up to 0.97-29.  I even wrote up a howto create your own theme in the sidux forums.

How about a link? I would certainly like to try - this version messes up the MBR on systems using EFI/GPT. (even though distros which come with gfxboot enabled from the start don't).

---

### Post by dizee on 2008-05-04
This guide worked well, eventually. I followed all the steps, but when it got to ```
sudo grub-install /dev/sda
``` it gave me the message: > /dev/sda does not have any corresponding BIOS drive

A quick google lead to [this](http://www.cyberciti.biz/faq/error-devhdx-does-not-have-any-corresponding-bios-drive-and-solution/) and the solution was that I had to run ```
sudo grub-install --recheck /dev/sda
```

It then installed correctly and after a reboot I can confirm that my GRUB bootscreen is really slick looking now.
:guitar:

---

### Post by chewearn on 2008-05-04
> **tattrat said:**
> How about a link? I would certainly like to try - this version messes up the MBR on systems using EFI/GPT. (even though distros which come with gfxboot enabled from the start don't).

To be honest, I have been following the gfxboot threads in this forum.

You will a few people who appeared suddenly in these threads simply to show off their knowledge on gfxboot.  Or they posted their creation of custom boot screen that you will find impossible to make using the "standard method".  [note: what I called the "standard method" is the one you find in this forum].

Then, someone jumped in and ask how they did that, and you hear a deafening silence.  For some reasons, when I was messing with gfxboot a few months ago, I keep encountering people who must be thinking gfxboot is the greatest secret in the world.

---

### Post by pingpongboss on 2008-05-05
Thanks this thread worked for me. I did have to use sudo grub-install in the end though.

---

### Post by 4tro on 2008-05-05
> **NeoFax said:**
> Why use the 0.97-5 version of grub-gfxboot?  Sid is up to 0.97-29.  I even wrote up a howto create your own theme in the sidux forums.

this guide was written for feisty fawn, therefor the package may be outdated.
I believe the reason it isn't included in hardy heron is because it disables password protection, but feel free to use the updated package.
But i can't guarantee it will work as you expect, because ubuntu and debian use different grub-settings.

---

### Post by NeoFax on 2008-05-12
Here is the updated gfxboot from sidux:

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

Here is the instructions to create a new theme:

[http://forum.sidux.com/PNphpBB2-viewtopic-t-5989-highlight-gfxboot.html](http://forum.sidux.com/PNphpBB2-viewtopic-t-5989-highlight-gfxboot.html)

If you need any more help, here is my email addy:

n e o f a x 9 [email]9@gmail.com[/email]

EDIT:  I am using this gfxboot right now with no side effects.

---

### Post by master_kernel on 2008-06-27
Thanks for the thread! :)

---

### Post by wsonar on 2009-02-25
I've tried this sevral times every time after I install gfxboot and try to find stage1 in grub is says error 15 file not found yet I can see the file is there.....

it gets frustrating following directions that repeatedly crash my system

all I want is a themed boot loader please someone help me

I will have to reinstall the old grub aGAIN or I can't boot my system

can someone please tell me why gfxBOOT will not work ????

---

### Post by wsonar on 2009-02-25
IM USING 8.10 getting frustrated because I had this working probably on 7.10

---

### Post by wsonar on 2009-02-25
wsonar@Den-L115315:~/Documents$ sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.
wsonar@Den-L115315:~/Documents$ sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
The file /boot/grub/stage1 not read correctly.

---

### Post by johnjohn2 on 2009-02-25
thanks man beautiful

---

### Post by wsonar on 2009-02-25
How did you get this to work with intrepid?

---

### Post by wsonar on 2009-02-25
my grub tmp file shows this

grub error 2: bad file or directory type

---

### Post by 4tro on 2009-02-26
I can't guarantee this howto is working for hardy heron, let alone intrepid ibex.

I'm using jaunty jackalope now, and better things are coming up like plymouth.

4tro

---

### Post by wsonar on 2009-02-26
Ok thanks I guess I will try some other stuff later,

I need to fix my grub I can only boot from the super grub cd

even after booting and tring to fix my grub it dosen't seem to take the settings not sure what is going on..

I never had a problem with gfxboot on 7.0 I remember it went pretty smooth

---

### Post by 4tro on 2009-03-02
you can also try Grub2.

I believe it has better graphics capabilities.

---

### Post by dgg_geko on 2009-03-20
Hello!


Hey, I've got 2 systems. The first one is an XPS M1330 where I am able to install gfxgrub without any trouble following this guide.

Mainly the following steps:

============================================
wget [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)
	
sudo apt-get remove grub
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb

sudo cp message.ubugrey /boot/grub/
	
sudo gedit /boot/grub/menu.lst

add>>	gfxmenu /boot/grub/message.ubugrey

	sudo grub
		find /boot/grub/stage1
		(hdx,y)      [wich in my case is hd0,4 ]
		root (hdx,y)
		setup (hdx)
		quit

		sudo apt-get install grub

sudo reboot
======================================================

I don't have the need to backup the update-grub file at /usr/sbin for this system.

But with my other system, an HP Pavilion dv1000, where I have exactly the same file system configuration, I'm not able to find 'stage1' after removing the grub. Wich actually becomes dreadfull if by any means I reboot, instead of it I can only redo the grub by 'sudo apt-get install grub'.

I've tried even backing up almost all the files within /boot/grub with no success, and even tried the 'sudo su' method plus the 'sudo grub-install --recheck' method with no progress.

Just after removing the grub, an Error code 15 comes out, wich seems to happen when stage1 doesn't exists but its still there... If I skip the find command, and just go ahead to 'root (hd0,4)' and 'setup (hd0)' even though I know that's its location, it wont work. At first I thought it could work for me that way but I ended with a 'stage 1.5' error at startup and my only solution was to remake partitions.

Err... any suggestions?


in this HP system, the fdisk -l prompts

Device     Boot    Begining         End      Bloqs   Id   System
/dev/sda1   *            63   132038234   66019086    7   HPFS/NTFS
/dev/sda2         132038235   194980904   31471335    5   Extended
/dev/sda5         132038298   192298049   30129876   83   Linux
/dev/sda6         192298113   194980904    1341396   82   Linux swap / Solaris

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111187[/ATTACH]

Hope this helps

---

### Post by José Serra on 2009-04-29
> **Malac said:**
> I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111187[/ATTACH]

Hope this helps

It really helps... thank you! I'm using your modified theme on Ubuntu 9.04.

---

### Post by Malac on 2009-05-01
> **José Serra said:**
> It really helps... thank you! I'm using your modified theme on Ubuntu 9.04.
You're Welcome. :)

---

### Post by aniruddha on 2009-05-01
Does this theme work on 64bit systems as well?

---

### Post by Malac on 2009-05-01
> **aniruddha said:**
> Does this theme work on 64bit systems as well?
You would need to compile the grub-gfxboot from tar for 64bit as to the theme file I don't have a 64bit machine so I cannot test it, sorry.
Perhaps someone could try it and see.

---

### Post by aniruddha on 2009-05-01
Well, once more unto the 64bit breach then...

Thanks for putting up the theme!

---

### Post by Malac on 2009-05-01
> **aniruddha said:**
> Well, once more unto the 64bit breach then...

Thanks for putting up the theme!
I can see that I'm going to have to get a 64bit at some point as I do a lot of programming and I should really test my stuff on 64bit just to be thorough.

Once again sorry I can't help this time. Glad you liked the theme.

---

### Post by josemegchun on 2009-05-06
> **wsonar said:**
> Ok thanks I guess I will try some other stuff later,

I need to fix my grub I can only boot from the super grub cd

even after booting and tring to fix my grub it dosen't seem to take the settings not sure what is going on..

I never had a problem with gfxboot on 7.0 I remember it went pretty smooth
Hi wsonar,

I am having exactly the same issue with grub after following the steps to add gfxboot. Also, I used gfxboot in Ubuntu 7... 

Did you eventually sort out the problem or just reinstalled the grub (I did whole re-installation just because is very quick)?

I used grub2 with Ubuntu 8 (and added some figures to it). I prefer the old gfxboot by far...

Any help is much appreciated...

---

### Post by Kor-Skarn on 2009-05-10
Finally got my gfxboot working on 64-bit system with ext4 root partition. Not much proper info out there. For those who were wondering why the instructions from the Howto don't work on their 64-bit architecture, particularly why they get error "grub> Error 15: file not found" for their "find /boot/grub/stage1" command (even when it's positively there), here's the answer:
 
 GRUB-gfxboot can't read your filesystem, because it doesn't support it. Especially true and confusing for ext4, when it detects the FS as ext2fs (seemingly correctly) with "root (hdx,y)" command, but can't read it (or search in it).
 
 This was valid for versions < -40, so version -11 doesn't work with ext4! Version -40 from sidux works fine though, I tried it with Debian Orange theme from KDE-Look.org on Jaunty. But maybe recompile for some themes is needed?
 
 (P.S. Big thanks to Malac for pointing out the new -40 package from sidux!)

---

### Post by hjacker on 2009-05-24
> **Kor-Skarn said:**
> Finally got my gfxboot working on 64-bit system with ext4 root partition. Not much proper info out there. For those who were wondering why the instructions from the Howto don't work on their 64-bit architecture, particularly why they get error "grub> Error 15: file not found" for their "find /boot/grub/stage1" command (even when it's positively there), here's the answer:
 
 GRUB-gfxboot can't read your filesystem, because it doesn't support it. Especially true and confusing for ext4, when it detects the FS as ext2fs (seemingly correctly) with "root (hdx,y)" command, but can't read it (or search in it).
 
 This was valid for versions < -40, so version -11 doesn't work with ext4! Version -40 from sidux works fine though, I tried it with Debian Orange theme from KDE-Look.org on Jaunty. But maybe recompile for some themes is needed?
 
 (P.S. Big thanks to Malac for pointing out the new -40 package from sidux!)

Eeeh, I'm a bit confused. I've got ext3 and it says "file not found". I've also attempted some extreme measures like skipping some steps which brought me to complete reinstall.:D
Such disasters make learning process more efficient.^_^
So, what should I try?

---

### Post by Xcerca on 2009-07-24
> **Kor-Skarn said:**
> Finally got my gfxboot working on 64-bit system with ext4 root partition. Not much proper info out there. For those who were wondering why the instructions from the Howto don't work on their 64-bit architecture, particularly why they get error "grub> Error 15: file not found" for their "find /boot/grub/stage1" command (even when it's positively there), here's the answer:
 
 GRUB-gfxboot can't read your filesystem, because it doesn't support it. Especially true and confusing for ext4, when it detects the FS as ext2fs (seemingly correctly) with "root (hdx,y)" command, but can't read it (or search in it).
 
 This was valid for versions < -40, so version -11 doesn't work with ext4! Version -40 from sidux works fine though, I tried it with Debian Orange theme from KDE-Look.org on Jaunty. But maybe recompile for some themes is needed?
 
 (P.S. Big thanks to Malac for pointing out the new -40 package from sidux!)


Sweet , I got it working.  I was using the amd64 version and ext3 with the grub-gfxboot from the tutorial and kept getting:

Error 15: file not found"  when i did grub> find /boot/grub/stage1 

and i got 
The file /boot/grub/stage1 not read correctly.
when i tried
sudo grub-install --recheck /dev/sda

So I tried the version 43 from the link earlier in the thread and it worked just as advertised.

---

