---
title: "Webcamoid issue"
date: 2020-06-05
forum: New to Ubuntu
---

### Post by karem1986 on 2020-06-05
I installed webcamoid from the website and the icon is on applications 

I tried to deinstall by using sudo apt-get remove webcamoid commmand in terminal and I receive the message 'is not installed' 

How this can be when I still see the icon for webcamoid in my applications

I need to remove it as webcamoid is not working on Ubuntu

Please help :)ons 

I tried to deinstall by using sudo apt-get remove webcamoid commmand in terminal and I receive the message 'is not installed' 

How this can be when I still see the icon for webcamoid in my applications

I need to remove it as webcamoid is not working on Ubuntu

Please help :smile:

---

### Post by coffeecat on 2020-06-05
You installed webcamoid from a downloaded executable run file, which is why you cannot uninstall it with apt-get. Only things installed from repositories in your sources lists with apt, apt-get or a graphical package manager can be uninstalled with those package managers. 

This is an 18-month old discussion on github, but it might help:

[https://github.com/webcamoid/webcamoid/issues/144](https://github.com/webcamoid/webcamoid/issues/144)

---

