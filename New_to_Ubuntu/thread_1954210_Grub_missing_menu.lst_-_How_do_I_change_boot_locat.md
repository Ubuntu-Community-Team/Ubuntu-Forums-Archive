---
title: "Grub missing menu.lst - How do I change boot locations?"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-04-07
My OS is on a USB HDD on a computer without a Hard Drive. I made the install on my good laptop which is also dual booted with Ubuntu and Windows. So the grub lists a much different order. I wanted to change it to boot off of sda1, which is where ubuntu is, because it trues to load off of sda instead. I plugged my drive into this laptop and opened it up to go edit the menu.lst so that my Acer will boot (it wont now) but ther is no menu.lst inside the /boot/grub. I attached a .jpg of what is inside of grub.....

---

### Post by Quackers on 2012-04-07
Which version of Ubuntu? Later versions use grub2 rather than grub.
Grub2 does not have a menu.lst

---

### Post by theducksfan2010 on 2012-04-07
12.04, so that would mean it's grub 2. How do I edit the grub inside of the USB HDD to reflect that only it is present and to boot off of sda1? I can't find anything understandable through google.

Going through my folders in Ubuntu 11.10 I found my 40 GB File system inside /media as af41e6ee-5fbc-43cc-b778-398661fd03a3. but when i try to get to it in the terminal i get this: 

josh@josh-Compaq-Presario-CQ60-Notebook-PC:~$ cd /media
josh@josh-Compaq-Presario-CQ60-Notebook-PC:/media$ cd /af41e6ee-5fbc-43cc-b778-398661fd03a3
bash: cd: /af41e6ee-5fbc-43cc-b778-398661fd03a3: No such file or directory
josh@josh-Compaq-Presario-CQ60-Notebook-PC:/media$ ^C
josh@josh-Compaq-Presario-CQ60-Notebook-PC:/media$

---

### Post by Quackers on 2012-04-07
So just to clear things up you are trying to boot a pc from a USB HDD. 
Once the bios is set to boot from the USB HDD first you are seeing a grub menu? 
What is on that menu please? And what order would you like things to be in?

---

### Post by ajgreeny on 2012-04-07
You do, indeed, have grub 2 on your system, which works totally differently to legacy grub.

There is now a grub.cfg file instead of menu.lst, but you can not edit that directly as it is read-only, but must use the configuration files /etc/default/grub and the numbered files in /etc/grub.d

See the grub 2 links in my signature for more details.

---

### Post by theducksfan2010 on 2012-04-07
> **Quackers said:**
> So just to clear things up you are trying to boot a pc from a USB HDD. 
Once the bios is set to boot from the USB HDD first you are seeing a grub menu? 
What is on that menu please? And what order would you like things to be in?


I did the installation on this laptop, because the Acer only has 256MB of RAM, so installation would not complete on it, although it will run the OS well. Only problem is it comes up with everything on this laptop in the grub screen also

GNU GRUB version 1.99-20ubuntu1

Ubuntu, with Linux 3.2.0-20-generic
Ubuntu, with Linux 3.2.0-20-genreic (recovery mode
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Ubuntu, with Linux 3.0.0-17-generic (on /dev/sda6)
Ubuntu, with Linux 3.0.0-17-generic (recovery mode)(on /dev/sda6)
Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda6)
Ubuntu, with Linux 3.0.0-16-generic (recovery mode)(on /dev/sda6)
Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)
Ubuntu, with Linux 3.0.0-12-generic (recovery mode)(on /dev/sda6)

This USB HDD only has 12.04 on it - with the grub on sda, the os on sda1, and a swap partition

The Acer has no internal HDD, so the computer sees the ext as sda.

When I click on the first option from the grub, it returns with: 
ata_id[199]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument

The order I want them to be in, Just the 12.04 and for the grub to boot off of the right partition, so I can actually get into the OS and passed the Grub screen.

---

### Post by oldfred on 2012-04-07
Your menu shows a Windows in sda1. So what are you booting? And is that part of the confusion.

