---
title: "Installation on a mid-2007 iMac"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by kiusau on 2011-10-31
I have a 24-inch, mid-2007 iMac with 2GB of memory and a 2.4 GHz Intel Core 2 Duo Processor.  I am running in a newly installed MacOS 10.7.2 environment and must decide whether I should partition or set up a virtual machine.

In addition, I have a MacBook and an Airport Extreme that are connected over a closed LAN and am connected to the internet via satellite.  I am using DHCP.  My current connection permits a maximum download speed of 1Mbs and a maximum upload speed of 250Kbs.

I would like to set up webserver that I can test in a virtual environment before exposing to the world WAN.  I have been told that a MAMP set-up is somewhat restrictive, and I do not want to be dependent on changes at Apple Computer for the future success or failure of my website.  I am very familiar with PHP and would like to use this as the language of my webserver.

After reading some of the horror stories about iMac Ubuntu installations and noticing that the documentation for installation is very old, I thought it best to make a query.  Probably the first several questions that need to be answered are:

[LIST=1]
[*]Is this the proper forum for someone interested in Xubuntu?
[*]Once having decided on Xubuntu or Ubuntu should I install on a virtual machine or use a partition?  Which would provide better performance?
[*]Where might I obtain "foolproof" installation instructions and required specifications so that I might avoid most or all of the problems that others have exhibited?
[/LIST]
Can you offer some insight and suggestions?

Roddy

---

### Post by gsmanners on 2011-10-31
I would say go with VM first. You can easily undo that if you don't like it, but undoing a full install on a partition would probably prove to be a lot harder.

I think most of the issues with iMacs is that they're probably trying to get PPC working, and that's been kind of hit or miss. I doubt the x86 has quite as much trouble, although I can't speak from experience.

---

### Post by Lars Noodén on 2011-11-01
> **kiusau said:**
> 
[LIST=1]
[*]Is this the proper forum for someone interested in Xubuntu?
[*]Once having decided on Xubuntu or Ubuntu should I install on a virtual machine or use a partition?  Which would provide better performance?
[*]Where might I obtain "foolproof" installation instructions and required specifications so that I might avoid most or all of the problems that others have exhibited?
[/LIST]



[LIST=1]
[*] Yes.  You can ask about Xubuntu, Kubuntu and Lubuntu here.
[*] I've installed dual boot on a lab of iMacs before and would strongly recommend running natively.
[/list]

3. As far as instructions go, use the OS X installation CD to make a largish partition for use in Linux.  Then boot the Xubuntu installation CD and from there erase that partition and put in the ones you need for Xubuntu.

Once Xubuntu is installed, you'll want to install [rEFIt](http://refit.sourceforge.net/) to be able to choose between OS X and Xubuntu at startup.

---

### Post by kiusau on 2011-11-02
> **Lars Noodén said:**
> Once Xubuntu is installed, you'll want to install [rEFIt]("http://refit.sourceforge.net/") to be able to choose between OS X and Xubuntu at startup.

Do you not acknowledge any of the problems cited with rEFIt and the Lion OS?
Some have suggested waiting until a new version of rEFIt is created.

Roddy

---

### Post by Lars Noodén on 2011-11-02
> **kiusau said:**
> Do you not acknowledge any of the problems cited with rEFIt and the Lion OS?
Some have suggested waiting until a new version of rEFIt is created.



No.  I currently use rEFIt to dual boot Lion and Oneric.  Please post a link to a page describing the problems.  There's nothing about problem on rEFIt's page over on Sourceforge.

---

### Post by kiusau on 2011-11-02
> **Lars Noodén said:**
> No.  I currently use rEFIt to dual boot Lion and Oneric.  Please post a link to a page describing the problems.  There's nothing about problem on rEFIt's page over on Sourceforge.

This is how I discovered the problems; I did a search for the following string of keywords in the Ubuntu Forum: **_iMac_**, **_Partition_**, **_Ubuntu_**, **_Installation._**  I agree that the Sourceforge page says nothing about the problems reported in the aforementioned search.  Then too, does Sourceforge have a strong incentive to report such problems, if they are unique to the Ubuntu OS family?  Would they even know that they existed?

I also looked elsewhere and could not find good confirmation that rEFIt and Xubuntu are compatible on a mid-2007 iMac running MacOS 10.7.2.

Roddy

---

### Post by kiusau on 2011-11-02
> **Lars Noodén said:**
> No.  I currently use rEFIt to dual boot Lion and Oneric.  Please post a link to a page describing the problems.  There's nothing about problem on rEFIt's page over on Sourceforge.

Also, I just found this in the French MacGeneration forum:  "Oui avec bootcamp, tu peux installer Linux au lieu de Windows (pas besoin de rEFIt si tu reste sur du double boot).

In translation:  "You can install Linux in place of Windows using BootCamp provided that you are able to double boot."

I have seen some confirmation of this elsewhere in English, as well.

Roddy

---

### Post by Lars Noodén on 2011-11-02
I've never used Bootcamp.  I have used rEFIt without problems on iMacs, Minis and MacbookPros.

---

### Post by kiusau on 2012-01-28
> **Lars Noodén said:**
> 
[LIST=1]
[*] Yes.  You can ask about Xubuntu, Kubuntu and Lubuntu here.
[*] I've installed dual boot on a lab of iMacs before and would strongly recommend running natively.
[/LIST]

3. As far as instructions go, use the OS X installation CD to make a largish partition for use in Linux.  Then boot the Xubuntu installation CD and from there erase that partition and put in the ones you need for Xubuntu.

Once Xubuntu is installed, you'll want to install [rEFIt]("http://refit.sourceforge.net/") to be able to choose between OS X and Xubuntu at startup.

I have now downloaded the following two ISO disk images and have been able to install neither:

1) xubuntu-11.10-desktop-i386.iso, and
2) ubuntu-11.10-desktop-amd64.iso

The error message is "no mountable file system"

The format for my partition is:  Mac OS Extended (Journaled).

---

### Post by Lars Noodén on 2012-01-29
I had that error, too, and I did not keep notes on how I managed to solve it.  It might have been that I installed 11.04 and then upgraded to get around that error with 11.10.

---

### Post by kiusau on 2012-02-01
> **Lars Noodén said:**
> I had that error, too, and I did not keep notes on how I managed to solve it.  It might have been that I installed 11.04 and then upgraded to get around that error with 11.10.

OK, but instead of downloading 11.04, I downloaded 10.04.2. (I wanted to be certain that it would work.)  When I clicked  on the ISO disk image, I was able to mount the image's contents, view  the folders, and even the files contained therein.  However, I am at a  loss about how to proceed.

1) There is no executable file in the mounted folder that will open in  my MacOS system.  I cannot even get the ReadMe file to open properly.  Using TextEdit will allow me to view the contents of each document, however.

2) If I were to copy the contents of the mounted folder onto my  partition set aside for Xubuntu, it is unlikely once again that anything  would happen, because the partition is formatted the same as that of my  MacOS partition -- namely, MacOS Extended Journaled.

Please advise.

---

