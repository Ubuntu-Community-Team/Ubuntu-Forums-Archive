---
title: "I need my space!"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by tethys on 2008-05-19
ok, so I have ubuntu installed and have free'd up some space on the Vista partition of my hard drive... I want this space transferred over to the Ubuntu partition. How do I do this without uninstalling and then reinstalling Ubuntu in order to use the built in partition manager?

I have tried gpart-whatever... I doesn't allow me to shrink any of my partitions, and the built in Windows partitioner does not allow me to shrink the Vista partition, and it also won't allow me the add the shrunken space from the Recovery drive to the Ubuntu partition...

WHAT TO DO?!?

---

### Post by Living2007 on 2008-05-19
> **tethys said:**
> ok, so I have ubuntu installed and have free'd up some space on the Vista partition of my hard drive... I want this space transferred over to the Ubuntu partition. How do I do this without uninstalling and then reinstalling Ubuntu in order to use the built in partition manager?

I have tried gpart-whatever... I doesn't allow me to shrink any of my partitions, and the built in Windows partitioner does not allow me to shrink the Vista partition, and it also won't allow me the add the shrunken space from the Recovery drive to the Ubuntu partition...

WHAT TO DO?!?
I've used GPArted lots. Just select the partioin, after compressing your files and drag the slider back, then for the other partition, darg it forward. DONE

---

### Post by tethys on 2008-05-19
that WOULD work, but gparted does not allow me to resize, it has almost every option greyed out

---

### Post by Living2007 on 2008-05-19
> **tethys said:**
> that WOULD work, but gparted does not allow me to resize, it has almost every option greyed out
 That would be a problem, Have you selected a partition and it still remains grayed out?

---

### Post by sdennie on 2008-05-19
You'll have to boot with a live CD because gparted won't allow you to mess with mounted partitions.

---

### Post by HotShotDJ on 2008-05-19
> **tethys said:**
> that WOULD work, but gparted does not allow me to resize, it has almost every option greyed outYou can't resize partitions that are being used by the system.  You'll need to get out your Ubuntu Installation disk and boot up with that.  Then you'll be able to use gparted.  Be prepared, the operations that you are proposing take a VERY long time.  

STANDARD, BUT IMPORTANT, WARNING: You should also backup any important data first.

---

### Post by Living2007 on 2008-05-19
> **vor said:**
> You'll have to boot with a live CD because gparted won't allow you to mess with mounted partitions.
Now I fill stupid, cause I failed to ask I he was using the OS or LiveCD

---

### Post by sirgogo on 2008-05-19
Greetings!

Either you can do that (boot from Live CD and use the gParted there), or you can use Vista's partition editor. Belive it or not, its rather awesome! It makes it really easy. What you are going to want to do is:

1. Boot into Vista right click on My Computer
2. Select "Manage".
3. Click the "Disk Management" sub-menu.
4. Right click on your Vista partition and click "Shrink Volume"
5. Enter the number of MB you would like to shrink your volume, and hence make a new partition.
6. Enjoy!

This is really easy and it doesn't take much time at all.

Though, if you've already installed Ubuntu, I'm fairly certain that Vista will not be able to see your ext3 partition. In which case, you will have to boot from the Ubuntu Live CD (or gParted Live CD) and use the partition editor there.

Cheers and Good luck!

---

### Post by overdrank on 2008-05-19
> **Living2007 said:**
> Now I fill stupid, cause I failed to ask I he was using the OS or LiveCD

No need to feel bad, everyone makes mistakes and that is the part of learning. :KS

---

### Post by roxyisgoofy on 2008-05-20
I don't know any technical terminology, science is my thing not computers. All I know is that I downloaded ardour. no problems. Made 5 songs and was out of space. I exported all my songs to a portable drive and erased all project files. It still tells me that I am out of space. Now I can't even open ardour becasue it saysthis when opened in terminal. How do I know how much memory I have? What is using it? How to clean up unused items and all that jazz. CAn someone point me in the right direction?

---

### Post by tethys on 2008-05-20
> **sirgogo said:**
> Greetings!

Either you can do that (boot from Live CD and use the gParted there), or you can use Vista's partition editor. Belive it or not, its rather awesome! It makes it really easy. What you are going to want to do is:

1. Boot into Vista right click on My Computer
2. Select "Manage".
3. Click the "Disk Management" sub-menu.
4. Right click on your Vista partition and click "Shrink Volume"
5. Enter the number of MB you would like to shrink your volume, and hence make a new partition.
6. Enjoy!

This is really easy and it doesn't take much time at all.

Though, if you've already installed Ubuntu, I'm fairly certain that Vista will not be able to see your ext3 partition. In which case, you will have to boot from the Ubuntu Live CD (or gParted Live CD) and use the partition editor there.

Cheers and Good luck!

ooooh, thanks for playing...

> the built in Windows partitioner does not allow me to shrink the Vista partition, and it also won't allow me the add the shrunken space from the Recovery drive to the Ubuntu partition...

---

### Post by tethys on 2008-05-20
anyone?

---

