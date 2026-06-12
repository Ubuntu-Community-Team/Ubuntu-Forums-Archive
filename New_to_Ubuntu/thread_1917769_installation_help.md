---
title: "installation help"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by harun123 on 2012-01-30
Hi...I've decided to change windows for ubuntu.Now, is it possible to keep music,movies etc.,which i have on one seperate partition??Can I install ubuntu on existing partition which i use only for windows, without having to delete my files on other partition?:confused:

---

### Post by halitech on 2012-01-30
if you actually have separate partitions then yes, you can keep your music, etc on a separate and install Ubuntu on the windows partition. Just make sure you pick the right partition to install Ubuntu on.

---

### Post by harun123 on 2012-01-30
Is 25 GB gonna be enough?

---

### Post by halitech on 2012-01-30
for the ubuntu install? yes it should be more then enough. I would give \ about 10-12gig and the rest for \home. Then you can mount the other partition after you get the install done.

---

### Post by Double.J on 2012-01-30
> **harun123 said:**
> Hi...I've decided to change windows for ubuntu.Now, is it possible to keep music,movies etc.,which i have on one seperate partition??Can I install ubuntu on existing partition which i use only for windows, without having to delete my files on other partition?:confused:

Welcome to the forums!

I agree 25GB is more than enough. If you are already using a separate partition for all your data, I don't really see a need for a separate home partition, but that's of course personal preference :)

If you are new to linux in general, it may be worth installing ubuntu alongside windows, so you can have the best of both worlds? then if you're sure you want rid of windows it's pretty easy to delete and give the space over to Ubuntu. I only offer this as Ubuntu can't do EVERYTHING and you have already paid for windows one way or another :)

As for your media from the windows partition, you'll probably want to install the ubuntu restricted extras package from the software centre so you can play all your media.

Also with data on a separate partition, it's probably good to allow that partition to mount automatically. Decide where you'd like it to mount - in your home directory, in the /mnt directory - basically not in /media; this is really for removable devices, and as you'll want access to it all the time (and probably not popping up in your launcher) it's best to mount it somewhere else. First use mkdir to create a directory. you could go for /home/user/media, but for simplicity, I'll use /data ;) -open terminal with CTRL+ALT+T
```
sudo mkdir /data
```

then use fdisk to find out your partition numbers:```
sudo fdisk -l
``` Taking note of the /dev/number of your NTFS data partition - i.e /dev/sda4 and use this numer and directory to mount at to make an entry in the fstab - this is the list of what to mount at boot, and where to mount it. back up your file with this
```
sudo cp /etc/fstab /etcfstab.bak
```Then edit the table with```
gksudo /etc/fstab
```A text edditor will open, add in a line similar to
```

#Windows data Partition
/dev/sda4   /data   ntfs-3g   rw,auto,users,exec,sync   0 0
```
and save! job done - just change the dev/number and /mountpoint to what you found earlier and when you restart the partition will auto mount there and become part of the system :)

All the best!

---

### Post by harun123 on 2012-01-31
Thank you guys:)I'm gonna install it alongside windows,see how it goes, it shouldn't affect performance, right?Also my laptop orriginally came with 25 GB OS partition(with windows 7 on it),which i couldn't expand..I've tried many software but it just won't.So now I have C partition for OS(25 GB),partition D(about 120 GB for games, programs,etc.),and partition E(around 320 GB for movies,music...)I have 5 GB free space on OS partition,but on others there's plenty of free space..Now my question is,when installing ubuntu alongside windows, do i install it one seperate partition just for ubuntu,or on partition where my current OS is? Cause I'm kinda limited with C partition..Thanks in advance;)

---

### Post by rgreener25 on 2012-01-31
you want to install ubuntu onto a separate partition

---

### Post by Bodsda on 2012-01-31
> **harun123 said:**
> Thank you guys:)I'm gonna install it alongside windows,see how it goes, it shouldn't affect performance, right?Also my laptop orriginally came with 25 GB OS partition(with windows 7 on it),which i couldn't expand..I've tried many software but it just won't.So now I have C partition for OS(25 GB),partition D(about 120 GB for games, programs,etc.),and partition E(around 320 GB for movies,music...)I have 5 GB free space on OS partition,but on others there's plenty of free space..Now my question is,when installing ubuntu alongside windows, do i install it one seperate partition just for ubuntu,or on partition where my current OS is? Cause I'm kinda limited with C partition..Thanks in advance;)

