---
title: "Help???"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by drmm411 on 2008-07-15
Hi, I know this might not be the best place to put this, but it said absolute beginner and thats what I am; so here goes...

I normally operate in windows, but I'm having some trouble with my external hard drive.
The problem is this;
I lent the hard drive to a friend so he could put some of his data on it. yesterday I plugged in the hard drive and it worked fine. then windows media player started crashing and froze my computer, I had to shut it down forcefully (holding the power button). The next time I turned my computer on, the drive shoes as corrupt/inaccessible. So next I boot into Ubuntu because unlike Windows, it doesn't suck and will actually tell you what's wrong with the drive. The error I'm getting now is saying that I cannot mount the drive because NTFS is marked to be in use.
It gives me the following line of code
```
mont -t ntfs-3g/dev/sdg1/media/My Book -o force
```
saying that I can type that into the command line and force the drive to be unmounted. I tried putting that in exactly and a few different variations of the line, but I could not figure out how to make it work correctly.

I have had this same problem once before but I cannot remember exactly how I fixed it. Any help is greatly appreciated.

BTW: I'm working with a 500 GB Mybook external hard drive.


SORRY, I double posted on accident. =/

---

### Post by aysiu on 2008-07-15
This command will not work as you typed it: ```
mont -t ntfs-3g/dev/sdg1/media/My Book -o force
``` It should read: ```
sudo mkdir /media/My\ Book
sudo mount -t ntfs-3g /dev/sdg1 /media/My\ Book -o force
``` To make sure you're entering the command correctly, you should **paste** the command into the terminal instead of retyping it.

---

