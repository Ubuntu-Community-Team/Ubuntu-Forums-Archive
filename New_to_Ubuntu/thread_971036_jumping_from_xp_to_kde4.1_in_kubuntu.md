---
title: "jumping from xp to kde4.1 in kubuntu"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by ELD on 2008-11-04
Well i have been using various linux flavours and i am going to try kubuntu for real now.

A few questions:

1: Is there a good IM client for msn i can use on it? I don't like the included one.

2: How can i get my ntfs partitions to auto-mount (i would change to ext3 but no place to backup 160gb of files atm heh).

3: Is it actually fast and stable in the newest release?

---

### Post by Cypher on 2008-11-05
1) By the included version, do you mean Kopete? If so, given Pidgin a shot. 

2) You'll need to add an entry to the /etc/fstab file to auto-magically mount your NTFS partition at boot time. [This guide]("http://www.psychocats.net/ubuntu/mountwindows") will help you.

3) Yes and yes. :)

---

### Post by wd5gnr on 2008-11-05
I agree with pidgin.

The only thing about mounting your XP partition you should be aware of (in addition to the guide already mentioned) is that if your computer shuts down abnormally (rare, but maybe a power outage, etc.) the volume will refuse to mount unless you force it or you boot XP and let it bless the disk. I hate to boot XP even though I still can but with a lot of work I made VirtualBox able to virtually boot my existing Windows partition (lots of work though; not for the faint of heart). Booting that virtual machine is good enough to clean the disk (and lets me get to everything I used to have on XP without rebooting).

KDE4.1 is great -- I use it. But it does still have its quirks. For example, the panels don't hide yet. Installing new widgets from the internet appears broken. The graphical time zone setting dialog crashes. Granted, this is on Hardy so I can't speak for the newest release, but I don't expect Plasma or KDE to have any real improvements in that release. Don't get me wrong -- I like it. But be aware if you don't have tolerance for little things, you might want to go with 3.x. Of course, you can install both or switch later if you just can't stand it.

---

### Post by ELD on 2008-11-07
I think i will wait a while it is still a bit iffy for me, i will use XP until it all stablises.

---

### Post by Cypher on 2008-11-07
If you're keen on goig to KDE, you could always install Hardy Heron 8.04 with KDE3, something that's been out for a long time and very stable. Then we KDE4 becomes stable, you could upgrade to Intrepid Ibex 8.10..

---

### Post by ELD on 2008-11-07
I didn't really like kde3 as much as i do kde4, just need it to stablise a little, it's deffinately getting there though.

---

