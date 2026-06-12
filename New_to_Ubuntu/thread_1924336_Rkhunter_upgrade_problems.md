---
title: "Rkhunter upgrade problems"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by Tekkin on 2012-02-12
hi i been using ubuntu 10.04 for atleast a month right now and getting used to it, from windows to Ubuntu. but i have a problem with a particular program called rkhunter. i seen a pervious post on how to upgrade rkhunter from version 1.36 to 1.38 but when i download the tar.gz file and go in the terminal and try to runn it, it gives me a error messaging saying 

"No such file or directory"
tar: Error is not recoberable: exiting now
Tar: Child returned Status 2
Tar: Exiting now with failure status due to previous errors

:(

---

### Post by wolfen69 on 2012-02-12
All you really need to do is 
```
rkhunter --update 
```
to have the latest database. Or is there a feature in the latest version you *must* have?

---

### Post by Tekkin on 2012-02-14
yes sorry i need to upgrade rkhunter i wasnt sure if sudo rkhunter --update was the database or the manager.

---

