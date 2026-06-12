---
title: "Beginners??"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by Sully_3118 on 2011-10-22
Hello,
I am brand new to this Linux stuff, (hope that didn't offend anyone) and was wondering if there is a place for beginners to go to learn commands for the terminal and how to install/remove applications from it. I just installed the Ubuntu 11.10 version and am already having issues with the wireless setup via ndiswrapper and similar troubleshooting forums. Thanks to all of you that are smart enough to understand this programming stuff, and any and all help is appreciated. I really am looking forward to learning a little bit, hopefully a lot, about linux OS. 

Sully

---

### Post by sisco311 on 2011-10-22
Welcome to the forums!

Thread moved to the **Absolute Beginner Talk** forum.

---

### Post by dFlyer on 2011-10-22
Lets start you out with bash: open a terminal and enter:

man bash  (press enter)

This will introduce you to the terminal shell and some of the command language with it.

Some of the more simple command are:

mv (move)
cp (copy)
ls -ahl (list files in a directory)
rm (deletes files) be very careful using this command as it's possible to remove files you may not want to remove.
sudo (superuser)
apt-get update (update archive) Must use sudo
apt-get upgrade (upgrades OS) Must use sudo
dpkg (install deb packages)


Just use man and then the command for a full listing of the options.

---

### Post by Frogs Hair on 2011-10-22
Cheat Sheet : [http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

---

### Post by Sully_3118 on 2011-10-22
Thanks everyone for the quick responses. I am already checking out the advice. I'm sure I will find myself in need of your expertise soon again. Until then......

Sully

---

### Post by mörgæs on 2011-10-22
[http://ubuntu-manual.org/](http://ubuntu-manual.org/) 
Written for 10.10, but most applies to the new releases as well.

Please mark the thread 'solved', if you have enough for now.

---

### Post by KingYaba on 2011-10-22
Allow me to throw in another tutorial. Google has three on this website: [http://code.google.com/edu/introductory_courses.html](http://code.google.com/edu/introductory_courses.html) and they cover terminal basics in the first lesson. Click on **Basic Linux Commands** and enjoy. :)

---

### Post by fractalman on 2011-10-23
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Good guide for getting started with bash.

or check this thread for some other programming guides, i found them quite handy

[http://ubuntuforums.org/showthread.php?t=1836517](http://ubuntuforums.org/showthread.php?t=1836517)

---

### Post by Ctrl-Alt-F1 on 2011-10-23
apropos is a good command to learn which commands do what.  It gives you a list of commands related to your "search term" and a short description.  You can then use the man page to learn more about any command.

for example:

```
apropos find
```

Gives the following results:

```
chkdupexe (1)        - find duplicate executables
ffs (3)              - find first bit set in a word
ffsl (3)             - find first bit set in a word
ffsll (3)            - find first bit set in a word
File::MimeInfo::Applications (3pm) - Find programs to open a file by mimetype
find (1)             - search for files in a directory hierarchy
find2perl (1)        - translate find command lines to Perl code
findfs (8)           - Find a filesystem by label or UUID
findmnt (8)          - find a filesystem
findsmb (1)          - list info about machines that respond to SMB name quer...
glob (3)             - find pathnames matching a pattern, free memory from gl...
globfree (3)         - find pathnames matching a pattern, free memory from gl...
gst-typefind-0.10 (1) - print MIME type of file
lfind (3)            - linear search of an array
locate (1)           - find files by name
memdiskfind (1)      - utility to search for a MEMDISK instance
mlocate (1)          - find files by name
mysql_find_rows (1)  - extract SQL statements from files
oldfind (1)          - search for files in a directory hierarchy
pidof (8)            - find the process ID of a running program.
sane-find-scanner (1) - find SCSI and USB scanners and their device files
tfind (3)            - manage a binary tree
tt***** (3)          - find the slot of the current user's terminal in some file
```

---

### Post by oldos2er on 2011-10-23
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

