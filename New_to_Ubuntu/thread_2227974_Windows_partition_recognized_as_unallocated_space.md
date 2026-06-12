---
title: "Windows partition recognized as unallocated space"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by jason98 on 2014-06-05
I am new to Linux. I was trying to dual boot windows 8.1 and ubuntu when I came across  this: ubuntu installer won't recognize windows as an OS and the C drive  is recognized as "unallocated space" by ubuntu. How can I install Ubuntu  alongside windows? I tried installing before, when windows 8 was UEFI, I  now reinstalled windows 8 and it's not UEFI now, what should I do?

---

### Post by fantab on 2014-06-05
Did you create space on HDD to install Ubuntu?
Can you boot Ubuntu DVD/USB Live and "Try Ubuntu (without installing)"? Do it.
After Ubuntu desktop loads, open Terminal (ctrl+alt+T), run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

It will be better if you can install both OS in UEFI mode.
Lets look at the output first.

---

### Post by jason98 on 2014-06-05
The first command (sudo parted -l) it says: Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT msdos partition table. Is this a GPT partition table?

---

### Post by fantab on 2014-06-05
Please post the full output, copy from terminal and paste it here.

---

### Post by jason98 on 2014-06-05
Full output:

ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?

---

### Post by jason98 on 2014-06-05
I don't even know what a GPT table is, so should I say yes or no? :o

---

### Post by fantab on 2014-06-05
Windows8 will only boot in UEFI mode if the HDD is GPT [GUID Partition Table].
To boot in BIOS/CSM/Legacy/non-UEFI mode Windows8 needs 'msdos' partition Table on HDD.
When you re-installed Windows in non-UEFI mode the installer must have changed the partition table on the HDD from GPT to 'msdos'. So far so good. 
However when the partition table was changed to 'msdos' the Windows installer does not take into account or remove the GPT backup table which is present on HDD.
This backup GPT table will confuse the Ubuntu installer... and hence the problem of 'unallocated space'.

To fix this you must run [fixparts]("http://www.rodsbooks.com/fixparts/"). It is part of 'gptdisk/gdisk' package and I think it is already there on the Ubuntu Live DVD/USB. If it is not then read the earlier link.
That should take care of the present situation.

Ideally you must install both OS in UEFI mode. UEFI is a replacement for older BIOS. And UEFI uses GPT partition table which has numerous advantages over 'msdos'.

I'd suggest that you reinstall Windows in UEFI mode and then install Ubuntu in UEFI mode.

[GUID Partition Table, [GPT] advantages]("https://wiki.archlinux.org/index.php/GUID_Partition_Table").

---

### Post by Luke M on 2014-06-05
Use fixparts to get rid of the leftover GPT table.

---

### Post by jason98 on 2014-06-05
What do I do in fixParts? And is there any ways I can easily switch from legacy to UEFI while keeping all data on windows? thanks for the help anyway :D

---

### Post by fantab on 2014-06-05
After installing fixparts you must run the following in the terminal:
```
sudo fixparts /dev/sda
```

It will tell you exact same thing about gpt signatures and offer to fix it. Say yes or 'y'.
Then 'w' to write changes and exit. Please read the fixparts tutorial I've linked you to.

Edit:
[s]NO, you cannot switch from GPT to 'msdos'... you have to start all over again.[/s]

You can switch from MBR (msdos) to GPT, but it won't be simple and clean: [http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
I haven't tried this before. And I cannot guarantee that it will work flawlessly.
I'd say give it a shot.. at worst you will lose data (I hope you have good backups) and or corrupt windows... give it a go.

---

