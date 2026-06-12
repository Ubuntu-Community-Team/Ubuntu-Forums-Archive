---
title: "Install Popcorn Time 3.2 issues"
date: 2015-03-08
forum: New to Ubuntu
---

### Post by furioususer on 2015-03-08
Hi, 

**I want to install Popcorn 3.2 but I am having issues. **
I go to the site [http://popcorn-time.se/](http://popcorn-time.se/) and download 3.2 for Linux users. I download the file and extract it, out comes three files that I don't know what to do with exactly. I can't open it like I normally do (either it opens through software center or I can execute file as program). 

So I googled and found the following suggestions: 
 Run in terminal:
sudo add-apt-repository ppa:webupd8team/popcorntime
sudo apt-get update
sudo apt-get install popcorn-time

It went great! But... the version that was installed was 3.1, not 3.2.  

[B]What do I do? How can I upgrade to 3.2? Can I use the file from popcorns own site or is there some alternative?

[/B]Btw, I am running Ubuntu 14.04 LTS. 64-bit.

---

### Post by mc4man on 2015-03-08
The ppa has version 3.7.2,  why do you think it's 3.1? It actually doesn't contain popcorn, just downloads & installs from here via a script  - 
[https://popcorntime.io/](https://popcorntime.io/)

(- the 3.2 version on the popcorn website you linked  is old & won't work in 14.04, uses old libudev version

---

### Post by furioususer on 2015-03-08
I'm sorry, you're absolutely right! It is 3.7.2 - don't know why I wrote anything else.

Anyway, [https://popcorntime.io/](https://popcorntime.io/) is another group that develops the program as I understand it, and it is the least favorite one. Why? Because the 3.2 version from the .se site has free built-in VPN, the one from .io site doesn't.
 
Are you saying that I can't use the 3.2 version from the .se site on my ubuntu 14.04? :/

---

### Post by mc4man on 2015-03-08
> **jhf85 said:**
> I'm sorry, you're absolutely right! It is 3.7.2 - don't know why I wrote anything else.

Anyway, [https://popcorntime.io/](https://popcorntime.io/) is another group that develops the program as I understand it, and it is the least favorite one. Why? Because the 3.2 version from the .se site has free built-in VPN, the one from .io site doesn't.
 
Are you saying that I can't use the 3.2 version from the .se site on my ubuntu 14.04? :/

Out of the box no, it was built & consequently links to an older version of libudev (- wants libudev.so.0 while 14.04 has libudev1, ie.  libudev.so.1 which links to actual .so, libudev.so.1.3.5

To see - unpack Popcorn-Time-  cd to the extracted folder & run - 

```
./Popcorn-Time

```
should produce this error or similar - 
> ~/Downloads/Popcorn-Time-linux64$ ./Popcorn-Time
./Popcorn-Time: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory
Likely that version would work in 12.04

---

### Post by furioususer on 2015-03-08
So in other words it's popcorn from the .io site or nothing at all (alt. stick to the &#8203;3.7.2 version[COLOR=#000000])[/COLOR]?

---

### Post by mc4man on 2015-03-08
> **jhf85 said:**
> So in other words it's popcorn from the .io site or nothing at all (alt. stick to the &#8203;3.7.2 version[COLOR=#000000])[/COLOR]?
I'd say so. Sometimes a newer .so can be used by creating a symlink using the old name. Or again sometimes one can get the older .so, put it in the apps folder  & preload it at run time. 
So tried both ways here. While that did allow the 3.2 version to open it errors &   hangs on "INFO:simple_index_file.cc(437)] Simple Cache Index is being restored from disk."

Ex.
> ~/Downloads/Popcorn-Time-linux64$ export LD_PRELOAD='/home/doug/Downloads/Popcorn-Time-linux64/libudev.so.0' 
doug@doug-Lenovo-IdeaPad-Y510P:~/Downloads/Popcorn-Time-linux64$ ./Popcorn-Time
[6980:0308/211932:INFO:gpu_info_collector_x11.cc(80)] NVCtrl extension does not exist.
[6980:0308/211933:WARNING:simple_index_file.cc(338)] Could not map Simple Index file.
[6980:0308/211933:INFO:simple_index_file.cc(437)] Simple Cache Index is being restored from disk.

libudev has changed a fair bit since Ubuntu used libudev0 so don't see any solution for that  until the 3.2 site rebuilds,  if they ever do..

---