Don't install it on the same partition as your windows install if you have free space elsewhere. 

It won't affect performance

Try a live 'gparted' cd to expand your win7 OS partition. I've used it dozens of times for win7 and it works brilliantly.

Hope this helps,
Bodsda

---

### Post by 3rdalbum on 2012-01-31
5 GiB free space on the OS partition is not enough. The Ubuntu default install takes nearly 4 GiB (maybe more, depending on how much RAM you have) and **Linux programs cannot be stored on a different partition** so you really won't have enough room for Ubuntu and the programs you want to use with it. The act of partitioning also causes some space to be lost, too.

I'd suggest downsizing either the Programs/Games partition, or the Music/Movies partition, and putting Ubuntu into some free space there.

---

### Post by harun123 on 2012-01-31
> **3rdalbum said:**
> 
I'd suggest downsizing either the Programs/Games partition, or the Music/Movies partition, and putting Ubuntu into some free space there.
Yes, this was my plan. And when I create that partition just for ubuntu, linux programs will be stored on that partition,without messing with Windows partition,right? 
Can you suggest how much space should I give to each windows and ubuntu(also for ubuntu, how much for root,swap,home..)I have 500 GB hard disk, 4 GB ram, i5 processor.

---

### Post by Double.J on 2012-01-31
Hi there, 

for Swap, your recommended size is 8GB - twice RAM, realistically though, 6GB will be plenty! :)

AS for your windows partition, it really depends on which Windows you have - for XP 25GB is plenty, for Vista/Seven you'd probably want to increease the size past 30... if possible you may want to do this anyway - it's best to keep system partitions under 75% full )

With regards to the Ubuntu partition(s) home and root are plenty - with all your data on shared NTFS partitions, it's not strictly necessary, but also not a bad thing. As for root - as said earlier 12GB and up? a base install is a little under 6 so that gives you flexibility. As for /home - well that's really up to you - what do you want to store there? I keep all my things on shared partitions, so my /home is really just configuration files and Wine programs, totalling 1.4 GB, but I always like to keep 5GB free on /home so I have room to move a full dvd image on it if need be.

But yes Ubuntu programs are installed inside the ubuntu partitions. The most common places are /usr /usr/local and /bin - but making extra partitions for these is just going to get complicated and isn't necessary :)

All the best!

---

### Post by harun123 on 2012-01-31
Hi. I've freed some space for ubuntu(I didn't create a new partition,just shrunk sume volumes,and it says 50 GB unallocated). And while installing ubuntu, when that windows for partitioning comes, it recognises free space, but instead of FREE SPACE, it says UNUSABLE..And i cannot do anything with it,when i double click it nothing happens, i cant press ADD button also..Some help please:)
On that bar there is: sda1(fat 32),sda2(ntfs),sda3(ntfs),sda4(ntfs) and free space

---

### Post by Bartender on 2012-01-31
Can you take a screenie?  You mentioned four partitions, and their numbering tells me that all four are primary.  That means you're boxed in.

You can't have more than four primary partitions.  You *can* have more than four partitions total if you have three or less primary partitions, then an extended partition, then logical partitions within the extended.

In other words, you could have three primary partitions, and an extended partition with several logical partitions inside.

I prefer to keep it to one or two primary partitions, then an extended partition.

---

### Post by harun123 on 2012-01-31
> **Bartender said:**
> Can you take a screenie?  You mentioned four partitions, and their numbering tells me that all four are primary.  That means you're boxed in.

You can't have more than four primary partitions.  You *can* have more than four partitions total if you have three or less primary partitions, then an extended partition, then logical partitions within the extended.

In other words, you could have three primary partitions, and an extended partition with several logical partitions inside.

