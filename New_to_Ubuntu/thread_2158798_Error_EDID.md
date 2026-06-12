---
title: "Error EDID"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by ramarla on 2013-06-30
Hi,

I´m trying to install lubuntu 13.04 but I am having some problems. This is it,

[IMG]http://img15.imageshack.us/img15/3310/7rke.jpg[/IMG]
Any body can help me?

Thanks in advanced and sorry about my english.

---

### Post by ajgreeny on 2013-06-30
It looks as if the iso file you used for the CVD or USB was corrupt, or the disk/USB drive was not burned or written properly.

Go to [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") to get all the info on md5sum values and how to check them. If your iso file does not match exactly you will need to download again, preferably with a torrent client which will check the download as it comes in.

---

### Post by ramarla on 2013-07-01
Thank you very much for your reply.

I tried with two diferents CDs, recordered in two diferents PCs and I have the same error.

---

### Post by squakie on 2013-07-01
Did you check the md5 sums as they mentioned?  Also - if you are actually using a CD that could be a whole lot of problem - the newer versions of Ubuntu have required a DVD disk and drive to create the disk.

Also - I'm assuming that if there was an error in the md5sum that you deleted your download and ran it again as they mentioned.

Be sure you actually burned the ISO as an image to disk - not just copying the file there.

---

### Post by ramarla on 2013-07-01
Yes, I check it and it is ok.
I burned the CD as a ISO image.

Thanks in advanced and sorry about my english.

---

### Post by grahammechanical on 2013-07-01
EDID = Extended Display Identifcation Date. It refers to the various screen resolutions and frequencies that the monitor runs at and it is stored in an intergrated circuit in the monitor. When Ubuntu loads it reads that data to find out the correct resolution and frequecy to run the monitor at. The monitor could be damage if it is run at the incorrect settings.

You can try to get the installation program to run the monitor at a lower but safe settings. I have not done this with Lubuntu but it is the same as Ubuntu I am sure. The colours of the screens will be different.

1) Load the DVD. At the first screen with the two icons (human & keyboard) press Enter.
2) at the next screen select the language and press Enter (English is default)
3) at the third screen (TRY LUBUNTU - INSTALL LUBUNTU) press F6

a menu will appear - look to the bottom right.

4) Select nomodeset and press Enter.
5) Press Esc to get back to the TRY LUBUNTU - INSTALL LUBUNTU screen
6) Select TRY LUBUNTU and press enter.

See what that does.

You may be able to install Lubuntu but you may need to put nomodeset as a boot parameter. But ask for help in how to do that if and when you need to do that.

Regards.

---

### Post by JKyleOKC on 2013-07-01
As grahammechanical has pointed out, the EDID error has to do with your monitor and has nothing at all to do with the CD. If the monitor has been working properly up until now, its internal memory may have been damaged somehow. And many older monitors do not provide the EDID format that modern software expects; I've experienced that myself!

Some older system installation code made allowances for such errors and provided a fallback if one happened; that's how I was able to use my misbehaving monitor. It's possible that newer software versions may have dropped this capability, and simply fail when they do not recognize the EDID (or its checksum fails as shown in your photo). There may be kernel options that can prevent the EDID-reading code from executing, but unless "nomodeset" solves the problem for you I don't have any to suggest...

---

### Post by dannyboy79 on 2013-07-01
hmm, you could try the textual installer version of the iso (i believe it's referred to as the alternate iso). they don't use a GUI at all, rather a ncurses type gui i believe.

---

### Post by ramarla on 2013-07-01
> **grahammechanical said:**
> EDID = Extended Display Identifcation Date. It refers to the various screen resolutions and frequencies that the monitor runs at and it is stored in an intergrated circuit in the monitor. When Ubuntu loads it reads that data to find out the correct resolution and frequecy to run the monitor at. The monitor could be damage if it is run at the incorrect settings.

You can try to get the installation program to run the monitor at a lower but safe settings. I have not done this with Lubuntu but it is the same as Ubuntu I am sure. The colours of the screens will be different.

1) Load the DVD. At the first screen with the two icons (human & keyboard) press Enter.
2) at the next screen select the language and press Enter (English is default)
3) at the third screen (TRY LUBUNTU - INSTALL LUBUNTU) press F6

