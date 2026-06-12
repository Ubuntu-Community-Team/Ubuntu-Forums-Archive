---
title: "annoying issue: vanishing sound"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by pablolie on 2008-10-05
i have noticed, ever since installing 8.04 on my Shuttle XPC, that some programs will lose their ability to play sound after a while. VLC Media Player or Mplayer, for example. Another application, called SoftSqueeze, will report it didn't find a sound card. Sounds like driver trouble. The Shuttle XPC's south bridge implements 8-channel HD audio via ICH9DH and Realtek ALC888D codec. Under system/preferences/sound, things seem to be OK, I use the ALSA driver and the system plays a sound. Also under system/admin/hardwaretest, a sound is correctly played. Hm.

If I restart the system, those programs will play sound ok for a while. After a while it'll stop (but the system tests above will still work). Restarting fixes everything, for a while.

Any thoughts?

---

### Post by lukjad on 2008-10-05
Same here. I have asked and as far as I have seen, for my computer it just is a problem with my computer not liking my hardware. What type of computer do you have and how old is it? Mine is about ten years old.

---

### Post by panhandle on 2008-10-05
Try using 

```
top
```

to alter the priority of your PID. Use the -r (or renice) option once in the program to change priority.

Check the man pages on both top and renice before using (if you haven't already done this:).

---

### Post by pablolie on 2008-10-05
> **lukjad007 said:**
> Same here. I have asked and as far as I have seen, for my computer it just is a problem with my computer not liking my hardware. What type of computer do you have and how old is it? Mine is about ten years old.

my computer is not even a year old, it is a shuttle xpc:

PROCESSOR Intel® Core™ 2 Duo E8400
                + 800/1066/1333 MHz FSB
                + LGA775 package

CHIPSET         + North Bridge Intel® G33 
                + South Bridge Intel® ICH9DH

MEMORY          + 2GB DDR2

GRAPHICS        + Build-in Intel® G33 Express Chipset
                + Intel® Graphics Media Accelerator GMA3100 

AUDIO           + Realtek ALC888S (embedded in Intel SB)
              
the system runs like a rock for most things - i use it as a server for everything from media streaming to other PCs and devices, and as a file server. but its own multimedia capabilities are marred by the audio issue.

---

### Post by markbuntu on 2008-10-05
read the very first sections and then start at the Multiple Application Sound Sharing section here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by lukjad on 2008-10-05
Thanks for the link since I can't thank the post.

---

### Post by pablolie on 2008-10-05
> **markbuntu said:**
> read the very first sections and then start at the Multiple Application Sound Sharing section here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

thanks a lot for the pointer! i have bookmarked it for future reference, it is the definitive guide :-)

---

