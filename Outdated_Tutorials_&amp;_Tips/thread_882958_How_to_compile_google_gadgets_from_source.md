---
title: "How to: compile google gadgets from source"
date: 2008-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by qbox on 2008-08-07
Hi
This is my first tutorial in the history so please dont be mad if I make something wrong :)

Please if anyone have any suggestion to post me. Now to begin.
I use ubuntu 8.04 64-bit version. This tutorial probably will work and with other versions.

[CENTER][COLOR="Red"][SIZE="5"]
Preparing the system[/SIZE][/COLOR][/CENTER]

First we need to prepare the system for installation. You need to install this libraries:

g++
gcc
libcurl4-openssl-dev
libdbus-1-dev
libgstreamer-plugins-base0.10-dev
libgtk2.0-dev
libmozjs-dev
libqt4-dev
libqt4-opengl-dev
librsvg2-dev
libxml2-dev
libxul-dev
xulrunner
libdbus-1-dev
libmozjs-dev
libxml2-dev
libgstreamer0.10-dev
libgstreamer-plugins-base0.10-dev
libltdl3-dev 
libxul-dev
libgtk2.0-dev
librsvg2-dev
libcurl4-openssl-dev
libqt4-dev
libqtwebkit-dev 

its a lot? dont worry I will make copy/paste line for you. :)
Now you can install this libraries with System->Administration->Software Sources (the repositories) or you can type or copy/paste this line in the terminal.

```

sudo apt-get install g++ gcc libcurl4-openssl-dev libdbus-1-dev libgstreamer-plugins-base0.10-dev libgtk2.0-dev libmozjs-dev libqt4-dev libqt4-opengl-dev librsvg2-dev libxml2-dev libxul-dev xulrunner libdbus-1-dev libmozjs-dev libxml2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libltdl3-dev libxul-dev libgtk2.0-dev librsvg2-dev libcurl4-openssl-dev libqt4-dev libqtwebkit-dev
```
Insert password :)

[SIZE="1"]Please any one dont know how to open the terminal window...[/SIZE]

This is around 150MB of packets. On the end maybe you will receive that there is a conflict between libqt4-dev libqtwebkit-dev packets but dont worry everything is fine.

Now the system is prepared to use Google gadgets.

[COLOR="Red"][SIZE="5"][CENTER]Downloading the google-gadgets-for-linux-*.tar.gz[/CENTER][/SIZE][/COLOR]

Now you need to download sources from this site [http://code.google.com/p/google-gadgets-for-linux/downloads/list]("http://code.google.com/p/google-gadgets-for-linux/downloads/list") Please download the latest version.

[COLOR="Red"]Have on MIND that this is still in DEVELOPMENT so you can have some BUGS![/COLOR]

You can download in the console with 
```
wget http://google-gadgets-for-linux.googlecode.com/files/google-gadgets-for-linux-xx.xx.xx.tar.gz
```

Type the correct version on the place with xx...

Fine you have all you need to build and install the google gadgets.

[COLOR="Red"][SIZE="5"][CENTER]Extracting and installing.[/CENTER][/SIZE][/COLOR]

Now you need to extract the .tar.gz packet.
Cd to the download directory and type.
```
tar zxvf google-gadgets-for-linux-*.tar.gz
```

This will make parent directory called google-gadgets-for-linux-xx.xx.xx

cd to this directory 
now configure.

```
./configure
```

wait for a while. If this pass fine go next. If not try to go next but I dont think that will work. If not work post here. :)

In the console type

```
sudo make
```
Take a coup of tea and some chocolate to eat, relax and wait. This will take more time. :popcorn:
This process depends of CPU.

Its finished? cool one line more and its over.

in console type

```
sudo make install
```

:) wait and drink you tea :) (15 seconds)

Ok its finished.

Applications->Accesories->Google gadgets

Start and ENJOY.
:guitar:

---

