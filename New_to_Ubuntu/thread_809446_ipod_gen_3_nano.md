---
title: "ipod gen 3 nano"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by DarinB on 2008-05-27
Does anyone know if the ipod nano gen 3 work in Hardy...
the forums aren't clear or up to date.
some old threads say yes but only from newbies.
any experts have an answer for me, before i buy a $200 coaster????????

---

### Post by wootah on 2008-05-27
Yes, I have successfully used a 3rd gen Nano with Linux using Amarok (and just browsing through the files).

I also successfully bricked the piece of crap after it failed to unmount.

I then successfully unbricked it.

:) Get a normal mp3 player with a non-specialized filesystem and you will be a lot better off.

---

### Post by wolfen69 on 2008-05-27
i wouldnt waste my time with an ipod. they dont care about giving linux users support, so i wont give them my money. save some money and get a non-ipod player. i heard sansa works well in linux. im sure others will chime in with other recommendations.

---

### Post by twright on 2008-05-27
it works in rhythmbox (minus the cover art) or amarok though you would be better off with something supporting ogg

---

### Post by wootah on 2008-05-27
> **wolfen69 said:**
> i wouldnt waste my time with an ipod. they dont care about giving linux users support, so i wont give them my money. save some money and get a non-ipod player. i heard sansa works well in linux. im sure others will chime in with other recommendations.


I like the sansa players! One of my friends has a sansa e250, but it keeps freezing on her to the point where she needs to take out the batteries. She really sucks with electronics though (she keeps dropping them... constantly) so it could very well be her :P

.ogg is a great format! Does anyone know of players that support this?

EDIT: I'm referring to Ogg Vorbis for you semantics punks :lolflag:

---

### Post by DarinB on 2008-05-27
wootah, i have read of many people that the sansa crashes...
what do you mean by bricked???? I know that bricked means essentially blocked by broadband companies, what is it in this case?????

---

### Post by wootah on 2008-05-27
> **DarinB said:**
> wootah, i have read of many people that the sansa crashes...
what do you mean by bricked???? I know that bricked means essentially blocked by broadband companies, what is it in this case?????


In this case, bricked = non-functioning/permanately broken. What actually happended was the ipod would go to turn on, flash bright white, then turn off--repeat. It wouldn't stop doing this. I had to reset it by going in to file mode (holding the centre button plus the bottom button) and then manually fixing the filesystem.

It sucked. But I learned a lot :)

---

### Post by eriqjaffe on 2008-05-27
Just over the weekend, I hooked my iPod up to Ubuntu for the first time, GTKPod had no problem at all transferring files to it.  Pain free.

---

### Post by DarinB on 2008-05-27
resets are common on all versions of ipods but i never heard of manually fixing a file system????

---

### Post by DarinB on 2008-05-27
eriqjaffe was that a nano gen 3 and hardy heron????????

---

### Post by Mortosa on 2008-05-27
I have used Amarok and GTKPod successfully a few times with my Ipod nano

---

### Post by eriqjaffe on 2008-05-27
> **DarinB said:**
> eriqjaffe was that a nano gen 3 and hardy heron????????Yep.

---

### Post by civillian on 2008-05-27
imo, you cant go wrong with an iPod on linux if you use floola, you can copy music, notes, contacts and videos to your ipod and its a free as in beer application. I use my ipod classic with hardy heron. Its also a standalone application so you just need to download it and double click the file!

Its an excellent app and you dont need any setup to get it working with your ipod.

---

### Post by twright on 2008-05-27
> **C!V!NT said:**
> imo, you cant go wrong with an iPod on linux if you use floola, you can copy music, notes, contacts and videos to your ipod and its a free as in beer application. I use my ipod classic with hardy heron. Its also a standalone application so you just need to download it and double click the file!

Its an excellent app and you dont need any setup to get it working with your ipod.
though it seems to crash alot with the nano 3g :(

---

### Post by wootah on 2008-05-28
> **twright said:**
> though it seems to crash alot with the nano 3g :(
I would still say find a different product (personal opinion). Even though the sansa has lockups, there are some firmware updates ([http://www.sebsgarage.com/2006/07/fixing-locked-sandisk-sansa-e250-audio-player](http://www.sebsgarage.com/2006/07/fixing-locked-sandisk-sansa-e250-audio-player)) that appear to be half decent to use. Try to find a player that allows you direct access to its filesystem (ie: is UMS/MSC [USB Mass Storage/Mass Storage Compliant] in otherwords, it acts like a flashdrive) and not MTP (Media Transfer Protocol). 

I remember using one mp3 player that had both modes, but you had to switch it using a Windows program (there is probably some sort of tool to do the same in Linux). Before I did that, there was no easy way to access the filesystem directly (in Windows). You could probably do some mount black magic in Linux though :)

Again, imho, iPods are way over hyped and too many people have them. I would strongly recommend getting another player that is more standards compliant (MSC).

EDIT: Please note that the MTP is Microsoft's invention. From what I have read, it is not that bad of an idea. There is support with Linux through the use of libmtp using MTPFS. The [Media Transfer Protocol Wiki]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol")

---

### Post by twright on 2008-05-28
when i get a new media player it will probably be an iriver or similar (or just an ipod that is old enough to run rockbox)

---

