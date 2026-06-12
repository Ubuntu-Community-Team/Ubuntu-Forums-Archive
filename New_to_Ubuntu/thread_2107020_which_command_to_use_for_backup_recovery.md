---
title: "which command to use for backup recovery"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-01-20
this one
tar xvpfj backup.tar.bz2 -C /
or this tar xvpfj ~/backup/backup.tar.bz2 -C /

or doesn't it make an difference
note the backup.tar.bz2 is in the home folder if that makes a difference. i run this scipt for a backup

#!/bin/bash
mkdir ~/backup && cd ~/backup
tar cvpjf backup-$(date '+%F').tar.bz2  --exclude=/proc4 --exclude=/mnt --exclude=/sys / --exclude=/lost+found --exclude=/tmp –exclude=/backup.tar.bz2
sleep 9999

---

### Post by rburkartjo on 2013-01-26
bump

---

### Post by rburkartjo on 2013-02-05
one last bump

---

### Post by Cheesemill on 2013-02-05
The first command will only work if it is run while you are already in the ~/backup directory, the second will work from anywhere as long as you are logged in as the correct user as you are specifying the absolute path to the archive file.

The outcome of both commands would be identical.

---

### Post by rburkartjo on 2013-02-06
tks cheese!

---

