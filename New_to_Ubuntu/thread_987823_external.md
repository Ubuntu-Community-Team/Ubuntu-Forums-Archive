---
title: "external"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by hialti2d on 2008-11-19
I accidentally partitioned ubuntu to an external hardrive and cancled a few seconds later now ubuntu OS won't "mount volume" for my external hardrive.  how can i fix this.  in replys please remember this is my first day using ubuntu or any linux based system.

I tried using a partition doctor but i cant get one to open in ubuntu.

---

### Post by Keen101 on 2008-11-19
try this

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Billybob97060 on 2008-11-19
you might try something as simple as plugging your usb drive into a windows machine, clicking safely remove, and than plug back into your ubuntu machine, its actually worked for me many times

---

### Post by hialti2d on 2008-11-20
ok so i downloaded it and wrote it to a disk but i can't figure out how to run it or use it to check the external hardrive.

---

### Post by Billybob97060 on 2008-11-20
if you are using gparted live you will need to burn the file to a disc as an image file and restart your computer and boot with that cd. if you dont burn it as an image it will not be bootable

---

### Post by hialti2d on 2008-11-20
so i got gparted to boot up and hooked it up to the external drive.  then i reformatted it to linux base and tried reopening it in ubuntu but now it doesn't even read like it is connected to the computer.

---

### Post by Billybob97060 on 2008-11-20
Did you format the drive to FAT or NTFS? if the drive is just left unpartitioned it wont show up

---

### Post by hialti2d on 2008-11-20
ok, so it is reformated and partitioned and i have like 15 gb taken up on it that i can't read bc ubuntu says I am not the owner.  So i can't add files or change readability of hardrive.  how do i verify that i am the owner.  it is formatted as ext 1 i think, thats what it did automatically after the partition.

---

### Post by Crafty Kisses on 2008-11-20
You're going to have to show me your fstab, post the following command:
```
sudo cat /etc/fstab
```

---

### Post by hialti2d on 2008-11-20
wait, i fixed it! i used gparted to partition and format to ntfs and now it all works.  but i can't rename the hardrive (not supported by backend) not that that is killer important.

---

