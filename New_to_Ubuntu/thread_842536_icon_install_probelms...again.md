---
title: "icon install probelms...again"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by golgo13 on 2008-06-27
hi
can someone please explain to me (simply..please) how to cahnge icons in the usr share icons wherever folder
how do enable root and then get to change these simply
any help appreciated

---

### Post by golgo13 on 2008-06-27
as you can see from my typos I need this explaining VERY simply

---

### Post by anderskitson on 2008-06-27
The easiest way by far, is to open terminal and enter
> sudo nautilus

Then your password go to filesystem and navigate to the folder and just replace the icons you want to. What is your final goal?

---

### Post by golgo13 on 2008-06-27
also can I do this without 'resorting' to the terminal as finding files in there really does my head in....:confused:
or please explain all the required steps "f**k off back to windows" not included:lolflag:

---

### Post by anderskitson on 2008-06-27
igonore this

---

### Post by golgo13 on 2008-06-27
hi anderkitson
sorry I missed your post
all I want to do is replace the trash icon with a funny tux one
but you know how these things are its a way to me learning more about linux file system in general

---

### Post by anderskitson on 2008-06-27
no you don't have to navigate in terminal, the command I gave you will launch the visual browser with root privileges, its really simple.

---

### Post by sydbat on 2008-06-27
> **golgo13 said:**
> or please explain all the required steps "f**k off back to windows" not included:lolflag:
No one here would EVER say that to you.

As for the terminal - typing in```
sudo nautilus
```and typing in your password will bring up a window allowing you to find the file/folder.

Nothing to be scared of.

---

### Post by golgo13 on 2008-06-27
so the root file just takes me to the desktop or
changing the actual .png icon does nothing to the actual icon that it is supposed to change
any ideas?
BTW I was only joking I do actually want this answer

---

### Post by golgo13 on 2008-06-27
ok so i changed the use trsh.png location image but not the actual icon when i open it i see the original icon but cannot change it....
:confused:

---

### Post by golgo13 on 2008-06-27
richard@richard-laptop:~$ sudo nautilus
Initializing gnome-mount extension
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7


(eog:6841): EOG-WARNING **: Service registration failed.

** (eog:6841): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(eog:6850): EOG-WARNING **: Service registration failed.

** (eog:6850): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(eog:6856): EOG-WARNING **: Service registration failed.

** (eog:6856): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(eog:6863): EOG-WARNING **: Service registration failed.

** (eog:6863): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(eog:6871): EOG-WARNING **: Service registration failed.

** (eog:6871): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Segmentation fault (core dumped)
richard@richard-laptop:~$ 

does this help because it means nothing to me:)

---

### Post by jakupl on 2008-06-27
Do 

```
gksudo nautilus
```

gksudo is ment for graphical stuff

---

### Post by golgo13 on 2008-06-27
what I mean is when I get to her... waht do I do?
any help appreciated

---

