---
title: "scripting help"
date: 2016-05-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-05-24
using 16.04.  backup just appears in my home folder not home/homebackup folder. what do i need to change./tks


#!/bin/bash

#-- enter your folders here!
backupfolder="/home/homebackup"
sourcefolder="/home"

cd "$backupfolder"
a=`date +%m-%d-%Y--%H-%M`
tar -czvf homebackup-$a.tgz --exclude=/home/homebackup/$a.tgz/home "$sourcefolder"
echo
echo "-------------------finished backup!-------------------"
echo "--hit ENTER to exit --"
read a
exit 0

---

### Post by howefield on 2016-05-24
backupfolder="/home/*user*/homebackup" ?

likewise for the exclusion.

---

### Post by rburkartjo on 2016-05-24
tks how but didnt work

---

### Post by howefield on 2016-05-24
> **rburkartjo said:**
> tks how but didnt work

Hmm, sorry to hear that.

I tested before posting, it worked for me on a live session using the path /home/ubuntu/homebackup

Sorry to mention the obvious, but you did substitute *user* with the real user name ?

---

### Post by rburkartjo on 2016-05-24
yes i did

---

### Post by rburkartjo on 2016-05-24
got it to work had a spelling mistake on my homebackup folder.

---

### Post by howefield on 2016-05-24
> **rburkartjo said:**
> got it to work had a spelling mistake on my homebackup folder.

Cool, you might want to check your exclusion line, assuming you don't want it to back up the backup folder :)

---

### Post by rburkartjo on 2016-05-24
i did that

---

