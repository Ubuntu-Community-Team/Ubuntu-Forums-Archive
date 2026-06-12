---
title: "I miss deleted files from NTFS,How can i recovery them ?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by jkll on 2008-10-21
> HI!.everyone:

I use Ubuntu 8.04 .

I miss deleted some files from NTFS drive (E) ,How can i recovery them ?


I cant find them in Trash Folder .

and i also cant find it in E:\$RECYCLE.BIN

the files were importent ,please help me ?

Thanks very much!




Thanks all my friends ,i workout now !

this what i do to recovery miss delete files

0.> df -h
Filesystem            Size  Used Avail Use% Mounted on
...
...
/dev/sda5             206M   59M  136M  31% /boot
/dev/sda7              19G   15G  3.5G  81% /home
/dev/sda1              31G   17G   15G  53% /home/hp/Windows/C
/dev/sda2              35G   26G  9.7G  73% /home/hp/Windows/D
/dev/sda3              28G  3.2G   25G  12% /home/hp/Windows/E [B]### where is my miss delete file's drive 
[/B]

1.> sudo apt-get install ntfsprogs

2.> umount /home/hp/Windows/E

3.> ntfsundelete /dev/sda3 -t 5d
Error: Volume name could not be converted to current locale: Invalid or incomplete multibyte or wide character.
Inode    Flags  %age  Date           Size  Filename
---------------------------------------------------------------
10869    FR..   100%  2008-10-22        24  <none>
10870    D...     0%  2008-10-22         0  <none>
10900    FN..   100%  2008-10-19     35534  <none>
10901    FN..   100%  2008-10-19   4253501  <none>
12866    D...     0%  2008-10-19         0  <none>
12872    D...     0%  2008-10-19         0  <none>
12880    FN..   100%  2008-10-19     27612  <none>
12881    FR..   100%  2008-10-19        78  <none>

Files with potentially recoverable content: 5


4.> ntfsundelete /dev/sda3 -u -i 10901 -d /home/hp/cd
Error: Volume name could not be converted to current locale: Invalid or incomplete multibyte or wide character.
Inode    Flags  %age  Date            Size  Filename
---------------------------------------------------------------
10900    FN..     0%  2008-10-19     35534  <none>

Undeleted '(null)' successfully.

---

### Post by bsharp on 2008-10-21
Since you referred to your other drive as "E", I'm assuming you're dual-booting windows. If that's the case, there is a program from the makers of CCleaner called Recuva ([http://www.recuva.com/](http://www.recuva.com/)) that restores deleted files.

---

### Post by jkll on 2008-10-22
Thanks,i have used Recuva to find miss deleted files .but no one were find,

is ubuntu delete files diffrent with windows?

any other Method &#65311;:confused:](*,)

---

### Post by taseedorf on 2008-10-22
in ubuntu, if you deleted them they should go to the recycle bin.  
can you get into that?

if not in there, they may only be fragments left...
get a recovery suite for linux, by searching synaptic

---

### Post by Nepherte on 2008-10-22
Go to you E:\ drive in Ubuntu (the file navigator in Ubuntu is called nautilus). Press ctrl+h to show hidden files and directories. There's most likely a map ".Trash-1000" with another subdirectory "Files" where deleted files are located in. You will only find them there if you deleted those files in Ubuntu and you haven't removed them from the trash yet.

---

