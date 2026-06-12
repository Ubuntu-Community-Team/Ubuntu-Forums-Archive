---
title: "Using Ubuntu to recover hard drive files"
date: 2016-01-18
forum: New to Ubuntu
---

### Post by heather8 on 2016-01-18
My laptop crashed several days ago and I have been trying to fix it since.  I downloaded a copy of windows 10 to a usb drive and tried to use it to fix the laptop, didn't work.  I found information on using Ubuntu.  I tried burning a disc but my laptop didn't recognize it so I put Ubuntu on a usb drive.  I'm not sure how to go about using it to boot my laptop as when I go into the setup utility, it doesn't give me the usb option like it did with the windows usb drive.  When I let my laptop attempt to boot on its own, it gets to a repairing 5% screen and never moves from there....even after 48 hours.  Any help you can offer will be ever so GREATLY APPRECIATED.  I have college information on there that I needed yesterday.....

Not sure which forum to post under but I need help using Ubuntu to recover files on my crashed hard drive.  I posted under the "Windows" forum since that's what my laptop has.  My laptop will not boot, just goes to the splash screen and states that it is trying to repair at 5% for over 48 hours.  I've tried a Windows 10 usb drive with no luck.  The laptop doesn't see the Ubuntu usb drive when I go into setup utilities.  Any help will be greatly appreciated because I have things on the laptop I needed yesterday for a college class.

---

### Post by The Cog on 2016-01-18
Is this a real USB hard drive, or a USB memory stick?
How did you install Ubuntu to the USB drive?

Here are some links to how to burn a USB memory stick. I found them using Google just now, can't guarantee them as I have never made an Ubuntu stick using windows.
The win32diskimager method looks closest to the way I do it with Linux.
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://wiki.ubuntu.com/Win32DiskImager](https://wiki.ubuntu.com/Win32DiskImager)

Once you get Ubuntu working, you should be able to find a file manager and copy the files from the hard disk to an external USB disk or stick. Don't try to copy the files to the one you just booted from as it is likely read-only and certainly in a format that windows can't read anyway.

---

### Post by yancek on 2016-01-18
Which operating system were you using on your laptop before it crashed?  If it was windows, which version?
I don't think downloading a copy of windows 10 to a usb is going to do anything useful. Windows can't be installed on a usb drive.

Define crashed, exactly what happened?  How did you put Ubuntu on the flash drive, which software did you use to do it?
If you have an Ubuntu iso file, you can burn it to a DVD and make it bootable if you select to 'burn as an image' on your disk burning software.

---

### Post by heather8 on 2016-01-18
Just the stick.  I have an external drive for the cloning of my laptop hard drive when I am able to do so.  I downloaded the program and then moved it over to the stick.  I haven't tried running it on the PC that still works (that I am using now).  I have a Dell laptop and I can't get it to move from the splash screen with Dell and Diagnosing your PC this morning.  I can get to the setup utilities and boot options but it doesn't have the memory stick listed.

---

### Post by heather8 on 2016-01-18
Windows 10, the laptop originally came with 8 and I did the free download of 10.  When you attempt to upgrade to windows 10 on a computer that doesn't have it, you are offered the option of putting it on a memory stick.  I did that with my PC as it still has Windows 7.

I received a message that my laptop was having hard drive issues but I don't recall the exact message.  The recommended fix was to make a backup disc.  I thought the message was odd as it had something about Windows 7 on it (remember my laptop came with 8 and I had downloaded 10) so I was going to attempt to restore to a previous point.  When I rebooted the machine, I started getting messages about repairing and it stayed at 5% for 48 hours.  I then tried to do the Windows 10 thing and then found information on Ubuntu.  For the Ubuntu flash drive, I tried burning a CD but had to put it on a DVD because my CD wasn't large enough.  It defaulted to Nero so I burned it using that.  I wasn't sure my laptop was reading the dvd drive so I decided to try the memory stick.  I just opened the folder the Ubuntu downloaded to and then opened the folder for the USB stick.  I just pulled the program over on it and it put it on there.

---

### Post by howefield on 2016-01-18
Threads merged.

---

### Post by The Cog on 2016-01-18
I think by default, Nero will open the .ISO file and just write the contents to a CD, which is not what you want.

You have to write the whole .ISO image to the stick, this includes the bootloader and two partitions. This is done by writing the entire image to the drive, not just selected contents.

I suggest you have a try with win32diskimager, linked in post #3 above (that page contains a link to a tutorial page).

---

### Post by ajgreeny on 2016-01-18
Whilst not wishing to be unhelpful, even if you can get Ubuntu to boot from a live USB system you may still have problems mounting the Windows disk, which I assume would be formatted as NTFS.  This is because Linux can not mount an NTFS filesystem which is still apparently in use by the crashed OS.

