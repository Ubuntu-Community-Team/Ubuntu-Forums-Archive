---
title: "ffmpeg-php"
date: 2007-03-30
forum: Programming Talk
---

### Post by lukemack on 2007-03-30
Hi,

I want to install ffmpeg-php:

[http://ffmpeg-php.sourceforge.net/](http://ffmpeg-php.sourceforge.net/)

however, i am getting the following error:

luke@DeepThought:/usr/lib/php5/20060613/ffmpeg-php-0.5.0$ sudo ./configure && make
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20060613
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.9.11 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for ffmpeg support... yes, shared
checking for ffmpeg headers... configure: error: ffmpeg headers not found. Make sure you've built ffmpeg as shared libs using the --enable-shared option


anyone know how to resolve this?

thanks,

<L>

---

### Post by lukemack on 2007-03-30
luke@DeepThought:/usr/lib/php5/20060613/ffmpeg-php-0.5.0$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
ffmpeg      SVN-rUNKNOWN
libavutil   3211264
libavcodec  3345152
libavformat 3278080


i installed ffmpeg using sudo apt-get install ffmpeg

---

### Post by DrFraser on 2007-11-13
> **lukemack said:**
> luke@DeepThought:/usr/lib/php5/20060613/ffmpeg-php-0.5.0$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
ffmpeg      SVN-rUNKNOWN
libavutil   3211264
libavcodec  3345152
libavformat 3278080


i installed ffmpeg using sudo apt-get install ffmpeg

Hey knuckle head, read that post again. They said FFMPEG-PHP not FFMPEG.

---

### Post by st4rdr1ft3r on 2007-11-13
> **DrFraser said:**
> Hey knuckle head, read that post again. They said FFMPEG-PHP not FFMPEG.

ummm, it was the same person, insult backfires...

@lukemack:
try installing the ffmpeg development files:
apt-cache search ffmpeg dev

---

### Post by weather15 on 2009-07-12
Sudo apt-get install php5-ffmpeg
or if you just want to install ffmpeg 
sudo apt-get install ffmpeg

---

### Post by alienbrain on 2011-05-12
You need those packages:

apt-get install libavformat-dev libavcodec-dev libswscale-dev libgd2-xpm-dev

How did I know, are you wondering? I checked the package dependencies here :) [http://packages.ubuntu.com/source/lucid/ffmpeg-php](http://packages.ubuntu.com/source/lucid/ffmpeg-php)

---

