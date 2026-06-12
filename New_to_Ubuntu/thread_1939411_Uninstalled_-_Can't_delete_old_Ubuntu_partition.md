---
title: "Uninstalled - Can't delete old Ubuntu partition"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by xyrana on 2012-03-11
I installed Ubuntu off a CD a while ago, then I decided I gave it too much space, so I uninstalled so that I could resize the partitions. When I try to delete the free space, though, after going through the warning (this may become inaccessible, etc), it says "There is not enough free space on the disk(s) to complete this operation." So... now what.

I'm using Window 7, and I believe the version of Ubuntu (if it matters) was 11.04. I tried gparted, and it wouldn't let me delete, either (though I'm not an expert with computers by any means, so I might have missed something).

This is somebody else's screenshot, but it essentially sums up what my hard drive looks like right now:

[IMG]http://i911.photobucket.com/albums/ac319/BLOBFUT/Discmanagement1.jpg[/IMG]

---

### Post by Bölvaður on 2012-03-11
Free/empty space cannot be deleted, it can only be converted/filled up by something new.

By going from the screenshot it looks like the only thing you need to do is expand the windows partition over the empty space.
But the error you gave is something completely different and indicates this is not your situation, please upload _your_ screenshot.

---

### Post by ajgreeny on 2012-03-11
A few points worth making!


[LIST=1]
[*]Is the old ubuntu partition already deleted?
[*]What do you mean by "uninstalled ubuntu"?  How did you do that?  Was it a wubi installation from within Windows?
[*]You can't delete free space, it is already free and empty.
[*]Your screenshot is from Windows Disk management utility which is almost useless for ubuntu partition management, as it can not see what the ubuntu partitions really are; it just calls them healthy.
[*]Boot to a live ubuntu CD and run gparted from that, then show us that screenshot; it will be a lot more informative.
[*]To use gparted you may need to right click on the partitions and choose unmount or swapoff, depending on what the partition is, as you can not work on mounted partitions.
[/LIST]

---

### Post by xyrana on 2012-03-11
Er, bad wording - I meant that I want to make it all one partition (namely, C), not "delete it". It apparently has to be "unallocated" rather than "free space" to be able to extend? It won't let me extend as it is. And when I right click on "free space" and say "Delete Partition" it comes up with that error message.

What is now the "free space" is where Ubuntu was, or at least the space it was taking up for files or something. That's how much space I gave it when I installed.
It wasn't Wubi (which is what I should have done, really, considering I'm new to this). I installed it through the CD, and I uninstalled it with the CD, somehow. Then Windows failed to boot, but I fixed that with the Windows disk.

I will try gparted again.

Also, to put pictures on it has to be from a website, I guess... But here is in disk management, from left to right. It looks like the other picture, with two extra partitions at the beginning before C (and different sizes, of course):

These are colored dark blue, as Primary Partitions:
100 MB - Healthy (OEM Partition)
Recovery - 14.65 GB NTFS - Healthy (Primary Partition)
OS (C:) - 186.51 GB NTFS - Healthy (System, Boot, Page File, Active, Crash Dump, Primary Partition)

This is colored as free space (green) / extended partition (dark green outline):
260.57 GB - Free space

This is colored dark blue, as a Primary Partition:
3.91 GB - Healthy (Primary Partition)

---

### Post by xyrana on 2012-03-11
Oops, my bad, failed to notice the attachment option at the bottom. Here's a screenshot.

---

### Post by Bölvaður on 2012-03-12
If you are using a partition manager on Windy that is running on the same partition you want to edit I am not too surprised you could have problems doing this.
I have no idea how to use partition tools in Windy, it would make much more sense asking people that actually use Windows about how to manage partitions in Windy. There is a reason why you should manage NTFS partitions with Windy tools, as this is their own filesystem.

But technically, I cannot see why it wouldn't work just booting up a live cd and use Gparted to extend the NTFS partition.
Look forward to seeing the results from trying Gparted.

---

### Post by audiomick on 2012-03-12
It puzzles me that you seen to have 5 partitions on there. The thing is, you can only have 4 primary partitions or three primary partitions and one extended. I can only assume that the first partition, labelled "OEM partition" somehow doesn't count.

Anyway, if we assume that the partition table isn't completely broken, I think this is what the problem is:

