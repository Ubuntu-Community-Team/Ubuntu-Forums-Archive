---
title: "Partition ?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by garyed on 2008-09-02
I'm not having any particular problems but I was just wondering about partitioning possibly overwriting needed files. Lets say I have a 100 gig drive using XP all in one partition. I want to use it & dual boot with Ubuntu but I'm using 40 gig of it already. When I install Ubuntu & partition 50gig 
for each OS how can I be sure that none of the original 40 gig in use is going to get overwritten. Maybe there are some files scattered on another part of the disk. I know its a good idea to defrag before partitioning but are there any ways to be sure nothing gets overwritten?

---

### Post by Pro-reason on 2008-09-02
A partitioning program doesn't just chop off the end of a partition.  Obviously it moves all the data to the end that will be left after the resizing.

For NTFS partitions, it is best to use a Windows program, because NTFS support on Linux is not at 100%

When in doubt, back up data first.

---

### Post by falcon61102 on 2008-09-02
The best way to prevent that is to defrag at least once before partitioning your drive.  With XP you will see a graphical representation of the drive when partitioning so you can see where your files are.  As long as there are no unmoveable files at the very end of the drive you won't have anything to worry about.  To be safe you can defrag a couple of times and that will help compress things.

Another option is to use a third party defrag utility because some are more powerful and faster than the windows one.  I use Ultra Defrag and it works well.

---

### Post by falcon61102 on 2008-09-02
Pro-reason,
I like you signature... funny, but true.

---

### Post by garyed on 2008-09-02
> **Pro-reason said:**
> A partitioning program doesn't just chop off the end of a partition.  Obviously it moves all the data to the end that will be left after the resizing.

For NTFS partitions, it is best to use a Windows program, because NTFS support on Linux is not at 100%

When in doubt, back up data first.
Are you saying that partitioning will always move any files that may be left on the new partition space back to their original partition assuming there's room.

---

### Post by falcon61102 on 2008-09-03
The partitioning utility should move everything to the front of your drive prior to sectioning off the space needed for a new partition.  As with anything, sometimes things get lost in the shuffle and a way to prevent you from losing any data is to make sure you defrag before hand and then you should have no worries but the likelyhood of you losing data from repartitioning is close to none.

---

### Post by Pro-reason on 2008-09-03
> **garyed said:**
> Are you saying that partitioning will always move any files that may be left on the new partition space back to their original partition assuming there's room.

I don't understand that question, the way it's phrased.

A partitioner does not destroy anything when it resizes a partition (unless there is an error, of course).  It's like squeezing the air out of a sack half-full of rice.  You still have all your rice.  

You may accidentally make a hole in the sack, but that's another issue.

When in doubt, back up your data.

---

### Post by garyed on 2008-09-03
I thought if I had some windows ntfs files that were in a part of a drive that was going to be partitioned ext3 that they could get deleted. 
I've read about always defragging before making any new parttions so I thought that was one of the reasons why.

---

### Post by Pro-reason on 2008-09-03
> **garyed said:**
> I thought if I had some windows ntfs files that were in a part of a drive that was going to be partitioned ext3 that they could get deleted. 
I've read about always defragging before making any new parttions so I thought that was one of the reasons why.

You have a small cupboard that contains a hessian sack less than half-full of rice.  You want to put a canvas sack in there, but the big hessian sack occupies all the space.

So, you press the air out of the hessian sack, allowing you to neatly push the sack to one side of the cupboard, thus making an empty space for the new, canvas sack, which you can fill with lentils.  The two sacks are now neatly sitting next to each other in the cupboard, equally accessible.

(Cupboard = hard-drive; hessian = NTFS; canvas = ext3; rice = Windows; lentils = GNU/Linux)

Before pressing the air out of the hessian sack, you might want to pick it up and shake all the rice down to the bottom.  It's not necessary, but it'll make it possible to pack the sack more neatly.

(Shaking the rice down = defragmenting)
[I]
Analogies aside, NTFS partitions are fiddly things, so it's always best to back up any important data, even if what you are doing should not theoretically do any harm.  See [this thread]("http://ubuntuforums.org/showthread.php?t=908987") for an example of a recent problem I had after resizing.[/I]

---

### Post by garyed on 2008-09-03
I think I get the picture, excellent analogy pro..
Thanks to both you guys falc.. & pro..
I was just curious about the possibility of rice leaking out of the sack & on to the floor after being moved around in the cupboard.
I'm not very good at sweeping up.

---

### Post by falcon61102 on 2008-09-03
Lol... No problem.  Hope it all works out for you.

---

