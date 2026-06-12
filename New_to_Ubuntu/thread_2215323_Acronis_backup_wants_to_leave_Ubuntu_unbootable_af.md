---
title: "Acronis backup wants to leave Ubuntu unbootable after disc clone"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by Don_Shipp on 2014-04-06
The last couple of weekends I've been setting up Ubuntu on my old Win XP Pro laptop (we all know why).  I've made it dual boot with half my 150 MB hard drive Windows (NTFS) and half Linux.  Now I want to clone the disc to an external drive using Acronis, which is Windows based, but I get a message saying after the clone operation my Linux partition will be unbootable.  This happens whether I run Acronis from Windows or the bootable recovery CD.  Questions:

1. After the drive is cloned, can I make my Linux bootable again by running the "Recover" selection in the boot menu?  This will be a bother but I can live with it because I don't use the laptop much and do the clone disc operation only every month.

2. Is there another backup application that will clone my disc without making either partition unbootable?  For example, EaseUS ToDo Backup seems to be popular, but will it work well?  I'm not unwilling to use another program, but I'm comfortable with the Acronis application.

Acronis says I can use a short series of terminal commands to make the Linux partition bootable again, but it's been a ***LONG*** time since MS-DOS and this geezer is not extremely comfortable with the CLI.  I'm still on the steep part of the learning curve.

There must be a cleaner way.  Suggestions, anyone?

Don
Hoover, Alabama

---

### Post by monkeybrain20122 on 2014-04-06
Instead of using Windows tools like Acronis use something Linux native, my favourite is fsarchiver. You can use it to clone the Linux partition, you can use it in a live cd or in your Ubuntu partition (live cloning) using the options -a and -A with savefs. It is very flexible in that you can clone individual partitions instead of the whole disk. It says it support ntfs as well but I never use it with ntfs since I don't use Windows. You can use whatever Windows tool for the Windows partition.
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

There is a gui version called qt4-fsarchiver, which is not as flexible as the cli but very easy to use (cannot exclude directories, for example)
[http://sourceforge.net/projects/qt4-fsarchiver/](http://sourceforge.net/projects/qt4-fsarchiver/)
[http://www.youtube.com/watch?v=oSKjGbLbflU](http://www.youtube.com/watch?v=oSKjGbLbflU)

---

### Post by Don_Shipp on 2014-04-06
Thanks.  That will be my Sunday afternoon project.  I want to do a complete disc clone, Windows and Ubuntu, because there are some programs I run in XP that have no equal in Linux, which is why I want to back up the whole disc.

---

### Post by Don_Shipp on 2014-04-06
I downloaded and extracted the qt4-fsarchiver but it only flashes a blank window when I click on the executable.  Do I need to download WINE for this?

---

### Post by Mark Phelps on 2014-04-06
You could also try using Clonezilla (which I use to backup Linux filesystems) or RedoBackup -- which is a GUI-based Linux filesystem backup tool.

---

### Post by Don_Shipp on 2014-04-06
Mark - Will these do a disc clone of both Linux and NTFS partitions without leaving one unbootable - or any other problems?  Cloning a disc is handy when the one in the computer quits and installing the cloned disc gets me running in ten minutes or less.

---

### Post by monkeybrain20122 on 2014-04-06
> **Don_Shipp said:**
> I downloaded and extracted the qt4-fsarchiver but it only flashes a blank window when I click on the executable.  Do I need to download WINE for this?

You should enter your password in the blank window.

I prefer fsarchiver to clonezilla because it doesn't clone empty space. clonzilla requires the target disk to be at least as big as the source. This is a show stopper for me as I move installations around, and for backup I don't need to clone all partitions (e.g I don't need to clone /home as often as I do / because I backup data with other tools)

---

### Post by Mark Phelps on 2014-04-06
> Mark - Will these do a disc clone of both Linux and NTFS partitions without leaving one unbootable - or any other problems? 

Clonezilla will, but regarding RedoBackup, don't know -- don't actually use it.  But, you can check at the RedoBackup website: [http://redobackup.org/]("http://redobackup.org/")

---

### Post by MartyBuntu on 2014-04-06
You keep using the word "clone". I'm not sure that's what you want.
If it's just simple drive backup, with the ability to restore entire drives, partitions or even individual files, your Acronis bootable disk can do that already.

"Cloning" would be a more suitable operation for migrating from one disk to another.

---

