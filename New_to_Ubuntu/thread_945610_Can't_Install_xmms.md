---
title: "Can't Install xmms"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by LVCNSOL on 2008-10-12
I have tried everything, i downloaded the source extracted it, cd, ./configured it but it says 

> *** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: *** GTK+ >= 1.2.2 not installed - please install first *** 

How would i get GTK exactly?

I then googled for deb packages of xmms, but they needed other dependencies, i tried getting the other dependencies, which conflicted with other dependencies lol

What's the easiest way to get xmms? lol
Its probably so simple but i've gone and complicated it for myself:neutral:

Thanks :)

---

### Post by gn2 on 2008-10-12
Have you tried [Audacious]("http://en.wikipedia.org/wiki/Audacious_Media_Player")?

```
sudo apt-get install audacious
```

---

### Post by WWSmith36 on 2008-10-12
To compile xmms from source you need these dependecies

```
sudo apt-get install autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev libgl1-mesa-dev libglib1.2-dev libgtk1.2-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev libsm-dev libvorbis-dev libxxf86vm-dev libxml-dev libssl-dev build-essential make
```

Download the source from the XMMS website and unpack the .tar.gz:
[http://xmms.org/](http://xmms.org/)

From a terminal move to the newly untarred director and type:
```
./configure --prefix=/usr
```

Compile the code:

```
make
```

Then install:

```
sudo make install
```

Hope this helps

---

### Post by houbysoft.xf.cz on 2008-10-12
Kind of LOL, but, hey, I thought it's in the repos? Or am I wrong? Sorry I'm not on linux right now, but isn't the easiest thing just to type
```

sudo apt-get install xmms

```? It will also install all dependencies it needs automatically...

---

### Post by steveneddy on 2008-10-12
> **gn2 said:**
> Have you tried [Audacious]("http://en.wikipedia.org/wiki/Audacious_Media_Player")?

```
sudo apt-get install audacious
```

this is what I recommend.

XMMS really isn't supported anymore and audacious will use the winamp/xmms skins and sounds great!

---

### Post by hellion0 on 2008-10-12
> **houbysoft.xf.cz said:**
> Kind of LOL, but, hey, I thought it's in the repos? Or am I wrong? Sorry I'm not on linux right now, but isn't the easiest thing just to type
```

sudo apt-get install xmms

```? It will also install all dependencies it needs automatically...Not in Hardy.

The Hardy .deb for XMMS is available on Launchpad, specifically [here](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2) (assuming you're using x86 Ubuntu - other architectures can be navigated to from the page, though). Try to install it with dpkg, install the dependencies with aptitude, and you should be set.

---

### Post by WWSmith36 on 2008-10-12
> What's the easiest way to get xmms? lol
Its probably so simple but i've gone and complicated it for myself

If you have hardy its is not in the repositories and must be compiled from source.  

If your are running gusty, fiesty, or dapper you can get it from the repositories. For gutsy, make sure you enabled the universe repository.

---

### Post by houbysoft.xf.cz on 2008-10-12
> **hellion0 said:**
> Not in Hardy.

The Hardy .deb for XMMS is available on Launchpad, specifically [here](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2). Try to install it with dpkg, install the dependencies with aptitude, and you should be set.

Ah, OK :D

---

