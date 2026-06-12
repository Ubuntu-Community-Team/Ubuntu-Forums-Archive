---
title: "Upgrading to 13.10 Issue"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by CCgirl6690 on 2014-03-06
Hello. Hope yall are fine
I'm trying to upgrade from 13.04 t0 13.10 
when i use software updater i click on upgrade then it starts download like 2 little files then i get a pop up saying "system problem detected"  then i searched n found else where to put this command into terminal.and i get this error..
```
none@None:~$ sudo do-release-upgrade
[sudo] password for none: 
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,142 kB]                                                  
Fetched 1,142 kB in 6s (134 kB/s)                                              
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
extracting 'saucy.tar.gz'
Can not run the upgrade
This usually is caused by a system where /tmp is mounted noexec. Please remount without noexec and run the upgrade again.
none@None:~$ 


 
```
Please help me, I'v had this problem for month. cant upgrade n since ubunto doesnt update my system so it's not safe to stay on 13.04
thank you so much

---

### Post by CCgirl6690 on 2014-03-06
Nvm, heres the solution 

sudo mount -o remount,exec /tmp

---

