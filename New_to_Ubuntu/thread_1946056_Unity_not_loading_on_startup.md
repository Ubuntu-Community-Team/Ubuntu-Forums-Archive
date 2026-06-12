---
title: "Unity not loading on startup"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by pras8421 on 2012-03-24
Hi,
The Unity interface is not loading on start up,
Until recently it was loading and this problem has occurred over a past few days.
I only get my wallpaper along with right click options.
I tried with typing "unity --reset" in the terminal but the process never ends(the terminal process,I did wait for 5-10 mins) and If i exit the terminal,while the terminal process is running,the system gets hanged.
I want the unity interface to be loaded at start up..
please help:confused:

---

### Post by MG&amp;TL on 2012-03-24
Okay, we might have a hardware or driver problem. Log into unity2d, then give us the output of the following command from a terminal:

```
/usr/lib/nux/unity_support_test -p
```

Thanks.

---

### Post by pras8421 on 2012-03-24
When i run the command I got the output as follows


```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


```

---

### Post by MG&amp;TL on 2012-03-24
Okay, that should mean you're good to go. I can't think of a reason why it's not running so my advice is to purge, reinstall, and try again.

```
sudo apt-get remove --purge unity
```

Purges unity.

```
sudo apt-get install unity
```

Installs it again.

---

### Post by pras8421 on 2012-03-24
I tried removing it and reinstalling it again but unity side pane and top pane just does not show up.

When I ran the purging command I got the following in treminal
```

prasanna@prasanna-Inspiron-N5110:~$ sudo apt-get remove --purge unity
[sudo] password for prasanna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  unity*
0 upgraded, 0 newly installed, 1 to remove and 287 not upgraded.
After this operation, 2,019 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 141035 files and directories currently installed.)
Removing unity ...
Processing triggers for gconf2 ...

```


when I reinstall it, I got the following in the terminal

```

prasanna@prasanna-Inspiron-N5110:~$ sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unity
0 upgraded, 1 newly installed, 0 to remove and 287 not upgraded.
Need to get 0 B/628 kB of archives.
After this operation, 2,019 kB of additional disk space will be used.
Selecting previously deselected package unity.
(Reading database ... 140976 files and directories currently installed.)
Unpacking unity (from .../unity_3.8.16-0ubuntu1~natty3_amd64.deb) ...
Processing triggers for gconf2 ...
Setting up unity (3.8.16-0ubuntu1~natty3) ...

```


its just that I cant see the side pane and the top pane.I even restarted and the result is same as before(getting only the wallpaper with right click options)..:confused:

---

### Post by MG&amp;TL on 2012-03-24
Okay, install *compizconfig-settings-manager* via the apt-get method and see if the Unity plugin is ticked.

Other than that, I have no idea. Sorry.

---

### Post by alquery on 2012-03-27
I have the same problem. I have tried everything short of a total reinstall, but I cannot get unity to load on startup. I have tried the following:

* resetting unity
* checking ccsm for the unity plugin
* purging and reinstalling unity
* purging *all* compiz settings

Unity still won't load automatically, and I have to manually start it each time I boot my computer. I get this error when I start it, however: unity-panel-service: no process found, then a bunch of junk.

---

### Post by pras8421 on 2012-05-04
Mine was 11.04.I upgraded to 11.10.The problem got cleared.

---

