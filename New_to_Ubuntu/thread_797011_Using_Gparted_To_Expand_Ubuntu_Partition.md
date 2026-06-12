---
title: "Using Gparted To Expand Ubuntu Partition"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by teamcoltra on 2008-05-16
When I first installed Ubuntu, I installed it to play around with, and I fell in love.

When setting up my partitions in the beginning I set them up like this:

[Windows(NTFS)][Linux(EXT7)]{[Extra Shared Space[NTSF]]}

{} = Extended


I would like to reduce the size of my shared space, and increase my tiny 11 gig linux partition to about 30 gigs (and reduce my 80 gig extra space down to 60ish of course) 


I am not TOO worried about losing everything out of my 80 gig partition because its just music and movies... however, I would prefer not to lose them. Losing my information in my Linux partition is not an option. So I would like to do this process without formatting. 

I assume I use gpart but I don't know what to do after that.

---

### Post by sam_delta on 2008-05-16
yes gparted is able to resize partitions without format, but keep in mind that it is always way safer to backup any data before any operations

also, to resize any partition, you will have to unmount it, that means, that if you want to resize your actuall ubuntu partition, youll have to unmount it, so youll have to do it with the live Cd, the live CD has gparted installed by default.

so you can resize your "shared partition" in ubuntu, but to make ubuntu larger, youll have to use the live cd

tell us how it goes, 
sam

---

### Post by mister_pink on 2008-05-16
Load up the live CD - you won't be able to do it in your normal install because its mounted, so it can't be changed. The interface is fairly self explanitory, shrink the right hand one then expand the other. Be warned this will take an absolute age probably, moving partitions involves shifting large quantities of data.

---

### Post by rlcomstock3 on 2008-05-16
I always seem to get errors when I do it to, just so you are warned.  Gparted isn't the most reliable tool in the world, but it gets the job done.

---

### Post by PinkFloyd102489 on 2008-05-16
To be compeltely honest, Vista's Disk Management blows Gparted out of the water. If you can, try to use it. I know it's being rather counterproductive with the whole open source thing, but if something works, it works.

It wont recognize the paritions by name, but you should still be able to resize them as long as you know which one is which.

---

### Post by teamcoltra on 2008-05-16
Well the last time I used gparted (before this last successful time) I created like 30 5 gig partitions by accedent, and am afraid to do it again. I might just try using a tool in windows (i am using XP Media... I rolled back from vista, i didn't like it)

---

### Post by Oldsoldier2003 on 2008-05-16
thats odd that you all have so much trouble with Gparted... I use it extensively and have yet to have a single issue. of course the day I blow off making a backup will be the time it goes nuts...

---

### Post by teamcoltra on 2008-05-24
[IMG]http://i27.tinypic.com/2nv6p7o.png[/IMG]

It says I cannot resize THIS partition (the only one I cannot)

---

### Post by louieb on 2008-05-24
Just an idea. once you shrink the NTFS data partition. Instead of growing your Linux partition. Make another partition and mount it as /home. The psychocats link in signature has a how to  on getting  your home data move over and setting up /etc/fstab to use the new location.

Has the advantage of being able to shirnk the data partition from the right. much safer and faster. 5GB is more that enough for the / (root) partition. I normally make mine around 7GB right now mine is using 3GB.    

something like this 

[LIST]
[*]Windows
[*]Ubuntu Linux Root (/)
[*]NTFS data partition
[*]Ubuntu Linux home (/home)
[/LIST]

---

### Post by mister_pink on 2008-05-25
Partition magic can't handle certain types of linux disk (ext3 with indexing on I think). Just give gparted (either on the ubuntu liveCD, or there's a gparted liveCD) a try, its never let me down. And remember - backup, backup, backup.

---

