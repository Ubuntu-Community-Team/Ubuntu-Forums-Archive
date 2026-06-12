---
title: "fsck advice please"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by jamewill on 2008-07-02
hi all

i (may) have a problem on my laptop

100GB disk with a few partitions
15GB windoze xp (rarely used these days)
10GB /home
10GB /
2GB swap
30 GB /data (all my files stay here - about 20GB)
oops doesnt add up - well near enough

a routine fsck on boot picked up some problems
i) with /home 
ii) with /data

the boot process dropped me into a command line env and told me to run fsck and get it to fix problems

it seemed to deal with i) quite happily
it tried to fix ii) and dumped some data to /var/log/somewhere but there is still one inode (whatever that is) that is a problem

BASIC QUESTIONS
---------------
i am continuing to run the computer is that wise?
is it new hd time?

THE REAL QUESTION
-----------------
i have a back up of 99% of /data from a month or so ago
how can i check which files are missing or corrupted on my laptop by comparing to my server (i can ssh into my server backup location)

sorry for the long email
and thanks for any answers

jw

---

### Post by bodhi.zazen on 2008-07-02
Since no one has answered yet I will try.

In general if fsck can not fix the problem "automatically" it can be difficult.

Boot a live CD, do not mount your hard drive.

Run this command :

```
fsck -rfv /dev/sdxy
```

obviously change "/dev/sdxy" to your bad partition.

If that does not fix the problem, could you post the exact error message (you can cut and paste from the terminal).

---

### Post by bliffle on 2008-07-03
I have a similar problem: during startup of my 7.10 ubuntu 'fsck' quits with code 8, and when I look in the /var/log/fsck/checkfs it says the check stopped in 'sda4'. That partition, sda4, is one that I made preparatory to installing 8.04 Hardy Heron to hold a backup of my /home directory. But then I got stymied from doing the 8.04 install by a hardware problem which i think I have now solved, so I'd like to get back to upgrading to Heron.

So I can delete that sda4 if I have to and then re-copy my /home to a backup.

But I don't understand what I did to make sda4 fail in fsck, and I don't know what to do to assure a good sda4 next time. sda4 is an ext3. I don't remember what I used to copy /home. Also, how can I be sure I won't just get the same result after I re-copy /home?

---

### Post by bodhi.zazen on 2008-07-03
> **bliffle said:**
> I have a similar problem: during startup of my 7.10 ubuntu 'fsck' quits with code 8, and when I look in the /var/log/fsck/checkfs it says the check stopped in 'sda4'. That partition, sda4, is one that I made preparatory to installing 8.04 Hardy Heron to hold a backup of my /home directory. But then I got stymied from doing the 8.04 install by a hardware problem which i think I have now solved, so I'd like to get back to upgrading to Heron.

So I can delete that sda4 if I have to and then re-copy my /home to a backup.

But I don't understand what I did to make sda4 fail in fsck, and I don't know what to do to assure a good sda4 next time. sda4 is an ext3. I don't remember what I used to copy /home. Also, how can I be sure I won't just get the same result after I re-copy /home?


Hard to know, fsck is often cryptic. Unless the log is more specific, I would start by running fsck manually from a live CD (look up at my last post).

---

### Post by nick_h on 2008-07-04
With a hard disk that might be failing it may also be worth running smartctl and badblocks.

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Disk manufacturers also supply diagnostic utilities.

---

### Post by bliffle on 2008-07-07
I think that 'fsck' problem was a hangover from the 3945 problem I had a couple months ago. I'm guessing that something went sour when I copied my '/home' to a backup partition. Now, the 3945 problem has gone away by itself and both my XP and 7.10 partitions work well. So i'm just going to delete the backup partition and start all over.

Maybe that will solve my new problem. When I try to change the session to mythbuntu (from gnome) it complains that there is a problem and I have to use a safe shell.

---

### Post by bliffle on 2008-07-22
I installed hardy to the old gutsy partition and still get the 'fsck' error and have to 'ctl-D' to override.

```

Log of fsck -C3 -R -A -a 
Tue Jul 22 12:15:37 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=dcc0c6c5-bf8d-45f7-ab2c-8326b36f7de1'
fsck died with exit status 8

Tue Jul 22 12:15:37 2008
----------------

```

---

### Post by bodhi.zazen on 2008-07-22
> **bliffle said:**
> I installed hardy to the old gutsy partition and still get the 'fsck' error and have to 'ctl-D' to override.

```

Log of fsck -C3 -R -A -a 
Tue Jul 22 12:15:37 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=dcc0c6c5-bf8d-45f7-ab2c-8326b36f7de1'
fsck died with exit status 8

Tue Jul 22 12:15:37 2008
----------------

```

Did you change or delete your partitions ? Check list your partitions with : ```
sudo blkid
```

Then update /etc/fstab with the proper uuid

```
gksu gedit /etc/fstab
```

---

### Post by bliffle on 2008-07-25
Thanks!

I did that, the sudo blkid, and got the right UUID for sda4, plugged it into /etc/fstab and it seems to have solved that problem.

Wish I knew how the UUID got wrong in the first place.

---

### Post by bodhi.zazen on 2008-07-28
> **bliffle said:**
> Thanks!

I did that, the sudo blkid, and got the right UUID for sda4, plugged it into /etc/fstab and it seems to have solved that problem.

Wish I knew how the UUID got wrong in the first place.

In general UUID will change when you format the partition, not sure if that applies in your case.

---

### Post by Happless on 2008-07-28
Thaanks bodhi.zazen, that has saved me from formatting my 250gb drive :)

---

