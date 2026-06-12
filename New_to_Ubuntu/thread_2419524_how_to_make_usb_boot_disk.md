---
title: "how to make usb boot disk"
date: 2019-05-23
forum: New to Ubuntu
---

### Post by billmaxey on 2019-05-23
I have totaled windows 10 and am trying to install ubuntu.  I copied the download file to a usb drive, ran the .iso file.  how do I make the usb bootable?
thanks

---

### Post by Autodave on 2019-05-23
It has to be installed on the USB as an .iso file: you cannot merely copy it onto the drive.  Are you trying to do this with a Windows machine or a Linux machine?

For Windows, you need UNetbootin installed and that will allow you to then create a bootable USB or disc.

---

### Post by billmaxey on 2019-05-23
I downloaded unetbootin-windows.exe and ran it on the usb drive but when I try to boot ubunto it tells me 'invalid or corrupt kernel image"
Thanks for your response.

---

### Post by billmaxey on 2019-05-23
BTW, I'm WAY over my head here.

---

### Post by Rubi1200 on 2019-05-23
I found UNetbootin to be less than reliable.

Try Rufus from a Windows installation:
[https://portableapps.com/apps/utilities/rufus-portable](https://portableapps.com/apps/utilities/rufus-portable)

---

### Post by billmaxey on 2019-05-23
Yeah, I tried Rufus.  Can't get past the run command.

---

### Post by Rubi1200 on 2019-05-23
Let's step back a minute with this.

With the version I linked to try like this:

Double click the file and follow instructions to install.

Once done, open the application and put the USB stick you want to use in the computer (Rufus will detect it automatically).

Then click Select and browse to where you saved the ISO image and add.

Click start.

There might be a warning about syslinux files just click yes and yes to ISO Image (Recommended) and yes to you know it will overwrite any data on the stick.

Then just wait until finished.

Once done you can close Rufus, take out the stick and then you have a bootable Ubuntu to try out.

---

### Post by billmaxey on 2019-05-23
I cannot make rufus work.

---

### Post by Rubi1200 on 2019-05-23
Right now, are you using Windows as the operating system or something else?

What happened when you tried it, what error messages are you getting?

---

### Post by billmaxey on 2019-05-23
Yes, Windows.
The error message says that the ubuntu iso file is not the
Oh, and thanks for your time and your help.  It is appreciated.

---

### Post by billmaxey on 2019-05-23
* add to the first line above* 'right size'.

---

### Post by Rubi1200 on 2019-05-23
Might be there is a problem with the ISO image.

Try downloading again from here:
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

If you prefer a torrent that is here under BitTorrent:
[https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

Place the downloaded image (after either a direct or torrent download) in the Rufus folder and then try again using the instructions from earlier.

Hopefully it will work this time.

---

### Post by billmaxey on 2019-05-23
[LIST]
[*][INDENT]Yes, Windows.
The error message says that the ubuntu iso file is not the
correct size.
Oh, and thanks for your time and your help. It is appreciated.[/INDENT]



[B][RIGHT][[IMG]https://ubuntuforums.org/clear.gif[/IMG]Edit Post]("https://ubuntuforums.org/editpost.php?p=13861276&do=editpost")   [[IMG]https://ubuntuforums.org/clear.gif[/IMG]Quick Reply]("https://ubuntuforums.org/newreply.php?do=newreply&p=13861276&noquote=1")   [[IMG]https://ubuntuforums.org/clear.gif[/IMG]Adv Reply]("https://ubuntuforums.org/newreply.php?p=13861276&noquote=1")   [[IMG]https://ubuntuforums.org/clear.gif[/IMG]Reply With Quote]("https://ubuntuforums.org/newreply.php?do=newreply&p=13861276")   [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/multiquote_40b.png[/IMG] ]("https://ubuntuforums.org/newreply.php?do=newreply&p=13861276")[/RIGHT] [ ]("https://ubuntuforums.org/report.php?p=13861276")  
[/B]

[*]

[/LIST]
[COLOR=#000000][/COLOR]

---

### Post by billmaxey on 2019-05-23
I'm working on it.

---

### Post by billmaxey on 2019-05-23
So, it wrote the usb drive.  I can't convince bios to
 boot from the usb.

---

### Post by Rubi1200 on 2019-05-23
Okay, for that please try one of the first 2 options here:
[https://www.tenforums.com/tutorials/21756-boot-usb-drive-windows-10-pc.html](https://www.tenforums.com/tutorials/21756-boot-usb-drive-windows-10-pc.html)

---

### Post by billmaxey on 2019-05-23
THANK YOU.
I booted Ubuntu from the usb drive... didn't install in on the hard drive.

---

### Post by Rubi1200 on 2019-05-23
First use the Try Ubuntu option and play around with it a bit to see whether you like it, what you can do etc.

Feel free to ask any questions you like, we are happy to try and help.

Good luck!

---

### Post by billmaxey on 2019-05-23
Thanks again.  I'm using it now.

---

### Post by oldrocker99 on 2019-05-24
Every Ubuntu .iso has a SHA256 checksum, and is the way to ascertain that the download is correct. In Windows, Microsoft makes a tool available: [https://www.microsoft.com/en-us/p/hash-tool/9nblggh4rrr2?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/hash-tool/9nblggh4rrr2?activetab=pivot:overviewtab).

The page from which the .iso was downloaded will have a SHA256 checksum for the .iso. Use that tool to compare the checksums. 

Now: To burn an image to a USB, it **MUST** be formatted as FAT only. Otherwise, you will come to grief.

Oops. Hadn't noticed that the USB had already been booted](*,)...

---