May be best to post link to bootinfo script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by theducksfan2010 on 2012-04-07
> **oldfred said:**
> Your menu shows a Windows in sda1. So what are you booting? And is that part of the confusion.

May be best to post link to bootinfo script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Yes, it shows other OS and items that are not present - I had to do the install on my Compaq, because the acer does not have enough memory to do the install on it, but will run the OS well, upon installation. All the items after the memtest are on sda of the compaq, but got imported into the grub on the USB HDD. The only OS on the USB HDD is 12.04 and it is located on sda1

If i boot the repair option I can get into a maintenance terminal, and if not it jus sits where it is now

fsck from util-linux 2.20.1
/dev/sda1: clean, 123495/2411920 files, 767017/9649152 blocks

---

### Post by NikTh on 2012-04-07
Hi ,
**I don't know if i understood correct** but you say that you have 12.04 installed on ext HDD , and you took this HDD plugged it in another pc and you want to boot the 12.04 to the new pc , from ext. HDD. I think this is not going to happen. 

Did you see the message ? invalid argument for ata id. 
Try to reinstall grub2 to the ext.HDD when you plug it in to new pc. You can reinstall grub2 with LiveCD. Read here how to -->[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Thanks.

---

### Post by theducksfan2010 on 2012-04-07
> **NikTh said:**
> Hi ,
**I don't know if i understood correct** but you say that you have 12.04 installed on ext HDD , and you took this HDD plugged it in another pc and you want to boot the 12.04 to the new pc , from ext. HDD. I think this is not going to happen. 

Did you see the message ? invalid argument for ata id. 
Try to reinstall grub2 to the ext.HDD when you plug it in to new pc. You can reinstall grub2 with LiveCD. Read here how to -->[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Thanks.

Yes and Yes, this is the ata argument I got:

ata_id[199]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument

It did boot up twice for me when I first installed it but then locked up using Chromium.

I can get it as far as to load into a maintenance terminal; but do not know what do do form inside of that.

---

### Post by oldfred on 2012-04-07
If it is the same as this bug you should report it as with only one person it is unconfirmed.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/931135](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/931135)

You have to create a separate login to launchpad.

---

### Post by NikTh on 2012-04-07
Hi , 
if you did reinstall grub and problem not solved then maybe hdparm did the mess . 
It is extremely dangerous to play with this tool. There is a command that may be fix(maybe not) the problem but it is DANGEROUS. 
Just read the man page , i quote  the DANGEROUS parameter . 
> --dco-restore
              Reset all drive settings, features, and accessible capacities back  to  factory  defaults  and  full
              capabilities.   This command will fail if DCO is frozen/locked, or if a -Np maximum size restriction
              has also been set.  This is EXTREMELY DANGEROUS and will very likely cause massive loss of data.  DO
              NOT USE THIS COMMAND.

My suggestion is to do a fresh install of 12.04 to your ext-HDD . I think it is the safest way. If you have any personal files you can backup them to your laptop or to another ext-hdd(if you have). 
Thanks

---

### Post by theducksfan2010 on 2012-04-07
> **NikTh said:**
> Hi , 
if you did reinstall grub and problem not solved then maybe hdparm did the mess . 
It is extremely dangerous to play with this tool. There is a command that may be fix(maybe not) the problem but it is DANGEROUS. 
Just read the man page , i quote  the DANGEROUS parameter . 


My suggestion is to do a fresh install of 12.04 to your ext-HDD . I think it is the safest way. If you have any personal files you can backup them to your laptop or to another ext-hdd(if you have). 
Thanks

There is NO internal hard drive, if i did this will it take the Lubuntu 12.04 back to fresh install where it re-installs all drivers?

---

### Post by anewguy on 2012-04-07
Clearly, you installed on the external drive via computer A, and computer A has a hard disk with Windows.  When the installer got to the part on building grub, it searched for all OS's on all disks on the computer it is running on at the time of the install - in your case computer A.

You've taken the external disk you installed to and plugged it into computer B.  This leaves the grub entries from computer A still in the menu.

What you want to do is clear the other OS's from grub (which is on the external disk) so that there is only Ubuntu, so that Ubuntu automatically boots with no menu when you boot computer B from the external drive.

Does that sum up what you are trying to do?

If so, the quick work around, but not something you really should do, is to edit the /boot/grub/grub.cfg file to remove all references to the other OS's. 

You really need to be forwarned about this, however.  This is NOT the proper way to do this, and that file will be overwritten any time a new kernel is delivered in an update, or potentially from any other update that has something that affects the boot.

You should follow the links posted in the signature of one of the previous posters.

Dave ;)

