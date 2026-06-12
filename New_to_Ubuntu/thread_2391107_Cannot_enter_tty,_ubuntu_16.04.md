---
title: "Cannot enter tty, ubuntu 16.04"
date: 2018-05-05
forum: New to Ubuntu
---

### Post by kulbear on 2018-05-05
Hi,

I want to use ubuntu 16.04 on my laptop so I use a bootable USB to install the system.

Now I want to install NVIDIA driver... another story, skip it. Anyway I need to use tty to install the driver as I need to shut down X server.

But when I use ctrl+alt+F1~6 to enter the tty, nothing happens. The situation is, first I login to my user, stay on the desktop. Then I press ctrl+alt+f1, then my mouse disappear, and the GUI directly got frozen (I test it by playing a youtube video and press the keys).

It looks like I stucked at somethere because if I press ctrl+alt+f7 the GUI goes back to working. 

Can anyone help? I can update any information about the system if you need. Thank you.

---

### Post by Xian on 2018-05-05
From a terminal:

```
sudo init 3
```

This should drop you into tty. After finishing:

```
sudo init 5 && exit
```

or

```
sudo shutdown -r now
```

---

### Post by hier-kommt-luis on 2018-05-08
Have you tried this one? [https://devtalk.nvidia.com/default/topic/979691/jetson-tx1/can-t-access-tty-terminals-ubuntu-16-04/](https://devtalk.nvidia.com/default/topic/979691/jetson-tx1/can-t-access-tty-terminals-ubuntu-16-04/)

---

### Post by kulbear on 2018-05-08
after typing 

    sudo init 3

My screen turns to whole black and I cannot return to GUI even with 

    ctrl+alt+f7

---

### Post by kulbear on 2018-05-08
> **hier-kommt-luis said:**
> Have you tried this one? [https://devtalk.nvidia.com/default/topic/979691/jetson-tx1/can-t-access-tty-terminals-ubuntu-16-04/](https://devtalk.nvidia.com/default/topic/979691/jetson-tx1/can-t-access-tty-terminals-ubuntu-16-04/)

Sorry I should clarify, I want to install nvidia driver later, but first I need to be able enter the tty with the default open source driver.

---

