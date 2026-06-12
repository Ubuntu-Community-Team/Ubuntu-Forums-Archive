---
title: "error: failure reading sector 0x819"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by tdjmd on 2013-10-27
What a mess.. 
**[COLOR=#ff0000]Just right now, I'm using my UBUNTU 12.10 Installation Disk to come Web in order to get a clue what to do now.[/COLOR]**

```
error: failure reading sector 0x819 
from "hd0" 

Entering rescue mode... 

grub rescue >
```



What a thing I must type over there!!!
Dear me! 

I try to do a new installation but I can hardly: 
the blessed system doesn't run..

My machine is an Acer Aspire One Series ZG5 AOA 150 144 HD with three partitions: Ubuntu in all of them (12.10 in two, and Saucy Salamander in the third). 

Days ago, I've made a stupid mistake, to delete an old partition but GRUB was in it, so, I create a new partition with Ubuntu 12.10. So, I got a new Grub that way. Working fine.

Yesterday, I've upgraded Ubuntu to version 13.10 in one of my partitions but today, I was working, as usual, with one of my 12.10 installations and accidentally, I pulled out my netbook wire so, when I turned on the machine again, I got the message above.

No idea what is GRUB RESCUE code the system is requiring from me.

---

### Post by Impavidus on 2013-10-28
When I see a grub rescue prompt I usually recommend [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), which can reinstall grub for you. With this error message however I would keep in mind the possibility of hardware damage.

---

### Post by tdjmd on 2013-10-28
Ah, thank you very much, Impavidus.

I'm going to try Boot-Repair from my Ubuntu Live-CD first.
(keeping in mind that other posibility)

---

### Post by tdjmd on 2013-10-28
> **tdjmd said:**
> Ah, thank you very much, Impavidus.

I'm going to try Boot-Repair from my Ubuntu Live-CD first.
(keeping in mind that other posibility)

Well, I'm afraid my HD is working fine. I've installed Windows, deleting all of those partitions. Running my Ubuntu 12.10 Live-CD again.
This time, everything goes very well: Ubuntu 12.10 was installed correctly.

I'm not a skiled Linux user at all, it's why I have  placed this post in this section, Absolute Beginner Section; so, that Boot-Repair app looked like a true tangled mess to me.

In any case, thank you for your support, Impavidus.

[Solved]

---

