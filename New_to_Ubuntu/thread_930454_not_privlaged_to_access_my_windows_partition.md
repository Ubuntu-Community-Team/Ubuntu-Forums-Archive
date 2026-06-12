---
title: "not privlaged to access my windows partition"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by RogerKorby on 2008-09-26
as in the title i lost access to my windows partition when i boot up , it was working fine for weeks now it is missing from the desktop and when i go to access it it says im not privlaged

i added them to the fstab a few weeks ago and its been working fine

---

### Post by iaculallad on 2008-09-26
> **RogerKorby said:**
> as in the title i lost access to my windows partition when i boot up , it was working fine for weeks now it is missing from the desktop and when i go to access it it says im not privlaged

i added them to the fstab a few weeks ago and its been working fine

Does the terminal command,

```
sudo mount -a
```

shows the NTFS drive on your desktop?

---

### Post by RogerKorby on 2008-09-26
> **iaculallad said:**
> Does the terminal command,

```
sudo mount -a
```

shows the NTFS drive on your desktop?

domovoi@Domovoi:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:



does this have something to do with me getting the ntfs config tool because i wasnt able to write to the windows partition so i got that to see if it would fix it    and it did   but its been working fine

---

### Post by lisati on 2008-09-26
> **RogerKorby said:**
> domovoi@Domovoi:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:



does this have something to do with me getting the ntfs config tool because i wasnt able to write to the windows partition so i got that to see if it would fix it    and it did   but its been working fine
It's probably not connected with the config tool. Have you recently used the partition within Windows?

---

### Post by RogerKorby on 2008-09-26
ooo and also i have shut down the right way and everything trying to get it to fix 
i dont know what it means unclean shut down :(

---

### Post by RogerKorby on 2008-09-26
i did earlyer today yes everything was working fine   i have one whole drive that is ntfs and my other one is part of the second drive

---

### Post by lisati on 2008-09-26
> **RogerKorby said:**
> ooo and also i have shut down the right way and everything trying to get it to fix 
i dont know what it means unclean shut down :(

An "unclean shutdown" can happen when you use the power switch to turn your computer off, without giving Windows a chance to note on the disk that it has finished with it.

---

### Post by bumanie on 2008-09-26
That message is saying that windows has not been shutdown cleanly. Either A) Boot into windows and shutdown cleanly or 
       B) > sudo apt-get install ntfsprogs > sudo ntfsfix /dev/sdb1 (assuming that is the windows drive, which it should be from the error message) On the next start up of the windows drive, ntfsprogs should fix the ntfs filesystem so it can boot.

---

### Post by iaculallad on 2008-09-26
Or try to force mount it:

```
sudo mkdir /media/Forced
sudo mount -t ntfs /dev/sdb1 /media/Forced -o force
```

---

