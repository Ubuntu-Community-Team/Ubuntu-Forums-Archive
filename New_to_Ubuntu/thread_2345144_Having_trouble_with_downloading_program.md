---
title: "Having trouble with downloading program"
date: 2016-11-30
forum: New to Ubuntu
---

### Post by mexikyan on 2016-11-30
So i am trying to download the processing IDE [https://processing.org/](https://processing.org/)

and i download it and unzip it but i do not know how to make a desktop icon for it or run it, any help? And do linux users ussally even make desktop icons? Like do they just run them from the terminal? What is the best option here?

---

### Post by TheFu on 2016-12-01
Ubuntu and Linux users in general, use the package manager to load and maintain programs. We don't download setup.exe or ZIP files. Generally, we don't download source files and compile tools ourselves.  Of course, Linux is flexible enough that you **can** do these things, but when you go that way, then you are in a different realm than "average Linux Desktop users."

The "best option" is highly subjective.  

The best option is to find a tool that is well used and included in the normal software repos. Then use any of the well-know package managers supported by Ubuntu to install and maintain the software.

2nd best option is to find a **trusted PPA** with the tool you like/want and add that to your repo list - understand that this PPA can install anything and run whatever they want at that time, effectively pwn'ing your box, hence why it needs to be trusted.

3rd best option is to find a trusted package maker and get the .deb file for the tool you like/want.  Understand that doing this will probably lock dependency for some core tools/libraries and may make this system un-maintainable in a few months. That is the risk.

4th best option is to get the source code, build, configure and install it. You access all maintenance going forward. The OS will not patch and libraries it depends on might change underneath the program(s) installed this way.  The code maintainer should provide startup and stop and status tools and if it is a GUI app, she should provide an icon and desktop file which will be added to the menu system and run. If that isn't the situation, complain to the group producing the code.

IMHO.  If you are really new to Linux, getting some background first would be smart: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - the first few links (about 45 min of reading) will really save you time.

If you normally use a different OS, it seems that tool works on all the major OSes. 

Ok ... so you can make a .deskop file for any program. There are thousands of examples on your Linux box right now.  Find them with any file system search tool you like.  I'm a CLI guy (it works without a GUI and on servers worldwide), so I'd do **find /usr ~/ -type f -iname \*desktop** - on my minimal desktop, 3675 ".desktop" files were found. They are just text. Copy one, edit it for your needs.  Icons are just .png files and stored in different sizes under /usr/share/icons/ somewhere.  BTW - [https://github.com/processing/processing/tree/master/build/linux](https://github.com/processing/processing/tree/master/build/linux) seems to have the .desktop file and points to /opt/processing/lib/icons/pde-256.png for the icon.

---

### Post by MrManican on 2016-12-01
There is also a great tutorial walk through for setting up Processing in Linux. You can check it out [here]("https://processing.org/tutorials/gettingstarted/"). As TheFu noted, making a .desktop file shouldn't be a problem and their instructions are pretty good. Good luck! Stop back if you have any other questions or concerns!

---

### Post by mexikyan on 2016-12-07
So I have tried EVERYTHING from every website I have looked at about installing the processing ide on ubuntu and I am getting no where. Any help?

---

### Post by QIII on 2016-12-07
Hello!

What is "the processing ide"?

Could you tell us what "everything" you tried so we don't try to get to to do that again?

Thanks.

---

### Post by usrnameistaken on 2016-12-15
No idea what is "installing the processing ide", more specific please.

---

### Post by lisati on 2016-12-15
Threads merged, which might help alleviate the bafflement of those who responded to the second thread.

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