I prefer to keep it to one or two primary partitions, then an extended partition.
Yes,they're all primary. So can i make one of them extended, without deleting everything from it..Btw one of them is HP TOOLS,would it hurt if i delete it? Here's the image [http://imageshack.us/photo/my-images/404/captureeix.png/](http://imageshack.us/photo/my-images/404/captureeix.png/)

---

### Post by mastablasta on 2012-01-31
back it up and delete it. it probably contains bloatware and drivers.

---

### Post by harun123 on 2012-01-31
OK guys, now i have 3 primary partitions. Now, when i install ubuntu, do root,swap and home count as 3 primary partitions..Also is home neccesarry if i'm gonna dual boot, and share partition on which i keep my data...

---

### Post by rgreener25 on 2012-01-31
root partion 20gb maybe and home however much you think you will need

---

### Post by harun123 on 2012-02-01
I installed ubuntu, and it has little kind of bug..While booting,when that ubuntu logo is supposed to show, the screen goes black,and comes back after 3-4 seconds, when logo is supposed to dissapear, and after that everything is OK...Any clues?

---

### Post by mastablasta on 2012-02-01
maybe plymouth bug...
 
it is fixable, though i have to admit i forgot the fix. :-) it's one command to fix it.
it doens't affect OS performance, just doens't make it look as good on start.

---

### Post by Bartender on 2012-02-01
I always got the big ugly Ubuntu splash.  Googled plymouth bug and followed the [second]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") set of directions.

That made it worse.  Instead of one big Ubuntu splash I got two crazy looking ones.  We're running dual monitor so that probly has something to do with it.  

I tried to reset everything the way it was in startup manager, then rebooted and uninstalled it.  I've still got the two crazy looking Ubuntu splashes.  

Shoulda left well enuf alone!

EDIT:
So I went back & followed the first set of directions in the above softpedia article.  More geeky and way more dangerous.  It worked.  I'm back to the ugly chartreuse "ubuntu" splash, but at least it looks more proportional on the screen.  "ubuntu" is smaller and clearer.

---

### Post by harun123 on 2012-02-01
I don't have that ugly logo, my case is that i don't have it at all.Like this [http://imageshack.us/photo/my-images/848/capturerq.png/](http://imageshack.us/photo/my-images/848/capturerq.png/), so i have everything like on this image, but with no logo...But I guess that it's better to have no logo than have an ugly one:p

---

### Post by varunendra on 2012-02-02
Good suggestions here. However, I think a slight correction to the swap concept is required:
> **gnu/mirow said:**
> 
for Swap, your recommended size is 8GB - twice RAM, realistically though, 6GB will be plenty! 
Well.. really realistically- anything 4GB+ is 'more than' plenty for the OP.

"Swap=Twice the amount of RAM" formula belongs to the days when a typical system used to have no more than 512 MB of RAM. A quote from [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F"):
> As a base minimum, it's highly recommended that the  swap space should be equal to the amount of physical memory (RAM). Also,  it's recommended that the swap space is twice the amount of physical  memory (RAM) depending upon the amount of hard disk space available for  the system (**although this "recommendation" dates back from a time when  physical RAM was very expensive and most Unix systems ran with many  processes in swap space - a situation that hardly applies in most  situations these days**..*<snip>*..In  reality, if you use hibernation you need what was outlined in the  relevant paragraph above, otherwise you need as much swap space as your  system will use - which actually may be very little in a modern hardware  setup.

Practically, for a modern system and typical user,
**if the user wants to use _Hibernation_**, then I would recommend:
Swap = amount of physical RAM present (or 2GB, whichever is larger)

**If _No Hibernation_ is required, then:**
Swap = 2GB (if RAM is equal to or less than 2GB),
or,
Swap = 1GB (if RAM is larger than 2GB)

It is notable that _swap can be completely omitted if you have 4GB or more RAM_, and are not going to use multiple 'extra-heavy' applications simultaneously.

Practically, even activities like basic video editing, along with other essential apps open (like multiple browser tabs, document viewers/editors, music players, lightweight image editors, etc.) do not reach 4GB memory usage (and thus 0% swap usage with 4GB or more RAM). The only practical scenarios where I can think of more than 4GB memory usage are:

[LIST]
[*]Highly professional video-editing/animation/CAD applications on peak load
[*]running multiple virtual machines
[*]highly demanding 3d games (which are almost non-existent for linux)
[/LIST]
For any user who thinks he/she is going to use up more than 4GB of memory, the best way to decide is to put the maximum load on the system he/she thinks would ever impose on it, then note down the memory-usage. In most of the cases, it'll hardly exceed 3.2 GB (not from any authentic source though, just my personal experience. So I'm open for corrections).


Sorry if it doesn't seem relevant to the thread, but I hope it adds some value to it (especially when a misconception was involved).

---

