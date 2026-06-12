---
title: "Reinstalling after hard dish won't boot"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by mmcl26554 on 2013-03-30
I did a procedure called "Disk alignment" after reading about it it seemed like the thing to do.  I have a Windows program called "MiniTool Partition Wizard" that would do it.   Well, in the end the hard drive became unbootable for both Windows7 and Ubuntu.  I do have a disk which is supposed to repair the MBR and make it boot again.  And, it had worked previously when after a Ubuntu update both failed to boot.   But, this time everything I tried didn't work.   Even using the Windows repair/reinstall disks only wanted to reinstall.   So I conveniently had another 750Gb dirive so I decided to just reinstall.   I can access the old disk data files, everything is there so I have done the reinstall of Windows7 64 bit and transferred my data.   Fortunately I have a network drive where I store a lot of data and program install files so I have everything back except Ubuntu.   Oh, by the way, I did have a recent backup file made by Acronis but it failed, said after an hour and a half the file was corrupt.  I even had an older backup but same story.  Strange because during the making of the backup files I do verify, so I know they were good once.   So I don't know about Acronis it works ok to clone a disk but backup files are unreliable.


Now to my question, I don't have much data in Ubuntu as I am just learning it and playing with it.   I was wondering, since I do have the original Ubuntu folder in the old windows, can I reinstall Ubuntu with the dual boot and then copy the file from the old hard drive and have back the programs I installed and settings.   I don't think it could ever be that easy but who knows, I certainly don't.   It's no big deal if I can't do this and besides it would turn out to be a learning experience to restore the programs, files and settings.

Michael

---

### Post by kc1di on 2013-03-30
though in theory what you propose may work, in reality I think you'd be better off re-installing a Ubuntu and re-install the programs you want. Then you can recover any documents, pictures ,etc from the old disk.  I always use a separate home folder when I partition by the way as it's much easier to recover from a major problem if it's kept separate. Good Luck.

you can do that by selecting other during the partitioning page.

---

### Post by mmcl26554 on 2013-05-04
Would it work if after reinstalling Ubuntu I copied the old "Home folder" to the new installation?
Michael

---

### Post by BluNova on 2013-05-04
Yes it should

---

### Post by oldfred on 2013-05-04
Copying /home will include all your data & user settings from the old install. You may want to backup new /home just incase some setting from that is what you want.
But it will not the programs just the program configuration files.

You have to use dpkg to export a list of installed apps from old install to reinstall to new install. I include making a new copy of that list in my rsync script.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages

You may be able to repair old install?

---

### Post by mmcl26554 on 2013-05-04
oldfred,
What I have is an Acronis backup of the whole Windows 7 install.  Including the Ubuntu folder.  I was wondering if I could install Ubuntu with "wubi" then copy the Ubuntu folder over the one just installed.  I have read where some say they install Ubuntu into it's own partition and "Home" into it's own partition.  This is supposed to make any future recovery easier, but if I can do what I want that would be easy also.  If you haven't read my first post please do so and you will understand  what happened,  
Michael

---

### Post by oldfred on 2013-05-04
I do not know wubi well. But as I understand you can just reinstall wubi and then copy your backup in place of the new root.disk and it should work. You just cannot copy root.disk into Windows.

But wubi is totally different on how it installs than a full partitioned install.

---

### Post by mmcl26554 on 2013-05-06
Since Acronis can backup and restore Linux based drives I believe restoring
the Ubuntu folder in its entirety from the Windows full backup (including
Ubuntu folder) is possible. I don't think Ubuntu is no place else in
Windows except the Ubuntu folder. The only concern I have is the version of
Ubuntu installed is a little newer than one that is in the backup. The one
installed is 12.04LTS and the one that is on the backup is 12.01 (I think,
but not 12.04LTS).  I'm certain if I use the backup Ubuntu  folder I can
always update it after.  In any case I'll make a backup of the hard drive
so if disaster strikes I'm prepared.    On the other hand, since I am an
"absolute beginner", the experience of installing the programs I use is
good experience.   One thing I noticed right away during the install is the
display.   When I first installed Ubuntu I always had to hit the brightness
key in order to see anything on the screen.    With assistance from this
forum I entered a command which fixed this.   Now that is not necessary.
 So I haven't decided which way to go but I am leaning toward keeping what
I have and installing the programs again

---

### Post by mmcl26554 on 2013-05-08
Well, I went with the new install as a learning experience.  I'm glad I did as I discovered how to share the same, bookmarks, password and other data files between the 2 versions of Opera, windows and Ubuntu.  The same is true for Keepass, which is one of my "Must Have" programs, I can share the same data files.   
Michael

---

