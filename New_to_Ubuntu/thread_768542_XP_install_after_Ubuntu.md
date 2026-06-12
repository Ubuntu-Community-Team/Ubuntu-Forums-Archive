---
title: "XP install after Ubuntu"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by spookyct on 2008-04-26
Hey guys,

I have a pretty stable version of Ubuntu running on my machine right now.  Unfortunately, I have to install Win XP on this machine also, due to work requirements.  I tried using VMWare, but it is painfully slow.

What is the process for accessing Ubuntu when installing XP after Ubuntu?

---

### Post by nicedude on 2008-04-26
google it and read a guide on it, thats way easier than screwing up something. And after your done you will still use grub boot loader to acces both XP & Ubuntu.

---

### Post by spookyct on 2008-04-26
Hmmmm...  I have very low coupling between my ubuntu OS partition and my data partition.

I think I might just go ahead and backup my data partition, then do a fresh install of XP followed by an install of 8.04.

---

### Post by seshomaru samma on 2008-04-26
actually its not that difficult
install XP and then reinstall GRUB


boot from the live cd
then
```
sudo grub 
```
```
find /boot/grub/stage1
```
replace the question marks with the output you got for the find command:
```
root(hd?,?)
```
(probably root (hd0,1))
```
setup (hd0)
quit
```

---

### Post by nicedude on 2008-04-26
Thats the recommended way. XP first then Ubuntu, and when installing XP I would specify a partition size to create and leave rest of space free so when you do the Ubuntu install you don't have to resize your XP partition. Good luck with your PC :-)

---

### Post by spookyct on 2008-04-27
Got XP installed.  :-(

```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root(hd0,0)

Error 27: Unrecognized command

```


??

---

### Post by spookyct on 2008-04-27
figured out that whitespace matters....


I just re-installed Ubuntu, but I am still not able to boot with grub.  What can I do??

---

### Post by seshomaru samma on 2008-04-28
> I just re-installed Ubuntu, but I am still not able to boot with grub. What can I do??
can't boot Win or Linux?

---

### Post by Bodsda on 2008-04-28
download a 'Super Grub Disk' from 
[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

burn it to a cd the boot it, reinstall grub and you should be sorted

---

