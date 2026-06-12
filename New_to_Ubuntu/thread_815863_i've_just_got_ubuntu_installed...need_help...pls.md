---
title: "i've just got ubuntu installed...need help...pls"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by amraam13 on 2008-06-02
Good day!

I just switched to Ubuntu. I've been using XP for quite a while.  I really want to learn about Ubuntu and i have been reading about a lot of stuff. I am really new to this.

After i wiped out everything in my HD...free space...I installed Ubuntu in it.  I used the entire space for Ubuntu, 80GB. Since I got used to XP before, I want to have a partition on my disk. I have questions: please, enlighten me... :confused:

Is it necessary to partition my HD like i had with XP (with C and D as my backup)?

I was looking for the Gnome Partition Editor and i had a hard time looking for it. Is it only found on the Live CD? What's gparted package? 

I don't need to install motherboard drivers for newly installed Ubuntu, right? 

I have Nvidia Geforce card...i can't enable it...i am not quite sure where to start...(it's autorun w/xp)how do i do it?

As I have said, I am very new to Ubuntu and I really want to get this thing going.

I would really appreciate any help from you guys.

THANK YOU!!!

-amraam13-

---

### Post by Rocket2DMn on 2008-06-02
You will have a couple of partitions:
1) root (mounted at /) of type ext3
2) swap (no mount point) of type swap
3) /home (mounted at /home - this is an optional partition.  /home will fall under / otherwise) of type ext3
You do not need other partitions, though having a second internal or external hard drive is extremely useful for backups.  The optional /home partition means you can reinstall the OS without losing your configuration settings or personal files.  Other partitions like external drives can be of basically any filesystem, like ntfs if you want to share it with a windows computer.

GParted is only available on the LiveCD by default, but you can install it after you install Ubuntu by running
```
sudo apt-get install gparted
```  You can't use GParted on your root (/) partition while Ubuntu is running since the partition is mounted during a normal boot.  So you need the LiveCD to fiddle with the partition if needed.

You shouldn't need motherboard drivers.

You can install restricted Nvidia drivers using a program called EnvyNG (if the ones from System->Administration->Hardware Drivers don't cut it) - [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

Welcome to Ubuntu!

---

### Post by HotShotDJ on 2008-06-02
> **amraam13 said:**
> After i wiped out everything in my HD...free space...I installed Ubuntu in it.  I used the entire space for Ubuntu, 80GB. Since I got used to XP before, I want to have a partition on my disk. I have questions: please, enlighten meA partition for what?  Once I know what you intend to do with the partition, I can tell you how to do it. :)> **amraam13 said:**
> What's gparted package? Leave that alone for right now... we can get back to it later if needed.> **amraam13 said:**
> I don't need to install motherboard drivers for newly installed Ubuntu, right? Right.> **amraam13 said:**
> I have Nvidia Geforce card...i can't enable it...i am not quite sure where to start...(it's autorun w/xp)how do i do it?System --> Administration --> Hardware Drivers should fix you right up

---

### Post by HotShotDJ on 2008-06-02
> **Rocket2DMn said:**
> You can't use GParted on your root (/) partition while Ubuntu is running since the partition is mounted during a normal boot.Actually, you can't use gparted on ANY mounted partition... which is why I suggested that you leave it alone for the moment. ;)

---

### Post by iaculallad on 2008-06-02
> **amraam13 said:**
> Is it necessary to partition my HD like i had with XP (with C and D as my backup)?

- That would be optional but you can create another partition for you to store you data backups.

> **amraam13 said:**
> I was looking for the Gnome Partition Editor and i had a hard time looking for it. Is it only found on the Live CD? What's gparted package? 

On your terminal, type in the codes below to get gparted

```
sudo apt-get install gparted
```


> **amraam13 said:**
> I have Nvidia Geforce card...i can't enable it...i am not quite sure where to start...(it's autorun w/xp)how do i do it?

- You can enable it using the "Restricted Drivers Manager"

---

### Post by Rocket2DMn on 2008-06-02
> **HotShotDJ said:**
> Actually, you can't use gparted on ANY mounted partition... which is why I suggested that you leave it alone for the moment. ;)

Exactly.  But you can unmount /home and swap during a normal boot if needed, though you may need to be at a root terminal for that.  I've never tried unmounting /home but you should be able to.  In any case, having GParted is nice when dealing with other hard drives.

---

### Post by HotShotDJ on 2008-06-02
> **Rocket2DMn said:**
> In any case, having GParted is nice when dealing with other hard drives.Absolutely.  But new users should NOT be trying to use it until they are more familiar with Linux.  Notice I didn't tell him NEVER to use it... I just suggested we postpone dealing with it. :)

---

### Post by Rocket2DMn on 2008-06-02
> **HotShotDJ said:**
> Absolutely.  But new users should NOT be trying to use it until they are more familiar with Linux.  Notice I didn't tell him NEVER to use it... I just suggested we postpone dealing with it. :)

Hehe, a matter of opinion.  The OP asked, so I told.

---

### Post by amraam13 on 2008-06-02
Thank You So Much Everyone! It's really wonderful to know that there are people like you out there ready to help someone like me.

I now got new information going inside my head...:)

THANK YOU!!!

-amraam13-

---

