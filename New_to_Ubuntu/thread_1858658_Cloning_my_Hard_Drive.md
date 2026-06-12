---
title: "Cloning my Hard Drive"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by sillyboy on 2011-10-12
Is there software that can clone my HD? Like Drive (C) to Drive (new) 
Like Migrate Easy or Ghost.

Looking to put a larger HD in.

Thanks

---

### Post by westie457 on 2011-10-12
Hi a lot of people on the Forum recommend 'Clonezilla' and/or 'Macrium Reflect'. There are probably others as well. Those are the two I have seen mentioned the most.

Having said that I used dd to copy one smaller to one larger with no issues at all.

---

### Post by The Sorrow on 2011-10-12
We use Clonezilla at work and its just as good as Ghost.

---

### Post by sillyboy on 2011-10-12
> **westie457 said:**
> Hi a lot of people on the Forum recommend 'Clonezilla' and/or 'Macrium Reflect'. There are probably others as well. Those are the two I have seen mentioned the most.

Having said that I used dd to copy one smaller to one larger with no issues at all.

Thank You

---

### Post by wildmanne39 on 2011-10-12
+1 for clonezilla.

---

### Post by sillyboy on 2011-10-15
> **westie457 said:**
> Hi a lot of people on the Forum recommend 'Clonezilla' and/or 'Macrium Reflect'. There are probably others as well. Those are the two I have seen mentioned the most.

Having said that I used dd to copy one smaller to one larger with no issues at all.

What is dd?

Thanks

---

### Post by westie457 on 2011-10-15
At its simplest 'dd' is a file copy tool. However one thing to remember is in Linux 'everything is a file' that includes partitions and hard drives.

An example of 'dd' is ```
dd if=/dev/sda of=/dev/sdc
``` where (if means input file) SDA is the drive you want to copy and (of is the output file) SDC is the one you want to write to. Always check and double-check or even get OCD on checking that things are correct before pressing the Enter key. One small mistake can and will wipe all information off the wrong drive.

'dd' does not care if the receiving drive has partitions or not as it takes the input from SDA starting with the MBR and copies everything to SDC until SDA has been read completely.

Probably the most dangerous form of 'dd' to use is ```
dd if=0 of=/dev/SDx
``` whcih will fill a hard drive with zeroes making all info virtually unrecoverable.

Use the 'dd' command with caution. 

Hope this helps.

---

### Post by beew on 2011-10-15
What if you want to clone to a smaller hd? (ie just image the partitions with data instead of everything)

---

### Post by westie457 on 2011-10-15
> **beew said:**
> What if you want to clone to a smaller hd? (ie just image the partitions with data instead of everything)

TBH have never tried that type of cloning. Though in that scenario if I could not find something to do that automagically I would shrink the partitions to sizes that would fit the smaller drive.

---

### Post by beew on 2011-10-15
> **westie457 said:**
> TBH have never tried that type of cloning. Though in that scenario if I could not find something to do that automagically I would shrink the partitions to sizes that would fit the smaller drive.

But I don't want to change the existing partition scheme. I just want to clone the disk in such a way that it skips the unused space. I think PartImage does that but since it does not support ext4 that rules it out for any system installed after 2009 or something like that.

---

### Post by mattubu16 on 2011-10-16
I had this issue when I switched to an SSD. I ended up booting a LiveCD (I used [Parted Magic]("http://partedmagic.com/doku.php")  - much faster than an Ubuntu LiveCD), running GParted, and using its  copy-paste tool to copy partitions. I didn't actually move my Ubuntu  partition because I was clean-installing Natty (I only copied my windows  partition), so you might have some GRUB issues, but this should be a  fairly straightforward and reliable method.

---

### Post by Gs Dewd on 2011-10-16
Clonezilla is great for this. Also i think there should be a sticky for Hd cloning and coping with the different ways people have done it and how they got over certain hurdles. Like cloning to a smaller driver or cloning to a larger drive and expanding the partition to use the whole drive.

---

### Post by BigSilly on 2011-10-20
> **Gs Dewd said:**
> Clonezilla is great for this. Also i think there should be a sticky for Hd cloning and coping with the different ways people have done it and how they got over certain hurdles. Like cloning to a smaller driver or cloning to a larger drive and expanding the partition to use the whole drive.

+1 for this. I would love to read user guides and experiences of cloning, especially using Clonezilla. 

I've only used the program twice and had beforehand never used cloning before. One attempt was a brilliant success, the second was a total failure. I had tried to reinstate an openSUSE install from a snapshot taken about a week ago, but on restoring it Clonezilla failed to restore the GRUB menu. I got GRUB error 6, and I could not find a way to fix it. Any commands or tools I used such as Rescatux etc just would not work.

So a sticky guide would be a fantastic idea, and would certainly have helped me. It would allow those somewhat greener users among us a bit of help with cloning and backup.

---

