---
title: "Removing Ubuntu in Vista Dual-Boot"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Justin125 on 2008-05-31
Okay, I've removed the partition via Vista and done /FixMbr. I'm stuck with a green blob of free space, how can I get this back into my main partition?

Image:

[http://i28.tinypic.com/b4ukj4.png](http://i28.tinypic.com/b4ukj4.png)

I've heard I need to go back into a Live CD and do something or what?

[if someone does answer this for me considering this is a half windows question I will be very happy]

---

### Post by forestpixie on 2008-05-31
~Use the vista tool to make it an ntfs partition and it will see it, then you'll be able to use it there. Assuming the vista tool is as up to date as others then extend your vista partiotion to include it.

---

### Post by Joeb454 on 2008-05-31
Yeah I think you can use the Vista tool to extend it's partition :)

---

### Post by FuturePilot on 2008-05-31
You can use GParted on the Live CD to expand the partition so you can reclaim the free space. I'm not sure if Vista can expand partitions.

---

### Post by Justin125 on 2008-05-31
> **forestpixie said:**
> ~Use the vista tool to make it an ntfs partition and it will see it, then you'll be able to use it there. Assuming the vista tool is as up to date as others then extend your vista partiotion to include it.

I can't seem to be able to NTFS format the free space; I get this error:

There is not enough space available on the disk(s) to complete the operation.

I'm lost as to how 168GB isn't enough...

---

### Post by Justin125 on 2008-05-31
> **Joeb454 said:**
> Yeah I think you can use the Vista tool to extend it's partition :)

Yeah, there is a Extend Partition option greyed out on the main partition.

---

### Post by forestpixie on 2008-05-31
> **Justin125 said:**
> I can't seem to be able to NTFS format the free space; I get this error:

There is not enough space available on the disk(s) to complete the operation.

I'm lost as to how 168GB isn't enough...

I could say - that's windows, but that would be sad :)

Sorry then - I only looked at vista twice - just assumed that as it get's all odd about partitions that was the best place to resize it :(

You could try it with an amount of unallocated space or gparted as has been mooted

---

### Post by Justin125 on 2008-05-31
I was afraid of that. :(

Thanks a lot though, I got way better replies than I expected considering this is a half-windows question. I love Ubuntu, but I'm a big PC gamer, Wine just doesn't offer good enough compatibility for games for me. For a few weeks I tried the 'Just Boot in and out of Vista for games, and then boot back in to Ubuntu after' approach but it's just too annoying. =(

---

### Post by forestpixie on 2008-05-31
> **Justin125 said:**
> I was afraid of that. :(

Thanks a lot though, I got way better replies than I expected considering this is a half-windows question. I love Ubuntu, but I'm a big PC gamer, Wine just doesn't offer good enough compatibility for games for me. For a few weeks I tried the 'Just Boot in and out of Vista for games, and then boot back in to Ubuntu after' approach but it's just too annoying. =(

You'll be back - can yuou mark thread when you've made your mind up 
Good luck with it

I'll help anyone if they're polite :D

---

### Post by Joeb454 on 2008-05-31
> **forestpixie said:**
> I'll help anyone if they're polite :D

+1 to that :)

---

### Post by archer6 on 2008-05-31
> **forestpixie said:**
> I could say - that's windows, but that would be sad :)

True..... I might ad that's windows vista !  Which is the precise reason I'm here in Ubuntu-Land reading as many posts and learning as much as I can about this terrific alternative.....:)

---

### Post by FuturePilot on 2008-05-31
> **joeb454 said:**
> +1 To That :)

+2 :)

---

### Post by SunnyRabbiera on 2008-05-31
Still I personally would dual boot, yes switching back and fourth is annoying but its better then just using a OS that has so many restrictions on it...
I rather have freedom over games anyday.

---

