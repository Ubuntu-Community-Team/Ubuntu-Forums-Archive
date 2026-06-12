---
title: "partition permission"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-01
I created a new ext3 partition so i can put more stuff on there. when i try to drag and drop a file into it, it says that i do not have the permissions to do it. how do i enable the permission to be able to put files into it?

---

### Post by iaculallad on 2008-06-01
> **adobrakic said:**
> I created a new ext3 partition so i can put more stuff on there. when i try to drag and drop a file into it, it says that i do not have the permissions to do it. how do i enable the permission to be able to put files into it?

Is the drive setup in fstab?

---

### Post by adobrakic on 2008-06-01
I don't think it is, i couldnt extend my partition for ubuntu, so i just added a new ext3 partition. So i doubt it's in fstab.

---

### Post by buntu_Geek on 2008-06-02
change the ownership and accessibility(permission) with chmod for the mount point...

for example...

if your mount point is /media/disk for u r ext3 partition...

then... the code goes like this...

```

sudo chown -R [owner]:[group] /media/disk
sudo chmod 777 /media/disk

```

The first command changes the ownership.. the second changes permission...( 777== full permission...)

And BTW, replace owner and group with your username ....

---

### Post by adobrakic on 2008-06-02
i just deleted the partition and put it space back onto windows. 
is there another partition editor tool thing that would allow me to put the space onto my current ubuntu partition?

---

### Post by buntu_Geek on 2008-06-02
Partition editor for ubuntu or windows...

If u r asking for windows.. then no... windows doesnt have any support for creating an ext3.. :P probably doesnt know the power of the journaling file system... :P

anyways..

if you want to access your ntfs partition in ubuntu there is a tool called ntfs-3g
```

sudo apt-get install ntfs-3g 
```

---

### Post by adobrakic on 2008-06-02
for ubuntu. i could take about 25gb off of my windows partition and put it onto ubuntu, but when i used the partition editor on the live-cd, i couldn't extend my ubuntu partition passed what it already was.

---

### Post by buntu_Geek on 2008-06-02
So you want to extend your existing partition in ubuntu??.. Be a bit more clearer...

---

### Post by adobrakic on 2008-06-02
yes, i wanna extend my existing partition in ubuntu, but when i tried doing it using the gpartition or gwhatever it's called off the live-cd, i couldn't add more space to my ubuntu partition. it wouldn't go passed what space it already had

---

### Post by iaculallad on 2008-06-02
> **adobrakic said:**
> yes, i wanna extend my existing partition in ubuntu, but when i tried doing it using the gpartition or gwhatever it's called off the live-cd, i couldn't add more space to my ubuntu partition. it wouldn't go passed what space it already had

Using your GParted partitioner to view partitions: where is your NTFS drive located, to the Left or to the Right?

---

### Post by adobrakic on 2008-06-02
to the left

---

### Post by iaculallad on 2008-06-02
> **adobrakic said:**
> to the left

You cannot resize partitions moving from right to left using GParted, so if NTFS as you say is on the left-side and Ext3 on the right-side then there's no chance that you can resize it.

---

### Post by adobrakic on 2008-06-02
is there an alternative i can do? such as make a new ext3 partition or something

---

### Post by buntu_Geek on 2008-06-02
You can solve it..but its a one way...no way back.. :D
You have to delete your ext3 partition .. and free the 25gb win partition .. then create the new partition...

Thats the only way i can think off now.. if you can afford to delete the ext3 partition.... probably after a backup..

---

### Post by adobrakic on 2008-06-02
i was thinking about doing that, but it was kind of a rough ride to get to having the settings i have now :x
none of my posts were answering some ones question, they were all me asking a question, haha. but i think i'm just gonna do that. thanks for the information, guys.

---

### Post by adobrakic on 2008-06-02
Okay, so i think im just going to delete my current ubuntu partition and  create a new one.

would i just go to gparted, make my windows partition smaller (freeing up 25gb) and create a new ext3 partition, or would i have to go back to the desktop and click on "install"?

---

### Post by buntu_Geek on 2008-06-02
You cant edit ntfs in ubuntu( only done with some third party softees....) so u have to resize the nfts partition in windows...

---

### Post by buntu_Geek on 2008-06-02
You have to resize your ntfs in windows and then do install (ubuntu live cd)...
When you get into the partition stage you do the deletion there.. (here you shud see the ntfs partition already resized which you can see as UnAllocated space...) you have those unallocated partitions merged... then create new partition as you desired....

Hope i was helpful.... (Often i dont want to mislead coz of misconception.. so that was why i was asking question.....)

---

