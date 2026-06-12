---
title: "Ubuntu Automaticly dismounts my Usb harddrives"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Troca on 2008-06-19
starting today Ubuntu Automatically dismounts my Usb hard drives happened 4times now. All the hard drive icons disaper from the desktop and i have to click the places menu on top and select each hard drive again for them to reaper enoying sens iam seeding on torrent on 2 of em and i use 1 to download on i have 3 in total. anyway running ubuntu for about 3month now and this is the first time it does this and i have no idea why.

as you might understand iam not a expert and still a new iam using the GUI as mutch as i can and slowly learning some console commands.

i think i know how to mounting works but i have never mounted a drive manualy i relie on the GUI atm sens iam still a newb. 

anyway any input on this problem would be gr8

sorry for my crapy spelled english.

Ubuntu vesrion 8.04 hardy and latest linux kernel installed.

---

### Post by Troll_the_Great on 2008-06-19
What format are your usb hard drives? NTFS? You can install ntfs-config and they will be mounted automatically at start-up.
Have a look here :

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Tell me if this works.
Cheers!

---

### Post by Troca on 2008-06-19
they are ntfs and they do mount automaticly on startup but all of a suden startion from today ubuntu just losses them (dismounts them i gues) randomly havent happend now tho for some time maby i just ben unlucky whith some bug or something i honestly dont know whats was or still is wrong

---

### Post by Troll_the_Great on 2008-06-19
Try with ntfs config. Maybe it will work.I am not a linux guru, so I can't tell you more. I use ntfs config and I don't have any problems.
Cheers!

---

### Post by kansasnoob on 2008-06-19
I'm a "gui-guy" myself. Call it lazy or dumb, whatever!

Anyway I've never encountered your exact problem, but for the purpose of auto-mounting external hard drives, pen drives, etc. I like to go to Synaptic and install either:

usbmount

or:

pmount and
hal

The only advantage to using the combination of pmount & hal is that an icon appears on the desktop whenever a USB device is plugged in.

Either is easily reversed by removing the aforementioned packages if it doesn't suit you or help solve your problem. I prefer usbmount.

---

### Post by kansasnoob on 2008-06-19
> **Troll_the_Great said:**
> Try with ntfs config. Maybe it will work.I am not a linux guru, so I can't tell you more. I use ntfs config and I don't have any problems.
Cheers!

+1

ntfs-config is indeed a great tool!

ntfsprogs is much "fiddlier" but it does extend more support for reading & writing to ntfs partitions (even encrypted files) along with a few more goodies. But it's not particularly simple!

---

### Post by Troca on 2008-06-21
well i have ntfs-3g and when i  boot ubuntu i auto mounts all my drives on the desktop but every now and then it dismounts the automaticly for some reason and i have to go In the Places menu and reselect eatch one for them to mount again,

---

### Post by cariboo on 2008-06-21
When this happens, what is the output of System-->Administration-->System Log messages this might give you a clue as to what is happening.

The terminal way:

```
cat /var/log/messages
```

Jim

---

