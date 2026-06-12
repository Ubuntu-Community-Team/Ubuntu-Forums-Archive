---
title: "read errors from livecd -- cannot install"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by maskiepop on 2008-07-20
Hi guys. 

I am trying to install UBUNTU 8.04.1 on my pc, a compaq presario. The pc is currently running Winxp pro SP2. I have installed an esata drive (300 gig) for ubuntu on this pc. If successfully installed, this will be a dual boot system.

My problem is that the livecd I built comes up with errors; on three files, according to UBUNTU, after I got UBUNTU to check and verify the integrity of the livecd I built. During install, i get a lot of splashfs messages, saying that it can not read a page, or block, or something.

I have checked the md5sums. First, against, the official UBUNTU md5sum and the ISO I downloaded. And then the md5sums of the livecd. Both checks passed. I built the live cd using infrarecorder software as suggested by the ubuntu install docs. 

I have another PC, an HP Pavilion. I tried the livecd on that machine, and ubuntu has no problem reading the livecd from that machine and coming up. I did not install on that machine. I shouldn't. That tells me the livecd was created correctly.

Is there a hardware problem with my dvd/cd writer or reader on the compaq presario? I am not sure, but if it is, how come I can generate md5sums from the livecd that check out with the md5sums I created from the ISO I downloaded, and then unpacked on my hard drive. I did this on winxp pro.

Is this a driver problem? Meaning that Ubuntu's dvd/cd driver may be different from what I am using on my machine. If it is, how do I get around this problem? How do I found out what driver ubuntu is using for my dvd/cd rw.

My dvd/cd writer is a Lightscribe 16xDVD RW. I wrote to a cd-r media, not a cd-rw; I set the write speed to 4 when I built the livecd. At one point, I even set the speed to 2.

I have already built more than half a dozen ubuntu livecds, none of which ubuntu can read on my machine.

Hardware? Driver? Any other possibilities?

---

### Post by stoneybroke on 2008-07-20
Looks like you have done everything right by checking the disk and the download so you might have dirty heads on your cd drive try cleaning them then see what happens. If the cd works ok on the other computer it just might be that.

Hope that helps

---

