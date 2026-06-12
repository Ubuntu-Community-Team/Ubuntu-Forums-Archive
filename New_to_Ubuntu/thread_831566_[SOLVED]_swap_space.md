---
title: "[SOLVED] swap space"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-16
what exactly is swap space? at [this site]("http://people.debian.org/~psg/ddg/node81.html") i deduce that i need 3gigs of swap to complement my one gig of RAM nicely. but what exactly is it? a slower version of virtual ram? how slow; as opposed to ddr2, like pc100, or a sort of gddr(1)? is a 3:1 ratio of swap:ram correct? what exactly?

---

### Post by st33med on 2008-06-16
Swap space is more room for your apps to stretch out their megabytes and use your hard disk as memory if the RAM becomes too full. Usually, it starts to be used when half of your RAM is used. If you did not have swap space and your memory becomes full, it would start 'thrashing'; the programs running wait their turn for a very long time and the programs that want to unload, or cache, their program to memory would have to wait or read directly from the slower hard drive. The hard drive is slower than RAM, thus, swap is used only when necessary.

---

### Post by rraj.be on 2008-06-16
Swap is something like pagefile.sys in windows..

You just need 1.5 X of your RAM as your swap and according to me

just 1.5 GiB of Swap is more than enough.

---

### Post by Zopiac on 2008-06-16
so...is 7.45gigs too much? lol

---

### Post by st33med on 2008-06-16
> **Zopiac said:**
> so...is 7.45gigs too much? lol

LOL yes!!! About one or two gigs should do fine.

---

### Post by dfreer on 2008-06-17
It's a bit tough to figure out how much swap space you need, if any. 3:1 sounds a bit excessive to me, I'd suggest 1.5:1 (so 1500 MBs of swap for your 1 GB of RAM). If you don't plan on using the hibernate/suspend feature, than you would probably be just fine with 0.5:1 (500 MBs of swap)

[http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29](http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29)

EDIT: Basically, the more RAM you have installed, the less swap you will need.

---

### Post by Zopiac on 2008-06-17
> **dfreer said:**
> It's a bit tough to figure out how much swap space you need, if any. 3:1 sounds a bit excessive to me, I'd suggest 1.5:1 (so 1500 MBs of swap for your 1 GB of RAM). If you don't plan on using the hibernate/suspend feature, than you would probably be just fine with 0.5:1 (500 MBs of swap)

[http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29](http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29)

EDIT: Basically, the more RAM you have installed, the less swap you will need.

hmm...really.  i thought, basically, the more the merrier. so i put in 7.45gigs, bringing my hd space to a nice 145gigs, so ill just bump it to 150/2.45 gigs, that should suffice; i doubt it could hurt too much to have more than your reccomendation, yet less than the other i found. plus, now i know that once i upgrade to 8gigs RAM i ddont need to have 24gigs of swap XP

---

### Post by Gone fishing on 2008-06-17
I seem to remember reading somewhere you need twice the RAM but not more than 500 Meg. On my Hardy (Home) machine I've got 2 Gig of RAM and the same Swap but I've never seen more than 128K being used.

on a SUSE server I'm running which has a similar spec, but running Postfix, Squid and Samba for about 50 PCs I've not seen it use more than 250K and both have usually all there swap free.

---

### Post by markbuntu on 2008-06-17
If you are a heavy graphics user then more swap is a must. Programs like gimp and blender and inkscape need a lot of ram to work at thier optimum when holding many undos for large files and other operations like rendering movies etc.

They will slow way down and may crash if they run out of ram and swap and the os is pushing them back into the filesystem.

---

