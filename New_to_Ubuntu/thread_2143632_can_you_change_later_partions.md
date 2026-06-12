---
title: "can you change later partions"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by DragonGirl123 on 2013-05-09
ok im installing lubuntu right now and i chose the partion sizes but can i change the partion sizes later? if it gets full?

---

### Post by DuckHook on 2013-05-09
You can but it's not easy and can be dangerous (partition changes always are). It will help us help you to know your intentions. Are you dual booting with Windows? Reserving room for future OSes?

---

### Post by DragonGirl123 on 2013-05-09
im dual booting with windows 7

---

### Post by Impavidus on 2013-05-09
Don't use the Lubuntu installer to shrink windows partitions. Use the windows tool for that. You can change partitions later, but it's rather tricky.

Partitioning is difficult, especially for beginners. There may be a limit to the number of partitions you can make on your hard drive (4), which complicates matters. If you don't know how to proceed it may be easiest if you quit the installer for a moment and run the program "gparted" from the live disk. It will show the layout of the disk. Post a screenshot and we can advise you on how to proceed. It can also tell you wether the disk uses MBR (master boot record) or GPT (not sure what it stands for) partitioning.

---

### Post by DuckHook on 2013-05-09
Then, ***without installing***, from LiveDVD/USB, please post output of:```
sudo parted -l print
```Also, tell us what you want to do: How much space do you want to set aside for Lubuntu? Will it be your main OS with Windows as secondary or other way around? Do you want a common data partition accessible by both OSes? Any other info about your intentions is helpful.

<edit>

Impavidus and I are on exactly the same track. My command will provide the same info as his request for screenshot. Do whichever is easiest for you.

</edit>

---

### Post by DragonGirl123 on 2013-05-09
Well i would like it to have equal data , because lubuntu is mostly for internet ,movie storage etc. While windows is for gaming. Also i dont know anything about common data partions.

---

### Post by DuckHook on 2013-05-09
A common data partition will allow you to access that data either from Windows or Lubuntu. This is very useful for some people who want to, say, listen to their music no matter which OS they are booted into. It is a simple matter of defining one more NTFS partition that both OSes can read. Since Impavidus has this well in hand, I will now go into lurking mode so as not to interfere with his further advice and instructions.

---

