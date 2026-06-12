---
title: "Changing swap memory"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by cheatos on 2011-09-30
Hi,

I had ubuntu installed already a few days ago but now I've recently read that the swap space should not exceed 1GB.

During my installation of ubuntu I didn't know what this space was good for (thought it might be for the system itself) allowing it a 21GB storage space.
Is there any way I can repartition my drive while I'm already having linux installed (and Windows on another partition)

Thanks for any advice

---

### Post by nothingspecial on 2011-09-30
Hi,

You need to boot a live cd or usb then run gparted.

From there you need to shrink the swap partition (and the partition that contains it if that's how it's set up), then grow your your Ubuntu partition into the free space.

Make sure all your data is backed up first.

---

### Post by CatKiller on 2011-09-30
Last time I tried it, gparted changed the UUID of the swap partition on a resize, even though it shouldn't have. You may need to edit your /etc/fstab to reflect this change after you're done.

There's nothing wrong with having your swap partition over 1 GB, although 21 is overkill. Twice your RAM if you use hibernate, no more than 2 GB if you don't, is the rule of thumb. Again, nothing wrong with having more than 2, it's just that it's unlikely to be used.

---

### Post by cheatos on 2011-09-30
okay so as the update to ubuntu 11.10 will be soon, will I be able to rearrange that while upgrading?
Because this seems to me as being not really important if I don't use all the free disk space, am i right?

---

### Post by CatKiller on 2011-09-30
If you're doing a fresh install for 11.10, sure.

---

### Post by Blasphemist on 2011-09-30
Please run GParted and take a screen shot of your partitions and post it. Depending on what space you have, there could be multiple options. You could actually create a whole new partition for oneiric or some other distro flavor to go into from what you remove from swap. The amount of swap actually should be just a bit more than the amount of memory you have. Depending on where the partitions are on the disk, the newly freed space could also go to your existing partition. How much do you available in your existing ubuntu partition?

---

### Post by QLee on 2011-09-30
I don't know why people still recommend twice RAM, that is a old recommendation from the days when systems didn't have as much RAM as modern systems.

In order to hibernate you need a swap partition of approx. the same size as RAM, so same size is the correct recommendation. Consider how suspend to disk (hibernate) works, it copies the contents of RAM to disk and then restores to RAM from disk when it resumes. You aren't going to have more than the contents of your RAM to store. (and usually less because your RAM isn't usually all being used, thus usually you need less than the size of your RAM).

CatKiller has a good point about the UUID of your swap file though. After following nothingspecial's advice to resize, do check and make sure your system knows the correct information for your swap.

As stated, if you do a complete new install of 11.10 you could adjust things then, just like when you installed 11.04 fresh. If you update to 11.10 there won't be an opportunity to change partitions and you would have to follow nothingspecial's advice to resize. Of course, having it too big won't bother anything except you won't have that space to use for something else.

---

### Post by CatKiller on 2011-09-30
> **QLee said:**
> I don't know why people still recommend twice RAM, that is a old recommendation from the days when systems didn't have as much RAM as modern systems. 

Because even if you have a lot of RAM, you might use a lot of RAM. Which means you could end up with stuff in swap. Then you'll need some extra if you want to fit everything in when you hibernate. Hard drives are extremely cheap and running out of addressable memory is very bad.

---

### Post by QLee on 2011-09-30
[QUOTE=CatKiller]Because even if you have a lot of RAM, you might use a lot of RAM. Which means you could end up with stuff in swap. Then you'll need some extra if you want to fit everything in when you hibernate. ...[/QUOTE]

I understand your logic but that is not the way it works. 

Using your logic a system with 8G RAM would use a 16G swap (2x), eh? 

I'm not expecting you to believe me, after all you don't know me. I'm going to point you at the Ubuntu Community swap faq, where it is stated under the heading, "How much swap do I need":

"As a base  minimum, it's highly recommended that the swap space should be equal to  the amount of physical memory (RAM). Also, it's recommended that the  swap space is twice the amount of physical memory (RAM) depending upon  the amount of hard disk space available for the system (although this  "recommendation" dates back from a time when physical RAM was very  expensive and most Unix systems ran with many processes in swap space - a  situation that hardly applies in most situations these days, but  ancient Unix/Linux myths like this "recommendation" tend to survive well  past their "use by" dates). In reality, if you use hibernation you need  what was outlined in the relevant paragraph above, otherwise you need  as much swap space as your system will use - which actually may be very  little in a modern hardware setup. The only downside to having more swap  space than you will actually use is the disk space you will be  reserving for it."

---

### Post by CatKiller on 2011-09-30
It's not logic, it's a rule of thumb. As I said quite some time ago.

If you hibernate, you need some quantity of swap that is some amount larger than your RAM.

If you don't hibernate, there is absolutely no point in having more than 2 GB.

With hard drive prices as they are, there is absolutely no point trying to optimise for swap size.

Clear?

Please stop trying to derail this guy's thread.

---

### Post by nothingspecial on 2011-09-30
Let's try to keep this thread nice guys :)

