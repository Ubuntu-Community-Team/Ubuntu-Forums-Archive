---
title: "Update Manager not prompting 10.04 to 12.04 update"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by paker on 2012-05-15
I am on 10.04 LTS. Shouldn't Update Manager prompt 10.04 LTS to 12.04 LTS update? It's not. 
Thanks.

---

### Post by Curtis6767 on 2012-05-15
Scroll down to the part where it talks about upgrading from 10.04LTS to 12.04LTS

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

GL

---

### Post by josephmills on 2012-05-15
please open you terminal and enter in 
```
sudo apt-get install update-manager-core
```
then 
```
gksudo gedit /etc/update-manager/release-upgrades
```
and make sure that the line 
[SIZE="2"][SIZE="3"][COLOR="Red"]Prompt=[/COLOR][/SIZE][/SIZE]

says 
```

Prompt=normal;

```
then save the file and close gedit. 
now update 
```
sudo apt-get update
```
then open update manger again.
Has it changed ? 
if not 
BACKUP 1st 
then in terminal run 
```
sudo do-release-upgrade
```
and follow the steps. 
Hope that this helps.

---

### Post by paker on 2012-05-15
Thank you for the replies.

EDIT: Update Manager prompting not until July according to Ubuntu official announcement

---

### Post by josephmills on 2012-05-15
Glad too see everything worked out :)

---

