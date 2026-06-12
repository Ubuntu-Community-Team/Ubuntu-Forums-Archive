---
title: "Installed Open SUSE on Ubuntu...   ...why?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by AndyGT on 2008-10-07
Last night I thought I would try to update my openSUSE from 10.3 to 11.0.  Instead I installed 11.0 onto my Ubuntu (Hardy Heron) and in the process deleted a lot of files....


Any advice??????

---

### Post by LeAstrale on 2008-10-07
Did you by accident delete the partition containing all your files? (the /home partition if seperate from /)

---

### Post by ostamp on 2008-10-07
[FONT="Courier New"][/FONT]ouch...that always sucks. this looks to be one of those learning experiences that can't be fixed, only prevented in the future. i would name the partitions more clearly to give an easy view of what it is that is on them.

---

### Post by AndyGT on 2008-10-07
Thanks for the replies.  Infact I formatted the partition as I thought it was the openSUSE 10.3 partition and not my Ubuntu partition.  I got the feeling immediately that the files would be un-recoverable but I thought there may have been a "sneaky fix" that someone may know?

Any possible fixes would be helpful although I'm not holding my breath!!!....

Thanks folks.

---

### Post by bodhi.zazen on 2008-10-07
First, STOP USING THE HARD DRIVE

you should run from a live CD

Second, restore from backup ?

no ?

Try this :

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)  

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by theDaveTheRave on 2008-10-08
AndyGT,

I have great sympathy for your situation.

I recently upgraded to Heron from the Gibon, in went the live CD and then I realise I had absolutely no idea which partition was my /home when I was about to install new Heron onto the HDD.

So, cancell of the install, boot into live, have a hunt around for the main fstab file, and work out which was the one that I wanted to keep. Then back to the install....

Brilliant, all my settings and stuff is retained, and I just have to put on the other software that I had on the Gibon and everything is at is was before, I'm amazed how easy it was:guitar:

Dave

---

### Post by billgoldberg on 2008-10-08
> **AndyGT said:**
> Last night I thought I would try to update my openSUSE from 10.3 to 11.0.  Instead I installed 11.0 onto my Ubuntu (Hardy Heron) and in the process deleted a lot of files....


Any advice??????

Everything is gone.

This might be a good time to test Intrepid Ibex beta.

---

### Post by nothingspecial on 2008-10-08
> **AndyGT said:**
> Last night I thought I would try to update my openSUSE from 10.3 to 11.0.  Instead I installed 11.0 onto my Ubuntu (Hardy Heron) and in the process deleted a lot of files....


Any advice??????


Ouch!! If it makes you feel any better. I lost nearly 450 gigs of music last week. I`ll tell you this - everything is backed up now.

---

### Post by billgoldberg on 2008-10-08
> **nothingspecial said:**
> Ouch!! If it makes you feel any better. I lost nearly 450 gigs of music last week. I`ll tell you this - everything is backed up now.

Ouch.

I've had the same thing with around 120gb of video and music files. I back up everything now once a week.

---

