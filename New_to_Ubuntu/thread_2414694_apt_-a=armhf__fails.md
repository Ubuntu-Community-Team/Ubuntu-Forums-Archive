---
title: "apt -a=armhf  fails"
date: 2019-03-13
forum: New to Ubuntu
---

### Post by anneranch on 2019-03-13
I am trying to install bluez package for architecture  amrhf , but it fails wiht the following message :


> 
jim@jim-desktop:~$ sudo apt -a=armhf install bluez 
[sudo] password for jim: 
E: Command line option 'a' [from -a=armhf] is not understood in combination with the other options.


How do I resolve this ?


sudo apt install bluez

works as expected

---

### Post by deadflowr on 2019-03-14
```
sudo dpkg --add-architecture armhf
sudo apt update
sudo apt install bluez:armhf
```

But you also need to have the ports repositories in your sources.
And if running regular Ubuntu (on x86 architecture), you then need to specify the normal repositories for amd64 and/or i386
and the ports repositories for the arm architecture.
So the sources.list entries would have to look something like this
```
deb [arch=amd64,i386] http://archive.ubuntu.com/ubuntu saucy main
```
and 
```
deb [arch=armhf] http://ports.ubuntu.com/ubuntu saucy main
```

you can read all about this here:
[https://wiki.debian.org/Multiarch/HOWTO]("https://wiki.debian.org/Multiarch/HOWTO")

---

