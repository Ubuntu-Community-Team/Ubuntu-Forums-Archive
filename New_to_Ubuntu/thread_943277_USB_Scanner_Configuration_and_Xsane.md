---
title: "USB Scanner Configuration and Xsane"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by captain_buckethead on 2008-10-10
I wanted to get my flatbed scanner working. 
I tried to get xsane to start the sacnner, instead I got the following error:

<code>
Failed to open device:'snapscan:libusb:001:024:' invalid argument.
</code>

I used lsusb to see if Ubuntu could detect the scanner, and this is the output that I got:

<code>
glenn@glenn-dell:~$ lsusb
Bus 
001 Device 024: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U
Bus 001 Device 023: ID 1307:0163  
Bus 001 Device 021: ID 045e:00a4 Microsoft Corp. 
Bus 001 Device 018: ID 05e3:0608 Genesys Logic, Inc. 
Bus 001 Device 020: ID 05e3:0608 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000  
</code>

So as you can see the OS detects the scanner but has not installed it. 
This is where my knowledge ends. I have opened device manager and there is an entry for the scanner. 
I dont know where to take it from here.

Im running Ubuntu 7.04 Feisty on Dell Inspiron 3500 Laptop. 40 Gb HDD, 256Mb Ram.



Thanks all. Glenn.

---

### Post by angelsguitar on 2008-10-10
Here's a link to the Xsane supported scanners list:

