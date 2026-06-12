---
title: "need help installing tar.gz files"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by bishopia on 2008-07-30
for some reason, when I try to install gnomad2, it doesn't install the most recent version, 2.9.1. So i'm trying to figure out this package installation process. I figured out how to get into a folder in the terminal, but i am very confused about the whole "./configure make make install" business. when I try to configure, this is what I get. any help for a newb?

```
No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you installed sofware in a non-standard prefix
```

what does this mean?

---

### Post by tuxxy on 2008-07-30
OPen the terminal and navigate to the directory, an example is below,

```
CD /home/user/Desktop/FolderName
```

Then type

```
./configure
```

If there are any error messages then they are because you are missing a required dependency. You can use synaptic to search for this package and install it

If no errors proceed to next command to compile,

```

make
```

then type:

```
sudo make install
```

---

### Post by t0p on 2008-07-30
First of all, you really should try to stick to installing software through Synaptic/apt-get.  Or at least from a .deb file.  But if you really *must* install from source:

1. You need to install the package **build-essential**;

2.  Extract the files from the .tar.gz archive.  Then look in the resulting folder for a file called something like **README** or **INSTALL**.  This will give you installation instructions specific to the app you are dealing with.

If you need more help, don't hesitate to ask!

---

### Post by Tsarj on 2008-07-30
What happens when you type```
locate glib-2.0
```
in the Terminal?

---

### Post by bishopia on 2008-07-30
my real problem is that I cannot drag folders onto my Creative Zen with the version of gnomad installed via synaptic. any ideas?

---

### Post by bishopia on 2008-07-30
to Tsarj, this is what happens:

```
/usr/lib/libglib-3.0.so.0
/usr/lib/libglib-3.0.so.0.1600.3
```

---

### Post by t0p on 2008-07-30
> **bishopia said:**
> my real problem is that I cannot drag folders onto my Creative Zen with the version of gnomad installed via synaptic. any ideas?

Sorry, can't help you with that.  *But* I am pretty sure the errors you got when trying to run the **./configure** command are due to the fact you don't have build-essential installed.  So, type

```
sudo apt-get install build-essential
```

or install it through Synaptic.  Then you should be able to install from your gnomad source file.

---

### Post by Tsarj on 2008-07-30
And when you type...```
sudo aptitude install gnomad2
```

---

### Post by bishopia on 2008-07-30
i got gnomad2 to work. unfortunately, i can't figure out how to make it transfer folders in the newer version. I'm trying to install banshee now. the './configure' worked, but it said this when I'd tried to type 'make':

```
make: *** No targets specified and no makefile found. Stop. 
```

any help?

---

