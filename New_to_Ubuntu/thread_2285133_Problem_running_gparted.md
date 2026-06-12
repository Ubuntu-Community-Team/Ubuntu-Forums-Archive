---
title: "Problem running gparted"
date: 2015-07-03
forum: New to Ubuntu
---

### Post by jeff131 on 2015-07-03
I have had some problems running gparted recently. I installed gparted with the command ```
sudo apt-get gparted
``` and it installed. I searched up gparted, and tried to run it. It asked for my password, and I clicked authenticate. Then nothing happened. I also tried running gparted with the command ```
sudo gparted
``` But it said, the process gpartedbin is already running. Only one gpartedbin process is permitted. Why is this? How can I fix this?


-Any help is appreciated, thank you

---

### Post by papibe on 2015-07-03
Hi jeff131.

Try killing whatever is running:
```
sudo killall gparted

sudo killall gpartedbin
```
And then call it from the menu instead. If you really want to call it from the terminal, do it like this:
```
gparted-pkexec
```
It will ask for your password using a graphic dialog.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Geoffrey_Arndt on 2015-07-03
Try installing synaptic (a great, legacy package manager) and then fully remove (uninstall) gparted, and then reisnstall it.   Your should get a start icon accessible via the dash.   Give it a shot and see what happens.

---

### Post by Mike_Walsh on 2015-07-04
Hi, Jeff.

A word to the wise. The terminal is great for installing things, and you can indeed perform all sorts of minor miracles with it.....ONCE you know what you are doing. I know Ubuntu (and Linux in general) has had this reputation for long enough as being a nightmare for new, especially ex-Windows users.....because **everything's** done by command line.

But you know, Ubuntu's made great strides in recent years. You **can **actually do things the easy way, nowadays... You don't HAVE to use the terminal for everything, you know!


Regards,

Mike. :D

---

