---
title: "HOWTO: Install &amp; run latest CVS amsn"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-10-13
Hello,

This howto will guide you through installation of the latest amsn..

so first we need tcl/tk/imlib libraries

```

sudo apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients

```

then you need to have CVS downloader so
```

gedit ~/amsn-installer

```

paste in the file
```

#!/bin/sh
###########################################
# Install aMSN CVS version & themes       #
#					  #
# Require : tar, wget, unzip		  #
#					  #
# Description : Easy install aMSN CVS &   #
#		new themes		  #
#					  #
# Infos : routes-linux.scooba.org	  #
# Author : mazzaru[AT]wanadoo[dot]fr	  #
###########################################

VERSION="1.3"
#--------COLOR-------------------
COLOROFF="\033[1;0m"
GREENCOLOR="\033[1;32m"
REDCOLOR="\033[1;31m" 
LILACCOLOR="\033[1;35m" 
#--------PATH--------------------
WGET=`which wget`
UNZIP=`which unzip`
SKINS_PATH=~/.amsn/skins/
BIN_PATH=~/msn/amsn
QUIT_MESS=`echo ""
echo -e "Binary amsn locate at : ${GREENCOLOR}${BIN_PATH}${COLOROFF}"`
#-------Themes url---------------
URL_TUX=http://aleron.dl.sourceforge.net/sourceforge/amsn/Tux.zip
URL_MSN=http://heanet.dl.sourceforge.net/sourceforge/amsn/MSN.zip
URL_FLUOX=http://heanet.dl.sourceforge.net/sourceforge/amsn/Fluox.zip
URL_AMAC=http://heanet.dl.sourceforge.net/sourceforge/amsn/aMac.zip
URL_CRYSTOLA=http://heanet.dl.sourceforge.net/sourceforge/amsn/crystola.zip
#---------------------------
URL_PING=google.com
URL_AMSN_CVS=http://amsn.sourceforge.net/amsn_cvs.tar.gz
HEADER=`clear 
echo -e "\t ${LILACCOLOR}+------------------------------+"
echo -e "\t |   ${GREENCOLOR}aMSN Install script ${VERSION} ${LILACCOLOR}   |" 
echo -e "\t ${LILACCOLOR}+------------------------------+"
echo -e "${COLOROFF}"`
#--------END----------------

#Display a warning message for newbies, usually login always as root.
if [ $UID -eq 0 ]
then
	echo""
	echo -e "${REDCOLOR}Don't run this script as root !! ;)${COLOROFF}"
	echo -e "\a"
	exit 1 
fi

ping -c 2 ${URL_PING} > /dev/null
if [ "$?" -ne "0" ]
then
	ALERT=`echo -e "${REDCOLOR}Bad Internet Connection${COLOROFF}"`
fi

FUNC_INSTALL_THEMES(){

while [ ! -z $1 ]
do
	ARCHIVE=`echo $1 | awk -F/ '{print $6}'`
	DIR=`echo $ARCHIVE | awk -F. '{print $1}'`
	if [ -e ${SKINS_PATH}${DIR} ]
	then
		echo -e "${DIR}........${LILACCOLOR}already install${COLOROFF}"
		shift
	else
		${WGET} -q $1
		${UNZIP} ${ARCHIVE} > /dev/null
		rm -f ${ARCHIVE}*
		mv ${DIR} ${SKINS_PATH}
		echo -e "${DIR}........${GREENCOLOR}install${COLOROFF}"
		shift
	fi
done
}

FUNC_DEPENDS(){

TCL=`locate libtcl8`
TK=`locate libtk8`

if [ ! -e ${TCL} ]
then
	ALERT=`echo -e "${REDCOLOR}Error depedencies : you must install tcl >= 8.3 first. ${COLOROFF}"
	echo "With Mandrake (root) : urpmi tcl"
	echo "With Debian (root) : apt-get install tcl"
	echo ""`
	FUNC_MAIN
fi
if [ ! -e ${TK} ]
then
	ALERT=`echo -e "${ALERT}"
	echo ""
	echo -e "${REDCOLOR}Error depedencies : you must install tk >= 8.3 first. ${COLOROFF}"
	echo "With Mandrake (root) : urpmi tk"
	echo "With Debian (root) : apt-get install tk"
	echo ""`
	FUNC_MAIN
fi
FUNC_INSTALL_AMSN

}



FUNC_TEST_AMSN(){

if [ ! -e ~/msn ]
then
		ALERT=`echo -e "$HOME/msn ${REDCOLOR}not exist, install aMSN first${COLOROFF}"`
		FUNC_MAIN
else
	echo "Waiting..."
	echo ""
	FUNC_INSTALL_THEMES $URL_TUX $URL_MSN $URL_FLUOX $URL_AMAC $URL_CRYSTOLA
	echo ""
	echo ""
	echo -en "Run amsn just for testing ? (y/n) [ ${GREENCOLOR}default : n${COLOROFF} ] : "
	read ON 
		case $ON in
			[yY]*)FUNC_RUN_AMSN;;
			    *)echo "${QUIT_MESS}" ; exit 0;;
		esac
fi
}

FUNC_RUN_AMSN(){

if [ ! -e ${BIN_PATH} ]
then
	ALERT=`echo -e "${HOME}/msn ${REDCOLOR}not exist, install aMSN first${COLOROFF}"`
	FUNC_MAIN
else
	${BIN_PATH}
	FUNC_MAIN
fi

}

FUNC_INSTALL_AMSN(){

cd ~/
echo ""
echo "aMSN CVS downloading please wait..."
# -q = mode quiet (cf. man wget)
${WGET} -q ${URL_AMSN_CVS} 
echo ""
echo "Installing aMSN CVS version"
tar zxf amsn_cvs.tar.gz	-C ~/		#Extract without verbose mode (-v)
rm -f ~/amsn_cvs.tar.gz*		#Archive can be removed
mkdir -p ${SKINS_PATH}
echo ""
echo -ne "Install correct, would you like install themes ? (y/n) [ ${GREENCOLOR}default : n${COLOROFF} ] : "
read ON

case $ON in
	[yY]*)FUNC_TEST_AMSN;;
	    *)echo "${QUIT_MESS}" ; exit 0;;
esac
}

FUNC_MAIN(){

echo -e "${HEADER}"
echo "This script installing aMSN and/or themes : "
echo ""
echo "${ALERT}"
echo ""
select CHOIX in "Install themes only" "Install the last aMSN version" "Run aMSN" "Quit"
do
	case $REPLY in
		1)FUNC_TEST_AMSN;;
		2)FUNC_DEPENDS;;
		3)FUNC_RUN_AMSN;;
		*)exit 0;;
	esac
done
}

#script start here (call FUNC_MAIN function)
FUNC_MAIN

#######
# EOF #
#######

```

