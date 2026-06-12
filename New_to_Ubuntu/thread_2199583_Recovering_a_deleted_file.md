---
title: "Recovering a deleted file"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by courseinmiracles2 on 2014-01-14
Ok, I am running ubuntu 13.10 and I have deleted a file. I have been trying for days now to find a simple way to recover it and maybe I am truly out of luck.

I have tried scalpel and foremost and ext4..something or other, with all of these I got partly way through then hit a snag, like unmount the partition, which I don't have access to, and do I unmount my /root or my /home and how would I unmount my /root isn't the operating system on it?  

I have used gparted to "attempt data rescue" and that scanned for over an hour and then came came up empty.

Is there really no hope of recovering this file?

Any suggestions greatly appreciated.

---

### Post by nothingspecial on 2014-01-14
I would try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec")

To recover files from a unmounted root partition you would have to run the recovery software from a live cd/usb etc

---

### Post by courseinmiracles2 on 2014-01-14
sudo  extundelete --restore-file tux/home/tony/Desktop/BV-rents.ods /dev/sda6                                                                         
[sudo] password for tony: 
WARNING: Extended attributes are not restored.
WARNING: EXT3_FEATURE_INCOMPAT_RECOVER is set.
The partition should be unmounted to undelete any files without further data loss.
If the partition is not currently mounted, this message indicates 
it was improperly unmounted, and you should run fsck before continuing.
If you decide to continue, extundelete may overwrite some of the deleted
files and make recovering those files impossible.  You should unmount the
file system and check it with fsck before using extundelete.
Would you like to continue? (y/n)

---

### Post by Bashing-om on 2014-01-14
courseinmiracles2; Hi !

Here is the why recovery of files is so "difficult":
[http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0)
And a few suggestions on how one might be able to recover a file.

Not much help, but knowing why
[INDENT][INDENT]may make one feel better
[/INDENT][/INDENT]

---

### Post by courseinmiracles2 on 2014-01-14
Hey Guys thanks for the responses but still no luck.

Maybe it has been written over.

I did use R-Linux to create an image of my /root dir but when I use it to recover the files it crashes 5 minutes into the process, i've done it twice.

My wife finally has some ammo when talking about windows verse linux. What a bummer.

---

### Post by dennis13 on 2014-01-14
As long as the ammo ain't the "Recycle bin" from Windows. Well, Linux has that, too. There's not much of a difference between Linux and Windows in that regard. Delete a file with the file manager, it goes to the "trash" or "recycle" bin. Delete a file on the terminal (rm on Linux or del in Windows) it's usually gone forever).

Dennis

---

### Post by mastablasta on 2014-01-15
del used to have undelete counterpart. i dont' know if they still have it. there were also programes that could restore the files but you needed to know the first leter of the file.

---

### Post by Impavidus on 2014-01-15
Linux assumes you know what you want. If you order the system to delete a file, it will be deleted.

(It should be possible to build an automatically emptying trash can. It can collect files indefinitely, but when disk space gets tight it can automatically permanently delete the oldest files.)

---

### Post by dennis13 on 2014-01-15
> **mastablasta said:**
> del used to have undelete counterpart. i dont' know if they still have it. there were also programes that could restore the files but you needed to know the first leter of the file.

Yes, I remember that from the Windows 3.x times. The command was undelete and you had to enter the first letter of each file you wanted to resurrect. This stems from the fact that on FAT file systems deleted files are marked by a special byte as the first letter of the file name.

I never tried if there was an undelete for NTFS.

Dennis

---

### Post by buzzingrobot on 2014-01-15
"Trash" and "Recycle Bin' are simply directories where so-called deleted files are moved. Nothing magical happening there on either OS. 

It's easy to alias the rm command to move files to Trash, or somewhere else, rather than delete them.

Backups, though, eliminate these kind of headaches.  Ahem. :)

---

### Post by mastablasta on 2014-01-16
it seems they have it for ntfs. 3rd party though: [http://ntfsundelete.com/](http://ntfsundelete.com/)

the also have a free one: [http://www.majorgeeks.com/files/details/freeundelete.html](http://www.majorgeeks.com/files/details/freeundelete.html)

otherwise i would use windows recovery tools to recover files in windows.: [http://pcsupport.about.com/od/filerecovery/tp/free-file-recovery-programs.htm](http://pcsupport.about.com/od/filerecovery/tp/free-file-recovery-programs.htm)

---

### Post by whitesmith on 2014-01-16
> **courseinmiracles2 said:**
> Ok, I am running ubuntu 13.10 and I have deleted a file. I have been trying for days now to find a simple way to recover it and maybe I am truly out of luck. . . . 
Is there really no hope of recovering this file? . . .

Here is a direct quotation from* The Linux Command Line* ([http://www.linuxcommand.org/tlcl.php](http://www.linuxcommand.org/tlcl.php)), a free pdf I recommend to all transitioning from Windows:
"Be Careful With rm!
Unix-like operating systems such as Linux do not have an undelete command.
Once you delete something with rm, it's gone. Linux assumes you're smart and
you know what you're doing.
Be particularly careful with wildcards. Consider this classic example. Let's say
you want to delete just the HTML files in a directory. To do this, you type:
rm *.html which is correct, but if you accidentally place a space between the “*” and the
“.html” like so:
rm * .html
the rm command will delete all the files in the directory and then complain that
there is no file called “.html”.
Here is a useful tip. Whenever you use wildcards with rm (besides carefully
checking your typing!), test the wildcard first with ls. This will let you see the
files that will be deleted. Then press the up arrow key to recall the command and
replace the ls with rm."

---

