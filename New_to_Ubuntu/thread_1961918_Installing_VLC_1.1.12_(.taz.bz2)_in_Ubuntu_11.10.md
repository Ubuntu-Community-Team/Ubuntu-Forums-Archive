---
title: "Installing VLC 1.1.12 (.taz.bz2) in Ubuntu 11.10"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by cedriod09 on 2012-04-20
Hello,
I'm new to linux and particularly to Ubuntu.
I'm having a headache installing vlc 1.1.12 with the .taz.bz2 extension in Ubuntu 11.10
Please help!
Since I'm a newbie, please give detailed explanations..thanks

---

### Post by ron999 on 2012-04-20
> **cedriod09 said:**
> 
I'm having a headache installing vlc 1.1.12 with the .taz.bz2 extension in Ubuntu 11.10

Hi
Those bz2 files are not installable.
Install VLC from command line like this:-
```
sudo apt-get install vlc
```
Or use software center.

---

### Post by cedriod09 on 2012-04-20
Hi,
result then executing command 
sudo apt-get install vlc

cedric@ubuntu:-$ sudo apt-get install ~/vlc-1.1.12/
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package /home/cedric/vlc-1.1.12
E: Couldn't find any package by regex '/home/cedric/vlc-1.1.12'
cedric@ubuntu:-$


What should I do?
Please note that I'm not having this computer connected to the internet.

---

### Post by NikTh on 2012-04-20
> **cedriod09 said:**
> 
Please note that** I'm not having this computer connected to the internet**.

This is important info . 

This tar.bz2 file that you downloaded is source code for compile - build the vlc player. Lot of work and i don't know if you will be able to do this in off-line mode. 

To install packages in Ubuntu without Internet is pain in the ***. 
You must find a .deb package (i don't know if vlc has one) and then install it from software center. 

I think there is a tool (i have not test it) for off-line mode installation . 
Check it here--> [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by sadaruwan12 on 2012-04-20
> **cedriod09 said:**
> Hi,
result then executing command 
sudo apt-get install vlc

cedric@ubuntu:-$ sudo apt-get install ~/vlc-1.1.12/
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package /home/cedric/vlc-1.1.12
E: Couldn't find any package by regex '/home/cedric/vlc-1.1.12'
cedric@ubuntu:-$


What should I do?
Please note that I'm not having this computer connected to the internet.

To install VLC it's best advised to have internet other wise its very troublesome for a new comer like you.

---

