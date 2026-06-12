---
title: "Help regarding file transfer from windows."
date: 2016-03-07
forum: New to Ubuntu
---

### Post by Seshal_Jain on 2016-03-07
Hello everybody, I am pretty much  noob when it comes to Linux commands. I am planning on shifting from Windows to Ubuntu shortly, and want to know how to move only my own files to Ubuntu, and not Thumbs.db and whatnot.
I have researched on the web, specially these forums and AskUbuntu, and simply want to know these things:
[LIST=1]
[*]How do I transfer only the files I need (not manually, all of them without the Windows system files, I accidentally unhid some of them.)
[*]How do I transfer (read: share) files between the two systems without any errors? I read about some packages which block some characters as filenames. Are they any good?
[/LIST]
Lastly, I appreciate any help. I've heard you are all very nice! ;)

---

### Post by mastablasta on 2016-03-07
> **Seshal_Jain said:**
> How do I transfer only the files I need (not manually, all of them without the Windows system files, I accidentally unhid some of them.)

How would the system know what files you need? it will transfer what you tell it to transfer.

> 
How do I transfer (read: share) files between the two systems without any errors? I read about some packages which block some characters as filenames. Are they any good?
Lastly, I appreciate any help. I've heard you are all very nice! ;)

Use NTFS partition. Linux can read NTFS, Windows can read NTFS. FAT32 is even more universal, but has it's limitations. you can have a data partition formatted as NTFS and use that to be accessed by both systems. assuming you will have a dualboot ?!

Linux file system make a difference between capital and small letters e.g. - "big.jpg" and "Big.jpg". for a windows file system this file is the same.

one thing to remember - windows can repair NTFS, Linux can not. Linux can repair Linux file systems.

Linux has many file system options including those that offer snapshots for backup purposes (BTRFS, ZFS).

---

### Post by grahammechanical on 2016-03-07
What files do you need to keep? And where are they stored? In a folder called Documents? Or Pictures? Or Videos. That sort of thing?

The Ubuntu file manager will let us copy folders and the copy action will include all the documents/files in that folder as well. We can select several files and copy & paste the whole lot of them at the same time. We can select several folders and copy & paste them all at the same time.

How easy it is to do this will depend upon how organised we are with our documents.

Regards

---

### Post by tom-bellas3rd on 2016-03-07
Imho, the easiest method is to copy the Documents, Pictures, Music and video folders to a USB disk (size permitting of course) and paste them to their respective folders in ubuntu.

---

### Post by SeijiSensei on 2016-03-07
By default, all your files are in C:\Users\username.  Just copy whatever you need from there to the USB device. Make sure the drive is formatted as FAT32 or NTFS, both of which Linux can read.

---

### Post by Seshal_Jain on 2016-03-07
Actually, while I am a newbie to Linux, I'm NOT a newbie to Windows. What I need to know is if there is a way to copy all my data from other drives than the Windows system drive (I only keep software in C:/ drive, all data is there in other partitions) When I view the drives from a liveCD, I see Thumbs.db and $RECYCLEBIN. So, I want to know of a method that will allow me to copy other data, but ignore all such files regardless of their visibility (hidden, not hidden). From what I see in answers written till now, people understood wrongly, all I want is to copy the data (NOT from the C:/../username, but from other partitions) to a preformatted hard disk temporarily and then paste it to Ubuntu, preferably without the system files, or to be able them delete them afterwards. Is there any direct method to do this, that is, without manually going to folders and deleting them? If not, a workaround or simply 'no' will do too.

---

### Post by SeijiSensei on 2016-03-07
Can't you just open Windows Explorer and drag-and-drop the directories you want to preserve onto the other drive?  Surely that is the easiest solution.

---

### Post by Geoffrey_Arndt on 2016-03-07
+1 for SeijiSensei's advice.    Linux *_DOESN'T care_* how your data got onto the external hard drive (or usb-flash-stick, or folder on Dropbox) . . . . use your "Windows" knowledge to do the copy/paste, and then you can use Linux to finish the transfer via selecting groups of directories to drag/drop or cut/paste.

By the way, . . . . _it is often better NOT to be a Windows expert or power user when switching to Linux_.   That knowledge set can OFTEN do more harm than good, as you may expect Linux to be managed and operated like Windows.

---

### Post by mastablasta on 2016-03-08
> **Seshal_Jain said:**
>  Is there any direct method to do this, that is, without manually going to folders and deleting them? If not, a workaround or simply 'no' will do too.

like I said system will copy what you tell it to copy. if you tell windows to copy everything but the files ending in .db or having a $ sign in them, than that is what they will do. you can set the parameters in more advanced file managers (e.g. free commander, total commander...), or use a CLI (console) for that - [https://technet.microsoft.com/en-us/library/bb490886.aspx](https://technet.microsoft.com/en-us/library/bb490886.aspx)

or with xcopy command: [https://technet.microsoft.com/en-us/library/cc771254.aspx](https://technet.microsoft.com/en-us/library/cc771254.aspx)
> [TABLE]
[TR]
[TD]/h
[/TD]
[TD]Copies files with hidden and system file attributes. [COLOR=#FF0000]By default, **xcopy** does not copy hidden or system files[/COLOR]
[/TD]
[/TR]
[/TABLE]


---

