---
title: "really stuck on 'Unable to mount the selected volume'"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by keithbrowett on 2008-09-14
Ok ,i'm completely new to ubuntu ,and wasnt that good with any other OS before this ,but i'm a musician and i have songs that are really important to me on my hard drive but ubuntu wont let me get to them ,when i click on my hard drive in 'computer' it says 'Unable to mount the selected volume' and under that it says 'error:device /dev/hdal is not removable
error:could not execute pmount'
I have no idea how to use terminal but these files are really important to me ,so please if any one could help

---

### Post by nothingspecial on 2008-09-14
Open a terminal (Accessories > Terminal in your menus) and copy and paste - 

```
sudo fdisk -l
```

Then copy and paste the gobbldygook that it spits out back here.

---

### Post by Dadsgé on 2008-09-14
i had the same problem a few days ago
first U have to find the name of the device that cannot be mounted
in terminal:
> sudo fdisk -l 

then u get a list with al the devices connected to your PC
there u search the specific device

then:
> sudo apt-get install ntfs-3g ntfs-config
follow the instructions...
> sudo mkdir /mnt/ntfs
(this was the installing part)

then the thing u can use every time one of your devices cannot mount
> sudo mount -t ntfs /dev/'name of device' /mnt/ntfs
name of device is the name u search and found in the first particion of my explanation ;)

---

### Post by Dadsgé on 2008-09-14
name of your device is probably 'hdal' as i assume from your first comm

---

### Post by acidsolution on 2008-09-14
are you using dual boot with windows ???

---

### Post by keithbrowett on 2008-09-14
> **nothingspecial said:**
> Open a terminal (Accessories > Terminal in your menus) and copy and paste - 

```
sudo fdisk -l
```

Then copy and paste the gobbldygook that it spits out back here.
It says 
Disk /dev/hda: 61.4 GB 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start       End      Blocks       Id    System
/dev/hdal   *          1       7475     60042906      7    HPFS/NTFS

---

### Post by keithbrowett on 2008-09-14
> **Dadsgé said:**
> name of your device is probably 'hdal' as i assume from your first comm
When i tried 'sudo apt-get install ntfs-3g ntfs-config' it said 'E; Couldn't find package ntfs-3g'

---

### Post by Dadsgé on 2008-09-14
ow, the name of your disk is 'hda'
try with this name ;)

---

### Post by keithbrowett on 2008-09-14
Sorry ,what am i replacing with 'hda' ,im really new to this sorry

---

### Post by keithbrowett on 2008-09-14
> **acidsolution said:**
> are you using dual boot with windows ???
No but i had windows on the drive before and need to get files off of the drive ,but i dont have windows anymore so cant use that to get them

---

### Post by miegiel on 2008-09-14
Just some thoughts:

I believe ntfs support is installed already by default in ubuntu.

I'd expect /dev/hda1 to be your 1st partition (often called disk or drive in windows) on disk hda and not /devhdal. Is that really a small L ?

---

### Post by keithbrowett on 2008-09-14
> **miegiel said:**
> Just some thoughts:

I believe ntfs support is installed already by default in ubuntu.

I'd expect /dev/hda1 to be your 1st partition (often called disk or drive in windows) on disk hda and not /devhdal. Is that really a small L ?
...no ,you'd be right there actully ,but i still dont know what to do

---

### Post by Dadsgé on 2008-09-14
hmm I think the l is a number one. (1)

---

### Post by keithbrowett on 2008-09-14
Yeah ,i've just realised that it is a 1 ,sorry ,so what do i type in

---

### Post by Dadsgé on 2008-09-14
try:
> sudo mount -t ntfs /dev/hda1 /mnt/ntfs

---

### Post by acidsolution on 2008-09-14
ok first 
```

cd /media
sudo mkdir folder
 
 sudo mount.ntfs-3g /dev/hda1 /media/folder


```
if your harddisk name is not hda1 than replace it with its name 
this must work for you

now you can browse thru media and than folder to access your drive

---

### Post by keithbrowett on 2008-09-14
> **Dadsgé said:**
> try:
It says 'mount: mount point /mnt/ntfs does not exsist'

---

### Post by acidsolution on 2008-09-14
> **keithbrowett said:**
> It says 'mount: mount point /mnt/ntfs does not exsist'

make directory in /mnt folder 
```

sudo mkdir /mnt/ntfs

```

---

### Post by supersnoop on 2008-09-14
> **keithbrowett said:**
> ...no ,you'd be right there actully ,but i still dont know what to do

NTFS is available in the Package Manager:System-Admin-Synaptic Then search.
The release notes say it does not install automatically.

Hope this is of some help

---

### Post by nothingspecial on 2008-09-14
Sorry about that, my internet crashed just as I was replying to you.

Now, it might be that you haven`t correctly unmounted (or safely removed) your drive. If this is the case then, in your terminal -
```

sudo apt-get install ntfsprogs
```

Then 

```
sudo ntfsfix /dev/hda1
```

---

