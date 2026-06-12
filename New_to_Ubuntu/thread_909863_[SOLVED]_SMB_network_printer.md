---
title: "[SOLVED] SMB network printer"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Mr.Pickels on 2008-09-03
I have a fresh install of Ubuntu Hardy, its all going really well.
But!  I have a USB Printer (Konica Minolta PagePro 1400w) connected to a "Print Server" for network access.  The server (ioGear 1 USB Port Server) is setup on my workgroup and all the windows PCs can see it, But in Ubuntu from 'new printer' to 'Windows Printing via SAMBA' it does not show up, The server (called 'Prints') on my network is visible in Gnome, but not in the printer setup network browser.  In Gnome I can see the server, but the printer on the server does not show.  I can also set this printer as a share on my Win2k Server in the basement, but I still can only see the server, and not the printer.

I have tried to manually enter the location as both a SMB printer and a IPP printer but I can never get it to connect at all....

On windows PC's this server is happier to run as a network printer (so, ipp i think) with address like [http://192.161.1.108:631/lp1](http://192.161.1.108:631/lp1)
But it will also run as a windows share //[workgroup]/Prints/pagepro

I do not have a driver for this printer, but I do have a PPD, is this my problem?

I have a feeling I have missed some fundamental detail along the way... 

--
Greg

Update: If I connect the printer directly to my Ubuntu Hardy PC it detects and installs and works...  So, this is a network problem

---

### Post by Meson on 2008-09-04
I am having a similar problem.

I have a TRENDnet TRE100-2U1P printserver.  It hosts the printers in a number of ways, I've been trying to connect to them from Ubuntu using Samba and LPP.

The two printers are an HP LaserJet 1020 (usb) and an HP LaserJet 6L (parallel).

I haven't been able to get either to work from the printserver, however when plugged directly into the computer and when plugged into a windows machine and shared, they work fine.

---

### Post by Mr.Pickels on 2008-09-05
FIXED!! 

an update of SAMBA and the client side of samba came though the update manager this morning, and now everything works as it should.

I was able to set up my network printer as an HPjetDirect via its IP address, port 9100, and the LP1 queue.

---

### Post by Meson on 2008-09-05
Interesting.  

What were the packages specifically?  samba and smbclient?  

Which level of repos do you have selected?  backports, proposed, updates, security?

---

### Post by Mr.Pickels on 2008-09-06
I'm not sure specifically what packages updates, is there a way to get a list of newest updates?

as far as I know my repos are Parter, Main, Multiverse,restricted, universe, medibuntu, and security

---

