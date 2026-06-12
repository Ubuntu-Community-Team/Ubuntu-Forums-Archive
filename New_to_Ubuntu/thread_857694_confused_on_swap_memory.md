---
title: "confused on swap memory"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by zamadatix on 2008-07-12
i was reading an Ubuntu forum that had me make a swap partition so i copied the code it made a 256 MB one but said i would need to change something to make it load on boot so i was wondering if it would be easier for someone to explain simply as possible how to make a swap file.

---

### Post by overdrank on 2008-07-12
> **zamadatix said:**
> i was reading an Ubuntu forum that had me make a swap partition so i copied the code it made a 256 MB one but said i would need to change something to make it load on boot so i was wondering if it would be easier for someone to explain simply as possible how to make a swap file.

Hi and this link helped me create a swap
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by oilchangeguy on 2008-07-12
> **zamadatix said:**
> i was reading an Ubuntu forum that had me make a swap partition so i copied the code it made a 256 MB one but said i would need to change something to make it load on boot so i was wondering if it would be easier for someone to explain simply as possible how to make a swap file.

when you install ubuntu, it creates it's own partitions. including a swap. there is no need to do any manual partitioning.

---

### Post by Vivaldi Gloria on 2008-07-12
Give the following command in a terminal

```
sudo fdisk -l
```

Find the line containing the swap partition to see that you indeed have a swap.

---

### Post by zamadatix on 2008-07-12
i thought i had 512 m of memory when i installed and did not make a swap partition in the beginning but found i only had 394 and Firefox would get stuck after a few minutes sand defiantly wasn't reinstalling.

i read overdranks link to the wiki but am stuck on how to save the swap file it is in use but i am lost on how to save it and keep getting access denied messages when i am the only user and administrator.

anyone ever saved a swap file? i could really use some help.

---

### Post by zamadatix on 2008-07-12
anyone? i cant restart until i have this swap thing finished :confused::(

---

### Post by overdrank on 2008-07-12
> **zamadatix said:**
> anyone? i cant restart until i have this swap thing finished :confused::(

Ok which step are you getting stuck on? there are 4 step. If you have the swap file running then you will have to add it to the Fstab
```
#

edit your /etc/fstab:

sudo gedit /etc/fstab

#

and add this line at the end of the file:

/mnt/512Mb.swap  none  swap  sw  0 0

# save and reboot 
```

---

