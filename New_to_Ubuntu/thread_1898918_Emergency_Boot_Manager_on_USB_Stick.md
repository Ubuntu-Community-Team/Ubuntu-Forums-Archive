---
title: "Emergency Boot Manager on USB Stick?"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-12-22
Many years ago, I remember making a GAG diskette for my old PC & believing that would always allow me to boot it to either XP or Ubuntu in an emergency.
I never actually had to use it, but still have it in the drawer...

Now, we have a netbook with Windows 7 & Ubuntu (sometimes, but that's another story on another thread...) but with no Diskette slot & no CD reader either.
It does boot OK from Live USB sticks though.

So I am now looking for an emergency GUI Boot Manager I can easily put on a stick.
I expected that to be an everyday request & to have lots to choose from.
Sadly, I haven't found my dream Manager yet.
I downloaded GAG4.10 & read the included instructions, which I find less-than-clear, but which don't mention USB sticks.
Do they imply that I should just read USB when they say CD, or do they imply it can't de done?
I also looked at Super Grub2 Disk & Rescatux & Ubuntu Rescue Remix, without being convinced.

Super Grub2 looks like it should be what I want (doesn't it?)
But the Wiki ([http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub2_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub2_Disk_USB)) starts with an "Official method (not recommended)" which seems highly complicated & error-prone, then gets worse.

Rescue Remix sounds like overkill & sounds as though it needs keeping up to date too (maybe not?).

Can anybody show me a nice emergency GUI Boot Manager & tell me simply how to put it on a stick?

Thanks in advance!

---

### Post by bryanl on 2011-12-22
If a 'dream' boot manager is your goal, you might have a problem as the term is poorly defined and usually quite personal.

If having a boot manager on a USB stick that allows you to find and boot whatever bootable partition is on your machine, then GRUB isn't that bad.

Installing GRUB on the USB stick isn't that much of a hassle if you have it installed on a Linux partition you can use to set up the stick. Pen Drive Linux has a good 'how-to' - [http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/) - fsm has another with some interesting stuff about booting ISO images: [http://www.freesoftwaremagazine.com/articles/grub_intro](http://www.freesoftwaremagazine.com/articles/grub_intro)

see [Ubuntu USB boot problem workaround](http://tcl.leipper.org/2009/08/ubuntu-usb-boot-problem-workaround/) for an example of finding bootable partitions from a GRUB command line to boot them.

If you know the partitions you want to boot, then you can write stanzas in GRUB.CFG so they appear on the boot menu.

---

### Post by oldfred on 2011-12-22
I find grub2 works. I was even able to create a Windows 7 repair USB but it used so little of the flash drive, I created another partition and put several repair ISOs on it and installed grub2. I was a little surprised that it still booted the Windows partition even though grub was in the windows partition.

If flash drive is under 8GB you can copy many ISOs and loopmount boot the ISO. If drive is 8GB or more you can do a full install and install ISOs.

The main disadvantage of grub2 is that the os-prober is not part of just a grub install, so you have to write your own grub.cfg. The pendrive site seems to down load one or you just create one.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

If you want to boot your installs on the hard drive from the USB drive you can use stanzas like these, but drive numbers change. Boot drive is always hd0, so then sda which is often hd0 becomes hd1.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Or you can chainload to the MBR of another drive.
menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

When booting you can use the e on the grub menu to edit boot stanza, so if hd1 is not correct you can change to hd2 or hd3 to make it work also. You can also copy boot stanzas that search by UUID from your regular install's grub.cfg.

---

### Post by 2CV67 on 2011-12-22
> **bryanl said:**
> If a 'dream' boot manager is your goal, you might have a problem as the term is poorly defined and usually quite personal.
You are perfectly correct there - excuse me!

What I need/want is something which can hope to boot W7 & Ubuntu in case of damage to normal boot processes.
But mainly I need to be able to put it on a stick & use it 100% GUI.
CLI instructions drive me crazy!

Dream on...

---

### Post by adrian15 on 2011-12-22
> **2CV67 said:**
> Super Grub2 looks like it should be what I want (doesn't it?)
But the Wiki ([http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub2_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub2_Disk_USB)) starts with an "Official method (not recommended)" which seems highly complicated & error-prone, then gets worse.


  The Gnu/Linux instructions are far easier than the Windows ones. :P
Whatever, I think that you are wanting to use [Super Grub2 Disk]("http://www.supergrubdisk.org/super-grub2-disk/"). It has a GUI and it autodetects OS.

  About dd I have found [Gdiskdump as a dd gui]("http://www.ubuntugeek.com/gdiskdump-gui-for-diskdump-dd.html"). But the process for identifying your hard disk device is the same one. So I think it is as difficult for you as it was before knowing about Gdiskdump.

  If you find me online on [super grub irc channel]("http://www.supergrubdisk.org/chat/") I might walk you through the steps of putting Super Grub2 Disk into a usb. In return you might give me some advice on how to rewrite the wiki page so that it is less confusing.

  I think that most of the confusion comes about not being English native. I remember Herman's zone webpage having so much technical stuff but everyone agreeing that it was very well explained.

---

### Post by 2CV67 on 2011-12-30
Thanks, adrian15, for your reply & offer of help.
The problem with the wiki is not the English, it's the fact that it uses CLI, with all the potential hazards of CLI.
It even uses "sudo dd" which I have seen many many warnings about using, as one slip can do lots of damage.
I HATE having to use fragile & dangerous methods to do what I should be able to do by clicking from a menu.
I am a careful sort of person, but I make a lot of typing mistakes, even when concentrating hard...
In fact, especially when concentrating hard!

What I really need is something as clear & simple & safe as your instructions for Windows, near the bottom of the wiki page:
> Download Unetbootin For Windows
Run Unetbootin. Select Distribution, and from the drop down menu select "Super Grub Disk"
Select the target drive, and hit OK.
That's what I need!

Actually, I have tried UNetbootin in Ubuntu 11.04 & it does propose Super Grub Disk (not SG2D) & it does look as though it puts the right stuff on the USB stick.
But when I try to boot it, I get "This is not a bootable disk".
Repeated the whole exercise several times with same result.
**_Any explanation or suggestion for investigations, please?_**

Anyway, I finally decided to try carefully following the wiki "Official method" to put SG2D on a stick too.
This actually seemed to go OK, except if I try to mount the stick, or just plug it in I get:
```
Unable to mount ISOIMAGE
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Syslog says:  ISOFS: Unable to identify CD-ROM format.

The stick has somehow been renamed "ISOIMAGE" with no obvious way to rename it.

If I try to boot to that stick, then I do get a new Grub screen, with choices of:
Detect any OS
Detect any Grub2 
etc.
So far - so good...
But if I try "Detect any OS" then I get a machine-gun noise & 4x "error: unrecognised fs"
If I try "List devices/partitions" then I do see a list, briefly, with machine-gun noise, then the Grub screen back again.
No point in trying to "Detect any Grub2..." as I don't have Grub2.
Which was another reason to look first at SGD, above.

If I try GParted, then my USB stick now appears as:
```
/dev/sdb1 - File System unknown - Size 1.93MiB - boot
unallocated - File System unallocated - Size 3.83GiB
```

I have tried several times, re-downloading the iso, getting the same md5 checksum, re-partitioning the stick as all one FAT32 partition, etc etc.
But am now stuck.

***Any help with either or both Super Grub Disks, would be appreciated!***

Thanks!

---

### Post by adrian15 on 2011-12-31
> **2CV67 said:**
> Thanks, adrian15, for your reply & offer of help.
The problem with the wiki is not the English, it's the fact that it uses CLI, with all the potential hazards of CLI.
It even uses "sudo dd" which I have seen many many warnings about using, as one slip can do lots of damage.
I HATE having to use fragile & dangerous methods to do what I should be able to do by clicking from a menu.
I am a careful sort of person, but I make a lot of typing mistakes, even when concentrating hard...
In fact, especially when concentrating hard!

What I really need is something as clear & simple & safe as your instructions for Windows, near the bottom of the wiki page:

That's what I need!

Take a look at: [4 ways to create bootable live usb](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html). It seems you want to use [usb-imagewriter](http://packages.ubuntu.com/oneiric/usb-imagewriter). [Some instructions on how to use usb-imagewriter.](https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu)

> **2CV67 said:**
> 
Actually, I have tried UNetbootin in Ubuntu 11.04 & it does propose Super Grub Disk (not SG2D) & it does look as though it puts the right stuff on the USB stick.

Yes, that's right. You are supposed to rename the iso file into img and being able to put into the usb as if it was a floppy image. But I have many reports of this not working with Unetbootin. But it might work after all.

> **2CV67 said:**
> 
But when I try to boot it, I get "This is not a bootable disk".
Repeated the whole exercise several times with same result.
**_Any explanation or suggestion for investigations, please?_**

I think it simply does not work... and now that the image is bigger than 1.44 MB it's even more difficult for it to work.
> **2CV67 said:**
> 
Anyway, I finally decided to try carefully following the wiki "Official method" to put SG2D on a stick too.
This actually seemed to go OK, except if I try to mount the stick, or just plug it in I get:
```
Unable to mount ISOIMAGE
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Syslog says:  ISOFS: Unable to identify CD-ROM format.

The stick has somehow been renamed "ISOIMAGE" with no obvious way to rename it.

Yes, that's it. You cannot use the pendrive as a normal pendrive once you have SG2Dized it. Unless you use the instructions about being to use it after SG2Ding it.

> **2CV67 said:**
> 
If I try to boot to that stick, then I do get a new Grub screen, with choices of:
Detect any OS
Detect any Grub2 
etc.
So far - so good...

That's great! It works!
> **2CV67 said:**
> 
But if I try "Detect any OS" then I get a machine-gun noise & 4x "error: unrecognised fs"

And you should usually get a menu with detected operating systems.
> **2CV67 said:**
> 
If I try "List devices/partitions" then I do see a list, briefly, with machine-gun noise, then the Grub screen back again.

Yes, that's a pity. They have a pause command (or something similar) but it does not work when you are running from a menu.
> **2CV67 said:**
> 
No point in trying to "Detect any Grub2..." as I don't have Grub2.
Which was another reason to look first at SGD, above.

You do have grub instead of grub2. Hummm... I was tempted to point you to the Put SGD into USB CLI instructions but... SG2D should detect your Gnu/Linux kernels anyway so I don't.
> **2CV67 said:**
> 
If I try GParted, then my USB stick now appears as:
```
/dev/sdb1 - File System unknown - Size 1.93MiB - boot
unallocated - File System unallocated - Size 3.83GiB
```

I have tried several times, re-downloading the iso, getting the same md5 checksum, re-partitioning the stick as all one FAT32 partition, etc etc.
But am now stuck.

That's ok. That's the expected result unless you use the [How to make SG2D USB and being usable for storage later](http://www.supergrubdisk.org/wiki/SGD_Howto_make#Gnu.2FLinux_.28and_being_usable_for_storage_later.29) instructions.
> **2CV67 said:**
> 
***Any help with either or both Super Grub Disks, would be appreciated!***

Thanks!
Hope my tips help you. I suppose that I have to add [usb writers tools found at webupd8 article](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html) to the official instructions.

---

### Post by 2CV67 on 2011-12-31
Thanks once again, adrian15, for your patience!
But I have now spent over 50 hours trying to get either SGD or SG2D to work on my old PC with XP & 2 Ubuntus with Legacy Grub, with absolutely no success.

Since your last post:
> Take a look at: 4 ways to create bootable live usb. It seems you want to use usb-imagewriter. Some instructions on how to use usb-imagewriter.
I tried, from the 4 ways...
1. Unetbootin:
- Just letting Unetbootin install its own SGD - 'This is not a bootable disk' even though GParted shows it to have boot flag.
- Unetbootin installs separately-downloaded SGD.iso - Very promising screen with 'Default' 'Super Grub Disk' 'try to detect boot device' etc but no action when trying any option.
- Unetbootin installs downloaded SG2D.iso - Minimal screen with 'Default' '$ st.color' '$ language' but no actions.
- Unetbootin installs SGD.iso with suffix changed to .img - screen with only 'Default' & no actions
- Unetbootin installs SG2D.iso with suffix changed to .img - screen with only 'Default' but succesive 'Enter's bring good Grub screen with 'Detect any OS' etc but that only results in 4x 'unrecognised OS'.
2. Win32 Image Writer - I didn't try that yet. What an admission if that was the only one which worked! My next move?
3. Usb-imagewriter:
- Does not find .iso files.
- Changed .iso suffixes to .img - gets as far as '/dev/sdb1 successfully unmounted' then stops forever...
3a Ubuntu Startup Disk Creator:
- Does not find .iso files
- Changed .iso suffixes to .img - 'Installation failed'
4. Mac only...

This really is a long, sad story!

---

### Post by 2CV67 on 2012-01-01
EUREKA! (but no naked runing through the streets at today's temperature...)
By repeated blind stabbing, I now have SGD working on USB sticks via 2 different methods.

But only after several more failures.

From the "4 ways to create bootable live usb." I tried the last possible one:
I went to XP & downloaded "Disk Imager".
Then I downloaded Super Grub Disk (not SG2D).
I first tried the "USB" version, but found it was a tar.gz file & didn't see how to handle that.
So I tried the "CDROM" .iso version.
But Disk Imager does not see .iso files, only .img.
Optimistically, I just changed the suffix from .iso to .img & that seemed to allow "Write" OK.
But trying to boot to that stick resulted in "Disk Boot Failure".
Probably if I had tried XP Disk Imager with the "Floppy" version (see below) it might have worked.

Back in Ubuntu, I tried installing SGD using the "Official" technique for SG2D.
Again, booting led to "Disk Boot Failure".

I repeated an earlier attempt to get Unetbootin to install a previously-downloaded SGD.iso.
As previously, this boots to a good-looking screen with "Default" "SGD" "try to detect boot devices" etc.
But none of the options works.

Browsing the SGD site, I noticed the "Floppy" version & thought I might as well try that.
Downloaded, that is a .img file, which rings a bell!
So I tried Ubuntu Startup Disk Creator.
But "Make Startup Disk" led to "Installation failed", so no good.

I had previously installed "Imagewriter" via SynApt, so tried that with the "Floppy" .img file.
Booting, I at first thought it was a complete failure, as the USB stick was not seen in the usual place in BIOS boot options (in HDD+).
I tried selecting the boot option "USB-FDD" but that was no good either.
Then I tried selecting "USB-ZIP" (why?) and that finally WORKS!
SGD successfully boots XP & both Ubuntu's. :D

That was all I really needed (before attacking SG2D, that is).
But I looked again at the "USB" versions.
I am sorry to say I still don't understand .tar.gz files, but in digging inside, I found a "USB-readme" which looked simple enough:
> 1 - Installation of SGD in a USB device from a Linux with grub installed
Mount your usb hd 
untar file in your usb hd (or copy contents of it to usb hd)
umount your usb hd 
open grub as root 
device (hd3) /dev/ubb # my usb device in linux is called /dev/ubb 
root (hd3,0) 
setup (hd3) 
quit 
reboot 

Not knowing how to "untar in usb", I drag-&-dropped the folder "boot" to my USB stick.
Then I did:
```
Safely remove drive (but left it plugged).
sudo grub
root (hd1,0)
```
but got "error 21 selected disk does not exist".
So I mounted the stick again & did:
```
sudo grub
root (hd1,0)
setup (hd1)
quit
reboot
```
In this case, the USB stick appears as usual in the boot options under HDD+.
And that stick now works too!  :D 

I will put the simple GUI method in my next post, in case that can help any other Dummies like me.

Now I just need a Dummy-level GUI method for Super Grub2 which actually works...

---

### Post by 2CV67 on 2012-01-01
Simple GUI method for getting Super Grub Disk (not SG2D) on a USB stick.

1. Download FLOPPY version of SGD from [http://www.supergrubdisk.org/category/download/supergrubdiskdownload/](http://www.supergrubdisk.org/category/download/supergrubdiskdownload/) to your Desktop (or wherever...)
(It should be a .img image, for instance "super_grub_disk_english_floppy_0.9799.img").
2. Plug in your empty FAT32 USB stick which should automount.
3. Applications > Accessories > Imagewriter (If not there: SynApt > Imagewriter > Install).
4. "Write image" > Navigate to .img file on desktop & double-click on it.
5. "to" > Select your USB stick. (Probably safest not to have other USB drives mounted at that time...)
6. "Write to device" > See warning about unplugging device too soon > "Success".
7. Boot to USB stick - in my case that meant selecting F12 at boot screen, then selecting boot option "USB-ZIP" but your PC may differ.

Done!

---

### Post by 2CV67 on 2012-01-05
OK - so I now have Super Grub Disk up & running successfully & able to boot 2 versions of Ubuntu & XP from a USB stick.
Thanks for all the help on this thread!

I also have Grub on a stick & able to boot all my OS's, thanks to the help on another thread:
[http://ubuntuforums.org/showthread.php?t=1900858](http://ubuntuforums.org/showthread.php?t=1900858)

From way back when, I have a GAG floppy, which I have now updated to boot all my OS's too.

That should really be enough for most purposes.

But while I am on "booting", I really want to find out how to get GAG & Super Grub2 Disk working from USB.
I have a long list of failed attempts at both.
The reason for wanting to continue is I also want rescue methods for a new/future netbook with no floppy capability & with Grub2.

Let's concentrate on GAG first.

I downloaded gag4.10 to the desktop & poked about a bit inside (not to mention days of Googling).
There is a very obvious cdrom.iso file in there.

I tried to use Ubuntu Startup Disk Creator, but it refuses to see that .iso...

Next, I tried Unetbootin on that .iso & the installation seemed to work, but when I boot to the USB stick, I just get a "Unetbootin" screen with "Default" & Autoboot 10 second timer, but no actions.

I read the instructions in gag4.10, which don't include USB, but found what I assume are the instructions for floppy:
> FROM LINUX/UNIX
Insert the formatted floppy in disk drive and type
   dd if=disk.dsk of=/dev/fd0 bs=512 count=2880
If you prefer, you can do too:
   cat disk.dsk > /dev/fd0
In other UNIX systems is possible you must use something different to /dev/fd0.
OTHER OPERATING SYSTEMS
You need a program that allows you to create floppies from disk images, and use it to copy the file DISK.DSK into the floppy.

So I tried "dd if=disk.dsk of=/dev/sdb bs=512 count=2880" & saw "1.5MB copied".
But when I boot, I just get:
"Verifying DMI Pool Data
GAG:1_" with no obvious issue.

I found some different instructions here:[http://sourceforge.net/projects/gag/forums/forum/230440/topic/3906428](http://sourceforge.net/projects/gag/forums/forum/230440/topic/3906428)
> Open Unetbootin. Select the "Diskimage" radio button and locate the image file "disk.dsk" delivered by GAG 4.10. Make sure "Diskette" format is selected, not "ISO".
Amazingly, this actually does something!
Booting from the USB, I get to "Unetbootin" screen with "Default" & Autoboot 10 second timer as before, but this time it passes to a GAG introduction screen with 5 Options including "Install GAG".

Install GAG actually works too, to some extent.
Having setup keyboard & language, after a bit of trial & error I find I can select Drive 2 which shows all my partitions, with Windows & Linux identified.
Then I can Add Windows, but need to select the option "Exchange drive letters", after which I can really boot to XP!

Not so good (yet?) for Ubuntu though.

I only get as far as my normal Grub screens, after which I get "Error 22: no such partition".
OK - I now know how to edit my way through that with e > (hd0,5) > (hd1,5) > b, which gets me to both Ubuntu's in the end, but not very elegantly!

Is there a better answer to that?

And will I finally be able to save the lot to the USB, as the options seem to be "Hard Disk" or "Floppy"?
But I am not there yet...

Thanks for any ideas!

---

### Post by 2CV67 on 2012-01-06
Let me re-ask a simple question which was maybe hidden in the last longish post:

With GAG on my USB stick, I can successfully boot XP & I can successfully get to the normal Grub screens for Ubuntu.
But selecting the Ubuntu kernels there gives me "Error 22 - no such partition"
I know how to recover from there, by editing (hd0,2) to (hd1,2) etc.
**But is there a way to avoid that error 22?**

Thanks!

---

### Post by oldfred on 2012-01-07
I do not know gag, but the error is from whatever gag uses for menu.lst. You can edit that to be the correct drive & partition. The error is like an error in grub legacy as grub2 does not have errors, but gives grub rescue or just a grub> command line.

---

