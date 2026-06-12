---
title: "backup help"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-02-15
i made an ubuntu backup file backup-2013-02-15.tar.bz it is on a terabite external drive /media/ray/My Passport. what would be the command to reinstall it if i need to. i would just plug the external drive in open it and then type what from the terminal. tks

---

### Post by acrazyplayer on 2013-02-15
Did you use anything special to make the back up? e.g. deja dup

if not then what did you do to make the back up in the first place?

---

### Post by rburkartjo on 2013-02-15
here is the backup script i ran
  
#!/bin/bash
mkdir ~/backup && cd ~/backup
tar cvpjf backup-$(date '+%F').tar.bz2  --exclude=/proc4 --exclude=/mnt --exclude=/sys / --exclude=/lost+found --exclude=/tmp –exclude=/backup.tar.bz2
sleep 9999

and a good idea to have the backup on an external device. what to make sure i have the right command to restore if need to.

---

### Post by acrazyplayer on 2013-02-15
take a look at the restoring part in...

[http://en.kioskea.net/faq/15206-restoring-ubuntu-with-tar]("http://en.kioskea.net/faq/15206-restoring-ubuntu-with-tar")

---

### Post by lmarmisa on 2013-02-15
Type this command if you want to list the files stored in backup:

```

tar tvjf backup-2013-02-15.tar.bz

```

---

### Post by lmarmisa on 2013-02-15
An additional comment. 

I have doubts about the reliability of your backup. Your system should be stopped if you wish a reliable full backup.

So, if you need to restore data from your backup, you could get corrupted data for some applications.

Consider to use clonezilla live for a reliable full backup:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

