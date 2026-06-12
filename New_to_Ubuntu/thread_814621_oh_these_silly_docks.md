---
title: "oh these silly docks"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-31
since ive been having too many issues just trying docks as i find them does anyone have any suggestions on a good dock. i seriously tried awn and found it a tad sluggish.

---

### Post by Joeb454 on 2008-05-31
There's cairo-dock.

And I've used Kiba-Dock in the past, which was pretty good :) Though you have to compile it from source.

---

### Post by overdrank on 2008-05-31
+1 cairo-dock
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by PatrickMoore on 2008-05-31
seems to be the consensus. im going to try it

---

### Post by Joeb454 on 2008-05-31
It can't hurt to try it ;) You can always uninstall it :)

---

### Post by PatrickMoore on 2008-05-31
any suggestions on the best way to install on a 64 bit system

---

### Post by overdrank on 2008-05-31
> **PatrickMoore said:**
> any suggestions on the best way to install on a 64 bit system

It should work with the debs provided, worked great on my 64bit. :KS

---

### Post by PatrickMoore on 2008-05-31
im going to try now

---

### Post by PatrickMoore on 2008-05-31
am i going to have issues with this running with compiz fusion i seriously spent a  larger part of my day trying to fix that.

---

### Post by Joeb454 on 2008-05-31
Some docks may even require Compiz to be running :)

So basically - no I don't think you'll find any issues - if you do, there'll probably be another dock for you :)

---

### Post by PatrickMoore on 2008-05-31
alright game time. im going to do this ill let you know how it turns out.

---

### Post by PatrickMoore on 2008-05-31
```
patrick@patrick-laptop:~$ autoreconf -isvf && ./configure --prefix=/usr/local && make 
autoreconf: `configure.ac' or `configure.in' is required

```

what should i do? help

---

### Post by Joeb454 on 2008-05-31
I thought there was a .deb for cairo dock?

---

### Post by PatrickMoore on 2008-05-31
> **Joeb454 said:**
> I thought there was a .deb for cairo dock? 

yeah i downloaded both .deb files and installed them in order of the guide with the plugins.

---

### Post by tact on 2008-06-01
> **PatrickMoore said:**
> yeah i downloaded both .deb files and installed them in order of the guide with the plugins.

Not sure what you have done so far..  
If you installed .deb files and they were not from here:
[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14679](http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14679)

I think better you UNINSTALL what you have installed and start over from below.


Cairo-dock needs some bits from the libglitz1 package so first:
```
sudo apt-get install libglitz1
```

Go to the developer's website 
[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14679](http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14679)

Download 
cairo-dock-plug-ins_v1.5.6_i686.deb   and 
cairo-dock_v1.5.6_i686.deb

Then install the dock first...  (double click on cairo-dock_v1.5.6_i686.deb)

Then the plug-ins (double click on cairo-dock-plug-ins_v1.5.6_i686.deb)

Then you should be good to go.  First time running do it thru a terminal so you can see if there are any errors.
```
cairo-dock
```

If everything is well exit or close the terminal window.   Press ALT+F2 and type cairo-dock to get it running again and not have to have a terminal window open.

If you want it to start on system startup - do the usual...  add "cairo-dock" in System>Preferences>Sessions.

---

### Post by PatrickMoore on 2008-06-01
i did what you said as far as teh libglitzl the terminal stated that i had it installed

```
patrick@patrick-laptop:~$ sudo apt-get install libglitz1
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglitz1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i installed cairo dock and then the plugins

 typed cairo dock in terminal

```
patrick@patrick-laptop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
patrick@patrick-laptop:~$ 

```

---

### Post by PatrickMoore on 2008-06-01
its inmy applications. but nothing starts up

---

### Post by tact on 2008-06-01
```
patrick@patrick-laptop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
patrick@patrick-laptop:~$ 

```[/QUOTE]

Is libglitz-glx1 installed?
```
sudo apt-get install libglitz-glx1
```

---

