---
title: "Installing Vista with Linux already installed"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Vinegarcat on 2008-08-24
I've got a problem where Vista acts up and won't install on the partition I made for it.  I initially have Linux installed, using it right now, and I booted with the LiveCD and shrunk the drive for a nice large Vista chunk.  When I try and install Vista, when I get to the part about which partition to install on, it will not allow me to continue after selecting the new partition.

It seems evident that the other partitions are set up properly as it says "cannot install on a non NTFS partition" just when selecting them (Next button greyed out) but the partition I created has no such message and "Next" highlights right up (I checked in partition manager and it is indeed properly formatted as a NTFS partition).  The problem is when I select that drive and click Next it errors saying something along the lines of "No suitable partition was found".  There's pretty much nothing else that I know of to do at this point.  I Googled a bit but didn't come back with much.  The only thing I found to be quasi-relevant was someone saying Vista might need to have the first partition piece in order displayed (the order is linx -> vista -> linux swap etc...).  Is there anyone who knows what to do from here?  If I have to swap the partitions somehow, can I keep my data and avoid reformatting my linux portion?

P.S. I'm using the partition manager on the LiveCD, all appears to work well.  I've also tried to format the drive under the vista menu itself to no avail as well as defining the "new" partition with vista itself on that same menu with the exact same results.

---

### Post by Sef on 2008-08-24
I know Vista if it is installed first, needs to use its partitioner to shrink its partition.  Likely the same thing is happening here.  I would use Vista's partitioner to reformat the partition that you have set up for it.

---

### Post by zipperback on 2008-08-24
Follow the guide on how to setup your dual boot system.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

There are several how to documents available on that page as well.

- zipperback
:popcorn:

---

### Post by sandysandy on 2008-08-24
post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by sandysandy on 2008-08-24
see this link for installing vista after ubuntu

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

regards

---

### Post by Vinegarcat on 2008-08-24
Ah, I had read that article and that's what I was going off, but I missed the part where it said to do the SHIFT + F10 and console stuff.  I thought that was just fluff if you couldn't do it with the partion manager in ubuntu, but it seems that is just to separate the drive, and not very good at actually installing a partition vista can use.

I gotcha :)

Guess that's what I get for attempting to do this half asleep last night :p

---

