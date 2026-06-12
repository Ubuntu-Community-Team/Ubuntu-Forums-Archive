---
title: "Fresh install of 8.04 on my existing Ubuntu partition?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by vidus on 2008-04-24
I currently dual boot xp and 7.10, I figured I'd do a fresh install of 8.04 on the ubuntu partition.

I insert the cd and install as normal, select manual for the partition options. There is a bunch of selections and I am lost as to which one I am supposed to choose.

I have a 60gb for xp, and a 10gb that I made for ubuntu. But then there is another that I dont know what it is, called swap.

Sooo.. what to I select for the install? Obviously not the xp one...

---

### Post by kk0sse54 on 2008-04-24
Instead of directly going into installation run the liveCD and open up the partition manager. Back up all your files and then delete the swap and the ubuntu partition and start the installer. When you get to the partition part instead of selecting manual just select install in largest continuous space. It will then automatically make the two partitions you need where your old version of ubuntu was.

---

### Post by neurostu on 2008-04-24
There should be atleast 3 partitions:
 
ext3
ntfs
swap

You select the ext3 partion for the install, set the mount point as /

---

### Post by twright on 2008-04-25
there is no need to remove the old swap partition :)

---

### Post by anuban on 2008-04-25
> **neurostu said:**
> There should be atleast 3 partitions:
 
ext3
ntfs
swap

You select the ext3 partion for the install, set the mount point as /

Exactly,
It will be good to delete the partition mentioned as ext3.
Then create the same partition with all details same, mount as '/' and select format check box when you say OK.

> **twright said:**
> there is no need to remove the old swap partition :)

There is no need to remove the swap.  Ubuntu will automatically do that for you.:)

---

### Post by vidus on 2008-04-25
Thanks for all the help guys. But I just did the upgrade in the update manager because I did not want to screw my partitions or anything up. I was scared!
Thanks everyone.

---

### Post by kk0sse54 on 2008-04-27
Forgive me you do not need to delete the swap i thought that each installation needed a fresh partition of each. ooops :p

---

