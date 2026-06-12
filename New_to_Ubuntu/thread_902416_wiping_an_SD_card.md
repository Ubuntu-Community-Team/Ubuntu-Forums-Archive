---
title: "wiping an SD card"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Stefanie on 2008-08-27
How can I wipe my SD card in Ubuntu? I want to make sure all data is erased.

---

### Post by sydbat on 2008-08-27
You should be able to simply format it. I assume you have a card reader, so format with FAT32 (so the card will still be recognized by all devices).

---

### Post by neurostu on 2008-08-27
Actually reformatting the card will only write over the partition tables on the card, this is a common mistake and forensics experts can recover data from disks with a re-written partition table.  Although the data is no longer accessible the 0's and 1's are still there the OS just doesn't know how to access them, programs can and have been written that try to extract this unknown data.

If you are really worried about completely wiping the card you need to completely fill the card a few time times with different data. This will make it pretty much impossible for the data to be recovered. (For HDD's  a few times is 3 or 4, which is pretty much a function of the medium in which data is stored... I'm not familiar with how many times is enough for a SD card)

If I were you I would suggest copying over the disk with junk data... deleting the data and writing over with more junk data...

Then you can be pretty sure that the data you're trying to secure is gone.

---

### Post by Stefanie on 2008-08-27
ok thanks maybe i can try that. aren't there applications like Darik's Boot and Nuke for SD cards?

---

### Post by neurostu on 2008-08-27
I'm not aware of any... but it certainly should be easy enough to fill the card with some sort of command like:
```

cat <largeFile> > <fileOnSdCard>

```
so if you were to type:
```

cat /dev/cdrom0 > /media/SDCard/junk.txt

```
that would copy whatever it in your cdrom drive in binary until the card is full...
pick a random DVD and do this and you can assume your data is gone.

---

### Post by Cadmus on 2008-08-27
There's a command 'wipe' which is pretty good at this stuff but it's overkill, otherwise use the 'dd' command to write garbage from /dev/urandom onto the card a few times. For instance to do it on a floppy you do:
```
dd if=/dev/urandom of=/dev/floppy
```

[COLOR="Red"]**Some call 'dd' data destroyer as one slip of the finger can annihilate your entire install, be VERY careful when using it**[/COLOR]

---

### Post by Rolcol on 2008-08-27
You can clear it completely (unformatted) by writting zeros to it.```
dd if=/dev/zero of=/dev/SD/Card/Path
```

---

