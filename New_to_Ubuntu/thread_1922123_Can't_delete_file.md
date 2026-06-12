---
title: "Can't delete file"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by mcstat on 2012-02-08
Hi, I'm trying to delete a file on my external hard drive but I'm failing I'm getting the following message in terminal:

mcstat@linux-bhgh:/media/Expansion Drive> sudo rm -r Tari
rm: cannot remove `Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/1808624357': Directory not empty
rm: cannot remove `Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/3481883629': Directory not empty
rm: cannot remove `Tari/Thumbs.dn/com1.{d3e34b21-9d75-101a-8c3d-00aa001a1652}/úø ../LastF': Directory not empty

Can any one please help me, I'm trying to avoid formatting my hard drive just because of that one file. I'm using opensuse 12.1 if that is helpful.

---

### Post by sudodus on 2012-02-08
> **mcstat said:**
> Hi, I'm trying to delete a file on my external hard drive but I'm failing I'm getting the following message in terminal:

mcstat@linux-bhgh:/media/Expansion Drive> sudo rm -r Tari
rm: cannot remove `Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/1808624357': Directory not empty
rm: cannot remove `Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/3481883629': Directory not empty
rm: cannot remove `Tari/Thumbs.dn/com1.{d3e34b21-9d75-101a-8c3d-00aa001a1652}/úø ../LastF': Directory not empty

Can any one please help me, I'm trying to avoid formatting my hard drive just because of that one file. I'm using opensuse 12.1 if that is helpful.

Look at the file permissions of the files not yet possible to get rid of:

```
ls -l Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/1808624357
ls -l Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/3481883629
ls -l 'Tari/Thumbs.dn/com1.{d3e34b21-9d75-101a-8c3d-00aa001a1652}/úø ../LastF'
```

I think it has something to do with the trashcan, so maybe the system locks these files. Can you clean your trashcan?

Maybe you can get rid of them, if you boot from a CD or USB drive.

---

### Post by SuaSwe on 2012-02-08
Out of interest, what happens if you navigate to those folders and try to remove the files initially, then remove the directories once empty? For example:

```

sudo rm -r Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/1808624357/*
sudo rmdir Tari/.Trash-1000/expunged/401778371/.Trash-1000/expunged/1808624357/

```

---

### Post by winh8r on 2012-02-08
Try using rm -R command first.

Or use shred command

shred -fuz <filename> to remove contents from directories first.

shred means that the contents will not be recoverable after processing.

use 

man rm 

man shred

for more info.

---

### Post by HiImTye on 2012-02-08
you could always try to chown it first
```
sudo chown -R yourusername Tari
sudo rm -R Tari
```

---

