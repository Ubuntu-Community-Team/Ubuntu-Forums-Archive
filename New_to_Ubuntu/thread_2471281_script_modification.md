---
title: "script modification"
date: 2022-01-25
forum: New to Ubuntu
---

### Post by rburkartjo on 2022-01-25
running 21.10

the below is a crontab script that runs daily. it backs uo my crontab jobs. 


#!/bin/bash
crontab -l > $HOME/crontabBackup-`date +"%d-%m-%Y"`


how to i modify so that when it runs it deletes the previous days backup

tks

---

### Post by vanadium on 2022-01-25
You could prepend a command that deletes existing $HOME/crontabBackup-* files before creating the one of today.

---

### Post by ActionParsnip on 2022-01-25
Is there only crontab backups in $HOME/crontabBackup folder please? Why not keep a few days worth of backups? Could be handy and costs very little

---

### Post by rburkartjo on 2022-01-26
tks

---

