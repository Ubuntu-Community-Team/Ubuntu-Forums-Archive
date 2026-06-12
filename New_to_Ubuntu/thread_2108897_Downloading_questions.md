---
title: "Downloading questions"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by Dounut on 2013-01-25
I'm new to Linux and I recently installed Ubuntu. Could anybody help me figure out how to properly download programs to my desktop. An example would be bittorrent.

---

### Post by papibe on 2013-01-25
Hi Dounut. Welcome to the forums ):P

Open the 'Software Center', look for programs that may interest you, and press install.

For torrent download, there's a pre installed program called transmission. It is the equivalent to uTorrent.

Let us know how it goes. Come here often and have fun.
Regards.

---

### Post by pspencil on 2013-01-25
actually I find this more convenient. 

"sudo apt-get install " + name of the software 

But you must make sure you enter the name exactly..

---

### Post by Untold on 2013-01-25
Installing synaptic software manager is a good tool for software as well.  I also use it to help me purge software I do not want and could not locate through other means.

---

### Post by Dounut on 2013-01-25
Wow thanks guys!! That actually helped me get set up :D. But one more question, with sudo get does it have to be programs within Ubuntu or does it search a program through the internet?

---

### Post by sffvba[e0rt on 2013-01-25
Have a look at this: [Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") 


404

---

### Post by deadflowr on 2013-01-25
> **Dounut said:**
> Wow thanks guys!! That actually helped me get set up :D. But one more question, with sudo get does it have to be programs within Ubuntu or does it search a program through the internet?


sudo gives you root access, aka, the ability to install programs system wide, otherwise you'd only be able to install programs in a user folder.
Running apt-get connects you to the Ubuntu repositories(and any repo you've added via ppa).

```
man apt-get
```

```
man sudo
```

---

### Post by gifford on 2013-01-25
One of the great features of Linux and Ubuntu is safety and security. It is probably a good idea for someone new to use the Software Center or Synaptic to install software. Most anything you want to use or do can be found there.

---

