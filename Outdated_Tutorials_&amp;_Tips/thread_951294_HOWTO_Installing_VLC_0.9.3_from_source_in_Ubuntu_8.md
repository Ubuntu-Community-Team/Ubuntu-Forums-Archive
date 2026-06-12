---
title: "HOWTO: Installing VLC 0.9.3 from source in Ubuntu 8.04 Hardy Heron"
date: 2008-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Neo_The_User on 2008-10-18
**_PLEASE NOTE: THIS IS VERY SIMILAR TO [http://ubuntuforums.org/showthread.php?t=924887](http://ubuntuforums.org/showthread.php?t=924887) EXCEPT THIS IS A MUCH MORE CLEAN GUIDE MAKING IT SIMPLY BETTER ALONG WITH NO VIOLATIONS OF THE GNU LICENSE! I DEEPLY APOLOGIZE FOR NOT FOLLOWING THROUGH WITH THE GNU PUBLIC LICENSE!_**

You might be tired of vlc 0.9.4 and up with the extended video pop-up instead of built-in embedded video with no external screen. It is simple, quick, and easy to change it all back the way it was. Follow my numbered instructions in this little step-by-step guide on compiling, making, and running VLC 0.9.3 the way it was. **_DO NOT_**type what is in parenthesis :lolflag:

(I am currently building a debian package for vlc 0.9.3)

1.) Download the tar.bz2 source for vlc 0.9.3 here:

[http://download.videolan.org/pub/videolan/vlc/0.9.3/vlc-0.9.3.tar.bz2](http://download.videolan.org/pub/videolan/vlc/0.9.3/vlc-0.9.3.tar.bz2)

2.) Extract the folder within the tar.bz2 file to a directory of your choice. :guitar:

3.) Open up a Terminal

```

sudo apt-get build-dep vlc

sudo apt-get install cvs build-essential subversion git git-core automake1.9 libtool libgcrypt-dev libfaad-dev libtwolame-dev libqt4-dev libjack-dev libxpm-dev libcddb2-dev liblua5.1-0-dev libzvbi-dev libshout-dev

```

Now for the fun part (sureeeeeee)

4.) Make sure you are in the root directory of the vlc-0.9.3 folder

```

./bootstrap

cd extras/

git clone git://git.videolan.org/x264.git

cd x264

./configure --disable-asm

make

sudo make install

cd ..

cd ..

mkdir build

cd build

```

(If it says that ../configure is not a directory or something then replace "../configure --prefix=/usr \" with "./configure --prefix=/usr \" except without quotes)

```

../configure --prefix=/usr \

```

```

--enable-snapshot --enable-debug \
--enable-dbus-control --enable-musicbrainz \
--enable-shared-libvlc --enable-mozilla \
--enable-lirc \
--with-ffmpeg-tree=../extras/ffmpeg \
--enable-x264 --with-x264-tree=../extras/x264 \
--enable-shout --enable-taglib \
--enable-v4l \
--enable-dvb \
--enable-realrtsp --disable-xvmc \
--enable-svg --enable-dvdread \
--enable-dc1394 --enable-dv \
--enable-theora --enable-faad \
--enable-twolame --enable-real \
--enable-flac --enable-tremor \
--enable-skins2 --enable-qt4 \
--enable-ncurses \
--enable-aa --enable-caca \
--enable-esd --disable-portaudio \
--enable-jack --enable-xosd \
--enable-galaktos --enable-goom \
--enable-ggi \
--disable-cddax --disable-vcdx \
--disable-quicktime --enable-lua \
--disable-live555

```

Now open up a graphical file browser such as nautilus and go inside the vlc-0.9.3. Browse to the modules folder. Now inside the codec folder, there should be an x264.c file (the speex.c file actually became messed up in vlc 1.0 making it a pain in the arsenal as in my other thread but luckily, vlc 0.9.3 doesn't require a re-programmed speex.c file as well)

Replace the x264.c file with the code on this pastebin.ca link located here:

[http://pastebin.ca/1229910](http://pastebin.ca/1229910)

Copy and paste all the source code in the box and save it in the modules/codec folder as x264.c and click "replace" or you can replace the x264.c file many different ways of your choice. It doesn't matter.

After replacing the x264.c file with the partially re-programmed file, go back into the terminal (or open a new one if you closed it up) and cd to the directory located in /vlc-0.9.3/build

```

make
sudo make install

```

***YOU ARE NOW DONE WITH COMPILING***

To launch vlc, go inside the vlc folder you compiled everything in yada yada yada. Inside the build folder, double click on vlc. Click on run. Boom!

*****END OF GUIDE*****

If you have any problems related to compiling vlc and need a specific .c file to be fixed, please post your exact problem and all make errors so I can make a fix. It will take 1 - 3 days depending on the amount of files and the amount of complexity for a complete fix to be made to meet your expectations. Please leave feedback, comments, and or questions and I will do my best to assist you. Thank you for your patience.

---

### Post by Neo_The_User on 2009-03-23
wow. lots of views. bump!

---

### Post by ChriX on 2009-06-02
Was just working through this guide and found the pastebin link no longer works!

---

### Post by viking_maniac on 2009-10-26
Are there any newer versions of this tutorial? Like installing VLC 1.0.2 from scratch?
 
Or can I just use the same tutorial for the latest version?

---

### Post by viking_maniac on 2009-10-28
> **viking_maniac said:**
> Are there any newer versions of this tutorial? Like installing VLC 1.0.2 from scratch?
 
Or can I just use the same tutorial for the latest version?

Sorry, my fault, VLC 1.0.2 is in the Karmic repository! :D

---

