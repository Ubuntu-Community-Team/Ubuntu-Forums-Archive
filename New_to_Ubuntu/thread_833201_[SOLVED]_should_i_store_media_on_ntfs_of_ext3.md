---
title: "[SOLVED] should i store media on ntfs of ext3?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-06-18
i have been dual booting windows and ubutu for a long time now, but untill now i have never really cared about how much disk space i was using.

i was storing all of my media on whichever OS i was using at the time, for instance i would put all of my music i have in ubuntu on the ubuntu ext3 partition and all of the music i have in windows would go to the ntfs partition

(i do have ubuntu set to automount the ntfs on startup and the same with windows set to mount the ext3)

so now i am running out of space and i want to put all of my media in one place

i want to make a new specific media partition that is easily readable from both ubuntu and windows

so should it be ext3 or ntfs?  or other?

---

### Post by yragrelluf on 2008-06-18
if both ext3 and nfts both automount, i would just keep the media on whichever OS i use most, (hopefully ubuntu).

---

### Post by steve101101 on 2008-06-18
if you mainly use the ubuntu store it on the linux drive. it will be faster this way. however if you still like to use windows as well to access these files use ntfs b/c windows i believe cannot read a linux dirve.

---

### Post by ibutho on 2008-06-18
If you want to share the files between Windows and Linux (if dual booting), then your best bet is to use ntfs.

---

### Post by MasterSander on 2008-06-18
I don't think it really matters, I prefer NTFS.

---

### Post by tjwoosta on 2008-06-18
> if you mainly use the ubuntu store it on the linux drive. it will be faster this way. however if you still like to use windows as well to access these files use ntfs b/c windows i believe cannot read a linux dirve.

i do mainly use linux, but with my xbox 360 i like to turn on my media center connectivity (requiring media from windows)

you can mount ext2 and ext3 from windows (it simply requires a compatibility driver)

i tried mounting my ubuntu media from windows and playing it on media center that way but it kept freezing, but same also happens when i try to play media on ubuntu from the ntfs partition( i simply wanted to know what others have done when encountering this problem)

> 
If you want to share the files between Windows and Linux (if dual booting), then your best bet is to use ntfs.


thanks, i will do this

---

### Post by steve101101 on 2008-06-18
glad we could help.

---

### Post by acidsolution on 2008-06-18
I would prefer on ntfs partition and i do the same coz i share the file between windows and linux .

---

### Post by YaroMan86 on 2008-06-18
> **acidsolution said:**
> I would prefer on ntfs partition and i do the same coz i share the file between windows and linux .

As tjwoosta said, there's drivers for Windows that allow ext2/ext3 read/write just like any other drive in Windows. If I were you, I'd keep 'em on an ext2 partition and install [this]("http://www.fs-driver.org/") in Windows.

ext2 and ext3 are much more reliable and efficient than NTFS or FAT32.

What *I* like to do is put my /home on a seperate ext2 partition and use that also as a shared partition with Windows. It works really well for me.

---

### Post by wolfen69 on 2008-06-18
i choose FAT32 for storage. that way, *any* OS can read it.

> ext2 and ext3 are much more reliable and efficient than NTFS or FAT32.
show me proof.

---

### Post by tjwoosta on 2008-06-18
> i choose FAT32 for storage. that way, any OS can read it.

as i mentioned above i have been having problems where my computer freezes when trying to play media from the opposite partitions (ntfs on ubuntu, and ext3 on windows)

have you experienced any problems with freezing when using fat32?

---

### Post by wolfen69 on 2008-06-18
no problems at all. some people will disagree, but ive never had a problem with it. after all, flash drives are fat32, and i dont see people complaining about that. but it sounds to me that you have other issues besides what format the drives are.

---

### Post by phoenix_abhi on 2008-06-18
> **wolfen69 said:**
> i choose FAT32 for storage. that way, *any* OS can read it.


show me proof.

I also prefer FAT 32 both windows and linux can read fat32 w/o any trouble

---

### Post by tjwoosta on 2008-06-18
> but it sounds to me that you have other issues besides what format the drives are.

what could be the cause of this problem then?

i can be on the computer all day playing media from whichever partition im using at the time and i dont have problems, i can even manually copy the files from one partition to another and all works fine then

its only when i try to play media on another partition, like if i go into windows media center and start to play a folder from my ubuntu partition it will play for a while then completely freeze. or if im using ubuntu and i go to exaile, or amarok and i try to play my media folder located on the windows partition it will play for a while then freeze.

anyway i am going to try the fat32 now and see if that works

---

