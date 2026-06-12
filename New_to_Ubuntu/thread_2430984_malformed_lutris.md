---
title: "malformed lutris"
date: 2019-11-10
forum: New to Ubuntu
---

### Post by joenuh71 on 2019-11-10
[ATTACH=CONFIG]284379[/ATTACH] I thought I was following the correct instruction to allow me to play Origin games. But all the updates seem to have frozen.
I added a screenshot of the message that I'm getting. I'm sure what went wrong or how I can fix it.

---

### Post by jeremy31 on 2019-11-10
Moved to New to Ubuntu
Please install inxi ```
sudo apt install inxi
```
Then post results for ```
inxi -r
```

---

### Post by joenuh71 on 2019-11-10
james@james-pc:~$ sudo apt install inxi
[sudo] password for james: 
E: Malformed entry 57 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.
E: Malformed entry 57 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.
james@james-pc:~$ inxi -r


Command 'inxi' not found, but can be installed with:


sudo apt install inxi

---

### Post by jeremy31 on 2019-11-10
Post URL for ```
cat /etc/apt/sources.list | nc termbin.com 9999
```
```
cat /etc/apt/sources.list.d/lutris.list | nc termbin.com 9999
```

---

### Post by joenuh71 on 2019-11-10
james@james-pc:~$ cat /etc/apt/sources.list | nc termbin.com 9999
[https://termbin.com/9mss](https://termbin.com/9mss)
james@james-pc:~$ cat /etc/apt/sources.list.d/lutris.list | nc termbin.com 9999
[https://termbin.com/b6o8](https://termbin.com/b6o8)
james@james-pc:~$ 

I'm suppose to find a download from a list?

---

### Post by jeremy31 on 2019-11-10
OK
```
gedit admin:///etc/apt/sources.list
```
Delete the last 2 lines in file, save and exit
Then do ```
sudo rm  /etc/apt/sources.list.d/lutris.list
```
Then do ```
sudo apt update
```

The commands to install on Ubuntu can be found at [https://lutris.net/downloads/](https://lutris.net/downloads/)

---

### Post by joenuh71 on 2019-11-10
OK. The (red circle) that was at the top of my screen is now gone.
This was the info from the terminal.

james@james-pc:~$ sudo apt update
Hit:1 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:4 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                            
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Hit:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:9 [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) bionic InRelease      
Hit:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease          
Hit:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease           
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
63 packages can be upgraded. Run 'apt list --upgradable' to see them.
james@james-pc:~$ apt list --upgradable
Listing... Done
wine-devel/bionic 4.19~bionic amd64 [upgradable from: 2.4.0~ubuntu16.04.1]
wine-devel-amd64/bionic 4.19~bionic amd64 [upgradable from: 2.4.0~ubuntu16.04.1]
wine-devel-i386/bionic 4.19~bionic i386 [upgradable from: 2.4.0~ubuntu16.04.1]
winehq-devel/bionic 4.19~bionic amd64 [upgradable from: 2.4.0~ubuntu16.04.1]
james@james-pc:~$

---

### Post by mastablasta on 2019-11-12
now do the system upgrade, but first check the list with 

[COLOR=#000000]apt list --upgradable


[/COLOR]

---

