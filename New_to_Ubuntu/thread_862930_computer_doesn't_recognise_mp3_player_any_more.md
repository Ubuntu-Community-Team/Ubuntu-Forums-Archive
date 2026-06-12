---
title: "computer doesn't recognise mp3 player any more"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by ritarmh on 2008-07-18
When I plug in a mp3 player to the USB port the computer doesn't recognise it any more.  For a while it did (but I couldn't get music loaded) now the icon doesn't pop up in rhythmbox or MpMan manager (just downloaded). MpMan says "make sure the device is plugged into USB port (when it already is) or try reloading USB module" (I don't know how to do that).  I have ubuntu version 7.10.

---

### Post by Zack McCool on 2008-07-18
Well, let's see the output of

```
 lsusb 
```

Also, before you plug in the device open a terminal and type

```
 tail /var/log/messages -f -n 20 
```

And see if there are any errors when you plug in the device...

---

### Post by SunnyRabbiera on 2008-07-18
Do you safely remove the drive?

---

### Post by ritarmh on 2008-07-18
No, I didn't safely remove the mp3 player.  I didn't push the eject.  I unplugged it. Is it fried?

---

### Post by ritarmh on 2008-07-18
I'm not sure where to type those codes.  How do I open a terminal?

---

### Post by cariboo on 2008-07-18
To open a terminal go to Applications-->Accessories-->Terminal and enter the commands. To make it easier to open a terminal you can right click on the menu command and click Add this launcher to panel.

BTW launcher is the equivalent to shortcut in windows.

Jim

---

### Post by houbysoft.xf.cz on 2008-07-18
Hi, btw, what s your mp3 player? Because if you didn t eject it and it is an iPod for example, it won t work, you must restore it. And do you see your mp3 in the file manager, so is it mounted?

---

### Post by canthus13 on 2008-07-18
You may simply have some kind of wonky usb issues like I do.... I actually added this little script to my bin as I have issues with usb at least once a week.

```
#! /bin/bash
# Fix dead USB ports

sudo modprobe -r -v ehci_hcd && sudo modprobe -v ehci_hcd
```

Try it with the MP3 player unplugged, and then replug it.  If it doesn't work, try again with the player plugged in.  Of course, I may be way off base and it's simply not recognized because of something that happened to the player itself from being unplugged by surprise.

--Me

---

### Post by ritarmh on 2008-07-27
Thank you for your suggestions.  I have checked the USB ports and they work with other devices (the scanner).  The mp3 player is a Curtis and another computer I tried it in recognises it.
I don't see the mp3 player listed in the file manager. Do I need to add it there?  How do I add it to that?

---

### Post by ritarmh on 2008-07-27
> **Zack McCool said:**
> Well, let's see the output of

```
 lsusb 
```

Also, before you plug in the device open a terminal and type

```
 tail /var/log/messages -f -n 20 
```

And see if there are any errors when you plug in the device...

when lsusb typed in:
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 001:  ID 0000:0000    
and when second code typed in:
no such file or directory
comes up

---

### Post by pettertorp on 2008-07-27
I have a similar problem. It tries to open my iPod touch as a camera,

any ideas?

petter@petter-laptop:~$ tail /var/log/messages -f -n 20
Jul 28 00:49:17 petter-laptop kernel: [610652.959491] usb 1-2: configuration #1 chosen from 3 choices
Jul 28 00:49:17 petter-laptop kernel: [610653.201377] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jul 28 00:49:17 petter-laptop kernel: [610653.338234] usb 1-4: configuration #1 chosen from 1 choice
Jul 28 00:49:17 petter-laptop kernel: [610653.392232] scsi12 : SCSI emulation for USB Mass Storage devices
Jul 28 00:49:17 petter-laptop kernel: [610653.407821] usb 4-1: USB disconnect, address 3
Jul 28 00:49:17 petter-laptop kernel: [610653.790885] usb 3-2: USB disconnect, address 3
Jul 28 00:49:18 petter-laptop kernel: [610618.474576] usb 4-1: new full speed USB device using ohci_hcd and address 4
Jul 28 00:49:18 petter-laptop kernel: [610618.712712] usb 4-1: configuration #1 chosen from 1 choice
Jul 28 00:49:22 petter-laptop kernel: [610658.453882] scsi 12:0:0:0: Direct-Access     Maxtor   OneTouch II      023g PQ: 0 ANSI: 4
Jul 28 00:49:22 petter-laptop kernel: [610658.509652] sd 12:0:0:0: [sdd] 586114704 512-byte hardware sectors (300091 MB)
Jul 28 00:49:22 petter-laptop kernel: [610658.564209] sd 12:0:0:0: [sdd] Write Protect is off
Jul 28 00:49:22 petter-laptop kernel: [610658.624459] sd 12:0:0:0: [sdd] 586114704 512-byte hardware sectors (300091 MB)
Jul 28 00:49:22 petter-laptop kernel: [610658.678871] sd 12:0:0:0: [sdd] Write Protect is off
Jul 28 00:49:22 petter-laptop kernel: [610658.678892]  sdd: sdd1
Jul 28 00:49:22 petter-laptop kernel: [610658.696717] sd 12:0:0:0: [sdd] Attached SCSI disk
Jul 28 00:49:22 petter-laptop kernel: [610658.696771] sd 12:0:0:0: Attached scsi generic sg2 type 0
Jul 28 00:49:27 petter-laptop kernel: [610663.952744] printk: 421 messages suppressed.
Jul 28 00:51:02 petter-laptop kernel: [610722.208017] printk: 424 messages suppressed.
Jul 28 00:51:02 petter-laptop kernel: [610722.208028] MD5 Hash NOT expected but found (74.229.245.29, 51697)->(83.143.116.162, 6885)
Jul 28 00:51:39 petter-laptop kernel: [610795.030769] usb 1-2: USB disconnect, address 2

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d49:7110 Maxtor 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
petter@petter-laptop:~$

---

