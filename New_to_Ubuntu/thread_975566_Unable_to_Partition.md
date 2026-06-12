---
title: "Unable to Partition"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by EPrips on 2008-11-08
So I've tried several times to install Ubuntu using the Guided Partition option, and every time I get a "Unable to resize the disk" error, or something of that nature. Another odd thing is that the proportions of the guided partition change sometimes, which is something I thought would be constant. Is there anything I can do in preparation for partitioning to prevent this error? Or anyway to get more details on the error so I know how to fix it?

---

### Post by kansasnoob on 2008-11-08
Would you please be as specific as possible about what you're doing?

Trying to set up a dual boot?

How many partitions already exist?

The general layout of the drive(s)?

If you can boot the live CD possibly post the output of:

```
sudo fdisk -l
```

Absolute best info for me would be a screenshot of the Gparted gui like this:

[ATTACH]91737[/ATTACH]

I do realize that can be a pain from the live CD (almost requires Photobucket or something of the nature).

---

### Post by Elfy on 2008-11-08
> I do realize that can be a pain from the live CD (almost requires Photobucket or something of the nature).Should be able to do so with the screenshot tool in the apps/accessories menu, assuming that internet is available.

Add it to the post with the manage attachments option in New Reply

Make sure that your win is defragged a couple of times before you try to resize.

---

### Post by EPrips on 2008-11-08
1. I'm trying to set up a dual boot between Vista and Ubuntu.
2. I believe three partitions currently exist. Vista, Free Space, and HP Backup.
3. Output of sudo fdisk -l:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c7ad93e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19537   156928928    7  HPFS/NTFS
/dev/sda2           28866       30401    12337920    7  HPFS/NTFS

4. GParted Screenshot

---

### Post by EPrips on 2008-11-08
Bump.

---

### Post by Elfy on 2008-11-08
Don't bump that quickly.

You could use the Use Free space option - I think that's what it's called, NOT the whole disk option.

ALternatively create partitions yourself - System > Admin menu - PArtition Editor

Create an extended partitionin the free space - then 3 logicals inside 

1 for / - approx 10Gb should be sufficient - format to ext3
1 for swap - if hibernate needed then swap = RAM; if not then swap 1.5X RAM if RAM less than 1Gb - otherwise 512Mb should be enough - format to linux-swap
1 for home using remaining space - format ext3

Start install - use manual partition - choose each partition and edit - pick / as mountpoint for the 10Gb partition and /home for the larger

---

### Post by EPrips on 2008-11-08
> **forestpixie said:**
> Don't bump that quickly.

You could use the Use Free space option - I think that's what it's called, NOT the whole disk option.

ALternatively create partitions yourself - System > Admin menu - PArtition Editor

Create an extended partitionin the free space - then 3 logicals inside 

1 for / - approx 10Gb should be sufficient - format to ext3
1 for swap - if hibernate needed then swap = RAM; if not then swap 1.5X RAM if RAM less than 1Gb - otherwise 512Mb should be enough - format to linux-swap
1 for home using remaining space - format ext3

Start install - use manual partition - choose each partition and edit - pick / as mountpoint for the 10Gb partition and /home for the larger

Sorry about the bump, still getting used to how quickly the forums move and whatnot. 

So here's a screenshot of GParted with those modifications, I have not yet accepted them as I wanted to make sure I did it correctly first. I'm unable to shrink the sda1 partition, I tried a few times before doing what you see in the screenshot.

---

### Post by kansasnoob on 2008-11-08
I would personally NOT do that! Much of the reason is personal choice!

Where Forestpixie said, "You could use the Use Free space option - I think that's what it's called, NOT the whole disk option." That's what I think you should do!

I'll grant you that you'll have no separate home partition or shared partition, but your planned layout is a bit of a mess!

I would definitely cancel that!

Another post following!

---

### Post by kansasnoob on 2008-11-08
Look at this screenshot:

