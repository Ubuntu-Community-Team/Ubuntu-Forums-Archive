---
title: "resizing"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by crazysawsaw on 2013-03-24
i found out that when i installed ubuntu i formatted every thing by accident and now i tryed to install windows 7 but when i did i find that all of my patition are gone and now i only have a big partition and another samll one so i cant to install windows 7 at all ..... i tryed to resize the big partition with a programme called GParted but it didn't work ... and i found a logo like a key beside the two partition ..... so what can i do to install win 7 even if thats mean to formate the ubuntu and HOWWWWWWWWWWW??????

---

### Post by nothingspecial on 2013-03-24
You need to make a new partition with a live cd or live usb. You cannot do it from your Ubuntu install because you cannot resize a partition you are using.

---

### Post by carl4926 on 2013-03-24
Ideally you should post a screenshot of what you see in gparted

But typically if you want to start over you can select create new partition table > (probably msdos type) unless you have 3TB +
Then you should be able to re-partition

---

### Post by crazysawsaw on 2013-03-24
>  You need to make a new partition with a live cd or live usb. You cannot  do it from your Ubuntu install because you cannot resize a partition you  are using


CAN YOU SHOW ME HOW ????

---

### Post by nothingspecial on 2013-03-24
Use the live cd or usb you installed ubuntu with.

Boot it up, press the windows key and start typing gparted.

Launch gparted, select your ubuntu partition, right click and unmount it if necessary. Then choose to resize it and use the slider. Then right click the empty space you just created and make a new ntfs partition there. Then install windows7 in that partition.

Finally, boot the live cd again and use the boot repair utility so that you can boot ubuntu or windows.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by crazysawsaw on 2013-03-24
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar491516_60.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=491516") 				 				 					 						 	[**[COLOR=#C61919][B]nothingspecial**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=491516")


MANY THANXX MY FRIEND .... but i want to know if the last step is neccesery ... and if i can after that remove ubuntu

---

### Post by nothingspecial on 2013-03-24
If you no longer wish to use ubuntu then the last step will not be necessary.

---

