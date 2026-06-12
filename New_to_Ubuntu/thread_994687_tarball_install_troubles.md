---
title: "tarball install troubles"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Gallo_Pinto on 2008-11-27
This is my first go at installing from a .tar.gz archive.

Following a tutorial I found online, I believe I have made the progress of installing check install, extracting the tarball, and now I am supposed to do something like:

```

gallo@GALLO:/media/sdb/Downloads/Linux/Apps/Songbird$ ./configure
bash: ./configure: No such file or directory
```

but that doesn't get me anywhere, just returns that error. I think I must be missing an important step or technicality. Or do I simply have to make that directory manually?

Thanks muchly to anyone who can help me get this installed.
-Gallo

---

### Post by adult swim on 2008-11-27
just double click the songbird file in the extracted folder

---

### Post by Dedoimedo on 2008-11-27
Hello,
Did you check the contents of the extracted archive. Is there a configure file in the directory to begin with?
Dedoimedo

---

### Post by ibutho on 2008-11-27
You don't need to build Songbird because the package they ship has prebuilt binaries. You need to double click on the songbird icon or run ./Songbird from within the extracted directory.

---

### Post by scottmac112 on 2008-11-27
Try this:

sudo chmod 755 'path.to.that.program/configure'
sudo sh './configure'

---

### Post by Gallo_Pinto on 2008-11-27
Okay, it installed and ran, but now I don't know how to run it a second time!!
It's not in my K menu and the command "songbird" does not work. Egad!!

I'd like to ask one more question. here's some more code from Konsole:

first I did
```
tar -xvvf (path to tar package of audacious plugins)
```
then as per instructions found in the extracted files
```
gallo@GALLO:~$ cd /home/gallo/audacious-plugins-1.5.1/
gallo@GALLO:~/audacious-plugins-1.5.1$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
gallo@GALLO:~/audacious-plugins-1.5.1$ make
Makefile:3: buildsys.mk: No such file or directory
make: *** No rule to make target `buildsys.mk'.  Stop.
gallo@GALLO:~/audacious-plugins-1.5.1$
```

Again I have no idea how to proceed. All I'm wanting here is the last.fm audioscrobbler plugin for Audacious, but there doesn't seem to be nay other way of getting it

thanks again

---

### Post by ibutho on 2008-12-01
> **scottmac112 said:**
> Try this:

sudo chmod 755 'path.to.that.program/configure'
sudo sh './configure'

There isn't a ./configure in Songbird. The files provided the the songbird devs are prebuilt binaries.

---

### Post by ibutho on 2008-12-01
[QUOTE=Gallo_Pinto]Okay, it installed and ran, but now I don't know how to run it a second time!!
It's not in my K menu and the command "songbird" does not work. Egad!![/QUOTE]
You need to create a menu or desktop shortcut. It should point to the path where your Songbird executable is located e.g. /home/user/downloads/Songbird/Songbird.

---

