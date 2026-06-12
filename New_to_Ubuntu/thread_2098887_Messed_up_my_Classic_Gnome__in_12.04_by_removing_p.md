---
title: "Messed up my Classic Gnome  in 12.04 by removing python 2.7"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by TooRight on 2012-12-27
After installing ubuntu 12.04 64 bit on a new harddrive for my new computer i was having trouble installing blender 2.49 (old version, but needed for scripts i wanted to use for it). Realized it wouldn't run because my system had too new a version of python for it, so I removed the newer version of python before installing the older python and the libs to go with it... in the process i kind of broke my gnome :O

My Applications menu changed in look and in what each contained... firefox was gone, as was my Terminal, ubuntu software center etc. Luckily I had installed synaptic (which i prefer anyways), so was able to reinstall firefox and python 2.6 (though now after installing the old version of blender i now have python 2.7.3 again -weird), and i used synaptic to install gnome-terminal, so got that back (thank god!!). My problem now is that windows on my screen look rather weird and ugly, not like how they did when i first installed classic (was using Gnome Classic -No Effects)and the Applications menu still shows folders, and a reduced number of icons within those folders... :(

Any ideas on what i broke and how i can get it back and still keep the older version of Blender working?

Thanks in advance :)

---

### Post by TooRight on 2012-12-28
upon rebooting, also realized that i lost my lil "applets" n my windows have reverted to oldddddd look with window minimizers/maximizers etc over on the upper right corner n now i have no MENU at all on my desktop :(

My windows looks like i have Win95 installed, ackkk :O

---

### Post by Yougo on 2012-12-28
it sounds like when you removed python, it pulled a lot op applications with it. it happens when applications depend on the part you removed.

by installing some of those applications back, you also pulled in the latest python again, since these apps need that version.

it probably won't help your blender-script issue, but to install your system back, you can install (or reinstall if it says it's already installed):

ubuntu-desktop (pulls in everything that makes ubuntu look an work like it should)
gnome-session-fallback (this gives you the classic Gnome session, and pulls in everything it needs.)

you can do that in synaptic, or from command line

```

sudo apt-get install [package name]

```
or
```

sudo apt-get install --reinstall [package name]

```


--------------------------------------------------------
as to your blender problem, i'm no blender expert, but from what i unsterstand, you can safely install different python versions alongside eachother
[http://askubuntu.com/questions/38081/how-would-one-install-a-side-by-side-installation-of-python-2-x-and-python-3-x](http://askubuntu.com/questions/38081/how-would-one-install-a-side-by-side-installation-of-python-2-x-and-python-3-x)

as to where to get your particular python version, and how to point blender to the right python, that's another question:-k

---

### Post by vanadium on 2012-12-28
Broken, but not yet to the extend that you cannot log in apparently. I'd start by removing the "offending" version of blender and the incompatible python version you installed. Then, you may try to restore the system by re-installing the "ubuntu-desktop" package (which should take in the correct python version again), and after that, the Gnome desktop environment (which is what is also providing the Gnome classic session).

---

### Post by TooRight on 2012-12-28
Thanks you guys, will give it a try :D wish me luck!! *crosses her fingers

---

### Post by Yougo on 2012-12-28
this thread on linuxquestions.org talks about needing and older version of python for blender, and mentions a startup script for blender that should point to the right python version. 

[http://www.linuxquestions.org/questions/linux-software-2/older-software-version-requires-python-2-5-to-run-926070/](http://www.linuxquestions.org/questions/linux-software-2/older-software-version-requires-python-2-5-to-run-926070/)

i hope it points you in the right direction

---

### Post by TooRight on 2012-12-28
OMGGG, it worked!! Yayyy!! I sooo owe you guys, thank youuu!!


...anddddd... Blender is working as it should too, woo hooo!! :D:D

---

### Post by Yougo on 2012-12-28
good to know it worked out for you :)

i see you found the [solved] button already. pleae take the effort to post your solution for blender and old python versions in your first post, so others may be helped by this too ;)

---

