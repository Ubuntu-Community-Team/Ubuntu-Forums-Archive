---
title: "[SOLVED] Using Gparted"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by ellalan on 2008-10-03
Hi
I wanted to reduce my swap partition, now I have left with 4.70 GB of unallocated partition, could some one tell me how to merge this with my main partition please.TIA.
PS: I have reduced my swap partition from 5.69GB to 750MB.

---

### Post by binbash on 2008-10-03
You need Gparted live cd for that.you cant resize or merge mounted partition.

---

### Post by ellalan on 2008-10-03
Where do I get the Gparted live CD?

---

### Post by tonyh6243 on 2008-10-03
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by houbysoft.xf.cz on 2008-10-03
> **ellalan said:**
> Where do I get the Gparted live CD?

You don't need it. Just use the Ubuntu LiveCD. Gparted is installed on the Ubuntu liveCD as well.

---

### Post by drs305 on 2008-10-03
There are many ways to do this. This one will do what you want - one primary partition for your linux, and one extended partition with your swap partition. (You don't even need the extended partition if you would just prefer two primary partitions.)

You will have to boot to the livecd or use a gparted or systemrescuecd. You can't change the size of the / partition while it is mounted.

1. Boot to the livecd Desktop and open gparted: Applications, Accessories, Terminal.
```
gksudo gparted
```

2. Highlight the swap partition and delete it (Partition, Delete). You should now have an empty extended partition.

3. Resize the extended partition to the size you desire and create a swap partition of the same size (New, Logical, linux-swap). It should fill the entire extended partition. Make sure it is to the far right (0 space after). This will help if you decide to make additional partitions later.

4. You should now have your original / partition, an empty space, and an extended partition filled with the (logical) swap partition.

5. Highlight the primary partition, then Partition, Resize and expand it to fill all the remaining space (0 before, 0 after).

---

### Post by ellalan on 2008-10-03
Hi
Thank you drs305  for the detailed explanation, however I am stuck at your instruction No5.
When I tried to extend the main partition(143.62GiB) I get the notification at the bottom:
Move/dev/sda1 to the right grow it from 143.63GiB to 143.63GiB

The unallocated 4.46GiB is not merged, could you please tell me what am I doing wrong here. I have attached the current position.

---

### Post by drs305 on 2008-10-03
You are doing this from the livecd and the partition is unmounted (Partition, Unmount)?

From the picture, it looks like the sda1 hasn't been selected. Click on the partition image and it should be highlighted. Then Partition, Resize should let you perform the operation.

**Added:** If you can't get it to work from the livecd Desktop, I would recommend creating a systemrescue cd. You can create a bootable cd with partimage, gparted, testdisk among others. Download the iso from here:
[http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964]("http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964")
or run this (the server is a bit slow at the moment):
```

wget http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-1.1.0.iso?modtime=1220820351&big_mirror=1

```

---

### Post by ellalan on 2008-10-03
Hi drs305,
I am pleased to say that I have managed to do what I wanted, with your help. I couldn't unmount as it was greyed out,so I deleted that unallocated(4.7GiB) volume then it was added to my main partition automatically. 
I created new extended partition of 750MiB and a swap partition of same value. I have Bookmarked your post as it is very detailed and easy to follow instructions by you, I am ever so Thankful to you.

---

