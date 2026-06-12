---
title: "error facing in installing wine in ubuntu 8.10 intrepid ibex"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by rkrajhan on 2011-11-09
i tried to install wine using sudo apt command like given below

$ sudo apt-get install wine

but it is showing the following error message & i could not proceed further.

E: Type 'adding' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.

please help me out i want to install wine,(its last stable version).

---

### Post by sadaruwan12 on 2011-11-09
Welcome to the forum, It seems like your sources.list file has an error in line 45 once you correct it.

To do that run this in the terminal or press Alt+F2 and type the below command.

```
gksudo gedit /etc/apt/sources.list
```

Press enter.

In the opened file go to the line 45 and see if theres any word starts with adding or better off paste the content here and we'll tel you what to do.

But my friend why are you using a very old and discontinued product as Ibex get a more resent copy of the distro 'cos the support and the update for the particular distribution are no more.

---

### Post by Enigmapond on 2011-11-09
Right...you need to update to 10.04 or higher. Support for your distro stopped some time ago.

---

