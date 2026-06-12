---
title: "[SOLVED] Booting from USB help"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by BluePlum on 2008-09-15
Hey, Just need some booting from USB help,

I have BT3F.ISO, I placed it onto my USB, I then booted from USB device, I get an error saying " Missing operating system " Does this mean I can't boot from the USB with this .ISO? Does it only work if i burn the .ISO to a CD first?

Thankyou

---

### Post by northern lights on 2008-09-15
It is the .iso's content, that needs be put on the flashdrive.

[unetbootin]("http://lubi.sourceforge.net/unetbootin.html") will be of help.

---

### Post by BluePlum on 2008-09-15
Will this make my USB unusuasable for other things?

---

### Post by northern lights on 2008-09-15
Nope.

---

### Post by BluePlum on 2008-09-16
I directed this program to the backtrack.iso then it just said to boot from USB which i did and it still didn't work.

---

### Post by northern lights on 2008-09-16
> **BluePlum said:**
> I directed this program to the backtrack.iso then it just said to boot from USB which i did and it still didn't work.

Exactly how did you "direct" it?

Mkey. Let's do this step-by-step.

You downloaded unetbootin-linux-281, right?

This is a bin file, so I assume you made it executable.

The packages 'mtools' and 'p7zip-full' are required for the USB setup to work. The application should tell you, actually. In case you don't have these installed, run ```
sudo apt-get update && sudo apt-get install p7zip-full mtools
```

Connect your flashdrive and execute unetbootin. You could select the .iso, but in fact BackTrack3 can be selected directly from the menu. So tick "Distribution" radio button and select Backtrack3. Select "Type: USB Drive" and pick the one in question from the "Drive:" drop-down menu. Click OK.

Let it do its magic.

---

### Post by ayenack on 2008-09-16
Have a look at [this]("http://icebuntu.6.forumer.com/viewtopic.php?t=24") it'll walk you through how to install to a USB device device. You will need to edit certain parts to set up your specific config because this was done for [IceBuntu]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu").

Might be an idea to give IceBuntu a go as it's a low drain version of Ubuntu.

Hope it helps.

---

### Post by BluePlum on 2008-09-16
I did that northen lights but it said " boot error ", Do i need a special USB .ISO ?

---

### Post by BluePlum on 2008-09-16
Wait i was doing it wrong :P. I was pointing to the .ISO not slecting the version :P, but now on my USB, there are files it wont let me delete !

---

### Post by wreti on 2008-09-16
I just went through this process and found both an easy way and a hard way. By the way, searching the BT forums will provide you with many answers and a new respect for the os.

If youre using windows, extract the files from the .iso to your flash drive. Open the boot folder and double click bootinst.bat. Follow the command line directives and that should be it.

Thats the quick way. It doesnt set up other partions for you which could come in handy if you want to save changes. I'll look for the link to the more lengthy set up process. Hope this helps!

---

### Post by BluePlum on 2008-09-16
I know how to do it theres just 4 Files on m y USB now they it wont let me delete!

---

### Post by BluePlum on 2008-09-17
Guys I cant even use my USB now, Please help!

---

### Post by wreti on 2008-09-17
Its not one of those sticks with a little locking switch on it, is it? Ive been troubled by those simple security devices before...

---

### Post by BluePlum on 2008-09-18
no.. Anyone else? I cant use my USB!

---

### Post by myidbe on 2008-09-18
Check the file permissions on the files you can't delete:

Navigate in a terminal to your usb drive and post the output of the following (after the - is a lower case L as in "list"):

```
ls -l
```

---

### Post by BluePlum on 2008-09-18
I dont really understand that but i tried deleteing the files in the USB and it said the file system is read only, or along those lines

---

### Post by halitech on 2008-09-18
open a terminal (Applications - Accessories - Terminal)

then type in ```
ls -l
``` and post the info back here

---

### Post by BluePlum on 2008-09-18
assasin@Invisible-Assasin:~$ ls -l
total 3111256
-rw-r--r--  1 assasin assasin 3182682112 2008-08-06 07:30 brasero.iso
drwxr-xr-x  9 assasin assasin       4096 2008-09-16 07:22 Desktop
drwxr-xr-x  3 assasin assasin       4096 2008-06-24 18:17 Documents
lrwxrwxrwx  1 assasin assasin         26 2008-06-23 20:43 Examples -> /usr/share/example-content
drwxr-xr-x 11 assasin assasin       4096 2008-06-28 12:13 kiba-dock
-rw-r--r--  1 assasin assasin      87890 2006-10-11 07:23 kiba-dock-0.1.tar.bz2
drwxr-xr-x  2 assasin assasin       4096 2008-08-21 14:23 lock
drwxr-xr-x  2 assasin assasin       4096 2008-06-23 20:56 Music
drwxr-xr-x  2 assasin assasin       4096 2008-08-04 16:11 Pictures
drwxr-xr-x  2 assasin assasin       4096 2008-07-22 17:46 Public
drwxr-xr-x  2 assasin assasin       4096 2008-06-23 20:56 Templates
drwxr-xr-x  2 assasin assasin       4096 2008-06-23 20:56 Videos

---

### Post by halitech on 2008-09-18
ok, that shows us how things should look so you now, we need to change to where the usb is mounted. Still in the terminal, type in ```
sudo fdisk -l
``` and post the output here

---

### Post by BluePlum on 2008-09-18
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             182        3529    26892810   83  Linux
/dev/sda2   *        3530        4676     9213277+   7  HPFS/NTFS
/dev/sda3            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0x419ade4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    c  W95 FAT32 (LBA)

```

