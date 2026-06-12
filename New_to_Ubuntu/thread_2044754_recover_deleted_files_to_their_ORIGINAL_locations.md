---
title: "recover deleted files to their ORIGINAL locations"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by Castiel on 2012-08-19
Hello all!
I was using both windows 7 and ubuntu with dual boot. One faulty driver setup in win 7 has deleted hundreds of my files in C: drive. Now windows won't boot and I don't want to touch the C: drive because I won't be able to recover my deleted files if they were overwritten.

My question is I am looking for a deleted file recovery software to use in Ubuntu to restore my files in C: drive, where windows resides. Problem is, all data recovery programs I found that works in Ubuntu recovers selected files and copies them elsewhere. But my deleted data is around 30 gb and deleted files are all in different folders. I am looking for a software that can find deleted files, and puts all of them to their ORIGINAL folder/location. Such software exits for windows but I can't find an equivalent for Ubuntu. And installing windows again may overwrite my deleted files, causing them to be lost permanently.

Thanks in advance!

---

### Post by Vaphell on 2012-08-19
>  I am looking for a software that can find deleted files, and puts all of them to their ORIGINAL folder/location. 

chances are slim because it is very filesystem specific behavior - native linux filesystems irreversibly destroy file descriptors during deletion leaving no info about the file, while NTFS leaves pretty much all file info around, but marks the file entry and the disk space unused. Unmark them - magic happens! ;-)
It's not hard to imagine that linux software tailored mainly for linux filesystems can't be bothered to do that.

i'd plug the hdd into some other windows box and then i'd try recovery with one of these windows recovery programs. Even if there was a linux tool that can do that i'd prefer windows solution either way. This stuff is too low level and hardcore to goof around with, i'd trust that the level of expertise is much higher in windows shops who live and die by the reliability of their specialized products.

---

### Post by asmoore82 on 2012-08-20
There are different classes of software: "undelete" tools and "data carving" tools. Data carving doesn't bother with folder structure but it is the far more powerful and more reliable option. Remember that the folder structure is virtually meaningless at the hardware level. Folders are just lists of Files and Folders; not actual containers. So when you "recover" a folder all you get is a list of file names while the actual data is still in jeopardy.

A very important file could be 10 layers deep in the folder structure, so to successfully "undelete" it you'd have to be lucky enough for all of that folder data to be uncorrupted. But with "data carving" you jump straight to finding the real file.

---

### Post by Mark Phelps on 2012-08-20
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