---

### Post by theducksfan2010 on 2012-04-08
> **oldfred said:**
> Your menu shows a Windows in sda1. So what are you booting? And is that part of the confusion.

May be best to post link to bootinfo script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Ok, I did the grub repair and when I booted up the Acer everything looked good in the Grub. but I know get a new ata_id error - 185

Anewguy - yes you summed it up perfectly. Any ideas on what to do now??

After sitting and waiting after the error - about 5 min later it just shut off. Now I think I am actually further away from getting this to work. I can't even get to a maintenance console....

ata_id [752] is error I get using recovery mode in grub

---

### Post by anewguy on 2012-04-09
On computer B, were you ever able to boot to the command prompt before doing everything mentioned here?

Dave ;)

---

### Post by theducksfan2010 on 2012-04-09
> **anewguy said:**
> On computer B, were you ever able to boot to the command prompt before doing everything mentioned here?

Dave ;)

No, I was able to get into a maintenance terminal as it progressed, but that was the only command prompt I could get to.

---

### Post by westie457 on 2012-04-09
Hello, It looks like you are going to have to purge and re-install grub to the external HDD using this How-to written by drs305 [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) or using Boot Repair from a link posted earlier by oldfred.

Which way you do this is upto you however it is probably best done on the machine used to do the original installation as that can run the Live Desktop. Also it is better this time to remove the internal Hard drive so the operating system is not found when you update grub for the external HDD.

Hope this helps.

---

### Post by theducksfan2010 on 2012-04-09
> **westie457 said:**
> Hello, It looks like you are going to have to purge and re-install grub to the external HDD using this How-to written by drs305 [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) or using Boot Repair from a link posted earlier by oldfred.

Which way you do this is upto you however it is probably best done on the machine used to do the original installation as that can run the Live Desktop. Also it is better this time to remove the internal Hard drive so the operating system is not found when you update grub for the external HDD.

Hope this helps.

I have re-installed the grub running live CD on the Acer that this will be on, it has no internal Hard Drive. It now sits at

ata_id[198]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid Argument

---

### Post by anewguy on 2012-04-09
What they want you to do is remove the hard disk from computer A, reinstall Ubuntu to the external disk using ccomputer A.  This way there will be no grub entry for Windows when you take it to computer B.

If you can get to any form of console so you can run the editor, editing the grub.cfg file as I mentioned is less work hardware wise.  The choice is yours.

---

### Post by theducksfan2010 on 2012-04-09
> **anewguy said:**
> What they want you to do is remove the hard disk from computer A, reinstall Ubuntu to the external disk using ccomputer A.  This way there will be no grub entry for Windows when you take it to computer B.

If you can get to any form of console so you can run the editor, editing the grub.cfg file as I mentioned is less work hardware wise.  The choice is yours.

I reinstalled grub off of the live CD on computer B when I was actually able to get it to load. Now the grub looks good when I turn it on, but it is stuck at:

ata_id[187]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument

---

### Post by anewguy on 2012-04-09
Did you, by chance, reconnect the hard disk and then try to boot?  What does your BIOS say for hard disks it knows about?  I only ask because we really do need to know what device sda is.  I suspect at this point that it may be outside of the grub.cfg and in one of the things discussed earlier in this thread - like the hd params.  

I will try looking more into that error code, but I can't guarantee I'll find something worth while.

If you could, post in complete steps what you did all the way up until ths problem occured.  Also attach your grub.cfg file.

