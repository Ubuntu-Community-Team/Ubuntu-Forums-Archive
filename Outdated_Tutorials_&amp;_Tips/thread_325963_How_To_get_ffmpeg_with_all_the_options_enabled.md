---
title: "How To: get ffmpeg with all the options enabled"
date: 2006-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by patsissons on 2006-12-26
This is a (very) quick tutorial on how to get ffmpeg installed with all the options enabled.  It's really very easy.

first make sure that you have your deb-src entries uncommented in /etc/apt/sources.list  otherwise you won't be able to get the build dependencies.

```

sudo apt-get install build-essential fakeroot
sudo apt-get build-dep ffmpeg
cd /tmp
apt-get source ffmpeg
cd ffmpeg*
DEB_BUILD_OPTIONS=risky fakeroot debian/rules binary

```

This will most likely error quickly, but this is expected.  Look near the top of the build ouptut for a line similar to this:

debian/rules:41: Make sure these packages are installed: liblame-dev libfaad2-dev libfaac-dev libxvidcore-dev

take the packages listed there and install them, as well as their respective libraries (if they aren't already)

```

sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore-dev liblame0 libfaad2-0 libfaac0 libxvidcore4
DEB_BUILD_OPTIONS=risky fakeroot debian/rules binary

```

This will take a little while to compile, but afterwards you will be left with a few fresh new deb's in the parent folder

```

sudo dpkg -i ../*.deb

```



====================================


NOTE: this does not compile with x264 enabled.  If you want x264 you have to do one more step after you download the ffmpeg source package.  You must edit ./debian/rules and add the following lines:
```

weak-build-deps += libx264-dev
confflags += --enable-x264

```
above
```

$(warning Make sure these packages are installed: $(weak-build-deps))

```

---

### Post by erasmo.da.rotterdam on 2007-01-30
Hi!
I need to convert different file formats into flv (mov|avi|wmv -> flv)
Following your instructions I have this configuration (using ffmpeg -version)

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --prefix=/usr
  built on Jan 30 2007 17:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
ffmpeg      CVS
libavcodec  3276800
libavformat 3211520

Before beginning the installation process I've also installed lame-3.97 from sources with --enable-shared

I can produce ogg files from wmv|mov|mpg
but when I try to produce a flv it doesn't work :( 

ffmpeg -i -acodec mp3 31737aaaaacB.mov 31737aaaaacB.flv

"-acodec: I/O error occured
Usually that means that input file is truncated and/or corrupted."

but from the same file I can produce an ogg one...

---

### Post by Hakimio on 2007-05-07
Thank you, **patsissons**! :)

---

### Post by m3alnemer on 2009-05-15
I was following this tutorial, but somewhere somthing stopped working i used [http://ubuntuforums.org/showthread.php?p=7283739#post7283739]("http://ubuntuforums.org/showthread.php?p=7283739#post7283739") to fix it


Thanks ;)

---

