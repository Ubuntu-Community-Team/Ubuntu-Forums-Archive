---
title: "Printer not detected (missing USB-to-parallel cable driver?)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by rrcs on 2008-05-26
Edit Sunday Sept 7th 1008:

I am trying to install a HP Deskjet 930C via a USB-to-parallel cable. The printer is not automatically detected when connected. I have tried "Add Printer" in Printer configuration, but I don't seem to get any usable options, cf. [screenshot]("http://img.photobucket.com/albums/v322/skufster/Screenshot-NewPrinter.png").

According to the [Ubuntu documentation]("https://help.ubuntu.com/8.04/printing/C/printing.html#local"), "If your printer was not automatically detected, you can try to select the port and printer driver manually" - how do I do this?

In Vista I finally got the printer working by selecting:

Printers > Add printer > Add local printer > Choose a printer port > Choose an existing printer port > USB001 (virtual printer port for USB) - and then choosing the model of my printer.

Surely there is a similar way of doing it in Ubuntu - telling Ubuntu that although it can't see it, just *pretend* there's a HP printer connected to this port.

_ _ _ _ _ _ _ _ _ _

Original entry:


Hello.

I am using Ubuntu 8.04 on a Medion Notebook.

I am trying to install my HP Deskjet 930c. According to [this]("https://help.ubuntu.com/8.04/printing/C/printing.html"), the printer is supported, so I assume/wonder if the problem is not the printer, but the cable - i.e. missing driver for the cable:

I bought a USB-to-parallel printer cable, and it came with a small cd with the driver, system requirements being Windows 95 - XP.

If it seems likely that the missing cable driver is the problem, will I be able to use the driver on the cd, or will it not work in Ubuntu? So sorry if this should be self-evident.

If I am able to use the driver on the cd, how do I go about installing it? (I am very new to Ubuntu/Linux, and have only installed packages via Synaptic).

Thank you in advance.

---

### Post by oldos2er on 2008-05-26
You shouldn't need any "cable drivers." Do you have CUPS installed?

---

### Post by rrcs on 2008-05-26
According to Add/Remove Applications, I have:

- Manage Print Jobs | Printer configuration GUI | A CUPS printer configuration tool and status applet.
- Printing | Printer configuration GUI | A CUPS printer configuration tool and status applet.

Synaptic shows several packages installed when searching for "CUPS" - will a list of them be helpful/needed?

---

### Post by oldos2er on 2008-05-26
What exactly isn't working for you? I have an older HP laserjet connected via a parallel-to-USB cable; all I did to install it was go to System, Admin, Printing.

---

### Post by rrcs on 2008-05-26
I used [this]("https://help.ubuntu.com/8.04/printing/C/printing.html#local") tutorial earlier:

Plugging it in and powering it in seems to have no effect.

Tried steps 1-5; not seeing the printer detected.

As HardwareSupportComponentsPrintersHp (linked above) listed HP DeskJet 930C as supported, I didn't know where to go from there, and thought maybe it was the cable.

I can't find the hpdj driver (listed in HardwareSupportComponentsPrintersHp) via Synaptic - I seem to have the hpijs driver recommended [here]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_930C"), though not "hpijs-ppds" according to Synaptic.

---