run the file..
```

chmod +x ~/amsn-installer
~/amsn-installer

```
press 2 to install (you can choose to install Themes or not)
anyway now go to ~/msn to compile it
```

cd ~/msn
./configure && make

```


now to avoid amsn hanging on logging in..
```

gedit ~/amsn

```

paste into the file
```
#!/bin/bash
export LD_ASSUME_KERNEL=2.2.5
/home/USER_NAME/msn/amsn&

```
and then chmod it
```

chmod +x ~/amsn

```

now all you have left to do is to create a launcher in gnome panel but remember to use /home/USER_NAME/amsn as a launcher and not/home/USER_NAME/msn/amsn and to use [COLOR="Blue"]esdplay $sound[/COLOR] in amsn configuration to have sounds

Hope that helps

---

### Post by meborc on 2005-10-13
[QUOTE=Gandalf]
press 4 to install
[/QUOTE]

its more like a 2 :rolleyes:

---

### Post by Gandalf on 2005-10-13
[QUOTE=meborc]its more like a 2 :rolleyes:[/QUOTE]
oops yeah sowwy :oops: i'll correct it

---

### Post by GavinX on 2005-10-13
Great how to. However, I followed the instructions to the letter and each time I run aMSN, it seems that everything is OK, but I as soon as I log on, it crashes in two seconds. WHat's up with that?

---

### Post by Rob2687 on 2005-10-13
It doesn't download any themes

---

### Post by Gandalf on 2005-10-13
[QUOTE=GavinX]Great how to. However, I followed the instructions to the letter and each time I run aMSN, it seems that everything is OK, but I as soon as I log on, it crashes in two seconds. WHat's up with that?[/QUOTE]
Are you sure you are running /home/USER_NAME/amsn ??

---

### Post by Gandalf on 2005-10-13
[QUOTE=Rob2687]It doesn't download any themes[/QUOTE]
did you get any errors?

---

### Post by stoffepojken on 2005-10-13
Thank you!

Working great for me except for the themes. I wanted this for a long time...:)

---

### Post by stoffepojken on 2005-10-13
By the way. I did not get any error messages about the themes. It just get coming back to the first stage in the install where I was promted to choose 1,2,3 or 4,

---

### Post by stoffepojken on 2005-10-13
I post my output:
> stoffe@Ubuntu:~$ ~/amsn-installer

         +------------------------------+
         |   aMSN Install script 1.3    |
         +------------------------------+

This script installing aMSN and/or themes :



1) Install themes only            3) Run aMSN
2) Install the last aMSN version  4) Quit
#? 2

aMSN CVS downloading please wait...

Installing aMSN CVS version

Install correct, would you like install themes ? (y/n) [ default : n ] : y







         +------------------------------+
         |   aMSN Install script 1.3    |
         +------------------------------+

This script installing aMSN and/or themes :

/home/stoffe/msn not exist, install aMSN first

1) Install themes only            3) Run aMSN
2) Install the last aMSN version  4) Quit
#? 1













         +------------------------------+
         |   aMSN Install script 1.3    |
         +------------------------------+

This script installing aMSN and/or themes :

