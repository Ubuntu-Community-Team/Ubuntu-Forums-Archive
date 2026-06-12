---
title: "partition help"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-11-17
i have two extra partitions both formated as ext 4

/dev/sda7 ext4 5.80 gib
/dev/sda5 ext4 4.00 gib

i want merge them together so i have one partition that is approx 9.80 gib.
how would i proceed. nothing is on either one. tks

---

### Post by hansdown on 2011-11-17
It depends.

If you wish to install ubuntu, just choose,

```
use entire disk
```

Everything will be overwritten.

If you would like to install windows, we can help, also.

---

### Post by rburkartjo on 2011-11-17
no i already have ubuntu 11.10 and linux mint on their own partitions. i just want to combine these two unused partition either for storage or for puppy linux.

---

### Post by hansdown on 2011-11-17
> **rburkartjo said:**
> no i already have ubuntu 11.10 and linux mint on their own partitions. i just want to combine these two unused partition either for storage or for puppy linux.

Sorry.

Run a live CD, USB, etc.

Use,

```
gparted
```

to see what your partitions look like.

Please, post a screenshot, so someone can give a better reply.

---

### Post by rburkartjo on 2011-11-17
what command do i need to run in the terminal to get output

---

### Post by tartalo on 2011-11-17
> **rburkartjo said:**
> what command do i need to run in the terminal to get output

Not sure to understand your question... you mean this?
```
parted -l
```

---

### Post by rburkartjo on 2011-11-17
tks but didnt work need command to get output of gparted so i can post in this thread

---

### Post by Mark Phelps on 2011-11-17
I believe that GParted is not installed by default anymore.  If you enter gparted in Dash and it doesn't find anything, you will need to install it using the Software Center.

Once that is done, you need to open that and look at your partitions.  You will be able to see if they are mounted.

If they are not mounted, see if the app has an option for merging the partitions.  I've not used it in a long time so sorry, I don't rember if it has that option.

If you don't want to mess around with Gparted, then use the Disk Utility app.  Again, you enter disk in Dash and it should show that as a selection.

---

### Post by garyed on 2011-11-17
Are you sure you have gparted installed?
```

gksudo gparted

```

AFAIK your partitions need to be continuous before you can combine them. So if you want to combine sda5 & sda7 you can't have sda6 in the middle. You'll probably have to delete one or both of the partitions extend a partition into the unallocated space & then shrink it for the space you need. If you can get a screenshot of gparted it might be obvious how to proceed.

---

### Post by rburkartjo on 2011-11-17
gary okay i got a screen shot

---

### Post by rburkartjo on 2011-11-17
here it is

---

### Post by garyed on 2011-11-17
It looks like 5 & 7 are the last two partitions. If that is so then all you need to do is delete the last one & then it will show the space as unallocated. Once you do that you can just resize the one next to it to use all the unallocated space. Just be sure that you are working with the correct partitions before you proceed because once you apply the changes all data will be lost on any partition you delete. It is always recommended to make sure you have your data backed up before messing with any partitions just in case you do make a mistake.
Good luck

---

### Post by Paddy Landau on 2011-11-17
It may be faster to delete both partitions and then recreate the new one.

---

### Post by garyed on 2011-11-17
> **Paddy Landau said:**
> It may be faster to delete both partitions and then recreate the new one.

Good point since he said there's no data on either partition.
The only advantage to doing it my way would be preserving data on the partition being resized or maybe one less chance of deleting data from the wrong partition.

---

### Post by rburkartjo on 2011-11-17
note error message i get when i try to delete either and they are not mounted

Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5


Unable to delete /dev/sda7!
Please unmount any logical partitions having a number higher than 7

---

### Post by garyed on 2011-11-17
Have you tried using a live CD? 
I like to use Gparted live.

---

### Post by critin on 2011-11-18
> **rburkartjo said:**
> note error message i get when i try to delete either and they are not mounted

Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5


Unable to delete /dev/sda7!
Please unmount any logical partitions having a number higher than 7

Number 8 is a swap--right click and click 'swapoff'   Then you'll be able to delete your partitions.

---

### Post by greendragons on 2011-11-18
this might help 
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by rburkartjo on 2011-11-18
cri that did the trick tks i know i had just over looked something

---

### Post by Paddy Landau on 2011-11-18
> **critin said:**
> Number 8 is a swap--right click and click 'swapoff'   Then you'll be able to delete your partitions.
Remember to click swapon after changing your partitions!

If this has solved your problem, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by rburkartjo on 2011-11-18
tks paddy

---

