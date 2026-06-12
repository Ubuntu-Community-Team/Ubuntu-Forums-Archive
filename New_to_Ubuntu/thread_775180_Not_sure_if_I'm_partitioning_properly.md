---
title: "Not sure if I'm partitioning properly"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by phoenix180 on 2008-04-29
Under 7.10,  I'm on the "Prepare disk space" part of the installation: now instead of the two options(guided-use entire disk and manual), I now have three: guided-resize SCSI1 (0,0,0), partition #1 (sda) and used free space and underneath it says:   New partition size:  __________51%(76.0GB)__________  Now-do I continue using this method and what exactly does this all mean? Does this mean that I am choosing(default) to use 51% of the drive for the installation?  I tried to do this under 8.04 but it froze so I'm trying my luck with 7.10 and then if everything goes well upgrade from there.  Under the manual option, I have the following: /dev/sda, /dev/sda1 ext3 /media/sda1 and the size for the is 162.3GB and underneath that /dev/sda5 swap and the size of that is 1.4GB.  If I tried to install manually, can I try install it on the second part? Sorry if this is all jumbled-I have been trying since this afternoon to get it working and so far nothing.  Thanks for your time everyone!

---

### Post by kk0sse54 on 2008-04-29
> guided-resize SCSI1 (0,0,0), partition #1 (sda)
This means that it is going to wipe your Hard Drive and install ubuntu fresh

> used free space 
This means that it is going to use the largest free space which is just unformated GB that isnt used in any partition and that it is going to install the swap and ubuntu partition on that.

> New partition size: __________51%(76.0GB)__________ 
I am assuming you are talking the little slider that you can slide back and forth which determines how much space you want ubuntu installer to partition from your hard drive for both swap and the ubuntu partition which will save your other OS and allow you to dual boot on start up.

---

### Post by Michl on 2008-04-29
I would recommend this approach (because it worked for me many
times and I am basically following instructions on [www.psychocats](www.psychocats)...
there is a how to on partitioning there that works well.

Run ubuntu off of a LIve CD.  I'd use 8.04.  With synaptic
download Gparted.  Run Gparted (enter gparted in terminal)
and then partition as you wish.  I do three partitions for
the disk with linux.  8 to 10 GB for the first one and it
is an ext3 partitio, then all but 2x your Ram for the second 
one, and this is also an ext3 journaling partition.  Then 2x your
ram for the third one and this is a linux swap partition.  You
will see these nicely represented on a bar and they will be
named when done, something like this:  sda1, sda2 and sda3.

Then I install ubuntu and do a manual partition.  The three
partitions you did show up and this is what I do. The first
partition has the mount point /.  The second partition has the
mount point /home.  The third is swap.  YOu choose the mount
points by highlighting the partition and click "Edit".
Since this is a fresh install all should be formatted.  So check
"format" for the partition.  There's nothing to check for the
swap partition.

So now you'll have /home on its own partition and so next time
when you upgrade ubuntu, you don;t have to format the parition with
/home on it.  The documents and other files will all be there and
many config files will be there, too.

I think I haven't missed anything, but double check with the
psychocats page I mentioned.  In any case, now is the time to
give /home its own partition.

---

### Post by phoenix180 on 2008-04-29
Thanks so much everyone!  I was driving myself crazy trying to figure it out.  I'm going to try the ideas listed once I can get 8.04 to run.  7.10(livecd) was running until it froze on me while I was waiting to see if my question(same one posted here) had been answered in the irc channel was but 8.04 just doesn't want to work-for now.  Anyway thanks again-you are lifesavers.

EDIT: Michl, this approach allows me to dual-boot? I can't dual boot because my windows partition is COMPLETELY screwed up. I want to be able to completely write over the C partition or rather just wipe out Windows and install Ubuntu as my main operating system.  I'm on the liveCD(7.10-hardy refuses to work on this computer) right now so I wanted to know what to do.  I just hope I get to finally install this wonderful operating system.  I was so nervous when starting out that my wireless connection wouldn't work but it worked immediately!  

C!oud, thanks as well for answering!  I feel completely lost and also silly for asking such simple questions

---

### Post by phoenix180 on 2008-04-30
Hello all! I tried to install 7.10 once again and the error that I keep receiving is in the screenshot that I have posted up.  Now I have had this problem in Windows also but it was never specifically stated.  I couldn't even do a proper system recovery(you know the whole press F10 to re-install windows to the C drive) because it would tell me that something is wrong with the C partition.  Is it possible to delete the C partition, leave the D partition alone and install 7.10 in the empty space? Thank you all in advance!

---

### Post by kk0sse54 on 2008-04-30
You can delete the C: partition by running the ubuntu live CD and then running the program Gparted which lets you manage your partitions on your computer.

---

### Post by kk0sse54 on 2008-04-30
Also have you tried burning another cd and check it for defects? Another alternative to the liveCD is the alternative installer which is just a text based installer.

---

### Post by Michl on 2008-05-02
What I was describing was partitioning a whole disk for linux.  I was assuming that windows is on a second hard disk.  If you dual boot from one disk, then gparted will show you where the ntfs partition is and you wouldn't mess with it. You would then partition per above the remaining hard disk.  That's what I do on my laptop.

But if the windows system on the windows parition is screwed and you can't recover, then here are some of your options.  You could keep the windows partition as you have it and just try to reinstall windows and then install ubunutu.  Windows will only see its own partition and install there.  An option I would consider is that I the hard disk was messed-up by my partitioning attempts and that's my problem.  So I would start from scratch and zero fill the hard disk, using gparted partition the hard disk so that I have a partition for windows and three partitions for linux per above, install windows and install linux.  ALternatively, zero fill, install windows and then install ubuntu in the free space. What you lose doing it that way is having a home partition, which I think is a good idea just for the kinds of problems you are running into.

Also, I would not mess with Gutsy anymore.  The installer
was buggy from my experience, but Heron;s installer is
smooth.

---

