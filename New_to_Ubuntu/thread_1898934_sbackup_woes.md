---
title: "sbackup woes"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by tophatandy on 2011-12-22
Hello! I haven't been on these forums in ages, and it is good to be back (if only it was under better circumstances). So I am running into some trouble with my netbook running 10.04 (I know, I really need to upgrade). I was actually about to upgrade, but decided to back everything up first. After hunting around I found sbackup for backing up my files in ubuntu.

After following a guide on the Ubuntu wiki, I eventually started to back up all of the files from my netbook onto an external harddrive attached to another computer (this was supposed to be done via ssh). Somewhere in the process sbackup decided to not back up my files and instead fill up my hard disk on my netbook. 

tl;dr

Sbackup filled up my hard disk with a temporary backup (I think), and I need help finding it so I can delete it. Also, any recommendations for a real backup program that can back up onto a drive on the network?

---

### Post by tophatandy on 2011-12-22
Still no breakthrough here. I tried copying just my home folder to the mounted network folder (it is mounted via samba), with the only result being that the copy would fail after the connection timed out. 


Anyone have any suggestions?

---

### Post by Temposs on 2011-12-23
Ubuntu now comes with a backup program called Deja-Dup by default in Ubuntu 11.10(the latest). But this backup program also works with older versions of Ubuntu. 

So if you do upgrade you'll have it installed by default. Until then, you can install it from here: [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

---

### Post by Ghost_Mazal on 2011-12-23
Look into rsync. By far the easiest and most reliable for me.

You can even look into grsync if you prefer a gui tool.

---

### Post by tophatandy on 2011-12-23
Thanks!

I still need help deleting whatever sbackup did to fill up my HD. Any tips?

---

### Post by Zill on 2011-12-23
tophatandy:  The *default* SBackup archive destination is /var/backup/ so I would look there first.

See [Simple Backup Suite (sbackup)]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") for more info.

You can also look for the line beginning "target = ..." in the SBackup configuration file to see what directory is defined there.
```
cat /etc/sbackup.conf
```

---

