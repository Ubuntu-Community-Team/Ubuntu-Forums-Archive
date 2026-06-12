---
title: "Problems installing Ubuntu on a P5Q"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by steve04 on 2008-09-30
I have been trying to install Ubuntu on my computer but when I do live cd or install it goes to BusyBox.  If I go and change the BIOS on my motherboard to recognize my drives as AHCI, I am able to get to Ubuntu and install it.  Unfortunately when I go back to Vista or XP they do not recognize the drives (since they were installed when the BIOS recognized my drives as SATA).  I have heard you can go install AHCI drives in windows but I havent found good instructions on how to do this if your triple booting (so I can fix it in both vista and XP).  I have an ASUS
P5Q-Pro motherboard if this is any help.  Thanks in advance!

---

### Post by steve04 on 2008-09-30
Anyone?

---

### Post by redbytex on 2008-10-01
Had the same problem.
Before booting, enter BIOS and change the drive type from IDE to RAID.

Took me hours to the find the solution, but that's it. IDE is the default option for this mobo, which ubuntu doesn't support, so you have to change it.
Let me know if this fixes the problem.

---

### Post by philinux on 2008-10-01
Ubuntu does support ide as Hardy is currently running on my old pentium 3 500Mhz pc at my girlfriends, and has been doing so since Feisty.

That pc was bought in 1999.

Maybe it's a quirky mobo.

However i would try RAID as it enables AHCI

---

### Post by Cew27 on 2008-10-02
i tried this, i get please install proper boot device (or something along those lines) when using raid

---

### Post by PereQuim on 2008-10-02
Hi,

I'm in the same trouble. I have bought two new machines and I need to run Windows (XP preferibely, Vista if there is no other option) and Ubuntu over them. 

Right now I could install and boot both of them, but I need to change the BIOS setup to access them (from AHCI to IDE or viceversa). Moreover, on Ubuntu, the network is not working (Marvel Technology LTD).

The equipement is as follows:

MotherBoard: Asus P5Q Deluxe
Graphic Card: Nvidia GeForce EN8800 GT 512MB GDDR3 PCI-E
CPU: Intel Core2 DUO Q9450
RAM: 2x 2GB DDR2 800MHz CL5 Knigston
Hard Disk: 500GB 32MB SATAII Seagate

There is no problem in doing a full reinstallation of both OS if that will solve the problems.

Thanks in advance for you help!

:popcorn:

---

### Post by redbytex on 2008-10-02
I'm sorry to hear that that did not solve the problem.
There's a 24-page thread that discusses this problem with various solutions here:
[http://ubuntuforums.org/showthread.php?t=765195]("http://ubuntuforums.org/showthread.php?t=765195")

Another solution for you to try:
[http://ubuntuforums.org/showthread.php?p=5893990#post5893990]("http://ubuntuforums.org/showthread.php?p=5893990#post5893990")

As for the Network issue, read post #7 of this thread:
[http://ubuntuforums.org/showthread.php?t=770173]("http://ubuntuforums.org/showthread.php?t=770173")
Just follow the instructions and it should work straight away, at least it did for me.

Hopefully that helps. Let me know how you go.

---

### Post by PereQuim on 2008-10-07
Hi,

I just finally found the point in the dual booting: I just install the drivers for massive storage devices of Intel in the XP.

I still have some troubles with the network. Mine is a Marvel Yukon 88E8001/8003/8010 PCI Gigabit Ethernet. If some one can give me a clue about it, it would be great.

Thanks in advance!

---