/home/stoffe/msn not exist, install aMSN first

1) Install themes only            3) Run aMSN
2) Install the last aMSN version  4) Quit
#? 1













         +------------------------------+
         |   aMSN Install script 1.3    |
         +------------------------------+

This script installing aMSN and/or themes :

/home/stoffe/msn not exist, install aMSN first


---

### Post by GavinX on 2005-10-13
[quote=Gandalf]Are you sure you are running /home/USER_NAME/amsn ??[/quote]Very sure that it is. When I run it in a terminal I get this error message after I log in:

libpng warning: Application was compiled with png.h from libpng-1.0.18
libpng warning: Application  is  running with png.c from libpng-1.2.7
libpng error: Incompatible libpng version in application and library
IMLIB ERROR: Cannot load image: /usr/share/amsn/skins/default/pixmaps/unread_tray.png
All fallbacks failed.
See /usr/share/doc/imlib1/README.fallback.
Segmentation fault

---

### Post by Gandalf on 2005-10-13
Ok guys, sorry there were a problem in the script.... now it is fixed so please re-create the script and run it to install themes...

---

### Post by Gandalf on 2005-10-13
[QUOTE=GavinX]Very sure that it is. When I run it in a terminal I get this error message after I log in:

libpng warning: Application was compiled with png.h from libpng-1.0.18
libpng warning: Application  is  running with png.c from libpng-1.2.7
libpng error: Incompatible libpng version in application and library
IMLIB ERROR: Cannot load image: /usr/share/amsn/skins/default/pixmaps/unread_tray.png
All fallbacks failed.
See /usr/share/doc/imlib1/README.fallback.
Segmentation fault[/QUOTE]
hmmm.... i did it after a fresh install many many times no dependicy problems...

---

### Post by stoffepojken on 2005-10-13
Thank you Gandalf. Works perfect for me now with nice themes :)

---

### Post by Gandalf on 2005-10-13
[QUOTE=stoffepojken]Thank you Gandalf. Works perfect for me now with nice themes :)[/QUOTE]
You're Welcome :D ;)

---

### Post by deception on 2005-10-13
Thanks for this, worked a treat :D

---

### Post by SilverTab on 2005-10-14
Worked like a charm! thanks :)

---

### Post by ykpaiha on 2005-10-14
thanks it worked fine here as well great!

---

### Post by jk-pc on 2005-10-14
Hi!
yeah, works fine! many thanks for the great howto!

jk-pc

---

### Post by joakim2 on 2005-10-14
And if you use the development version of TCL/TK you can make it look real sweet and more blended in with your antialiased GNOME desktop like this:

[IMG]http://www.our-own.net/amsn.png[/IMG]

---

### Post by Neo40 on 2005-10-15
[QUOTE=joakim2]And if you use the development version of TCL/TK you can make it look real sweet and more blended in with your antialiased GNOME desktop like this:

[IMG]http://www.our-own.net/amsn.png[/IMG][/QUOTE]

Hi,
How can I install the development version of TCL/TK? 
Thanks

---

### Post by DREMA on 2005-10-21
[QUOTE=GavinX]Very sure that it is. When I run it in a terminal I get this error message after I log in:

libpng warning: Application was compiled with png.h from libpng-1.0.18
libpng warning: Application  is  running with png.c from libpng-1.2.7
libpng error: Incompatible libpng version in application and library
IMLIB ERROR: Cannot load image: /usr/share/amsn/skins/default/pixmaps/unread_tray.png
All fallbacks failed.
See /usr/share/doc/imlib1/README.fallback.
Segmentation fault[/QUOTE]

I have this problem too, does anybody knows how to resolve it ?? Thanks a lot

---

### Post by Gandalf on 2005-10-21
Try to install (if installed then re-install) libpng12-0 and libpng12-dev

---

### Post by DREMA on 2005-10-21
I just reinstall my ubuntu, now I'm in Breezy :p, I use this script to install my amsn, and everything works perfect :D
Thanks guys!

---

### Post by Gandalf on 2005-10-21
[QUOTE=DREMA]I just reinstall my ubuntu, now I'm in Breezy :p, I use this script to install my amsn, and everything works perfect :D
Thanks guys![/QUOTE]
You were on Hoary before? :roll: :roll:

---

### Post by ounn on 2005-10-21
[QUOTE=joakim2]And if you use the development version of TCL/TK you can make it look real sweet and more blended in with your antialiased GNOME desktop like this:

[IMG]http://www.our-own.net/amsn.png[/IMG][/QUOTE]
Joakim2 how do you install cvs tcl and compile amsn with that?
Can you made a simply how-to? Please?
That amsn is very cool.

Thanks

ounn

---

### Post by joakim2 on 2005-10-22
1) Make a directory in your home directory called "tclbuild". 

2) Download the TCL/TK 8.5 snapshots to the directory you created in step 1 from here: [http://www.tcl.tk/software/tcltk/downloadnow85.html](http://www.tcl.tk/software/tcltk/downloadnow85.html)

3) tar zxvf tcl8.5a3-src.tar.gz && tar zxvf tk8.5a3-src.tar.gz