It may be easier to find a friend who has both Windows as an OS and a hard disk caddy in which you can use the disk. Windows has no problem mounting a "crashed" ntfs file system (as long as it is not totally corrupt, of course) and should be able to get your files back for you onto another flash drive or external HDD.

---

### Post by Bucky Ball on 2016-01-18
USB installers. Use the ISO you downloaded as your source file and the USB as the target (which is usually set by default):

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

When finished, try booting from the USB.


If you just want to clone your disk, then Clonezilla or fsarchiver may be options.

fsarchiver:
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by haplorrhine on 2016-01-18
> **ajgreeny said:**
> Whilst not wishing to be unhelpful, even if you  can get Ubuntu to boot from a live USB system you may still have  problems mounting the Windows disk, which I assume would be formatted as  NTFS.  This is because Linux can not mount an NTFS filesystem which is  still apparently in use by the crashed OS.

I haven't personally done it with Kali Linux, but...

[https://forums.kali.org/showthread.php?18787-Using-Kali-Linux-to-access-corrupted-external-Hard-Drive](https://forums.kali.org/showthread.php?18787-Using-Kali-Linux-to-access-corrupted-external-Hard-Drive)
"Thanks for your tips and info, I was able to remove most of my files  from the corrupted HD.  It took quite a while, but I was able to do it!"

[https://www.kali.org/kali-linux-features/](https://www.kali.org/kali-linux-features/)
**"Kali Linux forensics mode** &#8211; The bootable &#8220;Forensics&#8221;  mode available in Kali makes it perfect for forensics work, as the  forensics Kali live image option does not mount any drives (including  swap) with this option."

---

### Post by heather8 on 2016-01-18
How can I MAKE it boot from the USB?  I can get it to boot from the Windows USB stick but not the one I have Ubuntu on.

---

### Post by Bucky Ball on 2016-01-18
Enter BIOS and boot from the stick the same way as you do with the Windows stick? If that's not working, that's odd. You have created the stick using one of the methods described earlier? Please let us know exactly how you made the stick as you need to burn a disk image to it, not just copy the ISO.

---

### Post by heather8 on 2016-01-18
> **Bucky Ball said:**
> Enter BIOS and boot from the stick the same way as you do with the Windows stick? If that's not working, that's odd. You have created the stick using one of the methods described earlier? Please let us know exactly how you made the stick as you need to burn a disk image to it, not just copy the ISO.

It is possible that it just copied it over I guess because I just drug it from one folder to the other (from the download folder to the stick folder).  I will delete the stick and try again.

> **ajgreeny said:**
> 

It may be easier to find a friend who has both Windows as an OS and a hard disk caddy in which you can use the disk. Windows has no problem mounting a "crashed" ntfs file system (as long as it is not totally corrupt, of course) and should be able to get your files back for you onto another flash drive or external HDD.

I had read about the hard disk caddy stuff before but I have never heard  of it....unfortunately I am probably my best source of my own help with  that part.  I have a PC that has windows 7 that I am using and can use  for whatever.  I don't have the hard disk caddy but know how to add  drives and stuff to my own computer.  Is the caddy something I can order  or is it something I would already have?  No problems with ordering or  doing whatever, I HAVE to have those files from my laptop.  Once I get a  caddy, what do I do from there?

A sort of different topic but I had my passwords saved on the laptop so I  didn't have to put them in each time I logged into stuff online....any  chance I can find a way of getting those too?

> **The Cog said:**
> Is this a real USB hard drive, or a USB memory stick?
How did you install Ubuntu to the USB drive?

Here are some links to how to burn a USB memory stick. I found them using Google just now, can't guarantee them as I have never made an Ubuntu stick using windows.
The win32diskimager method looks closest to the way I do it with Linux.
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://wiki.ubuntu.com/Win32DiskImager](https://wiki.ubuntu.com/Win32DiskImager)

Once you get Ubuntu working, you should be able to find a file manager and copy the files from the hard disk to an external USB disk or stick. Don't try to copy the files to the one you just booted from as it is likely read-only and certainly in a format that windows can't read anyway.

So I went back and used the first link to create the USB stick and it works!  Now, my question is this.  I had passwords saved to my computer for things like my email and a lot of stuff that I use online the password was saved.  Is there anyway I can regain those?  I guess what I need to do is open up a browser through windows instead of through ubuntu.  I found a way to find my passwords, just not sure how to access the browser from the computer instead of the drive....I hope that makes sense.

---

### Post by haplorrhine on 2016-01-18
> **heather8 said:**
> It is possible that it just copied it over I guess because I just drug it from one folder to the other (from the download folder to the stick folder).  I will delete the stick and try again.

You can't just paste it onto the flashdrive.  A ubuntu iso image consists of the Grub boot partition, file system, and swap partition.  The flashdrive will have its own boot partition until it is formatted.

---

### Post by yancek on 2016-01-18
> I found a way to find my passwords, just not sure how to access the  browser from the computer instead of the drive....I hope that makes  sense. 				

No, not to me anyway.  The drive is attached to the computer.  If you are now able to boot Ubuntu on the flash drive, do that.  When you get the Desktop, open a terminal by clicking on the Dash icon, the Ubuntu logo in the extreme upper left of the Desktop.  There will be a Search box, type:  terminal in it and you should see an icon below showing terminal.  Click it to open and type:  sudo fdisk -l and then hit the enter key.  Also type:  parted -l and hit the enter key.  Lower case Letter L  in the commands.  Post the output here.  With this info someone should be able to explain how to access your folders/files on the windows partition.

---

### Post by Bucky Ball on 2016-01-18
Boot your Ubuntu install disk, choose 'Try Ubuntu', plug in an ethernet cable, launch Firefox and go online. Makes no diff in Win or Ubuntu. You can browse the net in either ...

---

### Post by heather8 on 2016-01-18
> **Bucky Ball said:**
> Boot your Ubuntu install disk, choose 'Try Ubuntu', plug in an ethernet cable, launch Firefox and go online. Makes no diff in Win or Ubuntu. You can browse the net in either ...

I can get online but it doesn't have my passwords saved that I had on windows.....I am using ubuntu now to be online but I still can't access the passwords that I need.

> **yancek said:**
> No, not to me anyway.  The drive is attached to the computer.  If you are now able to boot Ubuntu on the flash drive, do that.  When you get the Desktop, open a terminal by clicking on the Dash icon, the Ubuntu logo in the extreme upper left of the Desktop.  There will be a Search box, type:  terminal in it and you should see an icon below showing terminal.  Click it to open and type:  sudo fdisk -l and then hit the enter key.  Also type:  parted -l and hit the enter key.  Lower case Letter L  in the commands.  Post the output here.  With this info someone should be able to explain how to access your folders/files on the windows partition.

It didn't do anything with the "parted -l" but here is what I got with the sudo fdisk - l

```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

```

---

### Post by Bucky Ball on 2016-01-18
> **heather8 said:**
> I can get online but it doesn't have my passwords saved that I had on windows.....I am using ubuntu now to be online but I still can't access the passwords that I need.

Now I see. You can't click 'forgot password' and request a new password on the sites in question?

* Please use code tags for terminal output. See the link in my signature below for how. Thanks. ;)

---

### Post by heather8 on 2016-01-18
> **Bucky Ball said:**
> Now I see. You can't click 'forgot password' and request a new password on the sites in question?

* Please use code tags for terminal output. See the link in my signature below for how. Thanks. ;)

