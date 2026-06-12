---
title: "[SOLVED] &amp;quot;root&amp;quot; + &amp;quot;Documents and Settings&amp;quot; on shared partition"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by JSeb on 2008-09-06
I hope someone can help me with that.

I successfully installed WinXP and Ubuntu on my system. I want to use a shared partition for both OSes.

So I reserved a drive for sharing: it is formatted in **ext3**, and this is where I put my Ubuntu [FONT="Courier New"]home[/FONT] folder.

I know, ext3 is not recognized by WinXP. I thought I was being clever, and use [FS-Drive]("http://www.fs-driver.org") to access that partition from WinXP.

Oh, FS-Drive works fine, thank you. But then I wanted to move my [FONT="Courier New"]Documents and Settings[/FONT] folder to that shared partition. I have all the info to do that. Where I was not so clever is that FS-Drive is not available during boot time, so WinXP complains that it cannot find my home directory. Makes sense 8-[ Luckily, I was able to go back to my original configuration.

Now, I'm turning to you geeks and geekettes to see if you have an idea how I could achieve what I want. First of all, is it a good idea to put both my Ubuntu [FONT="Courier New"]home[/FONT] and my WinXP [FONT="Courier New"]Documents and Settings[/FONT] folders on the same drive?

If the idea makes sense, I figure I should use FAT32, or preferably NTFS (I belive it is possible to use NTFS in Ubuntu). Is it possible to reformat the shared drive and somehow reinstall my Ubuntu [FONT="Courier New"]home[/FONT] on it?

If not, well, I don't mind at this point reinstalling Ubuntu, but WinXP would be a pain in the ***. I just hope I wouldn't have any trouble reinstalling Ubuntu without disturbing WinXP (because of Grub and all -- hey, I'm a newbie).

Thank you so much!

---

### Post by hyper_ch on 2008-09-06
ntfs-3g + symlinks

---

### Post by JSeb on 2008-09-06
> **hyper_ch said:**
> ntfs-3g + symlinks

Thanks hyper_ch: that's what I call a short answer :)

So should I understand that I could put my folders on a shared NTFS partition, and use ntfs-3g on the Ubuntu side? As for symbolic links, I'm not too sure how to use them...

---

### Post by hyper_ch on 2008-09-06
ntfs-3g:  yes ;)

symlinks: I'm sure you can find what they are good for... they are not complicated and very useful ;)

---

### Post by egalvan on 2008-09-06
Was that FS-drive from:

[http://www.fs-driver.org/](http://www.fs-driver.org/)


This web-page hosts a kernel-level ext2 driver, and I thought that would work.


If this is what you used, what a bummer, because I was going to do exactly what you did,
move my Windows Docs&Settings to my Linux drives.
Also the Programs folder.


Let me know.

---

### Post by forger on 2008-09-06
Why not just partition the hard drive into two parts, one ntfs and the other one ext3?
You can read/write to both, I see no reason not keeping them on separate partitions on the same hard drive
Not to mention it's cleaner and less painful! :)

---

### Post by JSeb on 2008-09-06
> **egalvan said:**
> Was that FS-drive from:

[http://www.fs-driver.org/](http://www.fs-driver.org/)


This web-page hosts a kernel-level ext2 driver, and I thought that would work.


That's the same link. I could find only one executable there. Although I talked about ext3 before, the link talks about ext2. So yes, I think it is the same thing. It works fine on a ext3 partition.

> **egalvan said:**
> 
If this is what you used, what a bummer, because I was going to do exactly what you did,
move my Windows Docs&Settings to my Linux drives.
Also the Programs folder.


Let me know.

I found this today in the FAQ section:
[I]This software does not achieve booting a Windows operating system from an Ext2 volume.
[/I]

I assume that's why it won't work, unless I made something wrong while moving my [FONT="Courier New"]Documents and Settings[/FONT] folder. I mainly followed the instructions here [here]("http://www.dyonisii.com/cgi-bin/waterwheel/index.pl?case=win&sub=mds").

---

### Post by hyper_ch on 2008-09-06
ext3 is the same as ext2 - just without journaling... they are interchangable.

---

### Post by JSeb on 2008-09-06
> **forger said:**
> Why not just partition the hard drive into two parts, one ntfs and the other one ext3?
You can read/write to both, I see no reason not keeping them on separate partitions on the same hard drive
Not to mention it's cleaner and less painful! :)

Makes sense. And if you want to share stuff, like firefox profiles, would you use symbolic links? I'd like to have an opinion on that, as I have no notion how to accomplish that.

---

### Post by hyper_ch on 2008-09-06
yeah, you can use symlinks for that stuff

---

### Post by forger on 2008-09-06
well, either symlinks (symbolic links? the command ln -s?) or you could use **rsync** to keep your profiles synchronized

Either way, I think that you can make a bash script with a little reading :)

---

### Post by JSeb on 2008-09-07
OK, Geeks and Geekettes, I still believe my original conclusion was right (cannot move [FONT="Courier New"]Documents and Settings[/FONT] to an ext3 drive, even with FS-Drive), but I **cannot** confirm it.

I used the approach suggested by forger, but still had the problems. I figure it was something I did wrong in moving the folder. Now, it's working =D>

Thanks all!

---

### Post by egalvan on 2008-09-07
> **JSeb said:**
> Makes sense. And if you want to share stuff, like firefox profiles, would you use symbolic links? I'd like to have an opinion on that, as I have no notion how to accomplish that.

I keep my profiles on an external USB hard drive, and all my Firefoxes is belong to me (sorry, old joke)

I use several different computers here at home, and two different laptops at work and on the road.
 All dual booting XP & Linux.
 All running Firefix 3.01
Keeping shared stuff on an external drive means I don't have to worry about keeping stuff synchronized.

My "download" directory is similar.



but I am curious, ,,

do you know what, exactly, cured your problem?

---

### Post by JSeb on 2008-09-08
> **egalvan said:**
> but I am curious, ,,

do you know what, exactly, cured your problem?
Like I said, it's something I was initially doing wrong in the process of moving my [FONT="Courier New"]Documents and Settings[/FONT] folder. Since that in itself is a rather painful task, I won't dive into that.
Figuring that out didn't solve my original problem, because I finally chose to put [FONT="Courier New"]Documents and Settings[/FONT] in a NTFS partition, rather than ext3.

---

### Post by egalvan on 2008-09-09
> **JSeb said:**
> Figuring that out didn't solve my original problem, because I finally chose to put [FONT="Courier New"]Documents and Settings[/FONT] in a NTFS partition, rather than ext3.

So you sidestepped the issue, rather than found a solution.

Drats, means I'm gonna have to do some experimenting. :)

I'm still experimenting with moving as much XP stuff as possible onto Linux-type file system.

Thanks for all your comments.

ErnestG

---

### Post by hyper_ch on 2008-09-09
it's not side-stepping if windows blatantly refuses to work with ext3.

---

### Post by egalvan on 2008-09-09
> **hyper_ch said:**
> it's not side-stepping if windows blatantly refuses to work with ext3.


From the OP's first post:

[B]*So I reserved a drive for sharing: it is formatted in ext3, and this is where I put my Ubuntu home folder.*
[/B]

The original intent, and the original problem, involved putting part of XP onto an ext3 partition.

He "solved" the problem by using an NTFS partition.

Sorry, I call that side-stepping.

I can't speak for the OP, but part of my aim in life is reducing (to zero, eventually) my use of MS products, 
this also involves reducing that portion of my computing resources that MS products use to zero.

Getting XP to use less NTFS and more ext2/ext3 is, in my opinion, a step in the right direction.

It means I don't have to reserve a set amount of drive space to XP.
It means I don't have to use a closed, proprietary file system.

NTFS support in Linux is absolutely wonderful, don't get me wrong.

---

### Post by hyper_ch on 2008-09-09
> **egalvan said:**
> From the OP's first post:
[B]*So I reserved a drive for sharing: it is formatted in ext3, and this is where I put my Ubuntu home folder.*
[/B]
You need to read further:
> **JSeb said:**
> But then I wanted to move my [FONT="Courier New"]Documents and Settings[/FONT] folder to that shared partition.
And that's not possible as Windows refuses to work on ext2/3....
So it's no side-stepping.

> **egalvan said:**
> I can't speak for the OP, but part of my aim in life is reducing (to zero, eventually) my use of MS products, 
this also involves reducing that portion of my computing resources that MS products use to zero.

Do you use Mac products?

---

### Post by GeoMX on 2008-09-13
I was trying something similar: use an ext3 shared partition for Windows and Linux.

I'm using Windows Vista, I wanted to have a separate partition for /home and, at the same time, move my Windows profile folders (Documents, Pictures...) to this partition. I wanted it to be an ext3 partition, and tried using it from Windows with the ext2-IFS driver, however, I had some trouble executing installers and with some Visual Studio projects. Then, I switched to the open source ext2fsd driver, it solved the issue with VS projects but not the other one (install executables could not be run). However, this time I'm experiencing a lot of unstability, my PC would crash randomly when trying to access some files in the shared partition.

Guess I'll move to a shared NTFS partition + symlinks.

I posted a question sometime ago, if you're interested, this is the thread link: [http://ubuntuforums.org/showthread.php?p=5779918#post5779918](http://ubuntuforums.org/showthread.php?p=5779918#post5779918)

---

### Post by egalvan on 2008-09-15
> **hyper_ch said:**
> Do you use Mac products?

My brother owns an Apple laptop...I saw it once... does that count?

---

