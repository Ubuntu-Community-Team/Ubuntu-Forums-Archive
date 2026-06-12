---
title: "swapfile on separate, slower hd"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by eddski on 2013-04-05
i put together an amd quad core system and wanted to know if it would be beneficial to put the swapfile on a separate slower(sata1) hd and have the primary hd as sata2? not sure if 32bit or 64bit would make a difference, no video editing just burning BRs and regular DVDs.

---

### Post by tgalati4 on 2013-04-05
How much RAM do you have?  How large is your swap file?  In a terminal, post the output of:

```
free
```

I doubt that you would notice the difference.  Once you start swapping, your system will slow down to a crawl, so disk speed gets buried in system and page-handling requests.  Depending on your SATA controller you may or may not see a difference.  If your bluerays are larger than your RAM, then disk speed becomes more important.  64-bit is ~10% faster for certain operations that use large floating point or video/photo/audio editing.  

Only testing would determine the difference with your specific hardware, but building a system twice is probably not worth the effort to find out.

---

### Post by eddski on 2013-04-07
thanks for the reply, I am currently building the system and wanted to try it that way. If I have to rebuild thats fine, its always a learnig process for me anyway. thanks again for the reply

---

### Post by Paqman on 2013-04-07
You may want to [reduce swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") so that swap is used as little as possible. Zero works fine if you're packing enough RAM, in my experience 4GB is more than enough to set swap that low. 

SATA speed makes little difference if you're just using old-fashioned spinning drives. Except for a few very extreme exceptions they're not fast enough to push any kind of SATA bus to its limits. You certainly won't see any difference on normal 7200rpm drives.

---

