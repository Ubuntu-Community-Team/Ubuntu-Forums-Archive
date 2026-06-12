---
title: "Unable to compile mxe for 32bit win"
date: 2016-09-25
forum: Programming Talk
---

### Post by dsbig on 2016-09-25
Using Ubuntu 14.04.4 64bit and compiling mxe. I tell it to make i386 for 32bit windows. But it keeps doing the 64bit instead. I change the setting file to i386 and it still makes the other one. I download all the dependency and it still does it.

---

### Post by cariboo on 2016-09-26
Moved to programming, as you may get help quicker here.

---

### Post by spjackson on 2016-09-26
You've not given us very much to go on there. See [http://mxe.cc/#requirements-debian](http://mxe.cc/#requirements-debian)
```

apt-get install g++-multilib libc6-dev-i386

```
Did you do that?

---

### Post by dsbig on 2016-09-26
yeah sorry I was at work typing the post through my phone and needed to clock into work......

so more information

I already ran 
apt-get install g++-multilib libc6-dev-i386along with others 

and I need mxe to compile [COLOR=#242729][FONT=Arial]i686-w64-mingw32-gcc

and I followed this 

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Targets can also be specified on the command line. By default, only i686-w64-mingw32.static is built, but you can build your toolchain(s) of choice with:[/FONT][/COLOR]
make MXE_TARGETS='x86_64-w64-mingw32.static i686-w64-mingw32.static'[COLOR=#000000][FONT=&amp]and changed it to this 

[/FONT][/COLOR]
make MXE_TARGETS='i686-w64-mingw32.static'[COLOR=#000000][FONT=&amp]and this
or by adjusting the MXE_TARGETS variable in settings.mk.

and still makes x86_64-unknown-linux-gnu

 seems its having trouble detecting the system?

could it be because Im on ubuntu 14.04 LTS?

I had it working before. but that was on ubuntu 16 LTS,and I couldnt get my AMD 390x to work, and then also found out I had the 32bit version of ubuntu installed(which means it wasnt using all the systems memory. so I switched to ubuntu 14.04 64bit to get my amd card working and for the system memory.

am I right in assuming that x86_64-unknown-linux-gnu would only make 64bit exe? 

and now have to figure out why this madness is happening to me....



[/FONT][/COLOR]

---

### Post by andrew.46 on 2016-11-18
Perhaps go back a step and start with a basic installation. You may need to install some extras on Ubuntu:


```

sudo apt-get install \
    autoconf automake autopoint bash bison bzip2 flex gettext\
    git g++ gperf intltool libffi-dev libgdk-pixbuf2.0-dev \
    libtool libltdl-dev libssl-dev libxml-parser-perl make \
    openssl p7zip-full patch perl pkg-config python ruby scons \
    sed unzip wget xz-utils


```

Then install MXE from git:

```

cd $HOME
git clone https://github.com/mxe/mxe.git

```

Then change to the newly created directory and install a basic toolchain for building 32bit, static libraries:

```

cd $HOME/mxe
make gcc

```

This should definitely be enough to get you started...

---