Let's help the user and not get into a discussion.

+1 for checking your swap partition is still mounted correctly btw.

---

### Post by Kixtosh on 2011-09-30
> **cheatos said:**
> Hi,

I had ubuntu installed already a few days ago but now I've recently read that the swap space should not exceed 1GB.

During my installation of ubuntu I didn't know what this space was good for (thought it might be for the system itself) allowing it a 21GB storage space. ...I agree with what has been said on both sides of the argument about swap. I currently have a laptop with 2GB of RAM, and my swap is 2GB. It has always run perfectly, although I did notice quirky behavior when my swap partition was initially installed with just 1GB by default, for whatever reason. When I check the System Monitor (from the System Menu in the top panel, then choose "Administration"), swap is almost never being used. Generally, I'm not even using half of my RAM either.

I don't really use hibernation, although it has worked when I have tried it. It takes much longer to enter hibernation than the three seconds required for shut down, and there is no obvious improvement compared to the twenty-three seconds it usually takes to boot either.

So I would ask the following:

1) How much RAM do you have?
2) Do you want to use hibernation?

Proceed from there. I changed my swap partition from 1GB to 2GB using GParted on the same LiveCD I used to install Ubuntu, but you have to turn swap off (right click with your mouse on the swap partition in GParted and you'll see the option there) to stop using it before it can be resized.

---

### Post by cheatos on 2011-10-03
Thank you guys, I have been away over the weekend and will be running GParted tomorrow.
I hope you will then still be looking at this thread ;)

---

### Post by cheatos on 2011-10-04
Hi,
so here comes the screenshot, please give me the advice which fits best fo my computer ;)

I have 2GB RAM and actually I'm not using any of the Swap Partition (I don't know how this changes, when I'm running more programs, but I'm only using ubuntu to do some office stuff and games like super tux, so not too much to do, I think.

---

### Post by cheatos on 2011-10-04
Dmmit, I forgot the picture, here it comes.

---

### Post by Paqman on 2011-10-04
> **cheatos said:**
> 
I have 2GB RAM and actually I'm not using any of the Swap Partition (I don't know how this changes, when I'm running more programs, but I'm only using ubuntu to do some office stuff and games like super tux, so not too much to do, I think.

You'll probably find you almost never use any swap then. I would go for 1GB on a desktop, or 2GB if it's a laptop you want to hibernate.

To change the size of your swap now you'll need to right click on it in Gparted and "swapoff" before you can shrink it. Or you can do this using the "manual partitioning" option during a fresh install (which just uses Gparted anyway).

---

### Post by cheatos on 2011-10-04
Thank you, I'll do that then and come back here to tell you if it worked well.

Okay, the shrinking of the swap space worked very well, but how can I now add the free space to my Windows partition?

---

### Post by Paqman on 2011-10-04
You would need to move sda6 (and the extended partition that contains it) to the right, then expand the NTFS partition into the space created. Moving a partition to the left or right can be a very slow operation, so be patient.

Making a backup before doing it would be an excellent idea, too.

---

### Post by audiomick on 2011-10-04
Move sda6 to the right, *then shrink down sda2*, then expand sda1. This _will_ take some time. Do backup anything important before you start.

---

### Post by cheatos on 2011-10-04
So, I will be able to change the linux partitions size while being logged in to linux?
That seems like a pretty critical process to me...

Furthermore, how do I actually "move" the Widows partition?
If I click the Resize/Move button it just allows me to adjust the size of the partition.

---

### Post by Paqman on 2011-10-05
You have to boot into a LiveCD or USB and deactivate your swap partition before you'll be able to make changes. You can't change any partition while it's in use.

You don't need to move your Windows partition, just expand it into the space that will be created to the right of it when you move/shrink the Linux partitions.

---

### Post by cheatos on 2011-10-05
I still don't really get the shrinking part.
How is it done?

What I have done up to now is shrink the swap memory to 1GB (while I was logged in as usual)
Then what do I have to do next?
I can post another screenshot if that might help...
What I don't understand is that I can't change the Windows partitions size even though I unmounted it.

---

### Post by audiomick on 2011-10-05
Post a screenshot, so we can see where you are up to. That might help, I think.

---

### Post by cheatos on 2011-10-06
Okay, so this is how it looks like and what I understood was moving the Windows partition to the right so I can connect it to the free space on the right of the linux-swap partition.

How am I going to shrink and  move each partition now?
And in which direction because what I have seen I can shrink them in both directions, to the left and to the right.

I'm pretty confused at the moment sorry

---

### Post by audiomick on 2011-10-06
So you can get to the point where you are seeing something like in my screenshot, right?

What you have is your empty space at the end of (on the right hand side of) your extended partition.
To the left of that is the swap, then further to the left sda6 which has your Linux on it.

You can only move the start or end of a partition that you want to expand, into empty space that is adjacent to that edge. This applies, incidently, not only to Gparted, but to all of the 3 or 4 partitioning tools I have seen.
You want to expand your sda1, your windows partition. What you need to do is shuffle your empty space down until it is directly next to sda1.