[http://www.sane-project.org/sane-backends.html#SCANNERS]("http://www.sane-project.org/sane-backends.html#SCANNERS")

The bad news are that it seems your scanner is not supported, but take a look and see if you can find your scanner model.  Some of them need a firmware to work, which you can get from the manufacturer's website or the install disk that came with your scanner.

---

### Post by robert shearer on 2008-10-10
> Im running Ubuntu 7.04 Feisty on Dell Inspiron 3500 Laptop. 40 Gb HDD, 256Mb Ram.



Glenn, Ubuntu 8.04.1 probably has better hardware recognition and may work with your scanner.
If you have the live Desktop cd why not boot it up and see??
256Mb Ram is a bit light. Ubuntu needs 384Mb to run a  Desktop and 512Mb is really needed for smooth operation.

Waikato linux users group have this to say about your scanner....

[http://www.wlug.org.nz/Benq3300/4300ScannerSetup](http://www.wlug.org.nz/Benq3300/4300ScannerSetup)

---

### Post by captain_buckethead on 2008-10-10
> **robert shearer said:**
> Glenn, Ubuntu 8.04.1 probably has better hardware recognition and may work with your scanner.
If you have the live Desktop cd why not boot it up and see??
256Mb Ram is a bit light. Ubuntu needs 384Mb to run a  Desktop and 512Mb is really needed for smooth operation.
How is Feisty with this?

My dell has, and will only take, a maximum of 256Mb of Ram and has only a 400MHz PII processor, so feisty is about ambitious as I am going to get with this particular computer. There is no back end for this scanner so I think that I am going to have to get one that runs in windows...

---

### Post by robert shearer on 2008-10-10
Wait, see my edit post #3.

Also try these links...seem to have your scanner as supported..

[http://www.buzzard.me.uk/jonathan/scanners-usb.html](http://www.buzzard.me.uk/jonathan/scanners-usb.html)
[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

---

### Post by robert shearer on 2008-10-10
> My dell has, and will only take, a maximum of 256Mb of Ram and has only a 400MHz PII processor, so feisty is about ambitious as I am going to get with this particular computer.

Why not run Xubuntu on this machine and have the up to date Hardy release?
Xubuntu should suit this spec fine.

---

### Post by bayvista on 2008-10-23
My HP 4185 All-in one scanner is not supported by Xsane and does strange things if I try to use it. I have also tried the Scanner Utility under Hardy 8.04 and it does similar things.

Typical problems are:
1. If I scan a 6x4 photo I get an A4 scan and have to crop
2. With Xsane, the Viewer is flaky and freezes requiring a reboot.

Should I buy another scanner or try to scan using Wine?

:confused::confused::confused:

---

### Post by Kellemora on 2008-10-23
Hi CB

We converted our entire office over to Ubuntu and the ONLY BRICK WALL we have faced is that MANUFACTURERS write for the DOZE and could care less about Linux of any flavor.

You can't blame the Linux community for the shortfalls and stumbling blocks put in our path by the manufacturers.  Linux has come a long long way, thanks to Ubuntu in hitting Gates where it hurts!

We have 6 Scanners here, some are hi-end yet Sane supports NONE of them.
Not their fault either really.  Again manufacturers won't supply a backend for the lousy chips they use.

In fact, we have a few HP Scanners, connected to HP Computers of the same vintage and they WILL NOT WORK because HP failed to recognize the flavor of XP they installed on their HP Computers was NOT Compatible with the drivers for their Scanners, and they REFUSE to write scanners, even for the Doze XP family of OS's.........  I wouldn't expect them to write a Linux driver when they don't even support the OS's they install on their own computers.

In order to continue with Ubuntu as our exclusive OS (meaning dumping our last XP machine), we will have to immediately buy at least 4 Epson brand scanners.  Sane seems to support most Epson Scanners, probably because Epson provides them with decent backends to work from.  But I KNOW most of the features of whatever scanner I buy will not be supported UNLESS the manufacturer writes the software packages for those Scanners.

We've already learned (the hard way) that to get the most from Ubuntu, you have to THINK Ubuntu and erase Windoze from your mind.  Nearly everything in Ubuntu is Logical, can't say the same for the Doze though.  Nor most of the software written for the Doze.

When Windoze was only as old as Ubuntu, virtually NOTHING worked on it either!  We found the little Apple's and the Lisa to outperform anything in the Doze and set up our office that way, then moved up to Mac's.  It was a major step DOWN when we HAD to go to PC's to appease our clients.
But for inhouse work we went with Wang and used them for many many years.

I see Linux, thanks to Ubuntu, being the new wave of the future in desktop computing.  The faster Manufacturers realize this, the faster that snowball will plow old Gates under!

Take a look at what Epson scanners are available within your price range, then check the Sane web site for the ones that are Complete and updated.  There are some great rebates on some of the Epson Scanners right now too.

Since the ones I ordered won't be here for a week or more, I can't give a report on their performance yet.  But doing a web search on those models amongst Ubuntu users, the ones I ordered were raved about.  One of the higher end ones was said to work better on Ubuntu than it did on Vista, except for button support.  But one of the respondents to the post said that Epson is working on an both a Red Hat AND an Ubuntu package, unconfirmed.

FWIW:  Our best scanners were manufactured by Musetek and Microtek, neither of which will run on Linux and not supported by Sane.
Our all time WORST scanner was manufactured by HP (well duh!).

TTUL
Gary

---

### Post by robert shearer on 2008-10-23
> Should I buy another scanner or try to scan using Wine?


Well a new scanner will cost you $$$ and trying Wine is free.

If Wine doesn't work then you will only have lost some time and gained some knowledge. :)

Whatever the outcome do post and make it available to others. Thanks.

---

### Post by bayvista on 2008-10-28
Well, I downloaded Wine and followed the install instructions. Then I downloaded 150MB of HP Drivers for my printer (Deskjet F4185)> Wine started to install then crashed. I have written to the HP Linux Forum [https://launchpad.net/hplip](https://launchpad.net/hplip). Also, this site claims that my scanner has Linux support via Hplip which I have.

I may look at Vmware whilst waiting for a reply.

:confused:  :confused:  :confused:

---

### Post by bayvista on 2008-12-13
Purely by chance I found the Xsane doc today and it suggests that you can use it with Gimp. Now I scan pictures directly into Gimp and can crop and edit as required.

The problem I had with Xsane was the Viewer. It would not let me adjust the scan size.

If you haven't seen the Xsane doc, have a look. Just press F1. It's very good.

---

