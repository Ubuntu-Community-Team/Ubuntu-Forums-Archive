---
title: "Can't install any software on my Ubuntu OS"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by rocksandy on 2008-09-06
Hi,
After installing Ubuntu 7.10, i tried to install some software from the "Sound & Video" section of "Add/Remove Applications", but every time i try to install something, it gives me the following error (when i tried to install fmit):

Cannot install 'fmit'

This application conflicts with other installed software. To install 'fmit' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

i read through the forum and found many people who had the same problem and tried the solutions mentioned by many fellow Ubuntu-users, but i have not been able to solve the problem. Somebody help me pleeeeeeeeeeez.....

---

### Post by Absolute4Zero on 2008-09-06
Its very simple open up synaptic from system - administration than once application is up search for fmit remove it from there and then you will be able to install new software

---

### Post by Absolute4Zero on 2008-09-06
Right click on the application and choose Mark for complete removal

---

### Post by rocksandy on 2008-09-07
Thanks for the reply. But, you don't get it. My problem is not with uninstalling the application, but in installing one. What i mean is, say for instance, I want to install the gstreamer0.10-plugins so that i can play mp3 songs using the Totem media player, i get the following error:


Cannot install 'gstreamer0.10-plugins-ugly'
This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.
Switch to the 'synaptic' package manager to resolve this conflict.

The error tells me that there is a conflicting software, but never tells me the name of the conflicting software. So i don't know what I possibly have to do after opening the Synaptic package manager. Which software do I have to uninstall ????? :confused:

---

### Post by sanemanmad on 2008-09-07
Hi rocksandy~

Have you tried installing software with the -f option. Or have you tried *sudo apt-get autoremove ; sudo apt-get autoclean ; sudo apt-get install <program>*

---

### Post by Sef on 2008-09-07
> *sudo apt-get install <program>*

Open the terminal (Appliations > Accessories > Terminal) and then paste or copy this command:

```
sudo apt-get update && sudo apt-get install gstreamer0.10-plugins-ugly
```

If it does not install, it should give you a message as to why.

---

### Post by rocksandy on 2008-09-08
Well, i tried the ideas given by both "sanemanmad" and "Sef". The output that I got really didn't make sense to me (not one bit :( ). Anyways, I'm attachin the screen shot of my Terminal where I executed both the sets of commands. Pleez do lemme know if you guys understand anything out of it.

---

### Post by tangibleorange on 2008-09-08
could you please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by rocksandy on 2008-09-08
Here you go. Attached file has the contents of my sources.list

---

### Post by lazyart on 2008-09-08
nm.

---

### Post by tangibleorange on 2008-09-08
> **rocksandy said:**
> Here you go. Attached file has the contents of my sources.list

yeah this file is seriously messed up. no wonder it was failing! back it up, then open it for editing:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksu gedit /etc/apt/sources.list
```

and delete everything in there. now, paste the following in there:

```
#APT Sources File
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
```

now save the file and exit. then, run:

```
sudo apt-get update
sudo apt-get clean
sudo apt-get install -f
```

---

### Post by sanemanmad on 2008-09-09
I would not even bother trashing the file. All you really need to do is un-comment the same lines tangibleorange is mentioning and update.

---

