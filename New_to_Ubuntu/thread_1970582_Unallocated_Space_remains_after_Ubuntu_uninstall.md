---
title: "Unallocated Space remains after Ubuntu uninstall"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by plasticparadox on 2012-05-01
Hi, I downloaded and tried Ubuntu 12.04 last week and decided that it's not for me. Booting back into Windows 7, I used Windows' Computer Management program to remove the Ubuntu partition. Then I used the Windows 7 recovery disc to repair my boot loader.
So far, everything seems to be working but looking at my partition map from Computer Management, I now have unallocated space where the Ubuntu partition used to be. I can't seem to merge that space back into my main partition.
I would greatly appreciate some help with this. Is there any way to reclaim that unallocated space?

Thank you!

---

### Post by strask on 2012-05-01
> **plasticparadox said:**
> I can't seem to merge that space back into my main partition.
I would greatly appreciate some help with this. Is there any way to reclaim that unallocated space?

There *may* be a way to grow an existing windows partition, but I'm not sure how to do it. Hopefully someone else can provide instructions.

But if that is not possible, you can always make a new partition in the free space, format it for windows, and it will show up as a separate drive letter (like D:).

---

### Post by jerrrys on 2012-05-01
Not merge, but should be able to expand (resize) your windows partition to take up the extra space.

And welcome to the forum :)

---

### Post by strask on 2012-05-01
I think I found something that should help... 

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

I note in the image [http://www.howtogeek.com/geekers/up/sshot-2009-08-27-15-50-21.png](http://www.howtogeek.com/geekers/up/sshot-2009-08-27-15-50-21.png) there is an "Extend" option on the right-click menu. That should be what you need.

---

### Post by plasticparadox on 2012-05-01
Thank you for your replies. I managed to finally solve the issue.
 
I wasn't able to interact with the Ubuntu partition with Windows Disk Management, however I was able to use a free third-party tool (EaseUS, if you're interested) to grow my main partition. It is a bit nerve-wracking to play with my primary partition, but it did all work out in the end.
 
After all was done, I noticed that Ubuntu had an entry in the Uninstall Programs menu. I'm curious, if I had just clicked on that without touching partitions, would that have taken care of everything for me?

---

### Post by jerrrys on 2012-05-01
Are you looking for something more windows like?

[http://zorin-os.com/index.html](http://zorin-os.com/index.html)

---

### Post by plasticparadox on 2012-05-02
> **jerrrys said:**
> Are you looking for something more windows like?

[http://zorin-os.com/index.html](http://zorin-os.com/index.html)

Not so much! :p
I actually prefer OS X at home so I'm fine with the Ubuntu interface/file system. My work computer is Windows 7. I installed Ubuntu on it as a way of separating my personal stuff from my work stuff.

I'll give Ubuntu another go when I get my hands on a netbook later. ):P

---

