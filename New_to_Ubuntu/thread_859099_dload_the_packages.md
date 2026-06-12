---
title: "dload the packages"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by carrarin on 2008-07-14
Im still looking for all the packs i need. I dont have the internet so im kind of screwed. If i went somewhere wher there is internet, and use a live cd, and type 
sudo apt-get 
is there a way that i can send the packs to my flash instead of where they normalls go.

---

### Post by t0p on 2008-07-14
I dunno about **apt-get** - but you can go to [http://packages.ubuntu.com]("http://packages.ubuntu.com") with any computer, and download packages to save to a flash stick or whatever.  However, using this route can result in dependency hell!!

---

### Post by carrarin on 2008-07-14
i know, thats what ive beeen doing, ands its not fun.

---

### Post by carrarin on 2008-07-14
bump

---

### Post by hyper_ch on 2008-07-14
[http://www.linuxquestions.org/questions/linux-general-1/how-can-i-change-the-apt-get-download-location-172198/](http://www.linuxquestions.org/questions/linux-general-1/how-can-i-change-the-apt-get-download-location-172198/)

---

### Post by ajgreeny on 2008-07-14
If you use a live CD and also have a usb flash drive to save the packages you could do it with synaptic, I think.  Open up synaptic and use that to get all the packages and their dependencies, by using the check box "Download Package files only" when you chose apply in the dialog box when it appears.  That will just download packages to the /var/cache/apt/archives folder from where you should be able to copy them to the flash drive.  You can then use the flash drive as the source of the packages you need.

---

### Post by rraj.be on 2008-07-14
you can use aptoncd to create local repositarie's.

all you need is a system with all your required packages installed.

just get to a system in which all packages that you need are installed.

install aptoncd also in that system
```

sudo apt-get install aptoncd

```
now run ```
aptoncd

```
just select create.

it will automaticaly search for installed package's and make a list

use a blank dvd or cd  and click burn.

you had created the local repository with all installed packages in that system.

just take the disk to your system and insert it.

open synaptic and install all required package's.

this can be used as a backup mechanism if you dont have internet connection to install packages.

---

### Post by carrarin on 2008-07-14
this thing, aptoncd, if i have a live cd, it will only be installed in mem right. i dont wanna f* their comps

---

### Post by carrarin on 2008-07-14
bump

---

### Post by rraj.be on 2008-07-16
> **carrarin said:**
> this thing, aptoncd, if i have a live cd, it will only be installed in mem right. i dont wanna f* their comps

Cant get what you are telling.

Please be clear.

---

