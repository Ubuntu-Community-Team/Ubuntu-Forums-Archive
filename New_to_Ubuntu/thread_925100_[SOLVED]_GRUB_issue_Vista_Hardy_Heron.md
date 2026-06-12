---
title: "[SOLVED] GRUB issue Vista Hardy Heron"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Bambinodarebel on 2008-09-20
hello all, this is my first post, and I am having a confusing issue.

usually i look up other peoples problems and fix mine by looking @ their replies, but now I can't find anything and I need help.

I have been using Ubuntu exclusively for about 3 months now, and decided for the sake of others using my laptop, I would also put  Vista back onto my computer. However, I made the mistake of installing without preserving my GRUB.

Now when I try to follow directions as closely as i can when I am in threads such as [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

I can't follow thru, simply because when I have to load my hard drive installation of Hardy, i don't know how to find it.

there is only one hard drive with Vista Ubuntu and the extra little partition Ubuntu made. 

can someone help me figure out how to load up my hard drive? 

root (hd0) doesn't work and neither does any other variable besides zero whether i use root (hd0) or root (hd0,4)

---

### Post by jemate18 on 2008-09-20
So you have one HD with vista and Ubuntu.

You first installed Ubuntu and it works well.

After sometime, you decided to install vista on a separate partition.

Then, ubuntu was messed?

-> This is because VISTA tends to overwrite MBR. The default Ubuntu installation installs GRUB into the MBR. However, after installing VISTA, it has overwritten the MBR therefore deleting your GRUB......

-> You can search THREADS here on how to fix this kind of problem.......

---

### Post by jemate18 on 2008-09-20
Try this link.. Its from the community documentation HELP

> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Bambinodarebel on 2008-09-20
alright, i'll thank you guys in a little bit, right now im going to email this to myself and go and connect directly to my modem. and then load up my live CD

---

### Post by Bambinodarebel on 2008-09-20
Thanks you guys, I was able to fix it... funny though, i Know that I followed these same directions last night and i got no results... maybe because I tried to figure it out so many times, it ended up only giving me error messages. but now it appears like I can boot either option so much appreciation!!

---

