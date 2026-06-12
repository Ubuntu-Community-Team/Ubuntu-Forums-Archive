---
title: "Moving space between Ubuntu 14.04 and Windows 10 Pro"
date: 2016-08-05
forum: New to Ubuntu
---

### Post by svats7 on 2016-08-05
Hello everyone. I am fairly new to ubuntu and linux in general and I am not very much experienced in matters related to partitions and hard drives when it comes to linux. I want to move space from Ubuntu 14.04 to Windows 10 Pro, but am not able to do so. I have made a live USB of Ubuntu and created the unallocated space (according to this link: [https://ubuntuforums.org/showthread.php?t=2121623](https://ubuntuforums.org/showthread.php?t=2121623)), but due to my windows and ubuntu partitions being on separate partition tables (i think), I am not able to move this unallocated partition in front of my windows partition so that I can expand it. I can also make a separate partition on windows using the unallocated partition, if needed. Below I have attached screenshots of gparted and windows 10 disk manager. I need to get more space on my windows 10 partitions, due to very important reasons. Thanks in advance to everyone.
[ATTACH=CONFIG]270586[/ATTACH]
[ATTACH=CONFIG]270587[/ATTACH]

---

### Post by CatKiller on 2016-08-05
You'll need to move your / and swap partitions to the right into that unallocated space, so that the Windows partition has the space next to it. You can't move a partition that's mounted, so you'll need to do it from a live USB and you'll need to turn swap off in that environment.

Once you've moved those partitions you'll need to shrink the extended partition that contains them (the cyan box in your gparted output).

Windows throws a hissy fit if you use anything other than Windows tools to change its partitions, so once you've got the space next to the Windows partition you'll have to boot into Windows to do the last bit of expanding that partition. I haven't used Windows in over a decade, so I can't help you with that bit.

---

### Post by yancek on 2016-08-05
The key symbol next to the Extended and logical partitions indicate those partitions are mounted so as suggested above, unmount them from the Ubuntu DVD or flash drive you are using.   Extending partitions isn't that complicated if you have unallocated space adjacent to the partition you want to enlarge.  This is not your case so that complicates things and I would suggest you backup any valuable data before beginning.

Note the red circle with the exclamation point next to your windows partition.  It may be hibernated and if so, turn that off first.  It could also be that you need to run chkdsk from windows.

It would be much simpler just to use that unallocated space to create another windows partition.  If you do that, when you first reboot windows, run chkdsk as there will be a change to the partition table.

---

### Post by ajgreeny on 2016-08-05
If you choose to do what CatKiller suggests you will probably have to unmount the extended partition when using the live system as usually (always in my experience) a live Linux OS will find and use an existing swap partition, so don't be surprised when you find the extended partition locked even in a live Ubuntu.

Also be prepared for a long wait after starting the partition move and **DO NOT INTERRUPT** it in any way or you will lose everything.  If this is a laptop it is very important to make sure it is with the external power-supply attached not depending on battery alone.

As long as you have everything backed up it is OK to move the Ubuntu root partition and swap to the right, I have done a similarly several times with gparted with no problem; it just can take a long time.

---

### Post by svats7 on 2016-08-05
> **ajgreeny said:**
> If you choose to do what CatKiller suggests you will probably have to unmount the extended partition when using the live system as usually (always in my experience) a live Linux OS will find and use an existing swap partition, so don't be surprised when you find the extended partition locked even in a live Ubuntu.

Also be prepared for a long wait after starting the partition move and **DO NOT INTERRUPT** it in any way or you will lose everything.  If this is a laptop it is very important to make sure it is with the external power-supply attached not depending on battery alone.

As long as you have everything backed up it is OK to move the Ubuntu root partition and swap to the right, I have done a similarly several times with gparted with no problem; it just can take a long time.

I am a little bit confused as to what you mean by "if i have everything backed up". Is the backup just in case of a failure/error or is it given that loss of data will occur during the process of shifting the swap and root partitions?

---

### Post by svats7 on 2016-08-05
> **CatKiller said:**
> You'll need to move your / and swap partitions to the right into that unallocated space, so that the Windows partition has the space next to it. You can't move a partition that's mounted, so you'll need to do it from a live USB and you'll need to turn swap off in that environment.

Once you've moved those partitions you'll need to shrink the extended partition that contains them (the cyan box in your gparted output).

Windows throws a hissy fit if you use anything other than Windows tools to change its partitions, so once you've got the space next to the Windows partition you'll have to boot into Windows to do the last bit of expanding that partition. I haven't used Windows in over a decade, so I can't help you with that bit.

I will do as you said and get back to this thread within 12-14 hours. Just one thing I wanted to confirm first. Since I'm doing such sensitive operations, is it ok to leave the laptop on overnight, with the AC adapter connected of course, for the whole process to complete? It's just that I wont have a 5-6 hour window in which I am not using my laptop except when I am sleeping.

---

### Post by CatKiller on 2016-08-05
That should be fine, provided your laptop doesn't go to sleep part way through. Most will be intelligent enough to stay on, but it will depend on configuration.

And yes, backing up is just a precaution. I've never had any data loss, but it's better safe than sorry.

---

### Post by ajgreeny on 2016-08-05
> **CatKiller said:**
> That should be fine, provided your laptop doesn't go to sleep part way through. Most will be intelligent enough to stay on, but it will depend on configuration.

And yes, backing up is just a precaution. I've never had any data loss, but it's better safe than sorry.
+1 ^^^^^

You should always have backups anyway as you have over 450GB of data in home; what would you do if your disk failed?

---

### Post by tsjswimmer on 2016-08-14
Have you disabled Fast Startup mode (previously called "Fast Boot")? If not, that can cause big problems. See [this howtogeek]("http://this howtogeek") for why it causes problems, and how to disable it.

PS: in your GParted screenshot, there is an exclamation mark next to your Windows partition. This indicates some kind of problem. You should right-click on the partition to see what the problem is. If GParted says something about the partition being "hibernated", it's probably because of Fast Startup mode.

---

