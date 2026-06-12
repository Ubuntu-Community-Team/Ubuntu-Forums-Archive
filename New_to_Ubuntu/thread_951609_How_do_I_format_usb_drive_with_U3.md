---
title: "How do I format usb drive with U3"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by J03y on 2008-10-18
How do i format usb drive with U3 using gparted? :confused:

---

### Post by ARhere on 2008-10-18
????

What is U3?  You mean Ext3, or the new memory format for flash memory supported by the new kernel?

If you mean the latter, then you cannot as USB memory is a block device and the new format is for direct flash memory.  An example would be an embedded PC with 8051 and flash IC.

-AR

---

### Post by J03y on 2008-10-18
> **ARhere said:**
> ????

What is U3?  You mean Ext3, or the new memory format for flash memory supported by the new kernel?

If you mean the latter, then you cannot as USB memory is a block device and the new format is for direct flash memory.  An example would be an embedded PC with 8051 and flash IC.

-ARU3 is like a program(I think) that comes in a San Disk usb drive

---

### Post by ARhere on 2008-10-18
OK, I studied U3 from sandisk.  It is not a file format, rather an accessibility program.

When you cut down all the marketing hype, it seems to be an program that you load on your PC allowing you to install other applications onto the flash drive with their associated files.  The main benefit appears to be when you don't have a certain application installed on another computer, this will still allow you to open your files on the USB drive with a 'lite' version of that app.

This is nice, but is only necessary on a closed application platform like Windows where you need a licensed copy of each app on each PC.  You can install any app you want on Ubuntu as long as you have an internet connection.

So in short, if you use Ubuntu, it is not necessary.

-AR

---

### Post by Kareeser on 2008-10-18
*sigh* U3... the devil. I plugged it into my box and it installed garbage without asking me. Reeks of virus-like behaviour, if you ask me.

Ultimately, Sandisk caved to public pressure and put up a U3 removal tool for download.

Go to a windows box, plug in the U3 drive, and run this:
[http://www.sandisk.com/Assets/u3/launchpadremoval.exe](http://www.sandisk.com/Assets/u3/launchpadremoval.exe)

---

### Post by J03y on 2008-10-18
> **Kareeser said:**
> *sigh* U3... the devil. I plugged it into my box and it installed garbage without asking me. Reeks of virus-like behaviour, if you ask me.

Ultimately, Sandisk caved to public pressure and put up a U3 removal tool for download.

Go to a windows box, plug in the U3 drive, and run this:
[http://www.sandisk.com/Assets/u3/launchpadremoval.exe](http://www.sandisk.com/Assets/u3/launchpadremoval.exe)I opened it and then said, "Please insert a U3 media smart drive", and my U3 usb drive is already inserted.

p.s. I tried to open it with Wine

---

### Post by Kareeser on 2008-10-18
Oh. Smart media...

Try this:
[http://www.u3.com/uninstall/final.aspx](http://www.u3.com/uninstall/final.aspx)

---

### Post by J03y on 2008-10-18
> **Kareeser said:**
> Oh. Smart media...

Try this:
[http://www.u3.com/uninstall/final.aspx](http://www.u3.com/uninstall/final.aspx)That's the first thing i downloaded from the beginning  and the same thing happened when i opened with Wine. :mad:

---

### Post by mc4man on 2008-10-18
if you really want to remove the U3 partition then you have to do it in *windows*. For the SanDisk you need to use it's uninstaller, not the generic U3 uninstaller.
Otherwise you could just leave it, it has almost no effect in linux and only occupies about 6mb. (the U3 partition is seen as a cdrom drive and given some /dev links.

If you want to reformat the 'disk' partition you can do so in gparted.

---

### Post by karlmp on 2008-11-05
I'm trying to download the removal tool but for some reason it stops when is going at 45%

---

