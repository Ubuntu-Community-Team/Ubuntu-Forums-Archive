---
title: "[SOLVED] Looking for help/advice about partitions"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by supwest on 2008-10-29
Hi everyone,

I recently did Wubi installation of hardy, and I'd like to change it to a dual boot. I've got two HD's, and I'd like to leave the C: Drive as Windows and have the G: Drive as Ubuntu. Currently the Wubi installation is on the G: Drive, which has a capacity of about 75GB. I've used GParted (in LiveUSB partedmagic) to resize the NTFS partition to about 25GB (22GB used), and have 48GB unallocated after the NTFS partition (there is also 203 MB unallocated before the NTFS partition). I was about to create a new partition to which I can transfer the Wubi install, but I got cold feet. I've done some searching in the forums, and in various guides, but I'd like to be sure that I'm not going to mess it up :).


What I'd like to do is have a / partition of about 15GB and a /home partition as the rest (as from what I've read people seem to like having this set up), and then the swap partition. But I'm pretty new to this (this will be the first time I've created a partition), and I'm not sure the best way to do it. Should I create a new partition with most of the unallocated space, with some space at the end for the swap, transfer Unbuntu there and then create another partition where the NTFS partition is?

I'm sorry if this is a little confusing, but I'm a little confused about it, so it all works out :) 

Thanks

P.S. I'm planning on using intrepid when it comes out, and haven't done much in hardy, so I could just get rid hardy, set up the partitions, and then install intrepid. The only thing keeping me from doing that is I've downloaded WoW (since I can't find my install CDs) and I'd rather not have to do that again.

---

### Post by Kellemora on 2008-10-29
Hi Sup

I hate to see a question go unanswered for so long.
I'm a noob to and what you are saying sounds right to me.
But to be honest, I have no idea what Wubi is?
I have a triple boot, CentOS, Debian, Ubuntu on this machine.
Have Edubuntu on another machine, just learning that.

Here is where I think the confusion is in your post and why you haven't received any responses.
In your first paragraph you said you had the Doze on drive C and installed Ubuntu on drive G.
Then you continue with all the shrinking of the NTFS partition.  Spock says that's illogical!

If the Doze is on drive C and Ubuntu is on drive G, WHAT drive are you doing all this NTFS resizing on and why?????

You ARE on the right track with having a / partition a swap partition and it's very wise to keep /home as it's own partition using up the rest of the drive.  But all of Ubuntu really should be ext3 not NTFS.

You WILL need a bootloader to tell your computer WHICH OS you wish to boot up.
Stage 1 of the bootloader is placed in the MBR of the boot drive.  I would keep the rest of Grub on the drive (or partition) that contains Ubuntu.

Perhaps if you rethink your post and mark this one solved then make a new post taking into consideration what I said here, one of the Guru's might pick up on it and could help you better than I can.

TTUL
Gary

---

### Post by supwest on 2008-10-29
@Kellemora

I didn't know what Wubi was either until about 2 days ago :). Wubi is an installation of Ubuntu inside Windows, just like another program, but you can boot into it using the Windows Boot Manager. I guess it's another way of trying it out (I used it because I couldn't boot from my CD drive). So Ubuntu is running inside the NTFS partition on the G drive. I need to set up a partition to transfer it to, and then get rid of the NTFS partition to let Ubuntu have the whole drive. I just want to make sure I get the order right, so I have as much room as possible in the /home parition (which I think is what I want). I'm also not sure about naming the partitions, but that's later I suppose. I'll see if this post gets any hits, and if not I'll repost like you suggested.

Thanks,
CW

---

### Post by sharkster2007 on 2008-10-29
Hiya supwest

I too have two Hard disks in my PC and I am new to Linux. I find the best way is too install your windows to C: (probably already done this)

Then boot from an unbuntu Live CD and select the other drive in your PC for Linux in the partition manager part of ubuntu (be very carefull you dont select your windows one as this will erase all data on it). GRUB or sometimes called bootmanager part should be aimed at the 1st hard disk BUT NOT THE LINUX INSTALLATION ITSELF

This worked fine for me I was able to dual boot between Xp And Ubuntu (Before I migrated to a different Linux Distro because of hardware detection problems with 3d effects).

Hope this helps you, i know wubi is like a virtual Pc installation in windows but have never used it myself.

---