### Post by mar4ela on 2008-11-26
> **qbox said:**
> Hi
This is my first tutorial in the history so please dont be mad if I make something wrong :)

Please if anyone have any suggestion to post me. Now to begin.
I use ubuntu 8.04 64-bit version. This tutorial probably will work and with other versions.

[COLOR="Red"][SIZE="5"][CENTER]Downloading the google-gadgets-for-linux-*.tar.gz[/CENTER][/SIZE][/COLOR]

[CENTER][COLOR="Red"][SIZE="5"]
Preparing the system[/SIZE][/COLOR][/CENTER]

First we need to prepare the system for installation. You need to install this libraries:

g++
gcc
libcurl4-openssl-dev
libdbus-1-dev
libgstreamer-plugins-base0.10-dev
libgtk2.0-dev
libmozjs-dev
libqt4-dev
libqt4-opengl-dev
librsvg2-dev
libxml2-dev
libxul-dev
xulrunner
libdbus-1-dev
libmozjs-dev
libxml2-dev
libgstreamer0.10-dev
libgstreamer-plugins-base0.10-dev
libltdl3-dev 
libxul-dev
libgtk2.0-dev
librsvg2-dev
libcurl4-openssl-dev
libqt4-dev
libqtwebkit-dev 

its a lot? dont worry I will make copy/paste line for you. :)
Now you can install this libraries with System->Administration->Software Sources (the repositories) or you can type or copy/paste this line in the terminal.

```

sudo apt-get install g++ gcc libcurl4-openssl-dev libdbus-1-dev libgstreamer-plugins-base0.10-dev libgtk2.0-dev libmozjs-dev libqt4-dev libqt4-opengl-dev librsvg2-dev libxml2-dev libxul-dev xulrunner libdbuimgs-1-dev libmozjs-dev libxml2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libltdl3-dev libxul-dev libgtk2.0-dev librsvg2-dev libcurl4-openssl-dev libqt4-dev libqtwebkit-dev
```
Insert password :)

[SIZE="1"]Please any one dont know how to open the terminal window...[/SIZE]

This is around 150MB of packets. On the end maybe you will receive that there is a conflict between libqt4-dev libqtwebkit-dev packets but dont [phentermine without a prescription](http://www.phenterminepill.net/) worry everything is fine.

Now the system is prepared to use Google gadgets.



Now you need to download sources from this site [http://code.google.com/p/google-gadgets-for-linux/downloads/list]("http://code.google.com/p/google-gadgets-for-linux/downloads/list") Please [sildenafil citrate](http://www.sildenafilsoft.com/) download the latest version.

[COLOR="Red"]Have on MIND that this is still in DEVELOPMENT so you can have some BUGS![/COLOR]

You can download in the console with 
```
wget http://google-gadgets-for-linux.googlecode.com/files/google-gadgets-for-linux-xx.xx.xx.tar.gz
```

Type the correct version on the place with xx...

Fine you have all you need to build and install the google gadgets.

[COLOR="Red"][SIZE="5"][CENTER]Extracting and installing.[/CENTER][/SIZE][/COLOR]

Now you need to extract the .tar.gz packet.
Cd to the download directory and type.
```
tar zxvf google-gadgets-for-linux-*.tar.gz
```

This will make parent directory called google-gadgets-for-linux-xx.xx.xx

cd to this directory 
now configure.

```
./configure
```

wait for a while. If this pass fine go next. If not try to go next but I dont think that will work. If not work post here. :)

In the console type

```
sudo make
```
Take a coup of tea and some chocolate to eat, relax and wait. This will take more time. :popcorn:
This process depends of CPU.

Its finished? cool one line more and its over.

in console type

```
sudo make install
```

:) wait and drink you tea :) (15 seconds)

Ok its finished.

Applications->Accesories->Google gadgets

Start and ENJOY.
:guitar:
Good work like for newbie. I can send you some tutorials books.Contact me via PM if you are interested

---

### Post by mobile123 on 2009-07-06
great appreciable work keep going dude!

---