You want to extend the partition that is the windows C: partition to the right into the green area that is labelled as free space. If you are right, and the free space is inside an extended partition, then this extended partition is what is blocking you.

Consider an extended partition to be like a box that can contain a number of so-called logical partitions. Even if the box is empty, i.e. no logical partitions inside, the empty box, the extended partition, still takes up room on the drive.

what you need to delete to expand your windows partition is not the free space, but the extended partition that the free space is contained in.

I am sorry I can't say exactly how to do this with the windows partitioning tool, but I think it is just a matter of pointing to exactly the right place when selecting what you want to work on. Maybe something like on the border instead of in the middle of the free space. Try it out.

---

### Post by ajgreeny on 2012-03-12
> **audiomick said:**
> It puzzles me that you seen to have 5 partitions on there. The thing is, you can only have 4 primary partitions or three primary partitions and one extended. I can only assume that the first partition, labelled "OEM partition" somehow doesn't count.

Anyway, if we assume that the partition table isn't completely broken, I think this is what the problem is:

You want to extend the partition that is the windows C: partition to the right into the green area that is labelled as free space. If you are right, and the free space is inside an extended partition, then this extended partition is what is blocking you.

Consider an extended partition to be like a box that can contain a number of so-called logical partitions. Even if the box is empty, i.e. no logical partitions inside, the empty box, the extended partition, still takes up room on the drive.

what you need to delete to expand your windows partition is not the free space, but the extended partition that the free space is contained in.

I am sorry I can't say exactly how to do this with the windows partitioning tool, but I think it is just a matter of pointing to exactly the right place when selecting what you want to work on. Maybe something like on the border instead of in the middle of the free space. Try it out.
That is precisely why I asked for a gparted screenshot at #5 of my first post.  The wimdows disk management screenshot is no real help to me in understanding the partition situation on the machine.

I agree that there may be an extended partition, but which one, and how does it affect the attempts to edit partition sizes etc etc.  There is certainly no indication of an extended partition in the screenshot, but if the free space shown was a partition - - ?  Who knows!

Again to OP.  Can you please run gparted from a live ubuntu CD and post a screenshot from there.  I shall be able to understand that, whereas the windows screenshot is no help; not to me at any rate.

---

### Post by audiomick on 2012-03-12
> **ajgreeny said:**
> That is precisely why I asked for a gparted screenshot at #5 of my first post.  The wimdows disk management screenshot is no real help to me in understanding the partition situation on the machine.

It seems it is not much help generally when trying to look at Linux partitions. Attached two screenshots; one of my Laptop hard drive with the Windows tool, one of the same drive with Gparted. I know the one of the Windows tool is difficult to read, but it shows the Linux partitions as Primary, when in fact they are all logical inside one extende partition, as can be seen in the Gparted screenshot.

So, on the strenght of this, I suspect that the OP might not be able to solve the issue at all with the Windows tool. It certainly seems that the easiest thing would be to boot into a live CD and use Gparted to remove anything that had to do with Linux.

edit: changed the Windows screenshot for a better one.

---

### Post by Cheesemill on 2012-03-12
> **audiomick said:**
> It puzzles me that you seen to have 5 partitions on there. The thing is, you can only have 4 primary partitions or three primary partitions and one extended. I can only assume that the first partition, labelled "OEM partition" somehow doesn't count.

Unless you are using GPT. In which case you can have up to 128 primary partitions :)

---

### Post by Mark Phelps on 2012-03-13
As some folks have already said, Windows tools are best at managing NTFS partitions.  So, if you want to expand the Win7 OS partition to fill the free space, do NOT use Gparted; instead, use the Win7 Disk Management utility.

And ... yes ... you CAN do this while logged into Win7.  It actually lets you expand the Win7 OS partition.  It may or may not force a reboot to finish the partitioning.

Also, according to the Disk Management screenshot:
1) You have NO extended partitions
2) You already have the maximum of 4 Primary partitions

Also, if you have detailed questions regarding the interpretation of stuff you're seeing in Win7, you should really take those questions to a Win7 forum:  sevenforums.com.

---

### Post by xyrana on 2012-03-14
... well, it turns out I was just being a complete computer idiot, heh. =P There was a "linux-swap" in the extended partition that didn't show in Windows, but it did on gparted. Deleted it and the partition, and everything is back to normal.

Thanks for the help.

---

