---
title: "Soon to install ubuntu on my comp."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Aalnius on 2008-06-22
Right i run fedora 6(old i know thats why i'm going to ubuntu)
I was just wondering is there anyway i can install ubuntu without deleting my old files or at least protecting like 5gb of them as i can't back them up at the moment and theres only 5gb of stuff that i really want to keep hold of.
It says if your very careful you can install ubuntu without erasing all existing software so i was just wondering if i could keep hold of my files and how.
its only 5gb and i have 120gb hardrive.
I am an average comp user i use comps alot but i only know about windows and fedora really i have no knowledge about partitions or anything like that.:confused::confused:

---

### Post by TeoBigusGeekus on 2008-06-22
Why don't you use fedora's partition editor to create a new partition where you could save all your data?
Alternatively, boot up with Ubuntu's CD/DVD, go to System->Administration->Partition Editor and create a new backup partition from there.
Afterwards, when you install Ubuntu (don't forget: create a separate /home partition - I guess you know that already), leave your backup partition untouched.

Welcome to Ubuntu!!!:)

---

### Post by Zenze on 2008-06-22
Well when you install ubuntu when you get to the partition editor I would just use the default option and make the partition with those files on it as small as you can and have ubuntu take up the rest. Then once its installed you could just copy all the files to the ubuntu partition then delete your old parition and resize the ubuntu one to take up the extra space. That should work fine.

However if the files are so importation I would just back them up on dvds or something anyway.

---

### Post by KenBW2 on 2008-06-22
That's easy!
Boot up the Ubuntu LiveCD, install "gparted" and shrink the Fedora partition. to make room for Ubuntu. Partition out an ext3 partition for Ubuntu and install to that partition.

Ask if you need help

---

