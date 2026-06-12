---
title: "Error opening file '/media/disk/': Permission denied"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-10
Hello,

I have installed a new 120 gig Hard Drive and and tried to mount it using Partition Editor as advise on other thread i made.

Steps i took:

1. Selected the drive that was showing that was not mounted.
2.click on partition => format to ext2 
3. reboot as per request
4. it now shows that its mounted 

After this i tried to store some file and it gave this error:
Error opening file '/media/disk/cards.jpg': Permission denied

Seems like i dont have access on read and write.

Could i get some help on this please? Now, just to let you know i am very new to linux and i am still trying to learn this via GUI so if there is a coomand i have to run please give it to me on granpa noobie format :)

thanx for your advance help

---

### Post by appoloin on 2008-05-10
Oe more thing i forgot to mention the hard drive i installed in my machine is SATA

---

### Post by om1 on 2008-05-10
press alt + F2
```
gksudo nautilus
``` gives you root filemanager you can access the files now

---

### Post by malathion on 2008-05-10
You probably have a permissions problem. Therefore we are going to take ownership of the mounted filesystem.

Where 'user' is your username:

```
sudo chown user:user /media/disk/
```

---

### Post by malathion on 2008-05-10
> **om1 said:**
> press alt + F2
```
gksudo nautilus
``` gives you root filemanager you can access the files now

This will also work, and it may be more secure. If you aren't as concerned about security, and want more general write access to the filesystem, use chown.

---

### Post by appoloin on 2008-05-10
THANK YOU SOO MUCH!!! you are the best.

1 last question. I have another HDD that i want to add in my machine but im afraid that if UBUNTU dont detect it again and i use partition editor i might loose the files. is there a way to mount it without loosing any files?

---

### Post by malathion on 2008-05-10
> **appoloin said:**
> THANK YOU SOO MUCH!!! you are the best.

1 last question. I have another HDD that i want to add in my machine but im afraid that if UBUNTU dont detect it again and i use partition editor i might loose the files. is there a way to mount it without loosing any files?

You always run a risk of losing data whenever you edit partitions. The only defense to this is to securely back up your data before using gparted.

---

### Post by Mspirit on 2010-06-07
> **malathion said:**
> You probably have a permissions problem. Therefore we are going to take ownership of the mounted filesystem.

Where 'user' is your username:

```
sudo chown user:user /media/disk/
```

This made my day XD

---

### Post by Tronis on 2010-11-30
sudo chown user:user /media/disk/[FONT=monospace]
This did not work for me and I dont know why. It gave me back this message.

chown: changing ownership of `/media/sdc1': Operation not permitted


But the gksudo nautilus worked.

I just don't want to do it every time I want to add something onto my [FONT=Verdana]external hard drive. It is severely annoying.[/FONT][/FONT]
[FONT=monospace]
[/FONT]

---

### Post by tpchuckles on 2011-03-16
i have ubuntu installed on my laptop's internal hard drive, and xubuntu installed on a flash drive, i would be doing this rom the xubuntu flash drive to access the internal ubuntu hard drive:

if i do that (what you were talking about above, re-establishing ownership), would it mess up anything on the internal hard drive? i wouldn't have any issues with the internal hard drive were i to boot up on it then would i?

---

