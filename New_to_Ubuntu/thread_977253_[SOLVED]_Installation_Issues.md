---
title: "[SOLVED] Installation Issues"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by alexvision on 2008-11-10
I'm trying to run ubuntu 8.10 on my desktop, as a replacement for XP (s a hand-me-down so I'm not too sure whats in it but It has a pentium4 solo @2.0ghz, about 30gb ide hdd, old nVidia gpu (gforce 4 series or earlier) and an unnamed mobo with half a gig of generic ram.) 

When I put in the installer it loads the first 3 bars and then stops, a friend said that this could be a apic or something like that problem, I also tried installing xubuntu 8.10, ubuntu 8.4 and DSL to no avail. I've tried the cd's on other computers and they have all worked perfectly fine. I'm not sure where to go from here. 

If its a driver issue how do I fix it, any other Ideas or what apic (or something similar) is and how it could help me would be greatly appreciated

Alexvision

---

### Post by bscbrit on 2008-11-10
Does the computer run when using a Live Disk?

---

### Post by alexvision on 2008-11-10
nope, does the same thing in both, just goes up to 3 bars then stops, eventually the cd drive stops as well

---

### Post by bscbrit on 2008-11-10
Did you burn the CD yourself?  I suspect that you have a corruption.

Check the MD5SUM with the appropriate content of this file:

[http://releases.ubuntu.com/releases/intrepid/MD5SUMS](http://releases.ubuntu.com/releases/intrepid/MD5SUMS)

---

### Post by bscbrit on 2008-11-10
Re my last post - I see you have checked the disks in another computer and they seem to work.  Is XP still loaded on the computer (i.e is it a dual boot?)  If so, fire it up in XP and check that it is still running as you expect it to.

Next, download the 'Alternate' disk and try to install from that.  It has a far simpler interface which shouldn't get bogged down with any particular hardware problems.

---

### Post by alexvision on 2008-11-10
downloading the alt cd atm, what is the actual difference between the 2 ??
Oh and what is a program that I can sync my ipod with in ubuntu?

Thanks for you help, I just hope it works

Alexvision

---

### Post by jonofan on 2008-11-10
I use the default program, which is rhythmbox, it's never given me grief, although a lot of people seem to hate it.

---

### Post by alexvision on 2008-11-10
does it support m4a (the iTunes format) ??

---

### Post by bscbrit on 2008-11-10
There is no significant difference between the two with regards to the final installation.  You get exactly the same programs.  It is all to do with the installation process itself.  The Live Disk has to run on your computer with a fairly advanced video display and it expects certain features to be available.  The Alternate ([http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu) - see bottom of the page) make no such assumptions.  It might find the same problem **but** you will be able to see at which stage the problems occur and can then hopefully pin down the specifics.

The installation process under the Alternate is text driven, but still remains a powerful as the same process under the Live Disk.  In fact, you will see all the same questions regarding your requirements and hardware but using a very basic display.  Simply put the disk in the drive and reboot your computer.  However, take things slowly. Read what is on the screen and, if you are unsure, then accept the defaults.  If you are unsure at any point then simply ask for an explanation here.  Nothing is written to the disk until you have told the program how you want to partition your disk (which you can leave to the program to sort out if you prefer).  It will ask you to approve the change to the disk before the partitioning takes place.  Note, that the default selection here is NOT to accept the partitioning (this is, after all, the safest option in that it leaves on data on the disk intact but, of course, it doesn't install anything!).  You will have to click the tab button twice to get to the 'Yes' option.

During the installation, make quick notes as to which questions are asked because, if there is a crash, it will let others know exactly how far the installation got before finding problems.

I hope that helps you to understand the process.  Good Luck, and I will keep watching this thread all day.

---

### Post by alexvision on 2008-11-10
Yay, I found the problem !!!!!!!! 

It doesn't like my network hardware. I'm guessing that this is my wireless dongle, not my modem(correct me if I'm wrong) Ill take it out and try again

---

### Post by bscbrit on 2008-11-10
That sounds like you've found it!

Remove it and try again, but even if it cannot connect to a network it is fine to let the installation program continue.

---

### Post by alexvision on 2008-11-10
Ok, that didn't work, 

I get through the keyboard part fine, but then it does 

detecting hardware to find cd-rom
 scanning cd-rom 
loading additional components 
then gets stuck on detecting network hardware ?????

hmmmm, so its probably the modem(I can't remember if it was on board or not, hmmm) looks like I need to take a look inside. 

Its getting late now, so Ill have a go tomorrow, unless there is a software fix that is quick. 

Thanks for all your help so far. 

Alexvision

---

### Post by bscbrit on 2008-11-10
When it gets to a place where it seems to stick, leave it for at least 3 minutes.  Some of the timeouts in the installation program seem to be excessively long but often the program will recover itself.  If you have had enough for today we can continue tomorrow although I will be busy in the morning - which I assume is your evening.

---

### Post by alexvision on 2008-11-10
I've left it for 2hours previously, so I don't expect anything to happen, as well as the cd drive has gone all quite. Ill leave a message tomorrow late morning your time, on how I went (yay end of exams) and Ill take a look at you suggestions sometime tomorrow 

Thanks a lot for all your help

---

### Post by bscbrit on 2008-11-10
alexvision

I've had a few thoughts while you are probably sleeping.

I've never known an installation fail on discovering a dial-up modem.  That would be most unusual.  But it is stalling around the network configuration stage, and the next stage is ISO-Scan.  The installation process might be stuck configuring your network but it is also possible that the network configuration stage has actually completed and the hang-up is when it looks for an ISO image.  Only you can see your display and decide whether you think the network detection stage is complete.

I know that you have a modem card (unconnected) and you use a wifi dongle (also unconnected).  However, does your mobo have a built-in wired ethernet connection?  If yes, is there anything connected to it?  The installer might simply be stuck waiting for a reply from a NIC that is not connected or is not working correctly.  What does the display actually tell you about what is happening?  Does it say it is searching for a network, trying to configure using DHCP or what?  What does your wifi normally link to?  Do you have your own access point which acts as a modem/router/gateway to your ISP?  Does it also have the capability of taking a wired ethernet connection?

Please also confirm that you are booting from an Ubuntu disk (not an image on your hard-drive) and that it is in a CD/DVD drive and that there are no other CDs located in other drives on your system (i.e. if there are other drives that they are empty). Check that there are no other external hard drives or memory sticks connected via USB.

When your system locks up is there any disk activity?  How do you have to recover the system (press reset, Ctrl-C, disconnect the power?).  Do the keyboard board lights still work (press Num Lock and/or Caps Lock)?  I'm trying to determine if the CPU has actually locked up or whether it is stuck doing something.

Do you have any other distro disks to hand, either earlier Ubuntu (7.10 or 8.04 for example) or even a completely different distro (Fedora, Mandriva) or whatever?  It might be worth trying one of them to see if they get stuck at the same place or whether this is a problem with 8.10 specifically.

I'll be online late tomorrow morning, my time, which hopefully will be after you have had a successful evening!  Good Luck.

---

### Post by alexvision on 2008-11-11
I've got the system up and running now, thank you sooo much bscbrit. It turns out that I had a pci adapter for a wireless receiver with nothing plugged into it.

---

### Post by bscbrit on 2008-11-11
Great news.  Good luck and I'll see you around the forums. :-)

---

### Post by jonofan on 2008-11-17
> **alexvision said:**
> does it support m4a (the iTunes format) ??

Yes this is supported. iPod is plug and play.

---