a menu will appear - look to the bottom right.

4) Select nomodeset and press Enter.
5) Press Esc to get back to the TRY LUBUNTU - INSTALL LUBUNTU screen
6) Select TRY LUBUNTU and press enter.

See what that does.

You may be able to install Lubuntu but you may need to put nomodeset as a boot parameter. But ask for help in how to do that if and when you need to do that.

Regards.


IT WORKS, IT WORKS!!! (sorry caps)
I try it and it works, lubuntu load ok and sistem run fine, it isn't slow.

What must i do to install lubuntu with this option???

Thank you very much for your help.

---

### Post by ramarla on 2013-07-02
> **dannyboy79 said:**
> hmm, you could try the textual installer version of the iso (i believe it's referred to as the alternate iso). they don't use a GUI at all, rather a ncurses type gui i believe.


[COLOR=#333333][FONT=Ubuntu]Alternate ISOs are for low-RAM PCs. Computers with less than 700 MB of RAM are considered low-RAM computers.
My PC has 2037 MB, 133 MHz, DDR2. Is it low-RAM PC???

[/FONT][/COLOR][https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

---

### Post by ramarla on 2013-07-02
> **ramarla said:**
> IT WORKS, IT WORKS!!! (sorry caps)
I try it and it works, lubuntu load ok and sistem run fine, it isn't slow.

What must i do to install lubuntu with this option???

Thank you very much for your help.


I DID IT!!! (sorry caps again)

It was as easy as I can imaginate. The only think I must to do is select install lubuntu instead of try lubuntu.
lubuntu was installed at 800x600 and I try to update graphics drivers but I can change the resolution, how can I do it?

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1)

---

### Post by squakie on 2013-07-03
Geez - sorry I missed the whole edid thing - I guess I just got caught up in the reply about the disk being bad and didn't read the initial post well enough.  Sorry if I caused any confusion here.

---

### Post by ramarla on 2013-07-03
> **squakie said:**
> Geez - sorry I missed the whole edid thing - I guess I just got caught up in the reply about the disk being bad and didn't read the initial post well enough.  Sorry if I caused any confusion here.


No problem, any help is welcome.

---

### Post by ramarla on 2013-07-03
What I would like to do now is to set correctly screen resolution and monitor frequencie, how can I do it?

---

### Post by ramarla on 2013-07-04
grahammechanical, help me!!! Please.

---

### Post by dannyboy79 on 2013-07-05
using the alternate install ISO won't require that an X server be running for the installation which is why I suggested it BUT if you're saying that using the nomodeset option worked for you then you should see on your desktop an icon that says INSTALL LUBUNTU. Just perform the installation, then do make the nomodeset option permanent in your grub boot line you would follow this guide here (the section that says, "How to permanently set kernel boot options on an installed OS": [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ramarla on 2013-07-05
> **dannyboy79 said:**
> using the alternate install ISO won't require that an X server be running for the installation which is why I suggested it BUT if you're saying that using the nomodeset option worked for you then you should see on your desktop an icon that says INSTALL LUBUNTU. Just perform the installation, then do make the nomodeset option permanent in your grub boot line you would follow this guide here (the section that says, "How to permanently set kernel boot options on an installed OS": [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


Thank you very much for your reply.
I finally was able to install lubuntu using nomodeset, what I did was select install lubuntu instead of try lubuntu[COLOR=#000000]. What I would like to do now is to be able to change screen resolution and monitor frequencie because now is 800x600 and I would like to change to 1024x768. I try updating graphics card drivers but it doesn't works.

Sorry about my english.[/COLOR]

---

