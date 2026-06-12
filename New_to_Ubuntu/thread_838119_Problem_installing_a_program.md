---
title: "Problem installing a program"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Peterfc on 2008-06-23
Hi

I am trying to install a later version of Skype. Part way through installing i get a message.

(Reading database ... 159383 files and directories currently installed.) 

Preparing to replace skype 2.0.0.72-Omedibuntu1 (using ... /Skype-debian_2.0.0.72-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: error processing /home/peter/desktop/skype-debian_2.0.0.72-1_i386 (--install):
trying to overwrite '/usr/share/icons/skype.png'. which is also in package skype.common
dpkg-deb: subprocess paste killed by signal (broken pipe)

I tried to paste the message but do not understand the system so i have typed it as on the screen. I have a sound issue with Skype and need to try by installing the latest version i can.

Thanks for reading this thread.


[IMG]http:///home/peter/Desktop/Screenshot1.jpeg[/IMG]

---

### Post by sharks on 2008-06-23
which way did u tried to install?  terminal?

---

### Post by Peterfc on 2008-06-23
Hi 

I downloaded the program from skype on the option for Ubuntu 7.04.
I then clicked the downloaded package and the package installer started and the message below came up. I then closed the message in clicked on Install package. I then got the message i listed on the original thread.

Thanks for reading the thread.

An older version is available in a software channel

Generally it is recommended that you install the version from the software channel, since it is usually better supported.

---

### Post by ukripper on 2008-06-23
If you got Hardy then latest skype 2.0 is in the repos you can install it from synaptic or through terminal.

But if you want to install from their website then remove the previous skype installed completeley using follwoing commands in terminal:
```
sudo apt-get remove --purge skype
```

this will remove evrything for skype including skype config files

after this download and install your deb package from the website

---

### Post by brian_p on 2008-06-23
> **Peterfc said:**
> I tried to paste the message but do not understand the system so i have typed it as on the screen. I have a sound issue with Skype and need to try by installing the latest version i can.

Position the mouse at the beginning of the text you want to copy. Left click and keep depressed. Drag the mouse to the end of the text you want to copy. Middle click to paste.

The message you got installing Skype is harmless. The same file is in two packages.

---

