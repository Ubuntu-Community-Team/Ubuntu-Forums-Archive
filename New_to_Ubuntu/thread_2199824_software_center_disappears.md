---
title: "software center disappears"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by baronmountain1 on 2014-01-15
Whenever I attempt to open the obutuntu software center, which I presume is what is my only option in terms of getting flashplayer and other needed updates the window opens up briefly as commanded and then abruptly disappears. Is this is what is supposed to happen? I am not able to properly operate the center currently, is there another manner by which one can install upgrades and other new software?

---

### Post by Bucky Ball on 2014-01-16
For the moment, open a terminal and copy/paste these two commands, hitting return in between:

sudo apt-get update
sudo apt-get upgrade

Report any errors. If none, try Software Centre again. The updates may have fixed the issue. If you don't do regular updates odd things can happen. ;)

PS: You don't mention which release you are using ...

---

### Post by Impavidus on 2014-01-16
I saw your other thread. If you recieved a machine with Ubuntu installed, but with unknown history, missing passwords, errors and a completely unknown state, I usually recommend a new clean install of Ubuntu. That will bring the machine back to a default state, so that you know what has been done to the system, we know what state we can expect and everyone can be sure no security holes were left by the previous owner. Also, check which version of Ubuntu has been installed on your desktop. People recieving Ubuntu desktops from others often get one with an outdated release. You can run the command **lsb_release -r** in a terminal to find out.

---

### Post by Bucky Ball on 2014-01-16
> **Impavidus said:**
> I saw your other thread (which was closed maybe a little too hastily by Toz).

The thread was quite rightly closed. Read the ***Code of Conduct ***again. The forums do not condone cracking of any kind and any and all threads/posts asking for instructions to crack will be/are closed post-haste.

Please do not attempt to reopen the topic on this thread. If you have advice regarding the subject of the closed thread, PM the OP, do not post off-topic content on this thread. If you think the thread was closed unfairly or have a problem with it, post in ***Forum Feedback and Help***, not here, as it has nothing to do with the support request we are dealing with in this thread. Thanks.

---

### Post by andrew.46 on 2014-01-18
> **baronmountain1 said:**
> Whenever I attempt to open the obutuntu software center, which I presume is what is my only option in terms of getting flashplayer and other needed updates [...]

There is an older package manager still available:

```

sudo apt-get install synaptic

```

which might be enough to get you out of trouble but of course will not fix the issue of your broken 'Software Centre'.

---

### Post by Bucky Ball on 2014-01-18
Synaptics is not older, just different, and the weapon of choice for many.

It is completely up to date and maintained. I do minimal installs and never install Software Centre, preferring to go with the lighter, more straightforward Synaptics Package Manager. ;)

OP: The problem is, if Software Centre is playing up, it is quite possible Synaptics won't work either. Open a terminal and try these two commands, hitting return after each:

sudo apt-get update
sudo apt-get upgrade

Any errors?

---

### Post by deadflowr on 2014-01-18
Off topic, synaptic is a robust package manager on it's own, but it's not an as easy to use tool out of the box like the software center is(for a new user). There isn't any easy to recognize INSTALL button like the software center(among other things, probably).It takes a second to figure out.

On topic, if the OP runs the above update and upgrade commands and still has problems, try running
```
software-center
```in a terminal and post the output.

---

