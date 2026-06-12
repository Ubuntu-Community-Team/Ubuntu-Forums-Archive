---
title: "Ubuntu on multiple disks"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by ObiDamnKenobi on 2012-10-23
[COLOR=#000000]I'm relatively new to linux, but trying to plan out my HDD config for dual boot win7+ubuntu on my desktop (had it before with vista but wiped when I got 7). I'll probably go with separate disks for each OS. I'd like to put Ubuntu on an 128GB SSD plus half of a larger 1TB disk. And the same setup with win7 on SSD plus the other 500GB with Steam etc.[/COLOR]
 
[COLOR=#000000]This may be a stupid question; but is there an option in the package managers to install to the spinning disks, instead of the SSD? I haven't looked much into it, but I imagine if I keep hitting install there I might fill up the SSD unless there is a way to put some software on the larger disk. I want to try some games in wine for example. Can I apt-get and install somewhere else?[/COLOR]
 
[COLOR=#000000]sorry if these are stupid questions[/COLOR][IMG]http://forums.anandtech.com/images/smilies/familiar/blush.png[/IMG][COLOR=#000000] I'm trying to figure this out before I install and play around so I can plan my partitions etc. Bit of a chicken/egg problem.. [/COLOR]
 
Somewhat related: I edit my RAW photos in lightroom/PS at the moment, stored on another 1 TB internal drive. Would there be any problems trying to edit these in Ubuntu, on the same NTFS drive? I want to see whether or not I can do a decent photo edit workflow in ubuntu, to get over my Windows  dependancy.. :) 
 
Thanks!

---

### Post by Cheesehead on 2012-10-23
> **ObiDamnKenobi said:**
> is there an option in the package managers to install to the spinning disks, instead of the SSD? 
 
....

Somewhat related: I edit my RAW photos in lightroom/PS at the moment, stored on another 1 TB internal drive. Would there be any problems trying to edit these in Ubuntu, on the same NTFS drive?


With package management, you DON'T get to choose where a package installs in your directory tree.
However, your installed system should easily fit in much less than 10 GB. And you can mount different parts of your directory tree on any disk you want.
So, for example, you can leave the system (/) on 10GB on a partition of the SSD, but put /home/yourname on the spinning disk, and even put /home/username/frequently-used on a different partition of the SSD. The /etc/fstab file pulls it all together seamlessly, and it's not hard to figure out.

Using Ubuntu to write to NTFS is not recommended for more than occasional use. Microsoft owns the format, has never released it for public use, and has the right to change it at any time. Heroic volunteers have reverse-engineered compatibility, but it's not guaranteed.

---

### Post by ObiDamnKenobi on 2012-10-24
ok, thanks! 
From looking around too it seems like it's best to just throw ubuntu onto a 128 GB disk and not fuss with it. I shouldn't really have any problem with just OS and programs on that space. 
 
My image editing setup needs some more thought though. Your answer that NTFS and ubuntu don't play nice wasn't really surprising.. Sounds like the safest approach is to duplicate my images into separate Win/ubuntu storage, while I experiment with transitioning. Not like storage is that expensive these days. I do have them all backed up to a ubuntu home server, but I prefer to work with a local file. 
thanks

---

### Post by oldfred on 2012-10-24
The issue with NTFS is the Windows system partition, it does not like a lot of writes into it, it seems. But it may be more user issues. 
The Linux NTFS driver shows all the files & folders including the hidden one's Windows hides. So users can make mistakes. (In Windows I would unhide system files and get into trouble all the time.) 
Also some users try to hibernate in Windows, then read & write a file that was hibernated in Windows causing corruption to the hiberfile or losing changed file.

I always suggest making the Windows system partition as read only in Ubuntu and use a shared NTFS data partition. 

I have used a shared NTFS partition for years without issue. I have my Firefox & Thunderbird profiles and all my photos for use from the Windows version of Picasa in .wine.  I now do not use XP but ran the same applications from XP & Ubuntu and some were not even the same version. But it may depend on what applications you will be using.

---

