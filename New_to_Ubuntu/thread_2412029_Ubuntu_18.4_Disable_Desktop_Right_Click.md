---
title: "Ubuntu 18.4 Disable Desktop Right Click"
date: 2019-02-07
forum: New to Ubuntu
---

### Post by hstapleton2019 on 2019-02-07
Hello everyone,
I am working on converting some of our schools old laptops into thin clients to extend their life, currently everything is working in terms of Remote Desktop. I have an admin account and a standard account which logs in automatically, one the standard account I would like to disable the right click on desktop so that the users can't change the background image or add a new folder to the desktop. I tried creating a startup command and for some reason it only seems to work on my admin account. I have attached an image of what the desktop is like when the machine is booted. it would also be ideal to set the remote desktop connection to start up automatically but I could only seem to start remmina up automatically which isn't ideal. 

Any help would be appreciated as I don't seem to have gotten anywhere in the last hour :(

[ATTACH=CONFIG]282425[/ATTACH]

---

### Post by Impavidus on 2019-02-07
I'm not so familiar with remote desktop (whenever I do anything remote, it's command line), but I doubt blocking the right click on the desktop will stop all people from changing the background. I always change the background by command line – or rather, by shell script. You may have to lock it down completely.

---

