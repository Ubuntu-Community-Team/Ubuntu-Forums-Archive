---
title: "Can you 'clean' bad sectors?"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by lauren5 on 2014-07-16
Hey guys:
I inherited a network of computers in my lab, most of which run GNOME or RedHat or something like that. I'm a total new guy to Ubuntu but I really badly want to learn and to understand my way around instead of just hacking away like I've been doing so far. So forgive me if this question has been asked before or is really low level.

We have one of our computer hooked to a RAID array so essentially we have somewhere around 8 (6-8?) drives associated with this one computer. Things run decently but unfortunately we work in an old building where power outages are becoming more commonplace. One happened a couple of days ago and as I restarted the system the SMART program popped up to let me know that two of my drives had high "Reallocated Sector Counts" (one had 233 or something and the other had 80-something) and was in "pre-failure' mode. 

Now I'm not particularly worried at the moment because I've read other wonderful threads like this one -> [http://ubuntuforums.org/showthread.php?t=1924027&highlight=reallocated+sectors](http://ubuntuforums.org/showthread.php?t=1924027&highlight=reallocated+sectors) -> which seem to indicate that that particular attribute isn't a death knoll per say. Unfortunately the number IS somewhat high, probably because all of the read/write interruptions associated with these stupid power failures. I'm going to do a full backup tomorrow but I guess what my question is is:

I don't think anything is wrong with the drives themselves, just that the sectors are interrupted. So is there a way I can get these sectors back? Change them from 'bad' to useable again?

I guess some peripheral questions because I am so new to this may be:
Is there a better attribute to monitor for drive health? Or is there a better way than SMART to monitor drive health?
How do you guys do your backups? I was planning on using deja dup or something similarly dumb that google search tells me as this is my first time doing it.

Again so sorry for the new-kid questions. I've read a lot of the gnome.org pages and other threads but it's just so much to try to keep straight.
I appreciate any time you take to help me out.

Lauren

---

### Post by LukeMorrison on 2014-07-16
I would start with pulling each drive that is giving you problems and running Spinrite on them individually.  

[https://www.grc.com/sn/sn-112.txt](https://www.grc.com/sn/sn-112.txt) 

Search for RAID in the text and it will give a more detailed explanation.

Luke

---

### Post by whitesmith on 2014-07-16
I'd begin by testing the raid-ed disks individually with```
badblocks /dev/sda
```I think badblocks is in e2fsprogs (not looking at a Linux system now), which you'll have to install unless you already have it. Then give fsck a try to narrow down the problem sectors so they can be fixed. SpinRite is a fine tool but isn't FOSS. I think it costs around $70...and well worth the money if desperation has set in. Regards.

---

