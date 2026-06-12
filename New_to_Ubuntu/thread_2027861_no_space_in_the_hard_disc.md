---
title: "no space in the hard disc"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2012-07-17
Hi, I have a problem. I have ubuntu 11.10. If I try to load a file, a video, etc..., it says to my there is not enough space in the directory and I can't load it. I have looked into the disc analyzer and it says to me there is a lot of  Gibs I haven't used. What can I do? Can anyone help me? Thanks

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu

Open a terminal and run:
```
  sudo apt-get clean   
```
Then:
```
  sudo apt-get autoclean   
```
Then
```
 sudo apt-get autoremove    
```

---

### Post by Cheesemill on 2012-07-17
also can you post the output of:
```
df -h
```
So we can see where all your space has gone.

---

### Post by kansasnoob on 2012-07-17
> **Cheesemill said:**
> also can you post the output of:
```
df -h
```
So we can see where all your space has gone.

And possibly:

```
sudo parted -l
```

---

### Post by Jonatan Formentera on 2012-07-17
I'have used hmfal's method but it hasn't worked. I've introduced sudo parted -l and the results are:

Modelo: ATA WDC WD2500BEVT-2 (scsi)
Disco /dev/sda: 250GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Number      beginning     end     Tamaño  size               file's system  Banderas
 1      1049kB  14,0GB  14,0GB  primary  ntfs                 diag
 2      14,0GB  14,1GB  105MB   primary  ntfs                 arranque
 3      14,1GB  250GB   236GB   primary  ntfs


Modelo: Kingston DataTraveler G2 (scsi)
Disco /dev/sdb: 4010MB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Typo     Sistema de ficheros  Banderas
 1      4129kB  4010MB  4006MB  primary  fat32                start

Can anyone help me interpert these dates?

---

### Post by Paqman on 2012-07-17
Right, it looks like you've installed using Wubi? How much disk space you did you tell the installer to create?

---

### Post by Jonatan Formentera on 2012-07-17
I've used wubu. My micro portable has 250 at all. In the windows partition I've have used some 75 Gibs and in the ubuntu just a few Gibs. Perhaps I should do the ubuntu partition wider. I think, I should first spare my contents in an external disc before to proceed to it in order to avoid erase my documents

---

### Post by Paqman on 2012-07-17
When you use Wubi to install you have to tell it how much disk space to give to Ubuntu. Your disk might be 250GB, but Ubuntu will only be able to use as much space as you give it when you install. When you open up System Monitor and go to the File Systems tab, how much space does it show?

---

### Post by Jonatan Formentera on 2012-07-17
System tabs
It's says to me:
/dev/loop0/ ext 4 free 887,2 mib used 99%
/dev/sda/host fsublk free 162 Gib used 26%

---

### Post by Paqman on 2012-07-17
> **Jonatan Formentera said:**
> 
/dev/loop0/ ext 4 free 887,2 mib used 99%


That's your problem right there. The virtual disk that you've installed Ubuntu into is 99% full. You've got a few options:
[LIST=1]
[*]Move some of your data to another location
[*]Reinstall using Wubi and give it more space this time
[*]Reinstall as a normal dual-boot and give it as much space as you want
[*]Try [expanding your Wubi virtual disk]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk")
[/LIST]

---

### Post by Jonatan Formentera on 2012-07-17
I've done so. I've translated my files to another place, I've romoved ubuntu with wubi and installed it again. Yet, I don't know how to give ubuntu more space. I'm in hard disk and I seing a rectangle with tree partitions. Am I on the right way? Can anyone help? Thanks

---

### Post by Paqman on 2012-07-19
When you run the wubi installed there will be a drop-down box to pick how much space you want to give to Ubuntu. You should be looking at a screen like this:
[IMG]https://help.ubuntu.com/community/Wubi?action=AttachFile&do=get&target=Wubi3.png[/IMG]

---

