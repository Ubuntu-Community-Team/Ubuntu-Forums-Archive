---
title: "This is so basic and frustrating - pcmanfm"
date: 2017-08-13
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-13
This is so basic!

Is I mounted a folder through mount -t nfs and if I disconnect the pc of network without I do "sudo umount path/to/the/folder" my pcmanfm is freeze! Hooo, this is so basic! I am so upset with ubuntu :(
I need rebot the system, through terminal or menu, and the script ended freeze with message about unmount drives network....hooo, this is so frustrating.
How can I reolve this stupid issue? What can I do to if I disconnected the cable network the pcmanfm don't be silly!?

my system is:
```

xx@xx:~$ uname -a
Linux enonet 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
xx@xx:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

```
Thanks

---

### Post by vocx on 2017-08-13
> **Edgar_Oliveira said:**
> This is so basic!

Is I mounted a folder through mount -t nfs and if I disconnect the pc of network without I do "sudo umount path/to/the/folder" **my pcmanfm is freeze! **Hooo, this is so basic! I am so upset with ubuntu :(
I need rebot the system, through terminal or menu, and the script ended freeze with message about unmount drives network....hooo, this is so frustrating.
How can I reolve this stupid issue? What can I do to if I disconnected the cable network the pcmanfm don't be silly!?

PCmanFM is a file manager, right? It is made by one guy called PCman, not by Ubuntu. So, I think you should report this problem to him. That when the network connection stops, it should detect this in the software and not lock up. I would be surprised if this is not taken care of.

When a program locks up, you usually don't need to restart the computer, you can just kill the offending program.
```

sudo apt install htop

```

With "htop" you can see the running processes.
```

htop

```
So, when the file manager locks up, you can run "htop", see the "pcmanfm" process and kill it, by hitting F9 and choosing SIGTERM.

In the terminal if you know the name of the process that needs killing, you can use "pkill".
```

pkill pcmanfm

# if the process is owned by "root" you may need to use "sudo"
sudo pkill pcmanfm

```

---

### Post by user_of_gnomes on 2017-08-14
Sounds like a bug, try reporting it.
PCManF is the file manager used by Lubuntu and written for LXDE. Not sure how focused they are on making it run on Ubuntu.

---

### Post by sed_faster on 2017-08-14
> **user_of_gnomes said:**
> Sounds like a bug, try reporting it.
PCManF is the file manager used by Lubuntu and written for LXDE. Not sure how focused they are on making it run on Ubuntu.

But I use it on Lubuntu 17.04

---

### Post by sed_faster on 2017-08-14
The tip about htop this is awesome. I only know about top, and I don't know how works with him!
I will try report this issue to pcmanfm. I found it this website: [https://forum.lxde.org/viewforum.php?f=22](https://forum.lxde.org/viewforum.php?f=22) I will try put my question on this community!

Thanks

---

### Post by vocx on 2017-08-14
> **user_of_gnomes said:**
> Sounds like a bug, try reporting it.
PCManF is the file manager used by Lubuntu and written for LXDE. Not sure how focused they are on making it run on Ubuntu.
You are under the mistaken impression that Lubuntu and Ubuntu are different. They are not, they are the same system. The only thing that changes is basically the outer layer, the one that shows you the desktop when you log in. As long as the dependency libraries are installed in either system, the programs should run.

In particular, PCmanFM is made with the GTK+2 libraries, so these need to be installed. As long as they are present, the software should run. There is also a Qt version for PCmanFM, so for this, the Qt libraries should be installed.

---

### Post by user_of_gnomes on 2017-08-14
> **vocx said:**
> You are under the mistaken impression that Lubuntu and Ubuntu are different. They are not, they are the same system. The only thing that changes is basically the outer layer, the one that shows you the desktop when you log in. As long as the dependency libraries are installed in either system, the programs should run.

In particular, PCmanFM is made with the GTK+2 libraries, so these need to be installed. As long as they are present, the software should run. There is also a Qt version for PCmanFM, so for this, the Qt libraries should be installed.

I actually wasn't under that impression but I was mistaken in thinking he had installed it manually on an Ubuntu installation.

---

### Post by vocx on 2017-08-14
> **user_of_gnomes said:**
> I actually wasn't under that impression but I was mistaken in thinking he had installed it manually on an Ubuntu installation.
But that's exactly what you are implying when you say "installing manually in Ubuntu".

Whether it is installed on Lubuntu or in Ubuntu is not a concern.

---

### Post by Geoffrey_Arndt on 2017-08-14
Or just install one of several other file managers for Linux such as "Sunflower" . . . problemo resuelto

[http://www.noobslab.com/2016/08/are-you-looking-for-alternative-file.html](http://www.noobslab.com/2016/08/are-you-looking-for-alternative-file.html)

---

### Post by sed_faster on 2017-08-14
I like the pcmanfm because this is simply and light! I have a 8Gb of the ram but I like the purpose of the Lubuntu, faster, light and minimalist!

I need re-upgrade to the version 16.04 LTS. Because I have amount of the problems with this distribution. The pcmanfm freeze because I don't unmount the drives I think this is stupid! I don't really understand why this happen, maybe this is a issue of the system which I can't see/understand. But with this version of the system I have problem with the firefox. Suddenly the firefox freeze and I can't turn off the browser or kill the process. After some minutes the all system freeze and I need reboot the pc through the button! This is very frustration!

Thanks

---

### Post by cariboo on 2017-08-14
Before you re-install, I'd suggest you create bug reports for the apps you are having a problem with. Problems can't be fixed if no one knows about them. In a terminal run the following command for pcmanfm:

```
ubuntu-bug pcmanfm
```

and for Firefox:

```
ubuntu-bug firefox
```

to make things better all around, we all need to do our part.

---

### Post by sed_faster on 2017-08-14
I was reading about ubuntu-bug from man but I rapid question "it is possible collect reports which my system will be generate?

---

### Post by deadflowr on 2017-08-14
This sounds like what you're doing:
[https://bugzilla.redhat.com/show_bug.cgi?id=845565]("https://bugzilla.redhat.com/show_bug.cgi?id=845565")

---