Dave ;)

---

### Post by theducksfan2010 on 2012-04-09
Did you, by chance, reconnect the hard disk and then try to boot?  

No, the laptop has no HDD, looked for one for it in Okinawa, Japan in 2007 but the ones on the market are to new to fit the cabling inside. So I went USB HDD. 



What does your BIOS say for hard disks it knows about?  I only ask because we really do need to know what device sda is.

The only drive this laptop sees is the USB HDD, and it shows up as sda.


I will try looking more into that error code, but I can't guarantee I'll find something worth while.

I haven't found anything to help me with this using google on the errors.


If you could, post in complete steps what you did all the way up until ths problem occured.  Also attach your grub.cfg file.

I installed the OS on my Compaq laptop, finally got the Acer to run the live CD and re-installed the grub to sda. Lubuntu 12.04 loads up on , Compaq in less than a minute, moving past the errors. I will go pull up the grub.cfg and post it in here momentarily.

---

### Post by theducksfan2010 on 2012-04-09
Here is my grub.cfg

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root af41e6ee-5fbc-43cc-b778-398661fd03a3
	linux	/boot/vmlinuz-3.2.0-20-generic root=UUID=af41e6ee-5fbc-43cc-b778-398661fd03a3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root af41e6ee-5fbc-43cc-b778-398661fd03a3
	echo	'Loading Linux 3.2.0-20-generic ...'
	linux	/boot/vmlinuz-3.2.0-20-generic root=UUID=af41e6ee-5fbc-43cc-b778-398661fd03a3 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root af41e6ee-5fbc-43cc-b778-398661fd03a3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root af41e6ee-5fbc-43cc-b778-398661fd03a3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###


This is from inside the OS (Lubuntu 12.04) running on the Acer

---

### Post by anewguy on 2012-04-10
I'm not sure how to go about this.  Perhaps there is something in one of the device tables as mentioned earlier by another poster.  Right now I don't think I can be of any further help.

Dave

EDIT:  Just a hunch.  When you ran update grub from the LiveCD on computer B, did you follow a post or how-to for that?  I don't remember the exact procedure, but I know it you do it wrong you can also end up with the drive the LiveCD is in being the one in the grub.cfg to boot ubuntu.  Just a hunch, probably nothing to it.

---

### Post by theducksfan2010 on 2012-04-11
> **anewguy said:**
> I'm not sure how to go about this.  Perhaps there is something in one of the device tables as mentioned earlier by another poster.  Right now I don't think I can be of any further help.

Dave

EDIT:  Just a hunch.  When you ran update grub from the LiveCD on computer B, did you follow a post or how-to for that?  I don't remember the exact procedure, but I know it you do it wrong you can also end up with the drive the LiveCD is in being the one in the grub.cfg to boot ubuntu.  Just a hunch, probably nothing to it.

Yeah, I followed a how to tutorial, that was still a little beyond my own scope right now, lol. I'm getting it to boot up now, in 5-15 minutes. 

After I updated the grub with the how to, the grub looked good, but I only had wireless g on this comp at the time, so I did sudo apt-get update and sudo apt-get upgrade with the USB back on Comp A , and it added all the OS's back to my Grub again.

---

### Post by anewguy on 2012-04-11
> **theducksfan2010 said:**
> Yeah, I followed a how to tutorial, that was still a little beyond my own scope right now, lol. I'm getting it to boot up now, in 5-15 minutes. 

After I updated the grub with the how to, the grub looked good, but I only had wireless g on this comp at the time, so I did sudo apt-get update and sudo apt-get upgrade with the USB back on Comp A , and it added all the OS's back to my Grub again.

Yep - that would do it!  Glad you're getting it figured out.  Please post back after you have reinstalled again and let us know how it turned out.

And something you already know, but what the heck:

If you do put a hard disk in the PC, and you do happen to install another OS to it, remember that any time certain updates come through, including but not limited to new kernels, grub is automatically updated.  This would pick up the OS from the other disk and add it to the grub menu again.

Dave ;)

---

