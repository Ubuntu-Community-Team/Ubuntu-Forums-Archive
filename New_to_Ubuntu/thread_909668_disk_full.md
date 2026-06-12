---
title: "disk full????"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by naja74 on 2008-09-03
It appears that the / partition has 0 free space. Disk analyzer gives me no real indication of where this super large file is that's taking up 70gigs of my 80 gig drive. I've recently added a cron script to backup my home directory, which is only 6 gigs. This script is coded to tar the directory and store it on another, physically separate drive. Could it be placing a tmp file from this operation somewhere?

Please help!

---

### Post by perlluver on 2008-09-03
> **naja74 said:**
> It appears that the / partition has 0 free space. Disk analyzer gives me no real indication of where this super large file is that's taking up 70gigs of my 80 gig drive. I've recently added a cron script to backup my home directory, which is only 6 gigs. This script is coded to tar the directory and store it on another, physically separate drive. Could it be placing a tmp file from this operation somewhere?

Please help!

You could take a look in /tmp, other than that, it might be making one in the home directory.

---

### Post by naja74 on 2008-09-03
Found it! There were several located in /root/.local/share/Trash/files but they appeared to be from backups made from quickstart, which I removed several days ago...... I didn't reboot since then, until I came home today and found that I had no disk space left. Interesting. I now have 55 gigs free, which makes me wonder where the other 10 gigs are. My home is 6.6 gigs and / in its entirety is only 11 gigs. But disk analyzer tells me I've used 20 gigs, with 55 gigs free, from a 75 gig partition... 

Well, 10 gigs isn't much considering, but it bothers me that I can't locate it. I've unmounted all remote drives and everything mounted under /media.

---

### Post by mkvnmtr on 2008-09-03
I don't know if this will help. Look at the amount of space your old logs a taking up. I seem to remember on 6.06 when my disk was about full finding several gigs of old logs. I had also downloaded way more desktop pictures than I realized.

---

### Post by naja74 on 2008-09-03
> **mkvnmtr said:**
> I don't know if this will help. Look at the amount of space your old logs a taking up. I seem to remember on 6.06 when my disk was about full finding several gigs of old logs. I had also downloaded way more desktop pictures than I realized.

Ah.... log files, I didn't consider those.

/var/log/ is only 7.6mb in it's entirety though...

---

### Post by drs305 on 2008-09-03
Check out the link in my signature line about finding hidden trash.

---

### Post by naja74 on 2008-09-03
> **drs305 said:**
> Check out the link in my signature line about finding hidden trash.

Hey, thanx for the link drs305

---

