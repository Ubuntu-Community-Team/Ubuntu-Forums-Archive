---
title: "[SOLVED] Just a little help before finishing install."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nerd0795 on 2008-05-19
I'm just about to install and I would like for someone to tell me if this sounds right.  I have 2 hard drives each having about 117GB.  

I would like to keep vista.

Here is the partions:

DEVICE      TYPE   MOUNT POINT FORMAT?  SIZE  USED
/dev/sda
/dev/sda1   ntfs                       7736MB 32400MB 
/dev/sda2   ntfs                       78592MB 32400MB 
/dev/sda5   swap                       625MB   Unknown
/dev/sda6   ext3      /          yes   42327MB  Unknow
/dev/sda3   ntfs                        121174MB  3200MB

IS this right.  all ntfs are for vista... do I need to select what partitions?  Or does it know because it's swap and ext3?

I will ask more questions a second after you post so please stay in forum I don't have much time left.  and I have to install it by today!

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> DEVICE      TYPE   MOUNT POINT FORMAT?  SIZE  USED
/dev/sda
/dev/sda1   ntfs                       7736MB 32400MB 
/dev/sda2   ntfs                       78592MB 32400MB 
/dev/sda5   swap                       625MB   Unknown
/dev/sda6   ext3      /          yes   42327MB  Unknow
/dev/sda3   ntfs                        121174MB  3200MB

IS this right.Not quite enough information here.  However, I can tell you that your swap partition is terribly small.  It should be RAM X 2.  But why does Vista need 3 separate partitions.

---

### Post by nerd0795 on 2008-05-19
one is the first part of my hard drive, my second hard drive and the thing that stores procceses.  I have a gig of ram.

Should the partitions i want to use should be formatted?

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> one is the first part of my hard drive, my second hard drive and the thing that stores procceses.  I have a gig of ram.

Should the partitions i want to use should be formatted?According to that partitioning scheme, I'm only seeing one harddrive.  With a gig of ram, your swap should be 2 gig (2048 MB).  I have no idea what you mean by "the thing that stores processes."  And yes, once you've got your partitioning scheme sorted, the partition(s) that Linux will use will need to be formatting, but the installer will take care of that part.

---

### Post by nerd0795 on 2008-05-19
I know I have 2 hard drives.  That's all I know...

So as long as I don't click format on the other ones vista will be fine?

---

### Post by tom56 on 2008-05-19
The swap does not HAVE to be twice the ram. The amount he's chosen should be fine for now if he has a gig of ram already, though I'd recommend increasing it to future-proof.

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> I know I have 2 hard drives.  That's all I know...

So as long as I don't click format on the other ones vista will be fine?Vista will be fine as long as your don't tell the installer to use the entire drive.  But there is information missing here.  You know you have 2 hard drives, but there is only information regarding one of them in your original posting.  I can't really give you any intelligent advise without knowing what each of those partitions are for and what (if anything) is on the second drive.

---

### Post by nerd0795 on 2008-05-19
Is this right?

[IMG]http://usera.imagecave.com/alex_the_great/Screenshot.png[/IMG]

---

### Post by HotShotDJ on 2008-05-19
> **tom56 said:**
> The swap does not HAVE to be twice the ram.Well, technically, swap doesn't HAVE to be anything.  But we really should get him off on the right foot, and the RAM X 2 formula is tried and true.  Unless one has a very good reason and knows what he or she is doing, it is unwise to go below that amount.

---

### Post by tom56 on 2008-05-19
> **nerd0795 said:**
> I know I have 2 hard drives.  That's all I know...

So as long as I don't click format on the other ones vista will be fine?

The safest way to do this would be to delete the swap and ext3 (assuming it has nothing on it yet of course) partitions and let the installer set up the right partitions in the free space (which is an option in the installer - I think it's called "use largest continuous free space").

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> Can you screen grab in this? If you are using the LiveCD... just go to Applications --> Accessories --> Take Screen Shot.

---

### Post by nerd0795 on 2008-05-19
[IMG]http://usera.imagecave.com/alex_the_great/Screenshot.png[/IMG]

this is it.

Make sure this won't delete vista please.

---

### Post by nerd0795 on 2008-05-19
> **tom56 said:**
> The safest way to do this would be to delete the swap and ext3 (assuming it has nothing on it yet of course) partitions and let the installer set up the right partitions in the free space (which is an option in the installer - I think it's called "use largest continuous free space").

0_o what all I NEEDED TO DO WAS THAT?!!! omg...

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> 0_o what all I NEEDED TO DO WAS THAT?!!! omg...Yes.  you could have just freed up some space and let the installer do it automagically. :)  But that wasn't the question you asked, was it.

In any case, what you have there is ok.  Just check off SWAP for good measure.  Leave the NTFS ones unchecked.

---

### Post by nerd0795 on 2008-05-19
does it mater if the unallocated space is an extended partition?

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> does it mater if the unallocated space is an extended partition?Nope.  In fact, you could have let the installer shrink your Windows partition(s) to make room for Linux.  You just need to be careful to NOT check off "Use entire harddrive" or whatever the exact phrase is.

---

### Post by nerd0795 on 2008-05-19
and It will only use unallocated space right not my vista side which has a huge amount of free memory?

---

### Post by HotShotDJ on 2008-05-19
> **nerd0795 said:**
> and It will only use unallocated space right not my vista side which has a huge amount of free memory?Unless you TELL it to use the entire disk, it will not only NOT mess with your Vista partitions, it will even automagically set up the boot loader to allow you to effortlessly select which OS you want to boot to when you start your computer.

---

