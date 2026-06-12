---
title: "Package Troubles installing Ubuntu 8.10"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by SILLAT on 2008-11-27
I've been trying to do a Clean install Ubuntu 8.10 on a Desktop Pc at home but every time i run the installer it freezes at 95% of the installation when the installer says "[COLOR="Lime"]checking for packages to be removed[/COLOR]" 
I've run the cd about 3 more time and it still stuck at 95% & checking for packages to be removed, i've since given up on trying to reach 100% installation but instead opt to boot into ubuntu after a freeze at 95% an it works ;) i manage to login, install some updates, and the system is running fine 2me 
I just would like to kno if there is any consequences of not doing a 100% installation? and how about those packages that the system is checking for to remove? How can i Remove them myself? or how do they affect me?

---

### Post by drs305 on 2008-11-27
The last time I installed Intrepid I jotted down most (but probably not all) the steps I saw:
```

5% file system 	
12% scanning files 	
22% copying files 	
78% locale config 	
81% config target sys 
82% config apt 	
87% time / data 	
88% import settings 	
90% detect hardware
94% load modules / config hardware  	
95% look for other OS, install grub 		
95% remove packages 
99% post-install

```
So it appears you are mostly missing the cleanup. If it works, I wouldn't worry too much about the last 5%. ;-)

---

### Post by SILLAT on 2008-11-27
o.k kool
i just wanted to kno
thnx man

---