### Post by rrcs on 2008-05-29
Trying to manually add the printer via System > Administration > Printer > New Printer gets me this window: [http://img.photobucket.com/albums/v322/skufster/Screenshot-NewPrinter.png](http://img.photobucket.com/albums/v322/skufster/Screenshot-NewPrinter.png) - I understand that as my printer not having been detected?

I tried logging into my Vista partition, and Vista seemed to recognize something was connected (installing software, it said), but doesn't recognize the printer being connected.

Not knowing what's going on, I'm still wondering if it isn't a problem with the cable. Possibly it's not working (I got it online, so that's always an option&#8230;), or I need a driver??

I'm including screenshots of the two folders on the drivers cd that came with the cable, in case they tell anyone anything: [http://img.photobucket.com/albums/v322/skufster/drivers_folder1.png](http://img.photobucket.com/albums/v322/skufster/drivers_folder1.png) and [http://img.photobucket.com/albums/v322/skufster/drivers_folder2.png](http://img.photobucket.com/albums/v322/skufster/drivers_folder2.png)

Hope one of you has any information - even if it's just that the cable isn't working :(

ETA: Right, so the cd contains drivers for many different kinds of cables - my cable is called BF-1284, and the cd contains drivers for Win98 and WinME only.

I mailed the manufacturer (Bafo Technologies) to ask about the cable working in Windows Vista/Ubuntu Linux.

---

### Post by rrcs on 2008-09-07
According to the [Ubuntu documentation]("https://help.ubuntu.com/8.04/printing/C/printing.html#local"), "If your printer was not automatically detected, you can try to select the port and printer driver manually" - how do I do this?

In Vista I finally got the printer working by selecting:

Printers > Add printer > Add local printer > Choose a printer port > Choose an existing printer port > USB001 (virtual printer port for USB) - and then choosing the model of my printer.

Surely there is a similar way of doing it in Ubuntu - telling Ubuntu that although it can't see it, just *pretend* there's a HP printer connected to this port.

---

### Post by rrcs on 2008-09-15
Bump :/

---

### Post by rybec on 2008-11-01
Ok, so here is what I am seeing.  It appears Linux (Kubuntu 7.10 on my laptop, and Debian 4.0 on my desktop) cannot see *through* the adapter.  

The output from 'lsusb' gives me this line, **Bus 002 Device 004: ID 05ad:07d0 Y.C. Cable U.S.A., Inc**, when the adapter is plugged in, and not when it isn't.

This leads me to believe that the problem is that Linux can see the adapter, but cannot see *through* it.  Technically, it should treat it (the adapter) the same way it does an internal parallel card (ie, 'mounting' a device as /dev/lp? for it).  Evidently it does not.  There must be some way to trick Linux into thinking /dev/lp0, or something similar, is on the other side of that adapter (this is equivalent to making a virtual printer port point to it in Windows).

So my question is this:  Isn't there anyone out there who knows *how* to do this?  And if there is, please enlighten us.  I've been researching this all day and so far, this is the only coherent post I have found (anywhere) that looks like it might go somewhere.

Thanks in advance.  I will keep looking, and post the solution, if I can find one.

Lord Rybec

---

### Post by Riffer on 2008-11-01
Ok I'm going to ask a dumb question.  Your cable is it connected to your printer by the usb connector, and to your computer by the parallel connector?  If it is then the port you would select would be LPT1.

---

### Post by rrcs on 2008-11-04
> **rybec said:**
> It appears Linux (Kubuntu 7.10 on my laptop, and Debian 4.0 on my desktop) cannot see *through* the adapter.
Yes, that's the impression, I get, too - please do come back and post if you find a solution :) !

@Riffer: For me, other way around: usb in laptop, parallel in printer.

---

### Post by jlopez67 on 2008-12-08
Thank you for this thread - I am no able to print to my 930c printer.
It appeared to detect it automatically and would print sometimes, but not always. After using the New Printer setup it is working fine now :D

---

### Post by Xelort on 2009-08-11
Dude, try putting this URI when asked on the "add printer" wizard:

parallel:/dev/usb/lp0

Worked like a charm for my HP Deskjet 720C with a BF-1284 connected on a frontal usb.

Didn't found this answer anywhere else; had to figure it by myself by trying like a madman. 

If it doesn't works, go to your /dev/usb directory, and check out your USB device names there. Whatever the name, the trick is to use the "parallel:/" protocol for the URI, and not "usb:/".
That is, "parallel:/[your usb printer device name path]".

Good luck.

---

### Post by the red krawler on 2009-11-11
> **Xelort said:**
> Dude, try putting this URI when asked on the "add printer" wizard:

parallel:/dev/usb/lp0


Sir, you are a genius. I even dug up my old Ubuntu forums login to make sure someone told you ;)

I wasted many hours trying to get an old NEC Pinwriter 3200 installed under Karmic via a parallel -> USB adapter cable. 

This solution should be documented elsewhere to make it easier to find. Its the perfect solution! 

Speaking of solutions, heres another.... An NEC Pinwriter 3200 works perfectly when installing it under CUPS as an NEC Pinwriter P70, then connecting to it from Windows XP boxes and using the Windows XP supplied "NEC Pinwriter 3200" drivers.

My Windows XP virtualbox (under Karmic Koala Ubuntu) is now quite happily acting as a glorified fax machine and terminal server for 3 people (via the registry modification and termsrv.dll replacement) to work on MYOB remotely, and print to the old NEC dot matrix which they can then monitor remotely via a webcam mounted above it :) And I can login via freenx to use a GNOME desktop to fix things when they go wrong. And reboot Windows when it crashes without losing all the samba shares and rsync backup routines.

I love you, linux.

---