4 cd tcl8.5a3/unix

5) ./configure --prefix=/usr/local/tcl --enable-threads && make install

6) cd ../../tk8.5a3/unix

7) ./configure --prefix=/usr/local/tcl --enable-xft --enable-threads && make install

Tcl/Tk is now installed in /usr/local/tcl.

8) Check out aMSN from CVS (along with the extras which contain the Ubuntu skin and some other cool plugins)

9) go into your aMSN directory and configure and make it like so: ./configure --with-tcl=/usr/local/tcl/lib --with-tk=/usr/local/tcl/lib && make

10) open 'amsn' in your favorite editor and change line #3 to read: exec /usr/local/tcl/bin/wish8.5 $0

11) run: ./amsn and go into the preferences and change your font to an antialiased font. Change the skin to the Ubuntu skin you checked out from aMSN CVS and moved to your skins directory.

Voila :)

---

### Post by ounn on 2005-10-22
Thanks. It work just fine. Now amsn deserves a try :p its not so ugly like before.

---

### Post by Gandalf on 2005-10-22
[QUOTE=joakim2]1) Make a directory in your home directory called "tclbuild". 

2) Download the TCL/TK 8.5 snapshots to the directory you created in step 1 from here: [http://www.tcl.tk/software/tcltk/downloadnow85.html](http://www.tcl.tk/software/tcltk/downloadnow85.html)

3) tar zxvf tcl8.5a3-src.tar.gz && tar zxvf tk8.5a3-src.tar.gz

4 cd tcl8.5a3/unix

5) ./configure --prefix=/usr/local/tcl --enable-threads && make install

6) cd ../../tk8.5a3/unix

7) ./configure --prefix=/usr/local/tcl --enable-xft --enable-threads && make install

Tcl/Tk is now installed in /usr/local/tcl.

8) Check out aMSN from CVS (along with the extras which contain the Ubuntu skin and some other cool plugins)

9) go into your aMSN directory and configure and make it like so: ./configure --with-tcl=/usr/local/tcl/lib --with-tk=/usr/local/tcl/lib && make

10) open 'amsn' in your favorite editor and change line #3 to read: exec /usr/local/tcl/bin/wish8.5 $0

11) run: ./amsn and go into the preferences and change your font to an antialiased font. Change the skin to the Ubuntu skin you checked out from aMSN CVS and moved to your skins directory.

Voila :)[/QUOTE]
i think it's better to install tcl in home directory to avoid any conflict with any other already installed TCL/TK version, personaly i used /home/username/tcl instead of /usr/local/tcl

---

