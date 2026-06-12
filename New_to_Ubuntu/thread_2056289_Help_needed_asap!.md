---
title: "Help needed asap!"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by skipper386 on 2012-09-11
Hi can anyone help me with this problem? I can't install chrome and other stuff to my Ubuntu because everytime I install or update this will comes out. Just see my attachment.. I badly need some help sir..

---

### Post by NikTh on 2012-09-11
Hi , 

help asap arrived. Is this asap enough ? :p

I can see you use 10.04 (old gnome 2 Environment) , please close all the applications and open only a terminal (ctrl+alt+t combo keys) 

Then copy-paste from here to terminal bellow commands with order. One line at time. 

```
sudo rm /var/lib/apt/lists/* -vf 
sudo rm -r /var/lib/apt/lists/partial
sudo mkdir /var/lib/apt/lists/partial 
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update 
sudo apt-get dist-upgrade
```Hopefully above commands will solve your problem. 

Please give here any errors or fails from above commands. 

You can copy-paste the results from your terminal here in forum and place the results between ```
 brackets so can be easy to read. 

**[noparse][code]The results Here
```[/noparse]**

Thanks

---

