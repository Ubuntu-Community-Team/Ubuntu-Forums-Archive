---
title: "[SOLVED] Resizing Partitions??"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-06-07
Hi. I am currently dual booting between Ubuntu and Windows. The windows partition has all my music on it. Since I discover songbird :) I wanted to move all my music on my Ubuntu partition however it is only 20GB. I tried to resize it using GParted live CD however I can't start x for some reason. Can anybody help me. I am not good with partitions!!

---

### Post by PurposeOfReason on 2008-06-07
You could have mounted your NTFS partition and have songbird use that. Much easier IMO. But for your X problem, what errors does it give you?

---

### Post by Promaster91 on 2008-06-07
Yea. That is what I am doing now. Having songbird read from my C:/ drive. I will try to boot into the cd again.

---

### Post by jbrown96 on 2008-06-07
The command to start x is ```
startx
``` That may help. Another solution would be to use your Ubuntu disk (as long as you didn't use the alernate). The LiveCD has Gparted on it. 
You may not want to move your music at all. It's possible to automount your Windows partition and you can tell songbird to find your music that way.

---

### Post by Promaster91 on 2008-06-07
Yea that's what I tried when the GUI didn't load. When I run the command the screens looks like it is going to load then it fallsback to the terminal and gives me an error message.

---

### Post by bilbo.san on 2008-06-07
Hey,
I had the same problem, it was not because of music files, but photos and images (work stuff).

I was forced to install Acronis Disc Director 10 on Windows, this programs is quite cool as it gives complete control over each partition, you could merge, delete and resize partitions. Just tell the system to resize the ext3 partition taking available free space from any NTFS disc you may have. It takes some time to apply, and it may have to re-start the system, if it requests so, restart it loading Windows. 
It worked for me with no problems... HOWEVER, I remember reading somewhere that this method is not stable enough.

So it is up to you!

PS, perhaps just mounting the disk as you were suggested could be the easiest thing to do.

---

### Post by Promaster91 on 2008-06-17
Yea currently I am mounting my windows drive. I will to to edit the partitions in Windows. I think vista has a parition editing tool built in. I will have to check that out.

(Sorry for the long reply, I was on vacation)

---

### Post by PurposeOfReason on 2008-06-17
> **Promaster91 said:**
> Yea currently I am mounting my windows drive. I will to to edit the partitions in Windows. I think vista has a parition editing tool built in. I will have to check that out.

(Sorry for the long reply, I was on vacation)
It does. I believe it's start > right click computer > manage drives or something along those lines. It really isn't too great though.

---

### Post by Promaster91 on 2008-06-30
I was able to get Gparted CD to work. I just had to force my video driver.

---