### Post by bored2k on 2005-10-22
I have made **x86** ubuntu packages for the latest TCL and TK:
[LIST]
[*][http://rapidshare.de/files/6632929/tk8.5a3_8.5a3-1_i386.deb.html](http://rapidshare.de/files/6632929/tk8.5a3_8.5a3-1_i386.deb.html)
[*][http://rapidshare.de/files/6633036/tcl8.5a3_8.5a3-1_i386.deb.html](http://rapidshare.de/files/6633036/tcl8.5a3_8.5a3-1_i386.deb.html)
[/LIST]
[QUOTE=joakim2]Go into your aMSN directory and configure and make it like so: ./configure --with-tcl=/usr/local/tcl/lib --with-tk=/usr/local/tcl/lib && make[/QUOTE]

---

### Post by Orunitia on 2005-10-22
Well after annoying bored2k, I finally realized I messed something up. Got it running, and it is really nice. I'll actually use this along with gaim now.

---

### Post by bored2k on 2005-10-22
joakim2, what skin is that ?

---

### Post by Orunitia on 2005-10-23
I'd also like to know where you got that skin.

---

### Post by Gandalf on 2005-10-23
Guys you can find CVS skins & plugins [here](http://cvs.sourceforge.net/viewcvs.py/amsn/amsn-extras/) anyway about ubuntu Skin it's [here](http://cvs.sourceforge.net/viewcvs.py/amsn/amsn-extras/skins//viewcvs.py/amsn/amsn-extras/skins/Ubuntu%20%28Human%29/)

P.S: sometimes the folders (links i gave you) are down, because it's CVS so sometimes they are changing it, like this very moment ubuntu theme ain't available but it was 10 mns ago..

---

### Post by Orunitia on 2005-10-23
Thanks. :)

---

### Post by Orunitia on 2005-10-23
Edit: I'm a moron, don't mind what I asked in this post.

---

### Post by joakim2 on 2005-10-23
[QUOTE=Gandalf]i think it's better to install tcl in home directory to avoid any conflict with any other already installed TCL/TK version, personaly i used /home/username/tcl instead of /usr/local/tcl[/QUOTE]

/usr/local/tcl isn't going to interfer with any other Tcl/Tk version or installation unless you put one there :) I tend to avoid installing stuff in my home directory because every now and then I go through my home dir and just weed and whack. Otherwise it would take Nautilus a day and a half to draw my home dir :)

---

### Post by skyboy on 2005-11-05
Great great how to ! works like a charm and the webcam too ! finally a webcam client for Linux !!
Thanks

---

### Post by ubuntu_123 on 2005-11-05
Hi guys, this question maybe very stupid.

But how to "create a launcher in gnome panel"?
> now all you have left to do is to create a launcher in gnome panel but remember to use /home/USER_NAME/amsn as a launcher and not/home/USER_NAME/msn/amsn and to use esdplay $sound in amsn configuration to have sounds

Thanks.
yasir

---

### Post by Mandarb on 2005-11-09
Hello,

anyone knows how to compile linphone plugin in /usr/share/amsn/plugins/linphone ?

Thanks.

---

### Post by foolosophy on 2005-12-04
when I do the first step (*sudo apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients*)  it says that it will need to download & install al the following packages:

[FONT="System"][SIZE="2"]build-essential esound-clients g++ g++-4.0 imlib11 imlib11-dev libice-dev
  libjpeg62-dev libpng12-dev libsm-dev libstdc++6-4.0-dev libtiff4-dev
  libtiffxx0c2 libungif4-dev libx11-dev libxau-dev libxext-dev libxi-dev
  libxmu-dev libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxt-dev
  libxtrap-dev libxtst-dev libxv-dev tcl8.4-dev tk8.4-dev x-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-trap-dev x11proto-video-dev x11proto-xext-dev
  xlibs-dev xlibs-static-dev zlib1g-dev[/SIZE][/FONT]

all this is like 30MB in disk. is it necessary? I downloaded the *amsn_cvs.tar.cz* from AMSN website. It can't be installed like a package, or do I have to follow all the instructions you posted?

I'm sorry for posting stupid questions, but I'm a newbie on linux who was sick & tired of windows cr*p.

Thanks a lot.

---

### Post by Gandalf on 2005-12-04
[QUOTE=foolosophy]when I do the first step (*sudo apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients*)  it says that it will need to download & install al the following packages:

[FONT="System"][SIZE="2"]build-essential esound-clients g++ g++-4.0 imlib11 imlib11-dev libice-dev
  libjpeg62-dev libpng12-dev libsm-dev libstdc++6-4.0-dev libtiff4-dev
  libtiffxx0c2 libungif4-dev libx11-dev libxau-dev libxext-dev libxi-dev
  libxmu-dev libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxt-dev
  libxtrap-dev libxtst-dev libxv-dev tcl8.4-dev tk8.4-dev x-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-trap-dev x11proto-video-dev x11proto-xext-dev
  xlibs-dev xlibs-static-dev zlib1g-dev[/SIZE][/FONT]

all this is like 30MB in disk. is it necessary? I downloaded the *amsn_cvs.tar.cz* from AMSN website. It can't be installed like a package, or do I have to follow all the instructions you posted?

I'm sorry for posting stupid questions, but I'm a newbie on linux who was sick & tired of windows cr*p.

Thanks a lot.[/QUOTE]
Yes they are necessary...

---

### Post by Rob2687 on 2005-12-04
oops...wrong thread..

---

### Post by luminoso on 2005-12-05
```

luminoso@khona4:~/msn$ cd ~/msn
luminoso@khona4:~/msn$ ./configure && make
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib/tk8.4
checking for main in -lstdc++... yes
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for ftello... yes
checking for fseeko... yes
checking for getpt... yes
checking for strcasestr... yes
checking for memmem... yes
checking for dlopen... no
checking for pthread_create in -lpthread... yes
checking if mmx should be used... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/linux/capture/config.h

compile time options summary
============================

    X11          : yes
    Using Libng  : yes
    Tcl          : 8.4
    TK           : 8.4
    DEBUG        : no

(cd .; autoconf)
/bin/sh: autoconf: command not found
make: ** [configure] Erro 127
luminoso@khona4:~/msn$

```

apt-get sucessul.. already made "make" before.. :(

---

### Post by Turgon on 2005-12-10
Nice guide. Worked perfektly and is now installing the final aMSN 0.95:D

---

### Post by Sebby on 2005-12-10
First of all, thanks for this great guide. I used to really dislike aMSN, but the CVS build coupled with *jaokim2's* directions for using the development versions of TCL/TK is really useful. One thing, though:

[QUOTE=joakim2]11) run: ./amsn and go into the preferences and change your font to an antialiased font. Change the skin to the Ubuntu skin you checked out from aMSN CVS and moved to your skins directory.[/QUOTE]
How do I install the Ubuntu theme from CVS?

Also, I'm having some trouble with profiles. Is there a way to manually delete them so I can start again, i.e. not from in preferences?

---

### Post by Gandalf on 2005-12-10
[QUOTE=Sebby]First of all, thanks for this great guide. I used to really dislike aMSN, but the CVS build coupled with *jaokim2's* directions for using the development versions of TCL/TK is really useful. One thing, though:


How do I install the Ubuntu theme from CVS?

Also, I'm having some trouble with profiles. Is there a way to manually delete them so I can start again, i.e. not from in preferences?[/QUOTE]
Make sure cvs installed (apt-get install cvs)

type
```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/amsn login
```
press enter when prompted for password

```
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/amsn co -P amsn-extras
```

you will have an amsn-extras folder with all CVS Skins and Plugins (including ubuntu theme)

---

### Post by Sebby on 2005-12-11
Thanks! I know this is pretty petty, but I don't suppose there's a way to stop the mouse pointer pointing to the right when you hover over an option in aMSN?

Also, I'm still having problems with profiles, i.e. not being able to select my profile because it says it's in use, and not being able to delete another for the same reason! Any ideas?

---

### Post by ctaborda on 2005-12-16
Hi, im getting this error. I tried installing everything but I just cannot get it to work! :(

Please help me out.
> 
checking tcl build dir... warning: locate: could not open database: /var/lib/slocate/slocate.db: No such file or directory
configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

Carlos

---

### Post by Sebby on 2005-12-16
[QUOTE=ctaborda]Hi, im getting this error. I tried installing everything but I just cannot get it to work! :([/QUOTE]
Have you done:
```
sudo apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
```?

---

### Post by Gandalf on 2005-12-16
check [this](http://wael.nasreddine.com/Articles/Articles/Easy_aMSN.html) for auto installation ;)

---

### Post by fannymites on 2005-12-23
I still can't get the human theme via cvs as described in post 47.  I press enter at the password prompt and nothing happens, after waiting a long time I've tried just typing in the second line but still nothing happens for ages then I eventually get a timeout.
I've seen the amsn-extras with the human theme on the sourceforge site but I can't find a way to download it other than downloading each individual sound and image and recreating the directory structure.

---

### Post by Gandalf on 2005-12-24
Weird you are having this issue, try to delete the file ~/.cvspass  and retry again, anyway i have uploaded for you all CVS themes [here](http://wael.nasreddine.com/trash/skins.tar.gz) download, untar it to ~/.amsn

---

### Post by fannymites on 2005-12-25
Thanks for that.  It turns out the reason for the problem was that I hadn't allowed cvs in guarddog.  Oops.
I've tried since enabling it and everything downloaded fine.

---

### Post by WishMaster on 2006-05-07
First of all: I love your amsn-installer script :grin:

 _I have 2 questions:_
 1) Is it possible to show some sort of downloading information?
 In line 148, you say: 
 [COLOR=Red]${WGET} -q ${URL_AMSN_CVS} [/COLOR]
Sometimes, the CVS is down or the connection is slow, so I keep waiting for nothing to happen, because I don't see any progress. Does "-c" instead of "-q" solve that problem?
*edit: yes it does, I tried :-P*
 
 2) Line 152:
 [COLOR=Red]rm -f ~/amsn_cvs.tar.gz*        #Archive can be removed[/COLOR]
 That is good :smile: However, it would be nice if something like "aMSN cvs **20060512** was installed" would be printed to the console.
 It gives me an idea of which cvs-version (date/time of downloaded amsn_cvs.tar) was installed.
[I]edit: change line 150 in:
> echo "Installing aMSN CVS version: `stat -c --format=%y amsn_cvs.tar.gz`"[/I]
 
 Thank you :smile:



This is how it looks like:
The red selection is showing download information (speed, ETA,...)
The blue selection shows which CVS-version you are using (in this case: the one of May 8th)


[IMG]http://users.pandora.be/Nyx/Linux/aMSN.jpg[/IMG]

---

### Post by ampop on 2006-05-09
Gandalf,
This really works. Thanks a lot.

---

### Post by WishMaster on 2006-05-21
aMSN has stopped using CVS
So this script won't work

This one works
```
#!/bin/sh
###########################################
# Install aMSN CVS version & themes       #
#                      #
# Require : tar, wget, unzip          #
#                      #
# Description : Easy install aMSN CVS &   #
#        new themes          #
#                      #
# Infos : routes-linux.scooba.org      #
# Author : mazzaru[AT]wanadoo[dot]fr      #
###########################################

VERSION="1.3"
#--------COLOR-------------------
COLOROFF="\033[1;0m"
GREENCOLOR="\033[1;32m"
REDCOLOR="\033[1;31m" 
LILACCOLOR="\033[1;35m" 
#--------PATH--------------------
WGET=`which wget`
UNZIP=`which unzip`
SKINS_PATH=~/.amsn/skins/
BIN_PATH=~/msn/amsn
QUIT_MESS=`echo ""
echo -e "Binary amsn locate at : ${GREENCOLOR}${BIN_PATH}${COLOROFF}"`
#-------Themes url---------------
URL_TUX=http://aleron.dl.sourceforge.net/sourceforge/amsn/Tux.zip
URL_MSN=http://heanet.dl.sourceforge.net/sourceforge/amsn/MSN.zip
URL_FLUOX=http://heanet.dl.sourceforge.net/sourceforge/amsn/Fluox.zip
URL_AMAC=http://heanet.dl.sourceforge.net/sourceforge/amsn/aMac.zip
URL_CRYSTOLA=http://heanet.dl.sourceforge.net/sourceforge/amsn/crystola.zip
#---------------------------
URL_PING=google.com
URL_AMSN_CVS=http://amsn.sourceforge.net/amsn_dev.tar.gz
HEADER=`clear 
echo -e "\t ${LILACCOLOR}+------------------------------+"
echo -e "\t |   ${GREENCOLOR}aMSN Install script ${VERSION} ${LILACCOLOR}   |" 
echo -e "\t ${LILACCOLOR}+------------------------------+"
echo -e "${COLOROFF}"`
#--------END----------------

#Display a warning message for newbies, usually login always as root.
if [ $UID -eq 0 ]
then
    echo""
    echo -e "${REDCOLOR}Don't run this script as root !! ;)${COLOROFF}"
    echo -e "\a"
    exit 1 
fi

ping -c 2 ${URL_PING} > /dev/null
if [ "$?" -ne "0" ]
then
    ALERT=`echo -e "${REDCOLOR}Bad Internet Connection${COLOROFF}"`
fi

FUNC_INSTALL_THEMES(){

while [ ! -z $1 ]
do
    ARCHIVE=`echo $1 | awk -F/ '{print $6}'`
    DIR=`echo $ARCHIVE | awk -F. '{print $1}'`
    if [ -e ${SKINS_PATH}${DIR} ]
    then
        echo -e "${DIR}........${LILACCOLOR}already install${COLOROFF}"
        shift
    else
        ${WGET} -q $1
        ${UNZIP} ${ARCHIVE} > /dev/null
        rm -f ${ARCHIVE}*
        mv ${DIR} ${SKINS_PATH}
        echo -e "${DIR}........${GREENCOLOR}install${COLOROFF}"
        shift
    fi
done
}

FUNC_DEPENDS(){

TCL=`locate libtcl8`
TK=`locate libtk8`

if [ ! -e ${TCL} ]
then
    ALERT=`echo -e "${REDCOLOR}Error depedencies : you must install tcl >= 8.3 first. ${COLOROFF}"
    echo "With Mandrake (root) : urpmi tcl"
    echo "With Debian (root) : apt-get install tcl"
    echo ""`
    FUNC_MAIN
fi
if [ ! -e ${TK} ]
then
    ALERT=`echo -e "${ALERT}"
    echo ""
    echo -e "${REDCOLOR}Error depedencies : you must install tk >= 8.3 first. ${COLOROFF}"
    echo "With Mandrake (root) : urpmi tk"
    echo "With Debian (root) : apt-get install tk"
    echo ""`
    FUNC_MAIN
fi
FUNC_INSTALL_AMSN

}



FUNC_TEST_AMSN(){

if [ ! -e ~/msn ]
then
        ALERT=`echo -e "$HOME/msn ${REDCOLOR}not exist, install aMSN first${COLOROFF}"`
        FUNC_MAIN
else
    echo "Waiting..."
    echo ""
    FUNC_INSTALL_THEMES $URL_TUX $URL_MSN $URL_FLUOX $URL_AMAC $URL_CRYSTOLA
    echo ""
    echo ""
    echo -en "Run amsn just for testing ? (y/n) [ ${GREENCOLOR}default : n${COLOROFF} ] : "
    read ON 
        case $ON in
            [yY]*)FUNC_RUN_AMSN;;
                *)echo "${QUIT_MESS}" ; exit 0;;
        esac
fi
}

FUNC_RUN_AMSN(){

if [ ! -e ${BIN_PATH} ]
then
    ALERT=`echo -e "${HOME}/msn ${REDCOLOR}not exist, install aMSN first${COLOROFF}"`
    FUNC_MAIN
else
    ${BIN_PATH}
    FUNC_MAIN
fi

}

FUNC_INSTALL_AMSN(){

cd ~/
echo ""
echo "aMSN CVS downloading please wait..."
# -q = mode quiet (cf. man wget)
${WGET} -c ${URL_AMSN_CVS} 
echo ""
echo "Installing aMSN CVS version: `stat -c --format=%y amsn_dev.tar.gz`"
tar zxf amsn_dev.tar.gz    -C ~/        #Extract without verbose mode (-v)
rm -f ~/amsn_dev.tar.gz*        #Archive can be removed
mkdir -p ${SKINS_PATH}
echo ""
echo -ne "Install correct, would you like install themes ? (y/n) [ ${GREENCOLOR}default : n${COLOROFF} ] : "
read ON

case $ON in
    [yY]*)FUNC_TEST_AMSN;;
        *)echo "${QUIT_MESS}" ; exit 0;;
esac
}

FUNC_MAIN(){

echo -e "${HEADER}"
echo "This script installing aMSN and/or themes : "
echo ""
echo "${ALERT}"
echo ""
select CHOIX in "Install themes only" "Install the last aMSN version" "Run aMSN" "Quit"
do
    case $REPLY in
        1)FUNC_TEST_AMSN;;
        2)FUNC_DEPENDS;;
        3)FUNC_RUN_AMSN;;
        *)exit 0;;
    esac
done
}

#script start here (call FUNC_MAIN function)
FUNC_MAIN

#######
# EOF #
#######
```

---

### Post by *Serval on 2006-06-08
WishMaster : I used your script to install amsn by when I select "Run aMSN (just for test)" I get this error : You can't load TkCximage, this is now needed to run aMSN. Please compile amsn first, insctructions on how to compiler are located in the file INSTALL


Can you help me please ?


Thanks ;)

*Serval

---

### Post by Neo40 on 2006-06-08
Does that script work with Dapper too?
Thanks

---

### Post by *Serval on 2006-06-08
oh yeah i forgot to say i'm on Dapper ;)

---

### Post by mamadou on 2006-11-26
Hey

I personaly got stuck right from the start

> 
~$ sudo apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients

Reading package lists... Done

Building dependency tree... Done

E: Couldn't find package imlib11-dev



:confused:

---

### Post by CriticalStealth on 2007-01-02
after you paste in the code for it, you say "run the file" how do i run the file?

---

### Post by CriticalStealth on 2007-01-02
ok, i foudn the file in my home folder, and ran it.. but nothing happened, now im stuck at this part

chmod +x ~/amsn-installer
~/amsn-installer


i input his code into my terminal correct? it does not do anything.

---

### Post by flapane on 2007-01-05
how to change background in amsn 0.96?

---

### Post by Attedude on 2007-01-07
I had this error. I belive amsn-installer that I copyed above wasen't correct. 
shoul'd I change those lines somehow.



         +------------------------------+
         |   aMSN Install script 1.3    |
         +------------------------------+

This script installing aMSN and/or themes :



1) Install themes only            3) Run aMSN
2) Install the last aMSN version  4) Quit
#? 2
/home/atte/amsn-installer: line 84: [: too many arguments
/home/atte/amsn-installer: line 92: [: too many arguments

aMSN CVS downloading please wait...

Installing aMSN CVS version
tar: amsn_cvs.tar.gz: Toimintoa open ei voi suorittaa: Tiedostoa tai hakemistoa ei ole
tar: Virhe ei ole korjattavissa, poistutaan nyt
tar: Child returned status 2
tar: Viivästetty virhepoistuminen johtuu aikaisemmista virheistä

Install correct, would you like install themes ? (y/n) [ default : n ] :

---

### Post by oncemore on 2007-03-03
I'm stuck in the start...
I get this error when i try to run amsn-installer:

[: 50: 0: unexpected operator
/home/pedromfs/amsn-installer: 172: Syntax error: "do" unexpected (expecting "}")

---

### Post by Hyprkookeez on 2007-04-09
i get the same error. and i'm a complete noob. :(

---

### Post by ad0 on 2007-05-07
Then try this:

```
bash amsn-installer
``` 

Hope it helps.

---

### Post by Johnson on 2007-08-23
aMSN CVS downloading please wait...

Installing aMSN CVS version
tar: amsn_cvs.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Utsatt feil-avslutning for tidligere feil

Install correct, would you like install themes ? (y/n) [ default : n ] : 

What now!? :(

---

### Post by xgamma on 2007-08-24
I'm having the exact same problem as Johnson on feisty for x64

---

### Post by sway.jd on 2007-08-28
> **ad0 said:**
> Then try this:

```
bash amsn-installer
``` 

Hope it helps.

this worked.


but now I'm stuck on the next step,

it says to do this:

> cd ~/msn
./configure && make

but as i enter the "cd ~/msn" it says

> bash: cd: /home/sway (username)/msn: No such file or directory

what do i do?

---

### Post by ubu_dynamite on 2007-08-31
alternative amsn from source: works in feisty

download source:
[http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

open terminal:

sudo aptitude install build-essential checkinstall tcl8.4-dev tk8.4-dev libpng12-0-dev libjpeg62-dev
sudo aptitude purge amsn

cd "to directory jou downloaded the amsn-0.97RC1.tar.bz2"
tar -xvjf amsn-0.97RC1.tar.bz2
cd amsn-0.97RC1
./configure
make
sudo checkinstall
cp amsn_0.97RC1-1_i386.deb ../
cd ../
sudo rm -r amsn-0.97RC1

---

### Post by perro84 on 2007-09-21
Here you can find an easy tutorial on how to install aMsn 0.97 in Ubuntu easily!

[Install amsn 0.97 in Ubuntu]("http://www.justubuntu.com/install_amsn_097b_ubuntu")

---

### Post by Suprator on 2008-05-27
i stuck here too and nothing happens i entered all comands but i still cannot open amsn ...:(


```
cd ~/msn
./configure && make
```

---

