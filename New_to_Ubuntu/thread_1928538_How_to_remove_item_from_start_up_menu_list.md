---
title: "How to remove item from start up menu list?"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Penguin360 on 2012-02-20
I tried startup-manager to modify the start up menu list, but in vain. It only allows me to choose the boot order, but does not allow me to delete an item from the boot menu list. Can someone show me how to delete an item from the boot menu list?

Thanks,

---

### Post by Quackers on 2012-02-20
That would depend on what it is you want to remove.

---

### Post by HavarN on 2012-02-20
Yes, read this guide. It should help you to remove items from the grub2 menu:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by Penguin360 on 2012-02-20
> **Quackers said:**
> That would depend on what it is you want to remove.

I would like to remove Previous Version and Memory Test. I only need Ubuntu normal mode, recovery mode, and my Windows 7 entries.

Thanks,

---

### Post by Penguin360 on 2012-02-20
> **HavarN said:**
> Yes, read this guide. It should help you to remove items from the grub2 menu:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

Thank you for the link. However, it is for Ubuntu 9.10, I am not sure if it still works for 12.04, but I will give it a try.

---

### Post by Quackers on 2012-02-20
To remove the Memtest entry you can run this in a terminal ```
sudo chmod -x /etc/grub.d/20_memtest86+
```
then run ```
sudo update-grub
```
To remove the previous versions you can remove all previous kernels using synaptic package manager but it is normally recommended to leave at least one previous kernel (in case your current kernel developes any problems), then run the second command again.

But DO NOT remove your current kernel!

---

### Post by HavarN on 2012-02-20
It should work for 12.04 as well; since 12.04, as far as I know, uses grub2 too.

However, you are posting in the absolute beginners forum, so I draw the conclution that you are an absolute beginner. In that case, you should probably stick to a more stable or tested release than the development release. I would recommend trying 10.04 LTS or 11.10.

The development release will have numerous updates before the release and bugs that will be resolved during the testing fase will cause unexpected behavior.

---

### Post by Quackers on 2012-02-20
> **HavarN said:**
> It should work for 12.04 as well; since 12.04, as far as I know, uses grub2 too.

However, you are posting in the absolute beginners forum, so I draw the conclution that you are an absolute beginner. In that case, you should probably stick to a more stable or tested release than the development release. I would recommend trying 10.04 LTS or 11.10.

The development release will have numerous updates before the release and bugs that will be resolved during the testing fase will cause unexpected behavior.

Definitely true  ;)

---

### Post by Penguin360 on 2012-02-20
Thank both of you for your help!

---

### Post by Quackers on 2012-02-20
You're welcome :-)
If you still want to use 12-04 you should pay this forum a visit 

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=412](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=412)

---

### Post by Penguin360 on 2012-02-20
> **Quackers said:**
> You're welcome :-)
If you still want to use 12-04 you should pay this forum a visit 

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=412](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=412)

Thanks, I have been visiting that forum a lot. 

I am using the development release because it helps me to learn quickly. I have some basics of Ubuntu (obviously not enough) and I am not afraid of system crashes and bugs, it has been fun (I have a dedicated PC for Ubuntu 12.04).

Thanks to both of you again for your patience and help. :popcorn:

---

