---
title: "HOWTO: run ooPo's gp2x development toolchain installer script"
date: 2006-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by starpause on 2006-04-05
This thread will make more sense if you're familiar with the gp2x. 

The gp2x is an open source handheld (game console) with an ARM processer inside ... more info at the wonderful [gp2x wiki](http://wiki.gp2x.org/wiki/Main_Page). ooPo created an installer script to have you compiling for the gp2x without much sweat. 

**edit:** since i wrote this guide ooPo ran into trouble with bandwith so he is no longer distributing his own toolchains. there are other places you can grab them from. Also, the gp2x scene has been quickly advancing and his toolchain no longer has the best optimized libraries, but getting something compiled with his toolchain is still a reasonable starting point.

1) download gp2xdev-20060525.tar.bz2 under the "Gamepark Holdings GP2X Toolchain Files" header on [ooPo's Consoledev page](http://dev.oopo.net/). extract them with file-roller or your prefered unarchiver.

2) edit your .bashrc and paste the following at the bottom:

```

## GP2XDEV SETTINGS
export GP2XDEV="/usr/local/gp2xdev"
export PATH="$PATH:$GP2XDEV/bin"

```

3) [COLOR="Red"]create the GP2XDEV directory and give yourself access to it[/COLOR] (replace user:user with yourName:yourName) by running this command in the terminal:

```

sudo mkdir /usr/local/gp2xdev && sudo chown user:user /usr/local/gp2xdev

```

4) run the [COLOR="Red"]toolchain[/color] makefile as a regular user, from the terminal (in the directory where you've got the makefile, something like /gp2xdev/toolchain/):

```

make

```

5) run the [COLOR="Red"]libs[/color] makefile as a regular user

```

cd ../libs
make

```

5) after both makefile executions have compleated grab the [tester.tgz example](http://dev.oopo.net/files/tester.tgz) from [ooPo's site](http://dev.oopo.net/) and give it a whirl! the makefile included there will be a good starting point for creating your own projects and compiling your own code.

---

### Post by chadk on 2006-08-10
Where can we get the Gamepark Holdings GP2X Toolchain Files now?  It seems ooPoo isn't offering them any longer.

---

### Post by beowulf62381 on 2006-08-18
try this for the tool chain [http://archive.gp2x.de/cfiles/uploads/Home/gp2x%20-%20Development/Utilities/gp2xdev-20060525.tar.bz2 ](http://archive.gp2x.de/cfiles/uploads/Home/gp2x%20-%20Development/Utilities/gp2xdev-20060525.tar.bz2 )

---

### Post by starpause on 2006-09-25
i think open2x toolchain is the best option now, it's maintained by the guys of the open2x project and has all the latest hardware tweaks in the libraries!

however, for the time being there isn't much information available on installing the open2x toolchain ... so i'll keep this HOWTO updated until i can write one for open2x toolchain :)

---

### Post by Megatog615 on 2006-12-28
Someone should make an Open2x package for Debian/Ubuntu.

---

### Post by starpause on 2006-12-28
> **Megatog615 said:**
> Someone should make an Open2x package for Debian/Ubuntu.

i agree, setting up a toolchain is the most difficult step in gp2x development.

a package would be great, but i'm not familiar with the process of making one. do you know of a howto for that?

---

### Post by Tripmonkey_uk on 2007-01-08
Just thought I'd post to make sure that I get any updates on this thread :)

I'm currently tearing my hair out by trying to get a dev enviroment setup on Ubuntu for the GP2X.

Sods law that I can find tons of good tutorials for Winblows, but all the one's that I've found for Linux seem to have important info missing or simply don't work ](*,) 

I really hope that someone manages to get a Open2x package together for this.

---

### Post by Megatog615 on 2007-01-15
Yea, for a Linux-running device, you'd think there'd be a bit more Linux support? Developers want to set up their environment quickly and easily, for whatever distro they use.

---

### Post by Super Jamie on 2009-09-30
Have any of you guys got ooPo's old toolchain to compile in Ubuntu 9.04?

I've installed build-essential, autotools-dev and libtool, but it fails building collect2.o with

```
In function ‘open’,
    inlined from ‘collect_execute’ at ../../gcc/collect2.c:1580:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [collect2.o] Error 1
make[2]: Leaving directory `/home/superjamie/Desktop/oopo/toolchain/gcc-4.0.2/build-gp2x/gcc'
make[1]: *** [all-gcc] Error 2
make[1]: Leaving directory `/home/superjamie/Desktop/oopo/toolchain/gcc-4.0.2/build-gp2x'
make: *** [/opt/oopo/bin/gp2x-gcc] Error 2
```

Maybe I'd be better to install 6.06 in a VM or something.

---

