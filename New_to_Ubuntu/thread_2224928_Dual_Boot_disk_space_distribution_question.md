---
title: "Dual Boot disk space distribution question"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by w_Tran on 2014-05-19
Hello Community,

I am a new linux user and I have question about distributing memory on my hard drive if I am dual booting. I partitioned 87gb of hard drive space to install linux and when I did this I gave 60gb to root and 8gb to swap ( i have 8gb of ram) and the remaining 18gb to home. I was wondering if this is going to be a problem because my Home will run out of space if I install more software right? Unless I am suppose to install it on root, would that be a problem because root I heard is something I usually don't touch if I don't need to.

---

### Post by Impavidus on 2014-05-19
As long as you install software from the repositories (via the software centre), it will be installed on the root partition. Most software you install in a different way (not recommended for newbies) will also be installed on the root partition. You home partition is what you use for your documents, media files etc. So, no, your home partition won't fill up because you're installing software.

However, 60GB is very large for a root partition and 18GB is small for a home partition. Usually it would be about the other way around. It's likely that your home partition will fill up because of media files. Media files are much larger than installed software.

---

### Post by stalkingwolf on 2014-05-19
id reverse the setup you have. make 18-20 for / (root)  and the rest for /home.  as I recall / is where the "system" files are. everything else is in the home folder albeit most is hidden.  to see what is actually in there use the show hidden files option

---

### Post by mansonfan78 on 2014-05-19
If you're dual booting with windows do you have documents and media files stored in it's partition(s)?  If so, ubuntu/linux has no trouble reading and writing to ntfs partitions, so you could just keep your media files there and not have to worry about filling up /home.  A lot of people who dual boot have a seperate ntfs partition for files that can be shared between the two systems.

---

### Post by LastDino on 2014-05-19
> **mansonfan78 said:**
> If you're dual booting with windows do you have documents and media files stored in it's partition(s)?  If so, ubuntu/linux has no trouble reading and writing to ntfs partitions, so you could just keep your media files there and not have to worry about filling up /home.  A lot of people who dual boot have a seperate ntfs partition for files that can be shared between the two systems.

+1
If you do this, you may not even need to make /home and install the whole LInux system on as minimum as 20 GB. I do that quite often to check out different distro's as VM doesn't play nice on my old hardware. Also, you can do away with less SWAP too, especially if you've no plans to hibernate.

---

