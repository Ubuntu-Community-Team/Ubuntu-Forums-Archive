---
title: "replace my distro without affecting my Windows-partition?"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by DoPiDo on 2012-10-04
I'm new to Linux, so you 'll probably have to provide some detailed information (or provide a link to it)



 I recently installed Elementary OS on my machine, next to Windows 7, so I  have a dual boot.
 Now, I'm not sure Elementary OS is the right distro for me so I would like to  replace Elementary Os with Xubuntu, but I want to keep Windows 7. I did not  create a single file in Elementary OS, so I don't need to keep a thing of  that.
 How can I achieve that?
 

 During installation, I have get the question *This computer currently has  multiple operating systems on it. What would you like to do?*
 
[LIST]
[*]**Install Xubuntu alongside them** (documents, music and other personal files  will be kept. You can choose which operating system you want each time the  computer starts up)
[*]**Erase disk and install Xubuntu** (Warning: This will delete all your programs,  documents, photos, music, and any other files in all operating systems.)
[*]**Something else** (you can create or resize partitions yourself, or choose  multiple partitions for Xubuntu)
[/LIST]
 I don't have a clue on what to choose, so Elementary is gone, xubuntu gets  installed and Windows 7 is kept untouched.

---

### Post by albandy on 2012-10-04
> **DoPiDo said:**
> I'm new to Linux, so you 'll probably have to provide some detailed information (or provide a link to it)



 I recently installed Elementary OS on my machine, next to Windows 7, so I  have a dual boot.
 Now, I'm not sure Elementary OS is the right distro for me so I would like to  replace Elementary Os with Xubuntu, but I want to keep Windows 7. I did not  create a single file in Elementary OS, so I don't need to keep a thing of  that.
 How can I achieve that?
 

 During installation, I have get the question *This computer currently has  multiple operating systems on it. What would you like to do?*
 
[LIST]
[*]**Install Xubuntu alongside them** (documents, music and other personal files  will be kept. You can choose which operating system you want each time the  computer starts up)
[*]**Erase disk and install Xubuntu** (Warning: This will delete all your programs,  documents, photos, music, and any other files in all operating systems.)
[*]**Something else** (you can create or resize partitions yourself, or choose  multiple partitions for Xubuntu)
[/LIST]
 I don't have a clue on what to choose, so Elementary is gone, xubuntu gets  installed and Windows 7 is kept untouched.

Select "something else" and when the partitions where showed, show us a screenshot of them (As you cannot make an screenshot during installation, if you can, make the screenshot with a camera or a mobile phone).

---

### Post by DoPiDo on 2012-10-04
> **albandy said:**
> Select "something else" and when the partitions where showed, show us a screenshot of them (As you cannot make an screenshot during installation, if you can, make the screenshot with a camera or a mobile phone).
ok, I'll do that.
You'll have to wait for 12 hours when I come home from work :-)

---

### Post by Wim Sturkenboom on 2012-10-04
And just in case, make backups. Fiddling with hard disks can go wrong !

---

### Post by mips on 2012-10-04
From Elementary OS open a terminal and type in,

```
sudo fdisk -l
```

Copy and paste the output here.

---

### Post by Mark Phelps on 2012-10-04
BEFORE you mess around with installing Ubuntu, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  You may need this later to restore the Win7 boot loader if anything happens to it during your Ubuntu install.

---

### Post by DoPiDo on 2012-10-04
sdo fdisk -l 

gives me this:


Schijf /dev/sda: 250.1 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x947dc3bb

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1698    13631488   27  [onbekend]
/dev/sda2            1698        2220     4194304    c  W95 FAT32 (LBA)
/dev/sda3   *        2220        2233      102400    7  HPFS/NTFS
/dev/sda4            2233       30402   226268161    f  W95 Uitgeb. (LBA)
/dev/sda5            2233       23141   167946343+   7  HPFS/NTFS
/dev/sda6           23141       30100    55894016   83  Linux
/dev/sda7           30100       30402     2425856   82  Linux wisselgeheugen



My system is in Dutch, and I can't find quickly where to chenge language...

---

### Post by Wim Sturkenboom on 2012-10-04
Your Elementary OS is on /dev/sda6

Choose the option 'something else', choose sda6 and 'change' or 'edit'. I'm not exactly sure about all the terms as this is 'uit het hoofd'. There might be a tickbox to format; if so, tick it. And choose '/' as the mount point.

Step 7C in [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/) shows it more or less. You should have sda6 there.
The next picture shows what I'm referring to; the size should be the correct size, only thing you MUST change is the type (to logical) if it's not already set. And make sure the mountpoint is '/'.

---

### Post by NikTh on 2012-10-04
> **Wim Sturkenboom said:**
> Your Elementary OS is on /dev/sda6
Correct ! 

> **Wim Sturkenboom said:**
> Choose the option 'something else', choose sda6 **and 'change' **or 'edit'. I'm not exactly sure about all the terms as this is 'uit het hoofd'. There might be a tickbox to format; if so, tick it. And choose '/' as the mount point.
"Change" is the correct option , and Yes OP should tick the box for formating , also mount in root / as you said and also select the "Ext4 journaling filesystem". 

Thanks

---

### Post by DoPiDo on 2012-10-04
ok ,thanks for your input. I'll give it a try in a few days and let you know how that worked out.

---

### Post by DoPiDo on 2012-10-05
as requested, I provide a screenshot of the "Something else"-screen.

---

### Post by mips on 2012-10-05
Install to /dev/sda6 ext4 format the partition and use ext4 again and when it comes to GRUB install to /dev/sda, it will pick up your windows partitions.

---

### Post by oldfred on 2012-10-05
Your screen shot also shows installing grub2's boot loader to the MBR of sdb. It should be set to install to sda if that is the drive with Ubuntu.

---

### Post by funicorn on 2012-10-05
Before u proceed, I should remind you that the ext4 partition is too big for the root partition. I suggest you divide it into / and /home.

---

### Post by Elfy on 2012-10-05
> **funicorn said:**
> Before u proceed, I should remind you that the ext4 partition is too big for the root partition. I suggest you divide it into / and /home.
That makes more sense to me now :)

---

### Post by albandy on 2012-10-06
> **DoPiDo said:**
> as requested, I provide a screenshot of the "Something else"-screen.

Ok, I replicated your partition structure on a virtual machine. See my video:

[http://youtu.be/1MmA1kGN5_I](http://youtu.be/1MmA1kGN5_I)

---

