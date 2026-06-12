---
title: "Installation Doubts"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by siddharthshukla on 2008-08-11
i recently installed ubuntu on my system with dual boot along wid XP. during the installation i choose guided resize and i allocated 9gb of the 39gb on one of the partitions as ubuntu. The installer automatically adjusted the swap space in the 9gb itself. my question is 
1) Is 9gb (including swap ) sufficient for ubuntu
2) if i manage files on all  the partitions using ubuntu(fat32 and NTFS) will i be benefited by the superior disk management of ubuntu(no defrag) over xp.
3) can i at a later stage increase the size of the ubuntu installation

---

### Post by hyper_ch on 2008-08-11
> **siddharthshukla said:**
> 1) Is 9gb (including swap ) sufficient for ubuntu
For test driving it is... however when you want to add more programs and stuff you might want to have more space...

> **siddharthshukla said:**
> 2) if i manage files on all  the partitions using ubuntu(fat32 and NTFS) will i be benefited by the superior disk management of ubuntu(no defrag) over xp.
No, it's related to the filesystem and not to the OS

> **siddharthshukla said:**
> 3) can i at a later stage increase the size of the ubuntu installation
Yes

---

### Post by siddharthshukla on 2008-08-11
thnks a lot, can u tell me how i can resize the ubuntu installation.

---

### Post by hyper_ch on 2008-08-11
make the windows partition(s) smaller and the ubuntu one(s) bigger.

---

### Post by ajgreeny on 2008-08-11
> make the windows partition(s) smaller and the ubuntu one(s) bigger.Like hyper_ch says, but to clarify things a bit, run the live CD and use Partition Manager (gparted).  Make sure you defrag windows first a couple of times for safety's sake.

---

### Post by Bölvaður on 2008-08-11
Also you might want to make the partitions so it is easy for you to upgrate to different version of ubuntu or to switch between distros without fuss with backups. So having a backup parition or some secure place is good.
For a newbie in Linux who also uses windows for the data, he might want to have all his data on ntfs partition and/or also on his /home

---

### Post by hyper_ch on 2008-08-11
a backup partition is of now use if altering the partitions kills it all...

---

