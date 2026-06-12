---
title: "Is this a virus? Ufraw-batch spawning"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2008-08-16
Sorry about the title, didn't really know how to describe this phenomenon.

I have the ufraw package in my computer, which contains the ufraw gui and the ufraw-batch terminal program. I haven't used both for a long time. For some odd reason, my computer is slowing down and my harddisk is thrashing, with the HDD light constantly on. This is just minutes after booting and barely doing anything.

So I checked with top, and found SEVERAL (almost 10 I think) ufraw-batch processes!!! What the hell is happening?! So my first reaction to regain control was to do a sudo aptitude remove ufraw. Took a while before aptitude was able to remove ufraw, meanwhile there were already 3 or 4 ufraw-batch processes that were started.

Now that I'm back in control, I wanna figure out what the heck was going on. How can I figure out what is starting these ufraw-batch? What would happen if I reinstalled ufraw? And another thing, was there any output to the ufraw-batch rogue processes or did it possibly overwrite any of my existing stuff?

Lots of questions, but I don't know how to get to the answers. Any help would be highly appreciated.

Thanks!

---

### Post by hyper_ch on 2008-08-16
it's not a virus

---

### Post by punong_bisyonaryo on 2008-08-16
> **hyper_ch said:**
> it's not a virus

What is it then?

I know, I know, GNU/Linux supposedly doesn't get any virii, but I can't make heads or tails out of this. This seems like something out of my old Windows days.

---

### Post by punong_bisyonaryo on 2008-08-22
Was just wondering if anybody had any more constructive ideas. Anyone?

---

### Post by forger on 2008-08-22
Well uh.. after 5 days you can't really do anything :)

> The Unidentified Flying Raw (UFRaw) is a utility for converting and
 manipulating raw images from digital cameras.
(Just speculating here)
Hence, you either ran ufraw or gimp-ufraw (a plugin for the GIMP program) and you must've been viewing/converting some photos.
The program or plugin was probably doing some background work while you were shutting down, or simply, it had a bug and it didn't close entirely when you closed the program.

Next time, I suggest doing ```
ps aux
``` which will show you descriptively each process

---

### Post by punong_bisyonaryo on 2008-08-24
Thanks for the tip. I'll keep this in mind, especially since I'm going to reinstall ufraw soon.

---

