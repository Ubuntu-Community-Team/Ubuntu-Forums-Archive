---
title: "removing virtualbox icon from dash home"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Dave_Rose on 2013-10-21
Hi. I recently installed virtualbox on my computer. I am running ubuntu 12.10. I had some issues with it so I did some research. It seems I have possibly installed the wrong version of virtualbox, version 4.1 I want to install version 4.2, but I am told to uninstall the other version first. I thought I got rid of everything, but the virtualbox icon still appears in the dash home. I tried dragging it to the trash, with no luck. When I try to uninstall it through the terminal it tells me that the program is not installed. I'm a bit confused. I don't want to install the 4.2 with that icon still there. I'm not sure how it would affect anything. Is it possible for the program to be totally gone and that icon still stuck in dash home for lack of a better term?
Might I add that I am very new to linux, but am enjoying learning how to use it. It would be nice to be rid of windows all together some day. Not sure if that will happen for me, but we shall see. 
Thanks

---

### Post by varunendra on 2013-10-23
Hi Dave, Welcome to the forums !

If the virtualbox "Icon" still appears in the Dash home, you may not have removed everything, or not 'correctly'. It should have been removed automatically if removed properly.

Anyway, to get rid of it, you will have to remove its **.desktop** file from **/usr/share/applications/** directory. So, assuming its name is "virtualbox.desktop", please try this -
```
sudo mv /usr/share/applications/virtualbox.desktop ./
```
This will move the file from its location to your home instead of deleting it. If this solves your problem, you can delete it anytime you wish. If not, you may need it again.

---

### Post by Dave_Rose on 2013-10-26
Thanks for the help. Unfortunately I won't be able to try this as I ended up taking ubuntu off my computer. I was going to install another copy of windows that I received from a friend. I didn't have anything on my hard drive that I needed, so I figured what the hey, just delete the linux. I ended up having issues with that install as well, ( wrong product key). So it's back to the drawing board. A fresh install of ubuntu 12.10. Hopefully I get the proper version of virtualbox and everything works this time.

---

### Post by VMC on 2013-10-26
I just installed the latest vbox 4.3, and it works great. I just downloaded "virtualbox-4.3_4.3.0-89960~Ubuntu~raring_amd64.deb", and installed it on both Ubuntu 12.04 and Saucy and it works great. Not issues with libraries on either system.

---

### Post by varunendra on 2013-10-26
> **Dave_Rose said:**
> A fresh install of ubuntu 12.10. Hopefully I get the proper version of virtualbox and everything works this time.

Good luck ! :)

Although if it is not a problem for you, it is recommended to use 12.04.3 instead. 12.04 is an LTS ([Long Term Support]("https://wiki.ubuntu.com/Releases")) release and will be much longer supported (upto April 2017), and its point release 12.04.3 includes the much newer kernel 3.8 which you may need for [supporting newer devices/features]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#A12.04.3_.2B-_13.04_Hardware_Enablement_Stack_Policies_and_Procedures").

If you think it makes sense, it is recommended to download the ISO via torrent which is not only faster download, but also ensures the integrity of the download. Official torrents can be found here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

