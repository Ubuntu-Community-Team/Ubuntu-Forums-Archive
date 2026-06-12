---
title: "Altered totem source, installed, wont run"
date: 2008-12-14
forum: Programming Talk
---

### Post by hapveg on 2008-12-14
Ubuntu 8.10, Totem 2.24.3

This is my first try altering the source code of anything in ubuntu, so I'm probably making a newbie mistake, but I can't seem to see it.

As a project I want to download the Totem source and alter the mouse wheel to only jump back 3 seconds.

I've downloaded the totem source from [http://projects.gnome.org/totem/](http://projects.gnome.org/totem/)

I've altered the source to only jump back 3 seconds instead of 5.

I've installed a bunch of required packages.

I've run ./configure, make, make check and sudo make install

Now when I double click a movie my mouse pointer turns to the loading pointer for about 10 seconds, then returns to normal.

Totem doesn't start though. I've tried running it through the Applications menu, and the same thing happens.

What am I doing wrong?

---

### Post by Tim Sharitt on 2008-12-14
Try to run it from a terminal and see what (if any) error messages it gives you.

---

### Post by hapveg on 2008-12-14
Running totem from a new shell (in my home directory) causes a normal, unmodified Totem to run.

Running 'totem' in /usr/local/bin, or running 'totem' in the directory I was running config / make / make install from gives the following error:

totem: error while loading shared libraries: libbaconvideowidget.so.0: cannot open shared object file: No such file or directory

I'm not having much luck solving this myself, so advice is appreciated.

---

### Post by Tim Sharitt on 2008-12-15
I'm not real sure what to tell you. I don't know what you could have changed to cause that problem. I would think that configure would check for dependencies and either throw an error or configure without the library. 
However, if it is something built with totem, there may have been a problem with the installation.
Have you tried to run ./totem inside the src folder in the totem directory (ex. totem-(version)/src)? I built it my self and it ran from there fine.

---

### Post by hapveg on 2008-12-15
> **Tim Sharitt said:**
> Have you tried to run ./totem inside the src folder in the totem directory (ex. totem-(version)/src)?
Thank you Tim, very greatly.

That worked perfectly.

---

### Post by Tim Sharitt on 2008-12-15
If it works fine from there, you may have had a problem with make install.

---

### Post by Psyphre on 2009-02-16
Hi,

I too can confirm I get this problem aswell when compiling from source.
It has nothing to do with altering the source code because I never touched mine, I just wanted to compile it to practice my experience with compiling.

Running ./totem in the src folder works, but otherwise (just like original poster) I can't run totem with the same message:

totem: error while loading shared libraries: libbaconvideowidget.so.0: cannot open shared object file: No such file or directory

---

### Post by castrojo on 2009-02-16
Do you have all the build dependencies installed? Do a "sudo apt-get build-dep totem" to make sure they're installed.

---

### Post by bruce89 on 2009-02-16
Perhaps you are not adding a [FONT="Monospace"]sudo[/FONT] to [FONT="Monospace"]make install[/FONT]. Failing this, I find [FONT="Monospace"]sudo ldconfig[/FONT] fixes this sort of thing.

---

### Post by slavik on 2009-02-17
if it can't find a library, first step is to do ldconfig, after that, find the package where the file comes from and see if it's installed and if the file is on your system

---

### Post by Psyphre on 2009-02-17
thanks for the reply.

whiprush: I tried that and it installed a few things, then i tried to configure, make and make install again. It still didnt work. Same error.

The only way to activate totem is to go to the src folder and manually start it there. What is odd though, is that when I played a movie it asked to install the codec for it. I did and was suprised to find that it actually fixed the problem. Now I can start totem normally and it works fine.

That was on my laptop (which I use to mess around with), so now I'm doing it on my desktop  but I get the same problem. Since all the codecs are already installed I can't use that same trick to fix it. :(

Bruce and slavik:
I did use sudo with make install so its not that.
What is ldconfig? and how do I use it?

Thanks again.



EDIT: I just typed in sudo ldconfig and it magically fixed it all. I dont even know how it did it. Thank you so much!
But just out of curiousity what did it do? It seems like a really useful tool.

---

### Post by johnl on 2009-02-17
> **Psyphre said:**
> 
EDIT: I just typed in sudo ldconfig and it magically fixed it all. I dont even know how it did it. Thank you so much!
But just out of curiousity what did it do? It seems like a really useful tool.

It has to do with shared library versions.

Let's have an example.  Suppose I have a library 'libfoobar.so.3.1'; That is, version 3 revision 1 of libfoobar.so (in actuality, this version scheme can be more complicated)

so in /usr/lib/ I have libfoobar.so.3.1.  Any program compiled against libfoobar version 3 rev 1 can find it and use it, no problem.

But suppose I compiled a program against version 3 rev 0.  It should work fine with ANY revision of libfoobar version 3.  So I need to have in /usr/lib a libfoobar.so.3

Open up your /usr/lib and do a ls -l and you can see how this is resolved; you might have:

libfoobar.so.4.2 (real file)
libfoobar.so.3.1 (real file)
libfoobar.so.3 (link to libfoobar.so.3.1)
libfoobar.so.4 (link to libfoobar.so.4.2)
libfoobar.so (link to libfoobar.so.3.1 OR libfoobar.so.4.2)

What 'ldconfig' does is builds these soft links to different versions of libraries so that programs can look for generic versions rather than the specific version you have installed.  

Does that make sense?

---

### Post by Psyphre on 2009-02-17
> **johnl said:**
> It has to do with shared library versions.

Let's have an example.  Suppose I have a library 'libfoobar.so.3.1'; That is, version 3 revision 1 of libfoobar.so (in actuality, this version scheme can be more complicated)

so in /usr/lib/ I have libfoobar.so.3.1.  Any program compiled against libfoobar version 3 rev 1 can find it and use it, no problem.

But suppose I compiled a program against version 3 rev 0.  It should work fine with ANY revision of libfoobar version 3.  So I need to have in /usr/lib a libfoobar.so.3

Open up your /usr/lib and do a ls -l and you can see how this is resolved; you might have:

libfoobar.so.4.2 (real file)
libfoobar.so.3.1 (real file)
libfoobar.so.3 (link to libfoobar.so.3.1)
libfoobar.so.4 (link to libfoobar.so.4.2)
libfoobar.so (link to libfoobar.so.3.1 OR libfoobar.so.4.2)

What 'ldconfig' does is builds these soft links to different versions of libraries so that programs can look for generic versions rather than the specific version you have installed.  

Does that make sense?

Ya actually that does. Took a couple re-reads of your post but I get it now. Thanks for educating me.

---

