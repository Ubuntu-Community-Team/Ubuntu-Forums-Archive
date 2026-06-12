---
title: "Advanced install question"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-03-15
I'm going to be doing an Ubuntu install shortly. I've decided to use the "advanced" custom option to do the install. I just want to make sure I'm not missing any key items here.

I need to make a swap partition, and since I have 8gb ram, I'll need to make this 16gb, correct?

I also need a "/" logical partition which is where I install Ubuntu to, so that will be the largest partition.

I will not be making a separate home partition, so no worrying about that.

So doing a dual boot with Windows 7, I'll have:
Windows 7 C:/ primary partition
Windows 7 "System" primary partition (came with laptop)
Ubuntu swap partition
Ubuntu "/" logical

I've never done this before, am I missing anything? I do remember something about logical partitions needing to be inside extended partitions, so I'm a bit confused in that area.

---

### Post by wildmanne39 on 2012-03-15
Hi, > I need to make a swap partition, and since I have 8gb ram, I'll need to make this 16gb, correct?you only need 3 gigs of swap at most.

> I also need a "/" logical partition which is where I install Ubuntu to, so that will be the largest partition.I would make a separate home partition so you can easily reinstall and keep your current files if you need too. Also since you are using windows I would create a data partition using NTFS so you can access your personal files like pictures and music from both operating systems then the root partation only needs to be about 10 gigs at most.
Thanks

---

### Post by Thrashrokz33 on 2012-03-15
Interesting. I guess I could set something like that up. So the "/", and home/data partitions should all be logical, right?

And what would be the point exactly in having both a home and data partition? Wouldn't I only need the data one?

---

### Post by wildmanne39 on 2012-03-15
Hi, > So the "/", and home/data partitions should all be logical, right?Yes.

> Wouldn't I only need the data one?Yes you just need one but some people call it a data partition instead of the home partition.
Thanks

---

### Post by 3rdalbum on 2012-03-15
Sixteen gigs is too much swap.

You can make it only slightly larger than physical memory (8.5 gigs would be fine).

You don't need a separate /home. If you reinstall Ubuntu in the future it will detect the existing /home folder and retain it even though it is in the same partition.

Just make a partition in Ext4 format and set its mount point as /, and an 8.5 gig swap partition (set its type as swap) in the Something Else screen of the Ubuntu installer.

---

### Post by anewguy on 2012-03-16
Since this is a laptop, and the possibility exists that you would like it to hibernate, you do need a swap file that is slightly larger than your physical memory size.  Since you say you have 8gb of memory, a swap of 8.5gb should suffice.  I seem to remember you have to watch partition types when you have Windows 7.  The preferred method is to shrink the existing Windows 7 partition using Windows 7, but do the actual partitioning with the Ubuntu tools.  You should also check - there's a good chance there's recovery partition on the disk as well.  What you have to remember is the number of primary partitions is limited to 4 (if I remember correctly) - so you should make 1 primary partition for Ubuntu, and create logical (extended) partitions within that for swap and for what ever partition(s) you want for Ubuntu and users.

---

### Post by varunendra on 2012-03-16
> **anewguy said:**
> ..the number of primary partitions is limited to 4 (if I remember correctly)Yes, you are absolutely correct about that in case of MBR. The only exception is GPT which is only used in macs.

However, since no one has mentioned it so far, I would just like to add that unless the OP is going to actually use hibernation, he/she can do away with swap altogether. Except for hibernation, the swap won't be used at all with so much RAM. Exceptional cases may be running 5-6 virtual machines (with 'heavy' operating systems in them), or opening a few hundred firefox tabs simultaneously, etc. ;)

---

### Post by anewguy on 2012-03-16
> **varunendra said:**
> Yes, you are absolutely correct about that in case of MBR. The only exception is GPT which is only used in macs.

However, since no one has mentioned it so far, I would just like to add that unless the OP is going to actually use hibernation, he/she can do away with swap altogether. Except for hibernation, the swap won't be used at all with so much RAM. Exceptional cases may be running 5-6 virtual machines (with 'heavy' operating systems in them), or opening a few hundred firefox tabs simultaneously, etc. ;)

