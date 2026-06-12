---
title: "Is it possible to save to a flash drive while using live CD?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by pet_the_ibex on 2008-12-01
Hello,

I have my live CD running right now, and was wondering if I could save some Python files to my flash drive. I don't know much about console commands, but I wish I did. :) Any help would be appreciated.

Thanks and sorry for posting so many times!

-Lee

---

### Post by cdtech on 2008-12-01
You could mount your flash then it will be accessable through the places menu.

You need to open a terminal and type:
```
sudo fdisk -l
```
to find the device name. Then create a directory:
```
sudo mkdir /media/**?**
``` the **?** being the device.
Then mount the device:
```
sudo mount /dev/**?** /media/**?**
```

Hope this helps ya.....

---

### Post by pet_the_ibex on 2008-12-01
Thank you for the fast reply. I believe my drive is already mounted. Ubuntu displays my drive on the desktop and calls it a "mounted drive."

I was wondering if you could explain why I would need to run the steps you listed. I'm very curious, and love learning about operating systems and hardware. Thanks a lot!

-Lee

---

### Post by handydan918 on 2008-12-01
> **pet_the_ibex said:**
> Thank you for the fast reply. I believe my drive is already mounted. Ubuntu displays my drive on the desktop and calls it a "mounted drive."

I was wondering if you could explain why I would need to run the steps you listed. I'm very curious, and love learning about operating systems and hardware. Thanks a lot!

-Lee

Prolly cuz you mentioned terminal command and python, neither of which require a GUI...

If you have a GUI, it's all just drag and drop...

If you somehow run into a permissions issue, try ```
gksudo nautilus
``` to open the file manager with root privs.

---

### Post by pet_the_ibex on 2008-12-01
Thanks handydan and cdtech,

I think I can figure it out. Linux is great. :)

---

### Post by cdtech on 2008-12-02
> **pet_the_ibex said:**
> Thank you for the fast reply. I believe my drive is already mounted. Ubuntu displays my drive on the desktop and calls it a "mounted drive."

I was wondering if you could explain why I would need to run the steps you listed. I'm very curious, and love learning about operating systems and hardware. Thanks a lot!

-Lee
It's better understood if you read the manual pages that accompany any command line command. By using the "man (command name)" will give you the manual for that particular command. Type on a command line:
```
man sudo
```
This will explain the &#8220;sudo&#8221; command (execute a command as another user) etc...

As far as your device being mounted, just like handydan918 said "you can just drag and drop".

---

### Post by pet_the_ibex on 2008-12-02
Thank you.

---

