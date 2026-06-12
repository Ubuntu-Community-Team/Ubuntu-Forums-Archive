---
title: "Resizing partition for Ubuntu"
date: 2015-01-11
forum: New to Ubuntu
---

### Post by tripler2 on 2015-01-11
Hey everyone

I'm a total newbie when it comes to linux.
I recently installed Ubuntu alongside Windows 8.1
I used Windows 8.1 to Shrink the volume of my harddisk and to give Ubuntu 50gbs of space
After I discovered how *better* the operating system is than Win 8.1, I regret that fact that I gave it just 50gbs and I want to give it more
I need to know where I can resize my partition without damaging any folder on any operating system (since I use windows for gaming)
Should I use Ubuntu to resize the partition, or use windows? In both cases, I need to know how to do so please, so that both will keep running without any errors

---

### Post by Quarkrad on 2015-01-11
As you use 'gaming' I would definately use Windows to resize the partition.

---

### Post by tripler2 on 2015-01-11
Ok, how?

---

### Post by newb85 on 2015-01-11
How much more are you planning to give Ubuntu?  Expanding the Ubuntu partition will be a little trickier, since it will involve moving the start point of the partition.  It might be easier to create an additional ext4 partition in the space you relinquish from Windows, and use that as the mount point for your /home directory.

But as I said, that will depend on how much more space you want to give Ubuntu.

Generally, 50GB should plenty for all of Ubuntu, unless you're using it to store a ton of videos, music, etc.

---

### Post by tripler2 on 2015-01-11
I want to give it an extra 50 gbs

---

### Post by newb85 on 2015-01-11
I have no experience with Windows 8, but I would follow the steps at [http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/](http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/) but stop once you've created unallocated space (don't start creating the new volume).

Then, I would boot from your Ubuntu install media (DVD/USB) and use Gparted to create a new ext4 partition in the open space, using the /home mount point.  Then (while still booted from the install media) copy all the contents of the /home directory in your original Ubuntu partition to the new partition.

[s]I'm not sure, but you might have to manually create a symlink from your /home directory to the new partition.[/s]
Edit: on review, it's not a symlink, but a fstab entry that you need.  I should have known better...

---

### Post by yancek on 2015-01-11
You indicated in your first post you used windows 8 to shrink its partition.  Use the same method, Disk Management I think it is.  I don't use windows 8 either.

---

### Post by Mark Phelps on 2015-01-12
Use the Disk Management utility in Win8 to shrink it further ... but don't get too eager to shrink it too much.  Windows needs 15-20% free space for buffers and logs.  Shrink it more than that, and you will have performance problems -- something you definitely don't want when you are Gaming.

If Disk Management won't let you shrink it much, you could do that using the Minitool Partition Wizard Boot CD.  It's a windows-based partitioning tool and it will let you shrink the partition more than Windows Disk Management permits.  Just don't shrink it too much.

---

### Post by newbie13 on 2015-01-12
If you ask me, there is absolutely no need of 100gb for ubuntu.

The recommended size is 15 gb so 50 gb is already more than enough. Ubuntu can read ntfs file systems so you can put your movies, videos etc. in C, D or E drives of windows and still access it in ubuntu.

While trying to add more space for ubuntu you might end up hurting both of your operating systems and data.

I am too new to ubuntu and I have gone through same situation. I had given 40gb for ubuntu but seeing no need for this much space I reinstalled it in 20gb and installed kali linux in 20gb.

It's up to you what to do. I have shared my own experience. If you still want to add space for ubuntu then there many awesome people in this forum who have already told you what to do and will tell you in case you need further help..

---

### Post by oldrocker99 on 2015-01-12
I recommend a system partition, /, to be 64GB, which should be plenty. The rest should be /home, which can never be too big;).

The best way to do this, I'm afraid, is to reinstall, selecting "Something else" at the partition manager page and setting up a / and a /home partition. This way, you can install a new system in /, formatting it, and mount the other partition as /home, not formatting it, so you don't lose your settings and various downloads. If you want to keep Windows 8, defrag first from within Windows, since Windows puts little files all over the disk, and calls some of them "unmovable." Hopefully that won't happen to you.

Personally, I'd deep-six the M$ abomination, and use the whole drive, but that's me. **No** OS is more annoying for me to use than Windows, and my last experience was Windows 7, which at least Windows users **liked**. I found, after five years of Linux, to be incredibly frustrating in its inability to do things that Linux lets me do.

My pet peeve is the need to reboot to install updates, because "Windows cannot update system files while they are in use." In Linux, if a process is to be updated, you see this:
```
Process [name of process] stopped
Setting up [name of process]
Process [name of process] started
```

What a concept. The only times you **need** to reboot are when (1) a new kernel is installed (and you can reboot any time you feel like it), (2) if a new graphics driver is installed (in order to activate it), and (3) if you install a program that must run at startup, like loadahead. The rest of the time, you don't need to reboot at all.

---

### Post by newb85 on 2015-01-14
Edited my last post.  If you haven't gone too far with your current install, oldrocker99's suggestion to reinstall for a separate /home partition.  However, it is possible (though more in-depth) to create a separate partition after-the-fact, and there are tutorials to be had out there on the subject.

oldrocker99, I agree with your sentiments that Windows can be quite annoying (and I have to use it over 8 hours a day), but I'm not sure your statement about rebooting is quite an accurate depiction of Linux.  Yes, most updates can be made with a simple process restart, but kernel updates still require reboot to take effect.  (Of course, Ubuntu doesn't nag you about it the way Windows does.)

---

