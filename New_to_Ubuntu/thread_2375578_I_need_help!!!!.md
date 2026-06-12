---
title: "I need help!!!!"
date: 2017-10-25
forum: New to Ubuntu
---

### Post by johndoe1010101 on 2017-10-25
[IMG]https://imgur.com/a/UovCU[/IMG]Hello, 

I have googled for like 4 hours now and i'm considering paying someone money to fix my ubuntu OS.
Issue: [https://imgur.com/a/UovCU](https://imgur.com/a/UovCU)

I can't use sudo nautilus or anything else it says:
(nautilus:15569): Gtk-WARNING **: cannot open display: :0

---

### Post by oldos2er on 2017-10-25
Just a note,  offers of payment are unnecessary and usually frowned on here. 

Please provide some information e.g. Ubuntu version and hardware specs.

---

### Post by johndoe1010101 on 2017-10-25
Hey, I'm sorry.
I am running Ubuntu 17.10 (16GB Ram, core i7)

---

### Post by chris-lech on 2017-10-25
Try logging on with the Xorg session(click the gear icon on login and select). Then try running nautilus as sudo. I've read that Wayland sessions have issues with running some apps as sudo via the terminal.

---

### Post by deadflowr on 2017-10-25
For nautilus try using this:
[https://ubuntuforums.org/showthread.php?t=2374486&p=13699968#post13699968]("https://ubuntuforums.org/showthread.php?t=2374486&p=13699968#post13699968")
Run ctrl + L to access the Location address bar.

EDIT: sorry forgot about the other part if needed follow this
[https://ubuntuforums.org/showthread.php?t=2375077]("https://ubuntuforums.org/showthread.php?t=2375077")
(In post #1)

---

### Post by ian-weisser on 2017-10-25
It's also discussed in detail at [https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-work-with-wayland](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-work-with-wayland)
That includes how to make GUI applications work with Wayland.

---

### Post by Impavidus on 2017-10-25
As described above. This is an important change with Ubuntu 17.10, which has been released just a week ago, so you can assume that many tutorials you find on the web will be outdated for a while.

The Gtk-WARNING message you got is just what it says to be: a warning message, and gtk produces quite a lot of them. They can usually be ignored – although "cannot open display" may be a real problem.

---

### Post by oldfred on 2017-10-25
Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
sudo is not to be used for GUI applications. current recomedend method is
sudo -H # which keeps /home as location of files.

---

### Post by RobGoss on 2017-10-26
> **johndoe1010101 said:**
> Hey, I'm sorry.
I am running Ubuntu 17.10 (16GB Ram, core i7)

No need to be sorry John your questions are always welcome 

I know sometimes our questions may not get answers as fast as we would like the to but most of the users here at the are volunteers and try to answer the questions as soon as time allows then to

Another tip when posting questions is to use a better title for your post preferably related to your problem

---

