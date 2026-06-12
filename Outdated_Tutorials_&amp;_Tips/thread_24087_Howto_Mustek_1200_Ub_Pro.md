---
title: "Howto: Mustek 1200 Ub Pro"
date: 2005-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by teumima on 2005-04-05
Ok I've been struggling for a while with getting my Mustek 1200 UB PRO scanner to work with Linux. Everywhere I looked there were shouts of of it being incompatible.

Well I cam across this forum and I'll share with you what I did and then it should work for you, as it did for me.

You  need xsane. Now Hoary comes with xsane. 

Applications > Graphics > XSane Image scanning program

Most probably when you start it you get an error message:

error "coundnt open /dev/scanner0 invalid argument"

Ok grab your Mustek's CD. Put it in the drive. Browse the CD, go to the WinXP folder. Find the file: SBfw.usb 

Drag it to your desktop

Now lets go into command:

sudo mv /home/<your-user-name>/Desktop/SBfw.usb /usr/share/sane/gt68xx/

e.g. sudo mv /home/eric/Desktop/SBfw.usb /usr/share/sane/gtk68xx/

Now type: xsane

It should give you an the same "/dev/scanner0/ invalid argument" 
Look at the processes it did it should look something like this:

amichai@bzq-179-124-6:/usr/share/sane/gt68xx$ xsane
/home/amichai/.themes/Whiteplate/gtk-2.0/icons/iconrc:75: Unable to locate image  file in pixmap_path: "panel-utility.png"
/home/amichai/.themes/Whiteplate/gtk-2.0/icons/iconrc:76: Unable to locate 
image  file in pixmap_path: "panel-searchtool.png"

[color=black]NOTE ---->[/color][gt68xx] Couldn't open firmware file (neither `/usr/share/sane/gt68xx/PS1fw.usb'  nor `/usr/share/sane/gt68xx/ps1fw.usb'): No such file or directory
amichai@bzq-179-124-6:/usr/share/sane/gt68xx$ sudo nautilus

xsane is trying to to open the wrong filename. To solve this go to:

/usr/share/sane/gtk68xx/ and change the name of SBfw.usb to PS1fw.usb

If your not familiar with shell so much, just type sudo nautilus and navigate to the folder then right click on it and rename it.

Now when you type xsane or choose it form the menu it should start right up. You'll even seen a nice little green MUSTEK at the bottom left.

Scans in gray and colour.

Let me know if you're having any probs.

Hope it works for you like it did for me.


a.t.

---

### Post by burntwater on 2005-04-25
Hi

Xsane complained that it did not find ps1fw.usb so I downloaded it from the gt68xx backend website, copied it to /usr/share/sane/gt68xx/ and started xsane without a hitch.

When I try to acquire a preview scan I get the following error message after a pause:
"Failed to start scanner: Device busy"
If I then try to acquire the preview again, it immediately gives me:
"Failed to start scanner: Invalid argument"
The same errors occur in the same way for normal scanning.

Information:
Scanner: ScanMagic 1200 UB Plus
uname -r: 2.6.10-5-amd64-k8 (hoary)

Any information much appreciated

---

### Post by teumima on 2005-04-28
[QUOTE=burntwater]Hi

Xsane complained that it did not find ps1fw.usb so I downloaded it from the gt68xx backend website, copied it to /usr/share/sane/gt68xx/ and started xsane without a hitch.

When I try to acquire a preview scan I get the following error message after a pause:
"Failed to start scanner: Device busy"
If I then try to acquire the preview again, it immediately gives me:
"Failed to start scanner: Invalid argument"
The same errors occur in the same way for normal scanning.

Information:
Scanner: ScanMagic 1200 UB Plus
uname -r: 2.6.10-5-amd64-k8 (hoary)

Any information much appreciated[/QUOTE]
 hey bru

i never saw ur message.
u stil having the issue?

---

### Post by mflash on 2005-04-28
I've got a Mustek 1200 UB Plus (don't know if it's the same as the Pro ?) and managed to make it work by doing the following:

1. Open the file /etc/sane.d/gt68xx.conf

2. Change the line

```

#override "mustek-scanexpress-1200-ub-plus"

```
to:
```

override "mustek-scanexpress-1200-ub-plus"

```
Now the scanner is correctly recognized as a 1200 UB Plus and xsane also looks for the correct firmware (sbfw.usb, which must be in /usr/share/sane/gt68xx)

---

### Post by Fyrzen on 2005-08-28
I have the Mustek 1200 UB Plus, but the cd doesn't come with XP drivers eventhough the box advertises "Support for All-new Windows XP". There's folders win98 and win2k, 2k drivers worked on XP, but there are no .usb files on the cd, just SBusd.dll and .inf files.

Anyway i got an sbfw.usb file from the backend website as **burntwater** did(thanks for the tip  :smile: ) and uncommented all the override "mustek scanexpress... in the gt68xx.conf. Xsane worked fine at first, but soon i got the same "Failed to start scanner: Invalid argument" error.

I might as well have read the xsane documentation, that's not a bug. :) I remembered I'd closed the preview window(press Ctrl+1 or go to Windows>Show preview), seems the program requires you to specify and area in the preview windows, before it'll scan anything. Scanner works great on all modes now!(haven't tryed mentioned bug with 12bit 150dpi tho)

Thanks for the great HOWTO! :grin:

---

### Post by menaar on 2006-06-30
[QUOTE=mflash]I've got a Mustek 1200 UB Plus (don't know if it's the same as the Pro ?) and managed to make it work by doing the following:

1. Open the file /etc/sane.d/gt68xx.conf

2. Change the line

```

