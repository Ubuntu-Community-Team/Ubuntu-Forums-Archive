---
title: "Wubi versus Full Partioned Install"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-11-18
Could someone please explain what the key differences are between the installation of Ubuntu under Windows using qmenu.exe and doing a full installation that involves partitioning drives?

To my simplistic understanding, Windows sits on DOS in the same sort of way that Ubuntu sits on Linux, and applications sit on top of Windows or Ubuntu as appropriate. If that moderately correct, isn't a Wubi install of Ubuntu bypassing Linux? And if so, isn't that going to cramp its style, so to speak?

Let me explain my quandary.

I currently run Windows Vista (Home Premium edition). I need to have Apache Web Server, MySQL and PHP running locally. When it was XP, that was no great problem, but Vista and Apache (in particular) just seem to hate each other.

So, it seemed a good idea to get myself a Linux disro because those 3 apps are ideally suited to it (apparently), and Ubuntu seems to be the Linux flavour of choice at the moment.

However, I have a problem with connectivity. I use Mobile Broadband from Vodafone instead of usual broadband through a landline. Vodafone don't provide any software to connect through Linux other than some pretty ropey Beta versions from their R&D dept.

Not being a devotee of Linux means that I'm testing stuff 'in the dark'. I can't commit to wanting Ubuntu long term, so the option of partitioning my drive really doesn't appeal.

I've been trying for the past few days to install Ubuntu in various ways to an external drive connected through USB, but I've eventually given up on the idea because every time I try to do something Ubuntu throws up errors of one sort or another.

If I install Ubuntu via Wubi and boot Ubuntu, would I still need the Linux version of the Vodafone connection software or could I connect through Windows as normal? To what extent is Ubuntu under Wubi a Linux system and to what extent is it a Windows application?

---

### Post by ad_267 on 2008-11-18
> If I install Ubuntu via Wubi and boot Ubuntu, would I still need the Linux version of the Vodafone connection software or could I connect through Windows as normal? To what extent is Ubuntu under Wubi a Linux system and to what extent is it a Windows application?

Yes you would still need the Linux version of the software. The only way that Wubi is a Windows application is that the complete Ubuntu file system is contained in a file on your Windows partition, and that you can remove it in Windows using Add/Remove applications. In every other way it is a Linux operating system. When you boot into Ubuntu with Wubi Windows doesn't do anything, the Windows boot loader just tells the computer to load Ubuntu.

The Wikipedia page explains how Wubi works: [http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

---

### Post by sportscrazed2 on 2008-11-18
i used to run wubi then i switched to a full install and it seems alot faster

---

### Post by cwsnyder on 2008-11-18
I think what you want to do is install either VMware or VirtualBox under Vista and run your Linux as a virtual machine.  Both the WUBI and standard install will be a direct install on your system hardware and have the same problems that a Live CD would have with your Vodafone connection.  The major difference between the two is that the WUBI edition sits as a virtual file system installed on your Windows NTFS file system, which allows the WUBI system to be removed with the Windows Add/Remove Software.
A full virtual machine install would install on the virtual hardware which you set up, and could use the full Windows driver software to interface with the outside world, but could be set up as a server with port forwarding, etc. just like a separate server iron.

---

### Post by Roger Allott on 2008-11-18
Thanks guys. I think I feel happier now doing the Wubi install knowing that it really is Linux that I'll be running.

Is there anyone here who's familiar with Vodafone's connection software for Ubuntu and what the issues that invariably exist are? And of course, how the heck to overcome them!

---

### Post by GuruX on 2008-11-18
Vodafone has connection software for linux, but I don't know i you really need it. Wvdial might do the job without the Vodafone software. I'm not sure if Vodafone software is maintained properly. Wvdial is.

---

### Post by Orographic on 2008-11-18
I've been using Wubi (Intrepid) for a week or two now on my XP machine and love it so far. I have a dual core 1.8mhz with 2 gig of DDR2 667mhz ram and can't notice a speed drop from a full install. I do have an XP Acronis backup without Wubi though and also a full Intrepid and Hardy imaged to an external drive - just to play with. :-)

---

### Post by Roger Allott on 2008-11-19
> **GuruX said:**
> Vodafone has connection software for linux, but I don't know i you really need it. Wvdial might do the job without the Vodafone software. I'm not sure if Vodafone software is maintained properly. Wvdial is.

This is from [wiki]("http://en.wikipedia.org/wiki/Vodafone_Mobile_Connect_Card_driver_for_Linux"):
> Vodafone Mobile Connect Card Driver for Linux is a graphical frontend to wvdial to ease connecting to GPRS/3G networks and using mobility services (like SMS) through Vodafone Group datacards.

Your concern though about how well maintained and supported Vodafone's software is is highly valid based upon what I've seen of the company over the past 7 months. Just about everything they do is complete and utter bilge. But I've got a 24 month contract with them.

---