### Post by PatrickMoore on 2008-06-01
```
patrick@patrick-laptop:~$ sudo apt-get install libglitz-glx1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglitz-glx1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
looks like it...

 i got the same error message

---

### Post by PatrickMoore on 2008-06-01
i purged libglitzl and reinstalled now all im getting is

```
patrick@patrick-laptop:~$ cairo-dock
bash: /usr/bin/cairo-dock: No such file or directory

```

---

### Post by tact on 2008-06-01
> **PatrickMoore said:**
> i purged libglitzl and reinstalled now all im getting is

```
patrick@patrick-laptop:~$ cairo-dock
bash: /usr/bin/cairo-dock: No such file or directory

```

don't know what to say except purge everything to do with cairo-dock

- in synaptic search for and "remove completely" cairo-dock and plug-ins
(or sudo apt-get purge cairo-dock cairo-dock-plug-ins)

Then start from beginning....
- install libglitz1 and libglitz-glx1
- install the dock deb
-  intall the plugins deb

---

### Post by PatrickMoore on 2008-06-01
its still not working/ i dont know maybe i should try something else

---

### Post by sayakb on 2008-06-01
```
sudo apt-get install cairo-dock
sudo apt-get install avant-window-navigator
```

Avant window navigator(AWN) is yet another beautiful dock..

---

### Post by spiderbatdad on 2008-06-01
when you started this thread, I read along, earlier, and thought I would give it a try. It a installed and ran great. I started with:
```
sudo apt-get install libcairo2 xcompmgr
```
Then went to the download site got the cairo deb and the plugins deb...installed them in order.

Pressed alt+f2 and ran xcompmgr. Then opened a terminal and ran cairo-dock. Worked like a charm...selected a theme...played with some settings...etc.

Later discovered a launcher under the system tools menu. Most of the themes auto hide at the bottom center of the screen. The Cobalt theme places a transparent arrow there as an indicator...the others I tried would have been impossible to find, had I not tried the cobalt first...by luck. Right clicking on the dock opens an incredible configuration editor.

---

### Post by saratchandra on 2008-06-01
> **PatrickMoore said:**
> i did what you said as far as teh libglitzl the terminal stated that i had it installed

```
patrick@patrick-laptop:~$ sudo apt-get install libglitz1
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglitz1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i installed cairo dock and then the plugins

 typed cairo dock in terminal

```
patrick@patrick-laptop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
patrick@patrick-laptop:~$ 

```

I get the same error too and I'm running amd64 hardy

---

### Post by doorknob60 on 2008-06-01
Did you install 32 bit debs? If so, you'll need to install the ia32libs package. If there's no 64 bit debs, i'd just advise that you compile it from source.

---

### Post by spiderbatdad on 2008-06-01
> **saratchandra said:**
> I get the same error too and I'm running amd64 hardy

I also got that error but it was safely ignored. The dock still ran perfectly. It does not have to be launched from the terminal. You do have to have a composite windows manager running. Like I said I started xcompmgr first.

---

### Post by saratchandra on 2008-06-01
> **spiderbatdad said:**
> I also got that error but it was safely ignored. The dock still ran perfectly. It does not have to be launched from the terminal. You do have to have a composite windows manager running. Like I said I started xcompmgr first.

I have xcompmgr running. Should I install the plugins for it to work?

---

### Post by spiderbatdad on 2008-06-01
I would say yes. post #24 explained what I did. It was my first time trying cairo-dock. I did install the plugins...It looks like that is where the integration files are and themes.

---

### Post by IanW on 2008-06-01
No need to compile from source for 64-bit, here's the relevant page of the Cairo-Dock wiki:-
[Installing Cairo-Dock in a 64-bit system.]("http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en")

---

### Post by saratchandra on 2008-06-01
> **spiderbatdad said:**
> I would say yes. post #24 explained what I did. It was my first time trying cairo-dock. I did install the plugins...It looks like that is where the inintegrationtegration files are and themes.

Still doesn't work :(

> **IanW said:**
> No need to compile from source for 64-bit, here's the relevant page of the Cairo-Dock wiki:-
[Installing Cairo-Dock in a 64-bit system.]("http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en")

I already installed all the required libs and getlibs is not working anymore

---

