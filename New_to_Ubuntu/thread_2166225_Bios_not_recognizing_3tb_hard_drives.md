---
title: "Bios not recognizing 3tb hard drives"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by ocdkv on 2013-08-08
Hi there,

First post and total noob to anything linux.

I decided to repurpose my old desktop to a media server and learn a new OS while I was at it.  It was an HP media center m8430f with a Core2Quad Core Q6600 and an IPIBL-LB motherboard running Windows Vista and the latest BIOS Update (v 5.43).  I Purchased 3 x 3TB Seagate NAS HDD (ST3000VN000-1H4167) for storage and 1 x 128Gb Kingston SSD for OS.  I installed Ubuntu 12.04 LTS.  I checked BIOS and found the NAS HDD's were only being recognised as 801Gb.  I've cleared CMOS and spent a couple of hours searching the web for an answer to no avail.  I now turn to you for help & wisdom.

[COLOR=#000000][FONT=HPRegular]Thank you for any assistance you can offer

Kevin


[/FONT][/COLOR]

---

### Post by Boab1993 on 2013-08-08
Hi there ocdkv,

A good visual way to see the state of all partitions on your HDDS is by downloading gparted, its alwatys a useful tool to have.
Just search for it in your ubuntu software center.

You should be able to see where the missing space has gone easily from there

Hope this helps

---

### Post by ocdkv on 2013-08-08
FYI GParted recognizes them correctly as 2.73TB. Now I'm totaly confused.

---

### Post by ocdkv on 2013-08-08
just re-checked bios and still 801GB.

---

### Post by Boab1993 on 2013-08-08
Interdasting,

Do you know what BIOS chipset you have?

If gparted is recognising the full size of the drives, then they should be all accesiable during your logon session and should not cause a problem.

However i understand your concern, if something is not right, it should be fixed

---

### Post by ocdkv on 2013-08-08
I believe its Intel G33 (according to spec sheet)

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01324212#N55](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01324212#N55)

Thank you for your assistance

---

### Post by Boab1993 on 2013-08-08
Thats actually a great help, as it turns out its an outdated BIOS.

Your HDD's are not being recognised as there potential size because the BIOS was never made to do so.

The windows version of the update for your BIOS is here 

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=uk&lc=en&dlc=en&softwareitem=pv-67215-1](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=uk&lc=en&dlc=en&softwareitem=pv-67215-1)

Try running that in windows, then launching ubuntu.

I will post this also on your question about fans as this is also a possible solution for that.

---

### Post by Mark Phelps on 2013-08-08
> **Boab1993 said:**
> Thats actually a great help, as it turns out its an outdated BIOS...

So ... you tell the OP to "update" their "outdated" BIOS from what they have now (5.43) to the "newer" v5.35"?

Also, this so-called update says NOTHING about being modified to read hard drives greater than 2GB.

Updating BIOS is NOT something that should be done arbitrarily, especially if the update says nothing about addressing the problem the OP is experiencing.

---

### Post by ocdkv on 2013-08-10
Ok so I have a theory (semi supported elsewhere, thank you Mark Phelps for giving me another direction to look) that my MoBo being 5 years old simply will not support Hard Drives over 2TB (at least the BIOS will not).  Ubuntu does recognize them for what they are, 3TB, but cannot use them as such and need to be partitioned to 2Tb or less. 

However I had p[COLOR=#000000]urchased 3 x 3TB Seagate NAS HDD (ST3000VN000-1H4167) and 2 out of three were DOA, (BIOS seen them but SeaTools confirmed they're not working right), lots of grinding noises beeping and chatter.  I am therefore replacing them with 2TB drives and crossing my fingers that this will fix this issue. [/COLOR]

[COLOR=#000000]Some have suggested on other forums to replace the MoBo with something newer but that would defeat the purpose of this project and add a huge expense (MoBo + CPU) that neither I or the 'bank', aka the wife, would support. 

I will be keeping this thread alive and will report back when my new drives arrive and I get them up and runnig.  In the meantime if anyone has anything to add please do as I appreciate any and all feedback.

I have posted a question concerning the hard drives I want to puchase so if you have anything to add to that discussion please post it in the following thread: [/COLOR][http://ubuntuforums.org/showthread.php?t=2166614&p=12752004#post12752004](http://ubuntuforums.org/showthread.php?t=2166614&p=12752004#post12752004)

Thank you

Kevin

---

### Post by Linux90s on 2013-08-10
did you use gpt or mbr on the drive as your scheme?

for larger hard drives, the key factors are bios, o.s. and partitioning scheme.

---