[http://www.psychocats.net/ubuntu/images/dualboot10.png](http://www.psychocats.net/ubuntu/images/dualboot10.png)

You see where it gives you the choice to use "Guided - use the largest continuous free space"? That's what I think you should do!

Otherwise spend some time really studying this:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Then you can create a proper complicated layout!

---

### Post by kansasnoob on 2008-11-08
BTW, I think your bump was OK considering the complexity and possible downfalls regarding your issue!

---

### Post by EPrips on 2008-11-08
Alright, I guess I'll use the Free Space option to be safe. Hopefully it will actually allow me to partition this time.

Edit: Here's what happens when I select the Free Space option. It does 100% Ubuntu.

---

### Post by EPrips on 2008-11-08
Here's what the Guided Partition looks like as well.

---

### Post by kansasnoob on 2008-11-08
> **EPrips said:**
> Alright, I guess I'll use the Free Space option to be safe. Hopefully it will actually allow me to partition this time.

Edit: Here's what happens when I select the Free Space option. It does 100% Ubuntu.

I've noticed the new graphics leave a bit to be desired. I believe it's still safe to do what I said.

First of all be sure you have all that other partitioning canceled out!

---

### Post by EPrips on 2008-11-08
Ok, I'll take your word for it and try the free space partition.

---

### Post by kansasnoob on 2008-11-08
> **EPrips said:**
> Here's what the Guided Partition looks like as well.

But look at that!

You have the wrong thing ticked!

---

### Post by kansasnoob on 2008-11-08
> **EPrips said:**
> Here's what the Guided Partition looks like as well.

But look at that!

You have the wrong thing ticked!


This:

[http://ubuntuforums.org/attachment.php?attachmentid=91750&d=1226184374](http://ubuntuforums.org/attachment.php?attachmentid=91750&d=1226184374)

shows you have "guided resize chosen rather than "guided - use largest continuous free space"!

---

### Post by EPrips on 2008-11-08
Yeah, I was showing both just so people knew what each one was going to do.

---

### Post by kansasnoob on 2008-11-08
If you go forward you're going to wipe out Vista!

Read and pay attention!

There are four options! You chose the wrong one!

---

### Post by kansasnoob on 2008-11-08
> **EPrips said:**
> Yeah, I was showing both just so people knew what each one was going to do.

Well, you're giving me a heart attack!

---

### Post by EPrips on 2008-11-08
> **kansasnoob said:**
> If you go forward you're going to wipe out Vista!

Read and pay attention!

There are four options! You chose the wrong one!

If I use the Free Space I won't wipe Vista will I? The first image I posted? I just posted the second image to show people what it looked like. I'm planning to use Guided Free Space to install.

---

### Post by kansasnoob on 2008-11-08
> **EPrips said:**
> If I use the Free Space I won't wipe Vista will I? The first image I posted? I just posted the second image to show people what it looked like. I'm planning to use Guided Free Space to install.

Get it right in your mind: choose "Guided - use largest continuous free space"!

DO NOT USE: either of the other "guided" options or you'll muck it up! BAD!

---

### Post by kansasnoob on 2008-11-08
Absolutely, positively, if your hard drive still looks like this:

[http://ubuntuforums.org/attachment.php?attachmentid=91741&d=1226176027](http://ubuntuforums.org/attachment.php?attachmentid=91741&d=1226176027)

You just need to choose "Guided - use the largest continuous free space" and you'll be in business!

Why is that hard?

---

### Post by louieb on 2008-11-08
> **EPrips said:**
> 
So here's a screenshot of GParted with those modifications, I have not yet accepted them as I wanted to make sure I did it correctly first. I'm unable to shrink the sda1 partition, I tried a few times before doing what you see in the screenshot.

Thats a very  good way to go. Go for it. When you get to the partition part of the install choose manual.   Click the smaller partition chose edit and and make its mount point / (root). Do the same for the larger partition. Edit it and make the mount point /home. Don't worry about swap that will take care of itself.   
Some other partitioning ideas can be found on the psychocats site and here are some of mine. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

