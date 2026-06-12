---
title: "MLBTV 09 Ubuntu Jaunty"
date: 2009-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by raqball on 2009-06-25
Are you a baseball fan and an Ubuntu fan? Then this guide is for you!

You must have a MLBTV premium account. Also, your computer and internet connection speed must be up to par for it keep up with the HD video feeds.

1st we will download everything that we will need..

Java:

```
$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Build-essential:

```
$ sudo apt-get install build-essential 
```

Python-xml:

```
$ sudo apt-get install python-xml 
```

Python-simplejson:

```
$ sudo apt-get install python-simplejson 
```

Python setuptools:

```
$ sudo apt-get install python-setuptools 
```

Python extras:

```
$ sudo apt-get install python-distutils-extra
```

Subversion:

```
$ sudo apt-get install subversion 
```

Mplayer build-tools:

```
$ sudo apt-get build-dep mplayer 
```

Suds:

```

$ sudo easy_install suds

```

Next we will download medibuntu, x264 and the codecs needed for mplayer (thanks to andrew.46 and his excelent howto here:  [http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+jaunty](http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+jaunty))

Mediabuntu:

```
$ sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list \
--output-document=/etc/apt/sources.list.d/medibuntu.list 
```

Now add the Medibuntu keys:

```
$ sudo apt-get update && sudo apt-get install medibuntu-keyring \
&& sudo apt-get update 
```

x264:

```
$ sudo apt-get install build-essential checkinstall gpac libgpac-dev git-core yasm 
```

```

$ git clone git://git.videolan.org/x264.git
$ cd x264
$ ./configure --prefix=/usr --enable-shared
$ make
$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make distclean 
```

Codecs:```

$ cd $HOME
$ wget ftp://ftp.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
$ sudo mkdir -pv /usr/lib/codecs
$ tar xjvf all-20071007.tar.bz2
$ sudo cp -v $HOME/all-20071007/* /usr/lib/codecs
```

Now that all the preliminary stuff is out of the way, lets get down to business!

Next we download mlbviewer, mplayer, and the autobahn.jar:

mlbviewer:

```
$ svn co https://mlbviewer.svn.sourceforge.net/svnroot/mlbviewer/trunk mlbviewer

```

mplayer:

```
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

Download the autobahn.jar:

```
$ wget http://www.mlb.com/nexdef-jars/unsupported/autobahn.jar
```

Moving right along (almost done) we will now compile mplayer and set mlbviewer up.

Compile mplayer: (note: after typing the make command, sit back and relax as it could take a bit)

```

$ cd mplayer
$ ./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer --prefix=/usr --enable-dynamic-plugins
$ make
$ sudo apt-get remove mplayer mencoder
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean
```

Setup mlbviewer:

```

$ cd mlbviewer
$ mkdir -p ~/.mlb
$ cp MediaService.* ~/.mlb/
```

Now we configure the mlbplayer so we can log into watch some baseball:

In terminal navigate to the mlbviewer folder:

```

$ python mlbviewer.py
$ cd
$ cd .mlb
$ gedit config

```
Configure with your mlbtv user name and password. See the README.txt file in the mlbviewer folder for additional configuration options like favorite team, blackout area ect..

Last but not least lets watch some baseball!

Open terminal and navigate to the folder where you saved autobahn.jar and type:

```
$ java -jar autobahn.jar
```
Leave terminal open or minimize it. Do not close it as this is needed for Nexdef HD video feeds

Now open a new terminal and navigate to the mlbviewer folder and type this:
```
$ python mlbviewer.py
```

If all went as planned you should now see a list of games. Select a game and enjoy!!!!!

Here is a sample of my config file (note: you can try the 3000000k feed but you might have better luck using the 2200000k feed via the max_bps setting:

My config (in the .mlb folder)

```

# See README for explanation of these settings.
# user and pass are required except for Top Plays

user=your_mlbtv_username_here
pass=your_mlbtv_password_here

show_player_command=0

live_from_start=0

favorite_color=cyan

speed=800

video_follow=

video_player=mplayer -cache 2048 -really-quiet

show_inning_frames=1

x_display=

audio_player=mplayer -cache 64 -really-quiet

flash_browser=firefox %s

max_bps=2200000

bg_color=xterm

coverage=home

strict_stream=1

audio_follow=

top_plays_player=

favorite=ana

use_color=0

use_nexdef=1

debug=0

time_offset=

blackout=kc

```

If you want to add a front end GUI for the new mplayer we just built above you can easily add one that will show up in your applications list. To add a GUI:

```
$ sudo apt-get install smplayer
```

You are now all set up and ready to watch some baseball on your Ubuntu box! From here on out all you need to do is:

Open terminal and navigate to the folder where you saved the autobahn.jar and run the terminal code:

```
$ java -jar autobahn.jar
```

Open another terminal instance and navigate to the mblviewer folder and run the terminal code:

```
$ python mlbviewer.py
```

Now for some final tips... 

I find it easier if you have autobahn.jar located in the mlbfolder.

Want to make a simple script to open these commands?

For autobahn.jar:

Open a blank text document then copy and paste this into it:

```

#!/bin/sh
java -jar ./autobahn.jar

```

Save the file to where autobahn.jar is located and name it whatever you like.

Now to run autobahn.jar you simply open the folder where the file we created above is located and click on it. When asked what to do choose "Run In Terminal"

For mlbviewer

Open a blank text document then copy and paste this into it:

```

#!/bin/sh
python mlbviewer.py

```

Save the file to where mlbviewer is located and name it whatever you like.

Now to run mlbviewer you simply open the folder where the file we created above is located and click on it. When asked what to do choose "Run In Terminal"

If autobahn.jar is located in the mlbviewer folder then it is easy to make a copy of the entire folder and link it on your desktop. From there, you would simply open the folder and click on the 2 scripts we just made above.

Kris

---

