---
title: "Install software"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by cronin4392 on 2008-05-18
im trying to install Launch Box.
i went here:
[http://developer.imendio.com/projects/gnome-launch-box](http://developer.imendio.com/projects/gnome-launch-box)
downloaded the tar.gz and unzipped it. i then opened it up and read the INSTALL. the INSTALL told me to:
" 1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself."

when i do this all of this comes up:

"checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details."

what do i do? i dont really understand linux that well and how installing things works. it seems weird to me that somethings install through a file (like an .exe), others you install through terminal and others through the add/remove software. WHY ARENT THEY ALL JUST THE SAME!

---

### Post by tramir on 2008-05-18
First, type this into terminal:

```
sudo apt-get install build-essential
```

In general, what you need to do to install software from source is:

```
./configure
make
sudo make install
```

An alternative to the last command, which I personally prefer, is:

```
sudo checkinstall -D
```

This creates a package that you can uninstall from Synaptic later on. But for that, you need to install checkinstall--either from Synaptic or from terminal:

```
sudo apt-get install checkinstall
```

Finally, sometimes you need to install extra development libraries. Just let us know what ./configure spits out aftere you install build-essential.

Edit: If you still get the error about not being able to create executables, try installing libc6-dev-i386 (Syanptic or again sudo apt-get install ...)

---

### Post by SunnyRabbiera on 2008-05-18
remember it does say its experimental so keep on your toes.

---

### Post by jcwmoore on 2008-05-18
gnome launch box is available in the repositories, you could just install it via Synaptic, if you wish to build from source follow the advice above.

---

### Post by cronin4392 on 2008-05-18
> **tramir said:**
> First, type this into terminal:

```
sudo apt-get install build-essential
```

In general, what you need to do to install software from source is:

```
./configure
make
sudo make install
```

An alternative to the last command, which I personally prefer, is:

```
sudo checkinstall -D
```

This creates a package that you can uninstall from Synaptic later on. But for that, you need to install checkinstall--either from Synaptic or from terminal:

```
sudo apt-get install checkinstall
```

Finally, sometimes you need to install extra development libraries. Just let us know what ./configure spits out aftere you install build-essential.

Edit: If you still get the error about not being able to create executables, try installing libc6-dev-i386 (Syanptic or again sudo apt-get install ...)


No package 'gtk+-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libgnomeui-2.0' found
No package 'libgnome-menu' found
No package 'gnome-desktop-2.0' found
No package 'libebook-1.2' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LB_CFLAGS
and LB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


thats what i got once i did the first thing you said. n dude i lost you after the first thing you said lol. ive never used linux before and have no idea what your talking about.

---

### Post by SunnyRabbiera on 2008-05-18
> **jcwmoore said:**
> gnome launch box is available in the repositories, you could just install it via Synaptic, if you wish to build from source follow the advice above.

have you tried it might I ask?
I dont find this sort of thing useful but I am wondering if you have experience with it.

---

### Post by mkoehler on 2008-05-18
Let's just say that, if you want to compile this package from source (as you're doing right now), then you're going to need to install a lot of packages (and -dev packages).  Otherwise, you can simplify the process by installing from synaptic like others have suggested.

---

### Post by SunnyRabbiera on 2008-05-18
right, though I might give this thing a shot myself... I like experimenting and its good to know its in the repositories.

---

### Post by tramir on 2008-05-18
> **cronin4392 said:**
> No package 'gtk+-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libgnomeui-2.0' found
No package 'libgnome-menu' found
No package 'gnome-desktop-2.0' found
No package 'libebook-1.2' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LB_CFLAGS
and LB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


thats what i got once i did the first thing you said. n dude i lost you after the first thing you said lol. ive never used linux before and have no idea what your talking about.

:) Unfortunately, installing from source is more complicated than just downloading stuff and then running "setup.exe" :) The easiest thing, as suggested above, is to check if the program isn't already in the repositories (in Synaptic). There's also getdeb.net, which has a pretty good selection of updated packages, until they make it in the official repository. 

Anyway, those messages above tell you that you need to install a couple of packages that you don't have yet. Probably the easiest thing to do is to open Synaptic and go through each one of those, one by one. You probably need to add a "lib" in front of the names too. So, for example, search in Synaptic for "libgtk" and select for installation the package that ends with "-dev". Do the same for all of those packages, Apply (to install them) and the try ./configure again.

As you can see, it's a lot of work, so I really suggest installing the package that is already in Synaptic. Especially if you haven't done this before.

---

### Post by cronin4392 on 2008-05-18
> **jcwmoore said:**
> gnome launch box is available in the repositories, you could just install it via Synaptic, if you wish to build from source follow the advice above.

ok thanks that worked, but where do i find it now? i tried searching for it and couldnt find it. this happened to me with other apps. is there a place where i can see all my installed apps and launch them? the app. menu button doesnt show everything

---

### Post by SunnyRabbiera on 2008-05-18
> **cronin4392 said:**
> ok thanks that worked, but where do i find it now? i tried searching for it and couldnt find it. this happened to me with other apps. is there a place where i can see all my installed apps and launch them? the app. menu button doesnt show everything

well I installed it too and also have no menu entry, its possible you have to create a luncher for it but let me toy around with that bit before giving you instructions.

---

### Post by jcwmoore on 2008-05-18
[http://tuxenclave.wordpress.com/2007/09/25/gnome-launch-box-quicksilver-for-linux/]("http://tuxenclave.wordpress.com/2007/09/25/gnome-launch-box-quicksilver-for-linux/")

looks like it runs from command line...
so look at this guide (towards the bottom) to see how to run it and how to run it by default (if you desire) when you log in

---

### Post by SunnyRabbiera on 2008-05-18
> **jcwmoore said:**
> [http://tuxenclave.wordpress.com/2007/09/25/gnome-launch-box-quicksilver-for-linux/]("http://tuxenclave.wordpress.com/2007/09/25/gnome-launch-box-quicksilver-for-linux/")

looks like it runs from command line...
so look at this guide (towards the bottom) to see how to run it and how to run it by default (if you desire) when you log in

Nono, I was able to create a launcher.
To thre original poster, here is how to create a launcher to this application in your menus:
First go up to you menu and right click on it and select "edit menu's"
after that go to a catagory, to make it simple go to the system tools section and click on it then hit the bottom marked "new item"
For the name type in "Gnome Launch Box"
and then go down to the "browse" button next to the box that says "command" next to it.
then another window will pop up and go to filesystem
then to usr
then to bin and scroll down to "gnome-launch-box"
click it and then click "open"
you now have a launcher in your menu :D

Not all applications will appear in the menu's sometimes, it can be testy.

---

### Post by cronin4392 on 2008-05-19
ok thanks I'll try it once I get home

---

