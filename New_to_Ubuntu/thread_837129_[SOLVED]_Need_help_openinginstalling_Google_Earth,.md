---
title: "[SOLVED] Need help opening/installing Google Earth, please."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by L Campbell on 2008-06-22
Ubuntu 8.04 LTS

I have downloaded the file GoogleEarthLinux.bin and have it on my desktop.

When I try to 'open' it I get the message:-

.....

Couldn't display "home/qwer/Desktop/GoogleEarthLinux.bin"

There is no application installed for this file type

...... 

I would appreciate it if someone could tell me how I should proceed.

TIA.

---

### Post by chrisccoulson on 2008-06-22
Googleearth is available in the Medibuntu repositories. Once you have added the Medibuntu repositories to your sources.list as per [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"), you can install Googleearth by doing:
```
sudo apt-get update
sudo apt-get install googleearth
```
The launcher will appear in Applications -> Internet

---

### Post by L Campbell on 2008-06-22
> **chrisccoulson said:**
> Googleearth is available in the Medibuntu repositories. Once you have added the Medibuntu repositories to your sources.list as per [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"), you can install Googleearth by doing:
```
sudo apt-get update
sudo apt-get install googleearth
```
The launcher will appear in Applications -> Internet


Great job, thanks.

This worked perfectly.

Kind regards.

---

