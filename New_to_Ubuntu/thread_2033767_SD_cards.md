---
title: "SD cards"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Populus on 2012-07-26
I have files stored on a 32GB SDHC card which is now full. I recently bought a 64GBXC card but when I put it in my card reader, I got a message saying 'Unable to mount 64GB file system, Error mounting: mount: unknown file system type 'exfat'. The smaller card was msdos. Is there anything I can do so I can use the new card?

---

### Post by Derek Karpinski on 2012-07-27
```
sudo add-apt-repository ppa:relan/exfat
```

```
sudo apt-get update && sudo apt-get install exfat-utils fuse-exfat
```

---

### Post by Populus on 2012-07-27
Works fine now! Thanks for your help.

---

### Post by TimEnid on 2012-07-30
similar to this question, how do i format a card to exFat? In Disk utility and Gparted, the option is greyed out.

---

### Post by jayb151 on 2012-10-22
> **Derek Karpinski said:**
> ```
sudo add-apt-repository ppa:relan/exfat
```

```
sudo apt-get update && sudo apt-get install exfat-utils fuse-exfat
```

Worked perfectly in 12.10.

Thanks!

---

### Post by jayb151 on 2012-11-30
Actually,
I just got a new laptop, a Asus K55vd, and I can't mount the SD card on this one. I used this exact command for my T-101mt and it worked flawlessly, but now it won't work on the K55vd. Any thoughts?

---

### Post by Paqman on 2012-12-01
You could try reformating the card. If it's only going to be used on Linux systems then an EXT filesystem (EXT2 maybe?) or if you need cross-platform go for NTFS.

---

### Post by jayb151 on 2012-12-01
I don't want to do that because I'm dual booting with windows7. The Sd card (or another partition on the HD) makes it easy for me to have my data in both OSs.  I also already have a bunch of stuff on the Sd that I want to get off before I do anything with the card.

---

### Post by cmcanulty on 2012-12-01
Fat32 works on everything

---

