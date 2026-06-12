---
title: "Sharing character devices between an Android phone and a Linux PC?"
date: 2012-03-23
forum: Programming Talk
---

### Post by silverair on 2012-03-23
I am an amateur and need some help.
I am working on  a project, where character devices on an android phone must show up on the /dev directory of  a linux PC. It can be shared via bluetooth /wi-fi or maybe USB.

For example character devices like camera and accelerometer of the phone must me shared seamlessly from a Linux PC so that the PC thinks that these devices are its own.

Here is the framework on how to implement it. 

[img]http://s19.postimage.org/dv0ba4rg3/y_Cuxz_L.jpg[/img]

Server- Phone,    Client- PC

This was taken from an IEEE paper called "[Remote Virtual Peripheral Framework: Enabling Dynamically Composed Devices]("http://www.scribd.com/doc/86450585?secret_password=rmpxpx8o3bryje13m8h")". The paper implemented this on a nokia maemo device. I figure, it can be done on an android  device too, once its rooted.(I have a Desire HD and going root it)

I don't know where to start. I have looked all over the net, but nothing of this sort is present.
I have learnt about creating device drivers in linux, compiling them and adding them as modules and making them show up in /dev.
Since “everything is a file” on linux, Can it be shared , using bluetooth library or something.
Please direct me where to go next. Thank you.

---

### Post by ysangkok on 2012-03-24
The "everything is a file" sounds very nice, but sadly Linux doesn't really work like that. A device file is actually just it's minor and major device number, AFAIK. You can't share it over NFS or the like. See:

[http://unix.stackexchange.com/questions/4976/can-i-share-a-device-from-under-dev-across-hosts](http://unix.stackexchange.com/questions/4976/can-i-share-a-device-from-under-dev-across-hosts)

---

### Post by ysangkok on 2012-03-24
Also note that the linked reply recommends using a application-specific solution. That means you'd have to access the low-level video interface of Android which isn't documented AFAIK. Good luck, you'll need it :)

---

### Post by silverair on 2012-03-25
Thanks for the reply :) But
> **ysangkok said:**
> The "everything is a file" sounds very nice, but sadly Linux doesn't really work like that. A device file is actually just it's minor and major device number, AFAIK. You can't share it over NFS or the like. See:

[http://unix.stackexchange.com/questions/4976/can-i-share-a-device-from-under-dev-across-hosts](http://unix.stackexchange.com/questions/4976/can-i-share-a-device-from-under-dev-across-hosts)

Its very much possible , because they have implemented it on the paper as a  proof of concept (submitted by Nokia reasearch Labs)
(link in the first post)

[[img]http://s19.postimage.org/nb87h5ypb/pic1.png[/img]](http://postimage.org/image/nb87h5ypb/)

[[img]http://s19.postimage.org/lxgkluzfz/pic2.png[/img]](http://postimage.org/image/lxgkluzfz/)

as you can see they are accessing the accelerometer of a nokia maemo device from a linux pc. And its not an application specific solution. 
> **ysangkok said:**
> Also note that the linked reply recommends using a application-specific solution

That would defeat the purpose of the project. It was to demonstrate a smart environment, where all your devices- pcs,phones etc.. can access each other's sensors and peripherals - not using an application specific soln but a universal freamework.

---