When i tried to delete the files it deleted two of them but two of them didint delete.

---

### Post by halitech on 2008-09-18
ok, so the tumbdrive is mounted, where do you have it mounted at? You need to go to that directory in the terminal and then do the ls -l

---

### Post by BluePlum on 2008-09-18
```
assasin@Invisible-Assasin:~$ ls -l /media/disk
ls: cannot access /media/disk/}.ë6á: Input/output error
ls: cannot access /media/disk/ë&#9516;EIt
                                   fB.f9: Input/output error
ls: cannot access /media/disk/¼ &#9492;t	&#9508;â•—.: I&#9532;&#9147;&#9508;&#9500;/&#9146;&#9508;&#9500;&#9147;&#9508;&#9500; &#9226;&#9148;&#9148;&#9146;&#9148;
&#9500;&#9146;&#9500;&#9618;&#9484; 3830628
&#9229;????????? ? ?       ?             ?                ? Â¼ â””&#9500;?â”¤?â•—.?
&#9229;????????? ? ?       ?             ?                ? ?£.Ã«6Ã¡
&#9229;????????? ? ?       ?             ?                ? Ã«â”¬EI&#9500;?°B.°9?
-&#9148;&#9516;&#9474;------ 1 &#9618;&#9149;&#9149;&#9618;&#9149;&#9227;&#9532; &#9148;&#9146;&#9146;&#9500; 2305195040 2031-01-05 15:46 â”â‰¡+â•£?.°Â½0
-&#9148;&#9516;&#9474;------ 1 &#9618;&#9149;&#9149;&#9618;&#9149;&#9227;&#9532; &#9148;&#9146;&#9146;&#9500; 1617362456 1981-01-08 17:01 ?(·°â•‘?Â²M.â”´°Â¡
&#9229;&#9148;&#9516;&#9474;------ 7 &#9618;&#9149;&#9149;&#9618;&#9149;&#9227;&#9532; &#9148;&#9146;&#9146;&#9500;       4096 2008-09-16 22:58 ??&#9149;&#8804;&#9149;&#9484;&#9227;&#9532;.UX
-&#9148;&#9516;&#9474;------ 1 &#9618;&#9149;&#9149;&#9618;&#9149;&#9227;&#9532; &#9148;&#9146;&#9146;&#9500;          0 1980-01-01 01:00 â–*?â–“>â–„U &#9524;
&#9618;&#9149;&#9149;&#9618;&#9149;&#9227;&#9532;@I&#9532;&#9524;&#9227;&#9149;&#9227;&#9225;&#9484;&#9226;-A&#9149;&#9149;&#9618;&#9149;&#9227;&#9532;:·$ 



```

---

### Post by halitech on 2008-09-18
huh? what is that?

maybe we can do this another way, do you know if you have gparted installed? Would be under System - Admin - Partition Editor if you do

---

### Post by BluePlum on 2008-09-18
Yes i do

---

### Post by halitech on 2008-09-18
ok, open that up, select the thumbdrive from the drop down window in the upper right and then you should have an option to format from the actions menu I believe, just make sure you select fat16 or fat32 if you plan on using the drive in windows

do you have anything on there you want to save? if yes, don't do this

---

### Post by BluePlum on 2008-09-18
How do i find the thumb drive?

---

### Post by BluePlum on 2008-09-18
Wait i found it, I just cant find were to format

---

### Post by halitech on 2008-09-18
do you see a box that says somelike like /dev/sda1 ? click that down arrow and see if it has /media/disk or something similiar

---

### Post by BluePlum on 2008-09-18
Yeah im on that now, but i cant find were to format.

---

### Post by halitech on 2008-09-18
ok, in your tool bar at the top, go to Partition - Format to Fat32

---

### Post by BluePlum on 2008-09-18
Look at this [[IMG]http://img155.imageshack.us/img155/6343/screenshotdevsdbgpartedgz5.png[/IMG]](http://imageshack.us)

---

### Post by halitech on 2008-09-18
ok, the drive is mounted, thats why you can't format it. Unmount the drive and then you should be able to format it

---

### Post by BluePlum on 2008-09-18
IT WORKS! thanks so much! you saved me like $30, Im giving you so many thanks!

---

### Post by halitech on 2008-09-18
~L~ glad it works and just a single thanks is enough :D

---

### Post by BluePlum on 2008-09-18
> **halitech said:**
> ~L~ glad it works and just a single thanks is enough :D

To late!

---

