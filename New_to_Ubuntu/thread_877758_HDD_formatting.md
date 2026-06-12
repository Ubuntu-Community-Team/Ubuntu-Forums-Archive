---
title: "HDD formatting"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Bukarts on 2008-08-02
I have external Hdd 250 G, connected to the pc with USB cable, the problem is that I cant format it in Vista, but i can do it in UBUNTU, but i dont know    in what system i shuld format it! gparted gives me a choice from ext2  ext3  fat16  fat 32 linux-swap   and reisefs. 
       Please give me some advice!

---

### Post by stinger30au on 2008-08-02
id go fat 32 or ntfs.

reason being that is your going to plug it in to the windows machine it will be easily read. there is a few windows utilitys round to allow this to happen but why muck around.

and fat 32 and ntfs can be read / write by linux anyhow

---

### Post by Atomic Dog on 2008-08-02
If you want to use it with Vista, Ubuntu and even your PS3 then format it as fat32.

---

### Post by Bukarts on 2008-08-02
But isnt there some limitation in fat 32, like 4 g  files???  BTW it doesnt allows me to make it in ntfs

---

### Post by Bukarts on 2008-08-02
Ok there is one more problem! I formatted it in FAT 32.But the hdd doesnt show up in UBUNTU.  Then restarted pc and log in to Vista, It was there and I was able to send some files to hdd, then I disconnected it from pc. Once more restarted and tried to connect it again as soon as I pluged it in viska says that I need to Format hdd before using it!!

---

### Post by ingeva on 2008-08-02
> **Bukarts said:**
> ...to connect it again as soon as I pluged it in viska says that I need to Format hdd before using it!!

I would format it as NTFS, which can be read/written by both systems.
I'm surprised that Vista won't format the disk, but try this:

Delete all partitions using Linux, so when you start Vista you have a clean disk.
Enter the control panel, select "Administrative tasks" (This is just from memory, and based on me XP experience), then "Computer management" and "Disk Management". Maybe the sequence is slightly off here, but what comes up should be an image of the various disks in the system.

Right-click on the correct partition and select "Format", NTFS system. Choose quick format or else it will take a very long time. Assign a disk letter to the partition, or you may have a problem accessing it.

You should now be able to copy files files to the partition, and when you start Linux you should have the partition mounted automatically. An icon should appear on your desktop. Double-click it to start the filemanager.

---

### Post by Bukarts on 2008-08-02
already did that, it just cant format it! Maybe it is becose i dont have usb2 but the hdd case is made for usb2. but why then i can format it in ubuntu to FAT 32 and if I dont unplug it i can use it in vista ( But not in UBUNTU) !!

---

