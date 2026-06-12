---
title: "Disabling file buffer cache"
date: 2007-04-24
forum: Programming Talk
---

### Post by Shopping Skill on 2007-04-24
I've been trying to find a way to disable all caching on certain files without success without any luck. I thought O_DIRECT would work, but even when using that flag on open I still get speeds of over 1000 MB/s. I should be getting somewhere around 20-40 MB/s if I've successfully disabled any caches. Is there a way to do this?

I checked out the code for hdparm thinking that may help, but it's reading straight from the hard drive (opening a  file descriptor to /dev/hda for example instead of opening a file descriptor for a certain file like I'm trying to do.)

Any ideas?

---