I have tried that and one is my yahoo email.  The problem with that is verizon is my internet provider and yahoo says verizon has to change it, verizon says yahoo has to change it...yada yada yada.  No one ever wants to help.  When I got verizon as my provider, my sign in for that linked/merged/something with yahoo email and somehow yahoo says it's all verizons now.....who knows....it's the "pass the idiot" game every time I contact one of them.

Some of the other places are helping....others are not budging....sorry, not enough information to prove I am who I say I am so there is nothing they can do.....

---

### Post by dale18 on 2016-01-18
I recently used a copy of Ubuntu to recover important files from my B-I-L's desktop.

I inserted the Ubuntu disc, then accessed the BIOS and changed the boot order to CD.  I then restarted the computer, let it load then used Ubuntu to access the Windows files on the HDD.  I transferred the important files to a USB, then turned off the desktop after removing the Ubuntu disc.

It was actually easier than I though it would be.

---

### Post by heather8 on 2016-01-18
> **dale18 said:**
> I recently used a copy of Ubuntu to recover important files from my B-I-L's desktop.

I inserted the Ubuntu disc, then accessed the BIOS and changed the boot order to CD.  I then restarted the computer, let it load then used Ubuntu to access the Windows files on the HDD.  I transferred the important files to a USB, then turned off the desktop after removing the Ubuntu disc.

It was actually easier than I though it would be.

I need everything that is on that hard drive.  Do I just drag and drop?  I have an external hard drive I want it placed on, just not sure how to get the files over there....or how to get ALL the files I need.  I don't want to leave anything out.  There is a massive amount of information I need from this hard drive.

Believe it or not, I was able to gain access to my old passwords that were saved on the windows part of my laptop!!  I can now access all my stuff.  Now to get my hard drive cloned onto the external hard drive and to buy a new hard drive for my laptop.

---

### Post by Bucky Ball on 2016-01-19
> **heather8 said:**
> Believe it or not, I was able to gain access to my old passwords that were saved on the windows part of my laptop!!  I can now access all my stuff.

Great news. :)

Please see the first link in my signature and mark as solved.

> **heather8 said:**
> Now to get my hard drive cloned onto the external hard drive and to buy a new hard drive for my laptop.

Please start a new thread if you need any Linux help with that. It will greatly improve your chances of getting it. Good luck.

---