#override "mustek-scanexpress-1200-ub-plus"

```
to:
```

override "mustek-scanexpress-1200-ub-plus"

```
Now the scanner is correctly recognized as a 1200 UB Plus and xsane also looks for the correct firmware (sbfw.usb, which must be in /usr/share/sane/gt68xx)[/QUOTE]

Thnks.
This worked for me.
I had installed the driver for breezy, but apparently, with the upgrade to dapper, there was a bearpaw mustek driver made to be the default.

---

### Post by apuicewing on 2006-09-10
Thanks teumima!! I have a Mustek 1248UB and I just copied the .usb file to the destination you mentioned.. And it worked!!! There was no need to do anything else!!  Thank you very much.

---

### Post by AlphaBeta on 2006-10-05
Guys I am new to Ubuntu and I'm having this problem:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I did all the steps...Where did it go wrong?

I am using Dapper Drake.

Thank you!

---

### Post by melon2006 on 2006-12-08
Mustek 1248UB
I confirm that copying SBSfw.usb from Windows driver disk to /usr/share/sane/gt68xx/ makes xsane works. (Ubuntu Edgy Eft 64-bit)
:cool:

---

### Post by melon2006 on 2007-05-25
After upgrade to Feisty Fawn (64-bit) copying files from driver CD still works (for me). 
There is one important thing to remember: **change permissions** for files from windows drivers.
```
sudo chmod a+r /usr/share/sane/gt68xx/SBSfw.usb
```allows any user to use the scanner.

---

### Post by sdowney717 on 2007-06-01
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

this is how I got a Mustek Bearpaw 1200 CU Plus going.

I was wondering, should the quality of the scan be the exact same between linux and xp?

---

### Post by marcmoe on 2008-09-29
Worked for me as posted... thx a lot

ps. i didn't found the proper driver on cd, instade i used 

[http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/sbfw.usb]("http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/sbfw.usb")

and changed the name to PS1fw.usb.
Works fine for me with sane and Mustek 1200 UB Plus...

just rename and move the file 

sudo mv /home/<your-user-name>/Desktop/sbfw.usb /usr/share/sane/gt68xx/PS1fw.usb


enjoy ...

thx

---

### Post by zivley on 2008-11-19
Thanks, I've got my scanner working on Intrepid thanks to your howto, even it was written 3 years ago!

Teumima, ata totach!!! Toda Raba!

---

### Post by Oliverkat on 2009-02-08
Thanks for pointing me to the gt68xx website. My 2400TA Plus works perfectly now

---

### Post by ProxUbunNewbie on 2010-03-04
Hello.
I have Mustek 1248ub.

I had get problem in step:
sudo mv /home/bla2/bla2/bla2 /usr/share/sane/gt68xx/
Now type: xsane
dls003:~$ xsane
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

error: Failed to open device 'gt68xx:libusb:005:002': Invalid argument.

dls003:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `gt68xx:libusb:005:007' is a Mustek ScanExpress 1248 UB flatbed scanner

What's wrong?

---

### Post by ProxUbunNewbie on 2010-03-04
> **ProxUbunNewbie said:**
> Hello.
I have Mustek 1248ub.

I had get problem in step:
sudo mv /home/bla2/bla2/bla2 /usr/share/sane/gt68xx/
Now type: xsane
dls003:~$ xsane
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

error: Failed to open device 'gt68xx:libusb:005:002': Invalid argument.

dls003:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `gt68xx:libusb:005:007' is a Mustek ScanExpress 1248 UB flatbed scanner

What's wrong?

sorry =) I apologize for the inconvenience.
I solved the problem.
I has bad SBSfw.usb; just downloaded new one. =)

---

### Post by neilblue on 2010-05-10
Hello,
I have a Mustek A3 1200 pro on 10.04 and I have tried following these instructions, but when running xsane I only see a message saying 

scanning for devices

then

no devices available.

Am I missing something?

Thanks
Neil

---

### Post by zivley on 2010-05-11
> **neilblue said:**
> Hello,
I have a Mustek A3 1200 pro on 10.04 and I have tried following these instructions, but when running xsane I only see a message saying 

scanning for devices

then

no devices available.

Am I missing something?

Thanks
Neil

Yes, you're missing the main point, this thread was first posted on April 5th, 2005, that's 5 years ago, though it helped me to make my scanner work on intrepid, it may still be too outdated for lucid, you need to take this in consideration and try to find some more specific howto for lucid, a lot has been changed in lucid since then...
In my experience, most stuff I had to struggle with in the past work just out of the box in lucid, but I didn't try the scanner on it yet...

---

