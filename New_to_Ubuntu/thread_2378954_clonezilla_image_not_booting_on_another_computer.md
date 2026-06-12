---
title: "clonezilla image not booting on another computer"
date: 2017-11-29
forum: New to Ubuntu
---

### Post by indrekk on 2017-11-29
Hi,


I've managed to get all my previous problems solved from reading already posted/solved posts but this time it's different.


I am trying to clone a whole ubuntu partition from my laptop (Lenovo W520) to my work computer (Dell T1600) using clonezilla and this wonderful post: [https://ubuntuforums.org/showthread.php?t=2124458](https://ubuntuforums.org/showthread.php?t=2124458)


It wasn't successful so I tried reinstalled grub by following the steps here: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)


I get to the point where I can choose between three OS-es on the target computer:
1) the original ubuntu
2) the cloned ubuntu from W520
3) windows


1 and 3 boot without a problem. The clone starts to boot. Then I see the purple-backgrounded ubuntu logo and the white-orange dots changing colors for about 2 minutes. And them I'm greeted with a similar screen as here: [https://i.stack.imgur.com/clhB8.jpg](https://i.stack.imgur.com/clhB8.jpg) (only it's dev/sdb5, where the clone ubuntu is restored to).


Here's my grub pastebin: [http://paste.ubuntu.com/26072432/](http://paste.ubuntu.com/26072432/)


I wonder if what I'm doing is not meant to be done / impossible?
Do you guys have any ideas what to try next to be able to boot to this cloned ubuntu?


With high hopes and eternal gratefulness in mind,


Indrek
(my first post here :) )

---

### Post by VMC on 2017-11-29
> **indrekk said:**
> ...
I am trying to clone a whole ubuntu partition from my laptop (Lenovo W520) to my work computer (Dell T1600) using clonezilla and this wonderful post: [https://ubuntuforums.org/showthread.php?t=2124458](https://ubuntuforums.org/showthread.php?t=2124458)


It wasn't successful so I tried reinstalled grub by following the steps here: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)


I get to the point where I can choose between three OS-es on the target computer:
1) the original ubuntu
2) the cloned ubuntu from W520
3) windows


1 and 3 boot without a problem. The clone starts to boot. Then I see the purple-backgrounded ubuntu logo and the white-orange dots changing colors for about 2 minutes. And them I'm greeted with a similar screen as here: [https://i.stack.imgur.com/clhB8.jpg](https://i.stack.imgur.com/clhB8.jpg) (only it's dev/sdb5, where the clone ubuntu is restored to).


Here's my grub pastebin: [http://paste.ubuntu.com/26072432/](http://paste.ubuntu.com/26072432/)


I wonder if what I'm doing is not meant to be done / impossible?
Do you guys have any ideas what to try next to be able to boot to this cloned ubuntu?


With high hopes and eternal gratefulness in mind,


Indrek
(my first post here :) )
Your not stating what doesn't work. Output messages? Also Lenovo W520 and Dell T1600 have different hardware. How did you overcome that? Also the different partition must be equal or larger. '*fsarchiver*' would be a better option.

---

### Post by leunam12 on 2017-11-30
Did you change the fstab? The cloned partition has an fstab with the partition identifier from the Lenovo.
You have to boot from the working Ubuntu and type blkid on the terminal and write down the UUID for your /dev/sdb5, 
then you have to mount sdb5 and modify the fstab with the right information.
Then run boot-repair. If it doesn't work after that maybe there is a hardware conflict. I have been able to do what you 
are trying to do without problems, it is possible, but there is also the possibility of hardware conflicts that need to be resolved manually.

---

