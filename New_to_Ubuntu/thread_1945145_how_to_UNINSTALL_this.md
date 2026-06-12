---
title: "how to UNINSTALL this?"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by twocorners on 2012-03-22
i followed this tutorial >>>  [http://www.youtube.com/watch?v=nBRdSQh-AKQ](http://www.youtube.com/watch?v=nBRdSQh-AKQ)  to make recordmydesktop able to pick up sound from the desktop. it didn't work, but i've figured out a workaround for what i needed it for, so i'd like to undo the process because 1,073kB sounds like a lot of space to be taken up. :S this is what showed up in the terminal, if it helps any.  i'm using ubuntu 10.04. 

homeskillet@SoulsEntitled:~$ sudo apt-get install pavuctrl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pavuctrl
homeskillet@SoulsEntitled:~$ sudo apt-get install pavucontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-34 linux-headers-2.6.32-34-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglademm-2.4-1c2a
The following NEW packages will be installed:
   libglademm-2.4-1c2a pavucontrol
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 143kB of archives.
After this operation, 1,073kB of additional disk space will be used.
Do you want to continue [Y/n]? yes
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libglademm-2.4-1c2a 2.6.7-2build1 [21.8kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe pavucontrol 0.9.9-1 [121kB]
Fetched 143kB in 3s (41.3kB/s)             
Selecting previously deselected package libglademm-2.4-1c2a.
(Reading database ... 364193 files and directories currently installed.)
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2build1_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.9-1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers  for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up libglademm-2.4-1c2a (2.6.7-2build1) ...

Setting up pavucontrol (0.9.9-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by winh8r on 2012-03-22
To remove it 

```
sudo apt-get remove pavucontrol --purge
```

> because 1,073kB sounds like a lot of space to be taken up.

That is just over 1MB, that is not a lot of space

from Wikipedia:

> 1 kilobyte: (very) short story
2 kilobytes: typewritten page
10 kilobytes: page out of an encyclopedia

---

### Post by Frogs Hair on 2012-03-22
```
ldconfig deferred processing now taking place
``` This would indicate the program is being setup . Is it stuck at that point ? After installation the following command would remove the program.```
sudo apt-get remove pavuctrl
```

---

### Post by twocorners on 2012-03-22
@ frog's hair :  that's as far as it went. maybe i didn't wait long enough? i'll try again. :)
@ winh8r : haha thanks.  i was fooled by the number itself.

---

### Post by winh8r on 2012-03-22
It will return to a command prompt when it is finished installing.

Just give it time.

As for the numbers, well, easy mistake to make when you see things being mentioned in thousands, I suppose!!!!


Good Luck

---

### Post by twocorners on 2012-03-22
hi again! it turns out everything was fine, i just needed to go to volume control and change the settings. thanks for the help! =D

---

