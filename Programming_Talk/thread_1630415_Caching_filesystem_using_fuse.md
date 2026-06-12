---
title: "Caching filesystem using fuse"
date: 2010-11-25
forum: Programming Talk
---

### Post by Fafler on 2010-11-25
I've got a home server with a RAID 5 array. It's mainly used for streaming movies and runs idle the most of the time. I was thinking if it's possible to make a FUSE filesystem, that transparently copies the file from the RAID to a flash drive and streams the data from there, allowing the drives to power down the next hour and a half.

Is this a realistic idea? In Perl? What should i look out for? I haven't really programmed anything like this before. Just small scripts for this and that, but i guess i have to start somewhere.

---

### Post by ssam on 2010-11-25
have a look at
[http://sourceforge.net/apps/mediawiki/fuse/index.php?title=FileSystems](http://sourceforge.net/apps/mediawiki/fuse/index.php?title=FileSystems)
there is one caching fs in there already.

also look at offline fs (ohm fs)
[http://offlinefs.sourceforge.net/wiki/](http://offlinefs.sourceforge.net/wiki/)

and bcache
[http://bcache.evilpiepirate.org/](http://bcache.evilpiepirate.org/)

i am not sure any of them do exactly what you need, but they may get you some of the way.

---

### Post by Fafler on 2010-11-25
mcachefs seems to be pretty much it. Atleast, it's worth trying out.

bcachefs isn't really optimized for what i need. It seems to be more for optimizing random writes and works below the filesystem layer, so i can't make it read ahead large files.

I'm still confused as to what ohm fs actually does. But it might also be useful.

Thanks a lot for your help. Now i can do some testing :-)

---