Exactly correct - that's why I just mentioned it in terms of hibernation since it's a laptop.  A lot of people don't use hibernation (with modern hardware and OS boot times, it's not really needed unless you had a lot going and had to do something fast - like the battery going dead).  I just thought in case the OP didn't know that, they might want to know - you've seen the posts we get about hibernation not working and you go to find out they made like 512mb of swap.  But hey - I'm glad you help clarify that because I sure didn't present the rest of the picture!

Hope things are going great, and thanks again!
Dave ;)

---

### Post by varunendra on 2012-03-16
Ha-ha.. Now that you've encouraged me, here's more-

I frequently see posts about problems with resuming after sleep/hibernation, and have also seen at least one very experienced user mentioning in a post that 'it is very often' that hibernation in Ubuntu doesn't work very well so he doesn't recommend opting for it unless you really need it [should I duck for cover now..?? ;)]. However, I never use hibernation myself so can't say about the truth of that statement. Besides, it is obvious that we only get posts from those who get into trouble with it, not of those who have it going smooth. And maybe that number could make the 'problem cases' negligible, if can be obtained somehow.

So.. it would be best if users can decide whether or not they would be using hibernation. And the bottomline (IMHO) about the size of swap is-

[LIST]
[*]if hibernation is required, size=slightly larger than RAM;
[*]if NOT required, then plenty of swap is just a wastage of space, and with 8GB RAM, keep it 1GB or not at all.
[/LIST]
*[for others, who might be reading this post for an idea about their own requirement, usually 2GB swap is more than sufficient for 512MB-4GB RAM]*

(phew..!) Ok, enough of me now ;).

---

### Post by anewguy on 2012-03-17
> **varunendra said:**
> Ha-ha.. Now that you've encouraged me, here's more-

I frequently see posts about problems with resuming after sleep/hibernation, and have also seen at least one very experienced user mentioning in a post that 'it is very often' that hibernation in Ubuntu doesn't work very well so he doesn't recommend opting for it unless you really need it [should I duck for cover now..?? ;)]. However, I never use hibernation myself so can't say about the truth of that statement. Besides, it is obvious that we only get posts from those who get into trouble with it, not of those who have it going smooth. And maybe that number could make the 'problem cases' negligible, if can be obtained somehow.

So.. it would be best if users can decide whether or not they would be using hibernation. And the bottomline (IMHO) about the size of swap is-

[LIST]
[*]if hibernation is required, size=slightly larger than RAM;
[*]if NOT required, then plenty of swap is just a wastage of space, and with 8GB RAM, keep it 1GB or not at all.
[/LIST]
*[for others, who might be reading this post for an idea about their own requirement, usually 2GB swap is more than sufficient for 512MB-4GB RAM]*

(phew..!) Ok, enough of me now ;).

Yep!!

Does make you smile when you see people judging hibernation from the complaints - I just mention the number of complaints, not that it does or doesn't work.  As you said - nobody seems to think about all the others who DON'T post because things are going great for them.  And yet "outsiders" want to say some not-so-good things about Ubuntu, and Linux in general, because of the things reported on the forums!   It really does make you want to just scream "what about the 100,000's of users who AREN'T having problems?".  ;)  Bet we'll never win that one!

But, when I see a novice who is having trouble with general concepts in Linux, I try to steer them away from wanting to solve hibernation problems.  As I mentioned, I just don't see much use for it now for most of the users. They usually have a hard time trying to understand even the basics when you try to help them.  I know that's why I tell a lot of people to shy away from it.  Usually a bean-count below 20 indicates an extreme novice to me, and I figure it's best to save some things for when they have a better grasp of how things work.

BTW - my own personal experience:  hibernation on 3 laptops = fail, mainly because of how power options were handled, hibernation on 2 laptops - no problem.  Do I actually use it?  Only once in great great while - I usually just shutdown and reboot later - speeds being what they are these days.

Have a good one my friend!

Dave ;)

---

