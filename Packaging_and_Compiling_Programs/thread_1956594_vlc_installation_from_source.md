---
title: "vlc installation from source"
date: 2012-04-11
forum: Packaging and Compiling Programs
---

### Post by greendragons on 2012-04-11
Hello everyone.. 
Im trying to install vlc from source.....
i am getting error even though i've installed lua 5.1... also if i disable lua then getting PKG_CONFIG_PATH not set error... to what location do i need to set this env variable...
```

$>./configure --prefix=/home/kodedozer/Documents/vlc-1.1.13/vlc
checking for LUA... no
configure: WARNING: lua5.1 not found, trying lua >= 5.1 instead
checking for LUA... no
checking lua.h usability... no
checking lua.h presence... no
checking for lua.h... no
checking lauxlib.h usability... no
checking lauxlib.h presence... no
checking for lauxlib.h... no
checking lualib.h usability... no
checking lualib.h presence... no
checking for lualib.h... no
checking for luaL_newstate in -llua5.1 ... no
checking for luaL_newstate in -llua51 ... no
checking for luaL_newstate in -llua ... no
configure: error: Could not find lua. Lua is needed for some interfaces (rc, telnet, http) as well as many other custom scripts. Use --disable-lua to ignore this error.

```

---

### Post by andrew.46 on 2012-04-11
I suspect you could be missing the so-called 'dev' file for lua.You could get a few tips from this page perhaps which could easily be modified to compile the release version:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

You can see on this page that for Oneiric the file is *liblua5.1-0-dev*.

---

### Post by greendragons on 2012-04-11
I tried those steps....
```

checking for XCB_SHM... yes
checking for XCB_XV... no
checking for XCB_XV... no
configure: error: Package requirements (xcb-xv) were not met:

No package 'xcb-xv' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XCB_XV_CFLAGS
and XCB_XV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

I have XCB installed....

---

### Post by andrew.46 on 2012-04-11
Have a look at the method of the guide, it will help :). Search for the appropriate dev file with something like the following:

```
apt-cache search xcb | grep dev
```

and this should give you a start....

---

### Post by greendragons on 2012-04-11
All those missing deps are in ffmpeg what i downloaded and put it local....
but while installing how to link it to those files of ffmpeg... do i need to install ffmpeg also.... 
```

checking for SWSCALE... no
configure: error: Could not find libswscale. Use --disable-swscale to ignore this error. Proper software scaling and some video chroma conversion will be missing.

```
i have this folder in ffmpeg: /home/kodedozer/vlc_build/ffmpeg-0.10.2/libswscale
do i need to change some env vars....?

---

### Post by oldos2er on 2012-04-11
Thread moved to Packaging and Compiling Programs.

---

### Post by MadCow108 on 2012-04-11
the same again, you need libswscale-dev

it would be easier if you just install all at once:

```
sudo apt-get build-dep vlc
```

---

### Post by andrew.46 on 2012-04-11
> **greendragons said:**
> 
i have this folder in ffmpeg: /home/kodedozer/vlc_build/ffmpeg-0.10.2/libswscale
do i need to change some env vars....?

Did you compile this copy of FFmpeg or simply decompress it? To manipulate PKG_CONFIG_PATH have a look at the example here:

[http://www.andrews-corner.org/vlc.html#vlc](http://www.andrews-corner.org/vlc.html#vlc)

Can I ask are you compiling the release version and if so for some special reason?

---

