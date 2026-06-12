---
title: "[SOLVED] how to configure grub for 3 drives"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-11
Staples was selling 320gig IDE drives for 60$ this week.  So I bought one and stuffed it in.  I want to configure Grub for 3 drives.  I'm afraid of screwing up my current dual boot set up.  I realize some cli work is needed.  I just need how to set up grub to allow a 3rd and 4th op system.  I'll lay out what I want to do below.

I currently have:
32 bit Ubuntu on an 80 gig IDE drive set as master on the primary channel.  Grub is on this drive.  

I chainload XP Pro on a seperate 320gig SATA drive on channel 1.

I added the second IDE drive on the primary channel configured as a slave to the 80.

I want to install 64 bit Ubuntu on it and install Fedora 9 when it hits the mirrors.  I'm thinking to partition it with 2 100 gig partitions and 1 partition at 110 and a 10 gig swap.  I just may throw a 3rd op system in there as well.  Maybe Gentoo just to make me pull some more hair out](*,).  Any suggestions on how to accomplish this?  I really want to give XP an infiriority complex!

Mark Shuman

---

### Post by volkswagner on 2008-05-11
I am not sure I understand.  Is the XP currently working using grub?  I think 10gig is overkill for swap.  I would say double your ram unless you have more thank 2gig of ram.  I would cap swap at 2gig.  Some would say even less.

If you are currently using dual boot.  When you add a partition and os to that partition, most any linux install will add the new os and find all current os's to your new grub.  This will cause the latest install to be default though.  You can change the order later if you want.

---

### Post by phread59 on 2008-05-11
Ok I gotcha.  Yes XP is actually happy.  I have a completely functional dual boot set up on 2 drives as currently configured.  I have 4 gigs of ram available.  Memory is not a problem.  I just want to add another drive for operating systems.

I had to map the drives to get the dual boot to work.  I'm not sure if I have to remap.  If so how do I set it up.  I googled up info and it all was confusing.  Most articles on grub say that each hard drive has a number.  I understand that.  I just want to be sure grub can see it and use it.  I may need to add the other OS's to grub's list too.  

Any help would be appreciated.

Mark Shuman

---

### Post by phread59 on 2008-05-11
Shameless bump.

Mark Shuman

---

