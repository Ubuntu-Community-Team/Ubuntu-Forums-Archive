---
title: "Recommended NAS?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by dlstrife on 2008-07-01
I'm looking to get a NAS to provide a backup and large storage area that I can access from my laptop and won't have to carry around with me. Can anyone recommend one that works well with Ubuntu, has good transfer times (i.e. can copy a movie in reasonable time or stream it without lag), and isn't bulky?

---

### Post by LowSky on 2008-07-01
Not the answer you might want to hear but, building a file server out of an old desktop might be a better and cheaper option to consider.

Something called unison might help
[http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html]("http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html")

---

### Post by bluepowder7 on 2008-07-01
if you're not gonna move it, what's wrong with bulk?  i was just about to suggest finding an old PC and putting together a file server.  can add hard drives as you need (find a mobo with 2-4 sata ports for future additions).  that's basically what my server is - it's my old desktop mobo with a new big case.  the mobo has pri/sec IDE channels and 4 on-board SATA ports, so i can have 7 storage drives (plus 1 OS drive) just from that.  no raid, just LVM.  my desktop got a new mobo with a new processor.

reduce - reuse - recycle!

---

### Post by Paqman on 2008-07-01
I use a QNAP TS-209.

RAID1 on SATA drives
Built in torrent client (the NAS draws about 13W of power, so it's much more efficient than leaving your PC on overnight to torrent files)
uPnP media server
SSH/Telnet turned on by default

Size-wise I reckon it's pretty compact, and if you turn on smart fan control it's nice and quiet too.

Even though it runs on Linux itself, it's designed for Windows networks and uses Samba. [This thread](http://ubuntuforums.org/showthread.php?t=288534) tells you all you need to do to get your shares mounted in Ubuntu. 

[More info on the manufacturer's website](http://www.qnap.com/pro_detail_feature.asp?p_id=93)

---

### Post by dlstrife on 2008-07-01
I had considered the desktop route, but i travel between school and home a few times a year would like to be able to take it with me, or ship it without too great of cost, so I'd like to keep it small enough to fit in a large suitcase or light enough to ship at low cost.

---

### Post by chrisod on 2008-07-01
I've been using a Storagetech SimpleShare for a couple of years without any major issues.

---

### Post by Paqman on 2008-07-02
> **dlstrife said:**
> I had considered the desktop route, but i travel between school and home a few times a year would like to be able to take it with me, or ship it without too great of cost, so I'd like to keep it small enough to fit in a large suitcase or light enough to ship at low cost.

Looking at my QNAP NAS sitting under the desk, i'd say you'd get it into a large suitcase quite happily. It's about the height of a CD case, an inch wider, and 8 inches deep.

If you were shipping it you'd have taken the disks out anyway, so any NAS is bound to be pretty light. There's no way i'd trust a hard drive to the postal system. They're too delicate.

---

### Post by dlstrife on 2008-07-03
Thanks for the suggestions, I'll look into the QNAP and SimpleShare and let you know how it goes. I'm a compulsive researcher about this stuff so any other suggestions are welcome!

---

