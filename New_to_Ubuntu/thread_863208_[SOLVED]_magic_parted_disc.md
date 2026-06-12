---
title: "[SOLVED] magic parted disc"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by irishy on 2008-07-18
Hello and help please can you point me to instructions to install magic parted disc in hardy heron
thanks

---

### Post by ibutho on 2008-07-18
You don't install Parted Magic to a distro. You need to burn the iso to disc in order to use Parted Magic. If you just want to do disc management stuff in Ubuntu, use gparted.

---

### Post by bhadotia on 2008-07-18
> **irishy said:**
> Hello and help please can you point me to instructions to install magic parted disc in hardy heron
thanks
What is magic parted disc?:confused:

---

### Post by arpanaut on 2008-07-18
^^what he said^^

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Documents](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Documents)

---

### Post by irishy on 2008-07-19
Sorry for being a bit thick I need to know how to use magic parted now I have got it I want to alter partition in dual boot system 
thanks

---

### Post by bumanie on 2008-07-19
You would be much better off using gparted an open source tool designed for the job. Only exception is vista which works better with its own partitioner. > sudo apt-get install gparted then go to System --> Administration --> Partition Editor. Can only work on unmounted partitions.

---

### Post by Elfy on 2008-07-19
> Sorry for being a bit thickno one is thick - just never used soemthing before - there is documentation for the partition editor, looks like gparted - [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

> You would be much better off using gpartedParted magic is a fork of gparted apparently - they call it visparted. I've always assumed it to be opensource - but could be wrong :) I stoppped using gparted earlier in the year - I think I got caught with a dodgy version which wouldn't work even after I let the dog chew it. I think it was unsupported at the time.

I quite like having visparted and testdisk, photorec on the same livecd - and I could never get networking with gparted livecd.

One day I'll sort out how to make my own livecd and add supergrub to the pot and that should be nearly eveything I would use - I think I'll keep dban seperate though.

---

### Post by irishy on 2008-07-19
Thanks for all your advice gparted is already in system tools but so far I have not been able to launch it any ideas

---

### Post by bumanie on 2008-07-19
As I said above, partitions need to be unmounted. May be you should download the live gparted cd, because when the computer boots off that, the partitions are already unmounted.

---

### Post by irishy on 2008-07-19
Thanks are there steps to follow when I reach that stage or do I need to print off some instructions before rebooting

---

### Post by bumanie on 2008-07-19
It's pretty self-explanatory once you get into the gui, but there is some documentation. Start at Number 2 - General information -it's quite straight forward.

---

### Post by Yannick Le Saint kyncani on 2008-07-19
Gparted is available on ubuntu's livecd.

So, download the install/livecd (it's the same), boot it, then look for a partition editor software in a system menu somewhere.

---

### Post by irishy on 2008-07-19
Thank you all very much

---

### Post by bumanie on 2008-07-19
> **Yannick Le Saint kyncani said:**
> Gparted is available on ubuntu's livecd.

So, download the install/livecd (it's the same), boot it, then look for a partition editor software in a system menu somewhere.

That was suggested earlier, but irishy seemed to be having trouble unmounting the partitions he wanted to work on, thus the suggestion to use the live gparted cd, where partitions upon booting off the cd would already be unmounted.

---

### Post by Elfy on 2008-07-19
Maybe swap was in use - thus if it was a guided install so would the extended.

---

### Post by bumanie on 2008-07-19
> **forestpixie said:**
> Maybe swap was in use - thus if it was a guided install so would the extended.

Good point, however, at the end of the day irishy managed to do something he/she had not tried before. Ended up being  a bit of a round about way to go about it, but we were all lacking linux knowledge once upon a time. We all learn differently and obviously the live cd idea was right for irishy - he/she will learn other methods as time goes on.

---

### Post by Elfy on 2008-07-19
Yea too true - I have only just back after a day putting fences up - checked the subscribed threads - answered and then saw it was marked solved :D

I was petrified first time I had to muck about with partitions, luck that it was before I found out about / etc - so I had a bit of partition knowledge befor eI pitched up at the linux door.

Probably irishy has learnt an extremely useful lesson one way or the other - glad (s)he is sorted anyway.

---

