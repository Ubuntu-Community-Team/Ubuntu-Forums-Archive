---
title: "Can't get additional drivers"
date: 2017-01-04
forum: New to Ubuntu
---

### Post by rafacpitta on 2017-01-04
Hi everyone,

I'm pretty new to Ubuntu and Linux systems, so I'm experiencing some problems with it. Actually, I have a dual boot system (Windows 10 and Ubuntu 16.04), and I installed the Ubuntu with a bootable USB made with the Rufus and Ubuntu iso image. I'm able to boot to Windows and Ubuntu as well use it for almost anything basic.

I've been trying to install codecs for playing mp3 and mp4 but I just don't know what to do. Some people tell me to search at the Ubuntu Software application but at the Additional Drivers tab it shows me that "An error occurred while searching drivers" and also I get a pop up message telling some error has occurred. Screenshots of them were taken and they are attached.

Thanks for all,

Rafael.

---

### Post by rafacpitta on 2017-01-04
Just to let you know that I could solve it by myself!

The issue was that I got this error everytime I tried to install something (eg.: sudo apt-get install -f):

Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

Actually there is no more this Medibuntu list, so I had to delete it 

> 
sudo rm /etc/apt/sources.list.d/medibuntu.list

and change the "Download from:" section of the Ubuntu Software configs.

---

