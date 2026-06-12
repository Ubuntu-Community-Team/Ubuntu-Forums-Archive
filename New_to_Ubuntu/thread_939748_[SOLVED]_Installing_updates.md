---
title: "[SOLVED] Installing updates"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by mregister on 2008-10-06
Hello All,

I just downloaded updates for Hardy but I ran:
sudo apt-get update without the install command. So where are they downloaded to and how do I install them now? 

Thanks.

---

### Post by kosmiciatakuja on 2008-10-06
I believe that with apt-get update you just check which packages are in order for upgrade. then you have to perform ```
sudo apt-get upgrade
``` to actually upgrade them. apt-get install is not necessary for just upgrading packages I think...

---

### Post by hyper_ch on 2008-10-06
sudo apt-get update will just update the package information on what packages are available in each repo in your sources.list.

sudo apt-get upgrade will download and install the upgradable packages. The .deb files will be stored in /var/cache/apt/[something]

---

### Post by mregister on 2008-10-06
ok i see where they are stored and I see the differnce between update and upgrade. 

The reason for the updgrade is that I am getting the message in the auth log that root has expired when running cron (account root has expired). I found some info that this is a bug in Hardy and that I need to run an update. Is that correct?

---

### Post by kosmiciatakuja on 2008-10-06
In that case, yes, you should do 
```
sudo apt-get update
```
wait for that to finish, then
```
sudo apt-get upgrade
```
Maybe just doing 'upgrade' is enough, but I do both just in case, the first step doesn't take that much time anyway.

---

### Post by mregister on 2008-10-06
Ok I did that. Thanks for the help.

---

### Post by Sef on 2008-10-06
Always do ```
sudo apt-get update
``` before upgrading ```
sudo apt-get upgrade
``` or installing new packages ```
sudo apt-get install package_name
```.  That way the repositories are updated to the lastest versions.

---

### Post by mregister on 2008-10-06
That makes sense to check then run the update. Thanks for the help guys.

---

