---
title: "Whether OS on RAM is faster than on Hard Disc?"
date: 2008-06-23
forum: Other OS Talk
---

### Post by kagashe on 2008-06-23
The root file system of a Live Distro gets mounted on RAM. If the RAM is insufficient (I think) the balance is put on swap on Hard Disc. If the swap is not present or not accessible the OS may fail to load fully.

I don't know whether the above statement is correct. Please feel free to correct it if necessary.

I have an old Desktop with only 32 MB RAM and it can run Damn Small Linux and some applications on Puppy Linux. Puppy Linux can work on such low RAM because it has a swap of 128 MB.

I tried Slitaz on it but it fails because, although, Slitaz is 25 MB only  the root file sytem is highly compressed (uncompressed is about 80 MB). The swap can't be used unless the root file system is extracted fully.

I have a question here. Puppy with Seamonkey is also 80 MB. Does it mean Puppy uses swap before it loads fully?

Now let us switch to the main topic.

Suppose available RAM is much more than required by the OS. Like I am rubbing Slitaz now on 312 MB RAM. When I click on Firefox icon it opens and runs very fast may be because it starts from RAM. When I am opening one or two (may be more) tabs it is still working in RAM.

When I open Firefox on Ubuntu. It takes time may be because it starts from the hard disc. Another pertinent question is when I am opening tabs is it working in RAM or it is still using the Hard Disc?

kagashe

---

### Post by jrusso2 on 2008-06-23
If you have enough ram and its designed to load the whole OS into ram its very fast.  Damn Small Linux is designed to do this and you can even remove the CD if you have enough ram.

---

### Post by kerry_s on 2008-06-23
> When I open Firefox on Ubuntu. It takes time may be because it starts from the hard disc. Another pertinent question is when I am opening tabs is it working in RAM or it is still using the Hard Disc?

when it's first started it's loading from disk to ram, once running your in ram, but the disk is still used for things like cache, temp files, logs, etc...
it's not built like the mini-distro's so there's a lot more stuff going on.

---

### Post by kagashe on 2008-06-23
> **kerry_s said:**
> when it's first started it's loading from disk to ram, once running your in ram, but the disk is still used for things like cache, temp files, logs, etc...
it's not built like the mini-distro's so there's a lot more stuff going on.Suppose I minimise the "more stuff going on" in Ubuntu. Like I am running IceWM on Hardy command line system and the output of free is as follows:
> $ free -m
Total used free
Mem: 312 148 164
-/+ buffers/cache 32 279
Swap: 996 0 996
Notice only 32 MB buffers is being used to get to IceWM Desktop. I start Firefox, the Mem used increases to over 250 and buffers is say around 50 MB. Now I go on opening 4 or 5 tabs in Firefox. Suppose the web content is well within 312 MB available RAM. Is it similar to running it on mini distros?

If not, what can I do? Change swapiness?

kagashe

---

### Post by kerry_s on 2008-06-23
> **kagashe said:**
> Suppose I minimise the "more stuff going on" in Ubuntu. Like I am running IceWM on Hardy command line system and the output of free is as follows:
Notice only 32 MB buffers is being used to get to IceWM Desktop. I start Firefox, the Mem used increases to over 250 and buffers is say around 50 MB. Now I go on opening 4 or 5 tabs in Firefox. Suppose the web content is well within 312 MB available RAM. Is it similar to running it on mini distros?

If not, what can I do? Change swapiness?

kagashe

that looks good to me, you should be fine, google "lowering firefox memory use", there are a few tips you can use. with 312mb you can run firefox just fine, i only have 256mb and run firefox with several tabs with no problems. the more corners you cut on firefox the slower it will be in other places.

if your just trying to get more speed:
1. change the font, use bitmap fonts, bitmap fonts are faster & use less resources.
i try not to use truetype(ttf) fonts anywhere, a little trick i picked up from win2k.
2. brain freeze, i'll get back to you. :)

---