To do this, you will have to
Move the right hand end of sda 5 along to the end of the empty space, and the left hand end to the right until you are back at the size you want. This can be done in one operation, but I think this has to be done before you can do the next step.
The next step is to do the same with sda6. This will leave your empty space to the left of sda6, but still inside the extended partition sda2.
Therefore, you must now shrink down sda2 until there is no empty space inside, i.e. move the left hand end to the right. 
Now, you should have your empty space between sda1 and sda2, and should be able to expand sda1 into the empty space.

edit: which windows is on the windows partition? If it is Vista or Win7, you might be better advised to do the change to the windows partition, i.e. expand sda1 into the empty space once you have it adjacent to that partition, with the windows partitioning tool. Having done that, you should start windows a couple of times and let it do any disk checking stuff it wants to do.

---

### Post by westie457 on 2011-10-06
Hi cheatos the advice you have had already is very good so I am going to add more details.

The warning is 'This will take at least 2 hours to complete and DO NOT QUIT Gparted while resizing is in progress. If you do you will lose at least one operating system or completely bork (technical term) all of the partitions.
The recommendation is to work on one at a time and let it finish. This is for your sanity to stay at an acceptable level.

Ready, then we will begin.

Boot into a Live CD in try mode, open Gparted.
Ensure you are looking at the drive you want to work on and unmount all of the partitions.
Select the first partition to the left of the free space and click on Resize/Move. In the pop up window slide the whole thing to the right as far as it will go - you might end up with a 1MB area of free space, nothing to worry about though this is normal.
Click Okay/Accept and then click Apply.
Wait for this to finish (2 hours remember)

Edit- Do the above for every partition inside the extended one.

Next is the extended partition, just select as before and move the left hand end as far to the right as possible. Click Okay and Apply. Wait.

Finally the Windows partition. Select it and slide the right end to the right, Okay and Apply. Again WAIT FOR IT TO FINISH.

When everything has finished it is very important that you boot into Windows and let CHKDSK run and verify the Windows partition is okay. After that boot into Ubuntu as normal, everything should be working. 

If not post back here and we try to sort out where it went wrong.
Any questions along the way just ask.

---

### Post by larrypg on 2011-10-06
I know this is probably not the most helpful response but... Isn't this a lot of work to go through with the possibility of destroying either or both operating systems just to use 19 extra gigs of free space?  You already seem to have enough space in both.

---

### Post by audiomick on 2011-10-06
This is a valid point, of course.

On the one hand, it is good practice, and a good thing to know how to do.

On the other, there will most likely be a fresh install at some point in the future. You could wait until then and sort it out in the process.

I personally would be irritated knowing there was a bit of space on the drive that wasn't earning it's keep. ;)

---

### Post by westie457 on 2011-10-06
> **larrypg said:**
> I know this is probably not the most helpful response but... Isn't this a lot of work to go through with the possibility of destroying either or both operating systems just to use 19 extra gigs of free space?  You already seem to have enough space in both.

You are right.

All the way through the above quote. However the OP wanted advice and information and help. Whether they choose to act on it or not is up to them.

---

### Post by Elfy on 2011-10-06
> **audiomick said:**
> I personally would be irritated knowing there was a bit of space on the drive that wasn't earning it's keep. ;)

I'll not let you see my drive info ... 


The other option the OP could take of course is to boot the livecd - turn off swap - delete and recreate swap,edit fstab to account for new UUID create a partition with the unallocated and mount it in fstab for use.

---

### Post by cheatos on 2011-10-06
Okay, now I understand what you wanted to explain with all that shrinking and growing stuff.

I don't need the space at the moment, but my computer has been reset a few weeks ago, so I still have a lot of data on external drives and I will add it during the next weeks.
As this process seems to take a really long while and you've more than once warned me about it, I'm still thinking about doing that or just installing 11.10 not with the update.

Will all my personal settings be gone then or can I back them up in some easy way, before installing 11.10?

I still thank you all for your replies, especially Catiller and audiomick.

I'll mark this as solved.

---

### Post by Elfy on 2011-10-06
> Will all my personal settings be gone then or can I back them up in some easy way, before installing 11.10?
Any of this will be in your home directory - just backup what you want to keep safe - all I ever backup is mozilla/tbird and xchat 

Everything else gets new when I Reinstall

---

### Post by audiomick on 2011-10-06
> **cheatos said:**
> 
Will all my personal settings be gone then or can I back them up in some easy way, before installing 11.10?.

Your personal config preferences are all saved in your /home/user folder. If you allow viewing of hidden files, you will be able to see them.

If you copy out the config files you want to keep to somewhere else, then put them back after the install, your preferences should then be back for those things. I have done this successfully, but it is a fair amount of bother.

What is more common and less messing around is to have /home on its' own partition, and to re-use the partition without formatting it on the fresh install. I have done this a number of times. You don't have /home separate. If you are interested in reading about how to change this on an existing install, look here
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

