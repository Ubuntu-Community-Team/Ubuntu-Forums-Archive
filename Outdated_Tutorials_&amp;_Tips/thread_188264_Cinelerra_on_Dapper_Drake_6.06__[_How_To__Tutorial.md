---
title: "Cinelerra on Dapper Drake 6.06  [ How To / Tutorial ]"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by lprofil on 2006-06-03
**[Last major edit 4th Sep 06:07pm GMT]**

Hallo, 

To make a long story short: 

**Easy way:**
Go trough the stepps **5** till **7.2**.

Then you install a single Cinelerra deb file [from this side]("http://ww2.fs.ei.tum.de/~dr/") via:
```
sudo dpkg -i cinelerra*.deb
```

in case you are running a **i686 Processor**!
This will **work** on a 64-bit Processor 
but it will **not work** on a 64-bit Ubuntu-system.

For **Ubuntu-64-bit** you can download the **64-Bit binaries** from the same site 
and take a look to [this tutorial]("http://ubuntuforums.org/showthread.php?t=215252") which is based on my one.

When you are done step **12** and **13** might be interesting for you.

Thanks to **jstewart** from #cinelerra @ irc.freenode.net and **chainzz**.


**OR**


**The probably more up to date way:**

**Note!** You might run into dependecy problems which fiexed myself with the help of google when i tried this method.
To be sure to set up the most current version of Cinelerra follow the tutorial listed below.


**Preamble**
Back in the days before Ubuntu 4.10, i already messed around with Cinelerra under GNU-Debian-Linux. 
I learned how to solve dependecies and how to install this programm propper. 
But poorly i had no need for this nice tool so i lost interest and Cinelerra fell asleep.

Cannonical bundled a great pice of an OS in Ubuntu Dapper-Drake 6.06 with the help of GNU-Debian-Linux. 
It is neat and slim but there is the opportunity to install several libaries to get a fully featured development enviroment. 
In our case Video-Cutting and -Encoding.

After some research i found Cinelerra-packages for Breezy but i could not get it running. 
Why not give it a trial under Dapper Drake with the cutting edge CVS-Version of Cinelerra?!



**Cinelerra Cutting Edge Installation from CVS-Sources (Verison 2.0CV)**

This is the way to go:

**#1.** Setting  up a CVS Enviroment [CVS -> **C**urrent **V**erison **S**ystem]

First we need to set up a CVS Enviroment for our Cinelerra source-tree:
```
sudo apt-get install subversion
```


**#2.** Create a Cinelerra folder

Change to /opt , which is the path for optional programm packages which are not installed with e.g. apt-get.
You can install a programm twice, but all config files of the programm in /opt for example are only there
and do not effect other programms installed in /bin orr /usr/bin!
```
cd /opt
```


**#3.** Download the Source-Tree

Get the CVS-tree:
```
sudo svn checkout svn://svn.skolelinux.org/cinelerra/tags/r1_2_2-last/hvirtual
```


**#4.** Edit autogen.sh

Small changes have to be made in autogen.sh. 
First change to the cinelerra main folder:
```
 cd hvirtual
```

Edit the following lines:
# export AUTOMAKE=/usr/bin/automake-1.7 
# export ACLOCAL=/usr/bin/aclocal-1.7 

erase the hashes that the lines look like:
export AUTOMAKE=/usr/bin/automake-1.7 
export ACLOCAL=/usr/bin/aclocal-1.7

**To edit type:**
```
sudo nano autogen.sh
```


**#5.** Adding **"Restricted Respositories"**

To get all neccessary codecs we have to add the "Restricted Respositories".
How to do that with a **graphical interface** is described here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

How to do that in **command line** is described here:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)


Alternatively you can use my method. Type this lines:
```
sudo rm /etc/apt/sources.list
```

then type:
```
sudo nano /etc/apt/sources.list
```

and copy and paste this list:
```
deb http://de.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe main restricted multiverse

```

Do not forget to edit the the 6 URIs (Uniform Resource Identifier) for faster connections and less hops.
Note: Leave the line with "security.ubu..." as it is!

The URI is the **bold** marked part in this line:
```
 http://**de**.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
Change it to **"au"** if you are located in **Australia** or **"it"** if you are located in **Italy** or **"fr"** for **France** and so on.


**#6.** Update

To update you local respositories with all available ones type:
```
sudo apt-get update
```


**#7.** Installing neccesary libaries

You need several libaries for e.g. video-encoding. Type:
```
sudo apt-get install gstreamer0.8-faad gstreamer0.8-a52dec liba52-0.7.4-dev fftw-dev sfftw-dev sfftw2 fftw3 fftw3-dev mffm-fftw1c2 mffm-fftw-dev fftw2 fftw3-doc liblame0 liblame-dev lame-extras lame toolame glame openexr libopenexr-dev libopenexr2c2a exrtools libraw1394-5 libraw1394-dev libmjpegtools0c2a libmjpegtools-dev mjpegtools libuuid1 uuid-dev libvorbisfile3 libtheora0 libtheora-dev libtheora-bin gstreamer0.8-theora ffmpeg2theora libvorbisenc2 libvorbis0a libvorbisenc2 libvorbisfile3 libvorbis-dev ffmpeg2theora gstreamer0.10-ffmpeg ffmpeg avifile-mjpeg-plugin gstreamer0.10-ffmpeg libfaad2-dev libfaad2-0 libavc1394-dev libavc1394-0 libavcodec-dev libavformat-dev libavifile-0.7c2 gstreamer0.10-ffmpeg gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-plugins-multiverse gstreamer0.8-xvid libdirac0c2a autobook libclutils0-dev libclutils0c2 autoconf autoconf-doc autotools-dev libguile-ltdl-1 libltdl3 libltdl3-dev libtool libtool-doc libtiffxx0c2 libtiff4-dev libtiff4 libtiff-tools libtool libltdl3 avidemux libfame-0.9 libpvm3 transcode xvid4conf quicktime-x11utils libpng3 libpng3-dev libpngwriter0-dev libpngwriter0c2 pngcheck pngquant  libdv-bin libdvb-dev libdvbpsi4-dev libdvdplay0 libdvdplay0-dev libdvdread3-dev libasound2 libasound2-dev automake1.7 nasm libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev libx264-dev libsndfile1 libsndfile0 libfaac-dev make libsndfile1 libsndfile1-dev quicktime-utils libxv-dev dvgrab libasound2 libasound2-dev libesd0-dev
```

(Click 4 times with your left mouse button on the line above and paste
the content then with a middle-click to you konosole window)


**#7.2** Installing a suiting Video-Encoder

In order to install a video-encoder which is optimized for you processor choose one of the following options:

mencoder - MPlayer's Movie Encoder
mencoder-386 - MPlayer's Movie Encoder (dummy package)
mencoder-586 - MPlayer's Movie Encoder (dummy package)
mencoder-686 - MPlayer's Movie Encoder (dummy package)
mencoder-amd64 - MPlayer's Movie Encoder (dummy package)
mencoder-custom - MPlayer's Movie Encoder (dummy package)
mencoder-g4 - MPlayer's Movie Encoder (dummy package)
mencoder-k6 - MPlayer's Movie Encoder (dummy package)
mencoder-k7 - MPlayer's Movie Encoder (dummy package)
mencoder-powerpc - MPlayer's Movie Encoder (dummy package)

In my case (Pentium III 700) i installed mencoder-686 by typing:
```
sudo apt-get install mencoder-686
```


**#8.** A Little Bug-Fixing
It is the 29th of July today and there is still this nasty 
bug during the compiling process. I do not want to bother you with details
but there some path-names for plugins changed and the compiler does
not find them at the right place.

To fix the **first error** type:
```
cd /opt/hvirtual
```
```
sudo mkdir plugins/chromakey-hsv && cp plugins/chromakeyhsv/* plugins/chromakey-hsv
```

To fix the **second error** type:
```
sudo mkdir plugins/seltempavg && cp plugins/denoiseseltempavg/* plugins/seltempavg
```


**#8.1** Execute the autogen-file

Type:
```

cd /opt/hvirtual/

sudo sh autogen.sh
```

to run the autogen.sh script.


**#9.** Creating makefiles

To tell the compiler on which hardware it runs and which libaries are available type:
```
sudo ./configure
```


**#10.** Creating an executable

We compile the Source-Code to get a executable with:
```
sudo make
``` 


**#11.** Installation 

```
sudo make install
```


**#11.1** Alternative Installation

This method installs Cinelerra and generate a debfile at a time:

```
sudo checkinstall
```
is our friend.

There will be few dialogs asking you some questions
but you can continue by pressing enter until is says:


```
 Done. The new package has been installed and saved to
 /opt/hvirtual/cinelerra2.1_2.1-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r cinelerra2.1

**********************************************************************
```


**#12.** Start Cinelerra :
```
sudo cinelerra
```

I have read in another forum that you need root permissons for 
different reasons. Run Cinelerra as root or as sudo.


**#13.** Important Settings :

I first had some trouble encoding my edited video-clips and could not figure out why.
After reading the very helpfull wiki **[5]** i found out that there are some setting 
which might be important for you.

As i think OSS is outdated you should first change your preferences to **ALSA** on both **Playback** and **Recording**.

Thatfor you go to:

Settings --> Preferences and on the top you choose the slider of you choice.
The picture shows you what i mean:
[IMG]http://ww2.fs.ei.tum.de/~dr/cine_prefs.jpg[/IMG]

A Second thing is that you might **"Force single Processor use"** in for Cinelerra. You find the switch under:
Settings --> Preferences --> Performance

That should do the trick.

**Enjoy!**



**#Helpfull links for your installation:**
[http://cvs.cinelerra.org/svnusage.html](http://cvs.cinelerra.org/svnusage.html) **[ CVS-Site of Cinelerra ]**
[http://www.codepoets.co.uk/docs/mplayer_debian_sarge_compile_howto](http://www.codepoets.co.uk/docs/mplayer_debian_sarge_compile_howto) **[ Fix of the xvid ./configure error ]**
[http://www.linuxforum.com/forums/index.php?showtopic=110503](http://www.linuxforum.com/forums/index.php?showtopic=110503) **[ Fixed: tiffio.h: No such file or directory ]**
[http://www.ftconsult.com/twiki/bin/view/Cinelerra/Gentoo](http://www.ftconsult.com/twiki/bin/view/Cinelerra/Gentoo) **[ Common explenation about CVS ]**
**a.m.o.m**


**#Tutorial about how to use Cinelerra:**
[http://ftconsult.com/twiki/bin/view/Cinelerra/CinelerraManualTOC](http://ftconsult.com/twiki/bin/view/Cinelerra/CinelerraManualTOC) **[ Nice WIKI / very informative ]**
[http://robfisher.net/video/cinelerra1.html](http://robfisher.net/video/cinelerra1.html) **[ Old fashioned / Screenshot tutorial ]**
[http://heroinewarrior.com/cinelerra/cinelerra.html#THE%20MAIN%20WINDOWS](http://heroinewarrior.com/cinelerra/cinelerra.html#THE%20MAIN%20WINDOWS) **[ very extensive documentation ]**


**#Other very interesting video cutting alternatives:**
**Lives** [http://lives.sourceforge.net/](http://lives.sourceforge.net/)
**Mainconcepts mainactor** [http://www.mainconcept.com/site/index.php?id=399](http://www.mainconcept.com/site/index.php?id=399)
**Jahshaka** [www.jahshaka.org](www.jahshaka.org)
**Kino** [http://www.kinodv.org/](http://www.kinodv.org/)


**#Live-CD Video-Editing-Distros:**
**mediainlinux** [http://mediainlinux.org/](http://mediainlinux.org/)
**dynebolic.org** [http://dynebolic.org/](http://dynebolic.org/)
**VideoLinux** [http://videolinux.net/](http://videolinux.net/)

**#Cinelerra Discussion Forum:**
**Helpforum** [http://sourceforge.net/forum/forum.php?forum_id=42724](http://sourceforge.net/forum/forum.php?forum_id=42724)


**Fahrvergnügen**

/lprofil



**ps:** please feel free to correct misstakes or to add your comments!

---

### Post by eqisow on 2006-06-03
I'm glad you took the time to do this tutorial, and it will probably be helpful for many users. However, this is not the appropriate place for Howto's. They go to the [howto forum]("http://www.ubuntuforums.org/forumdisplay.php?f=100") and the [wiki]("http://wiki.ubuntu.com/").

Cheers :)

---

### Post by chainzz on 2006-06-04
Thank you for the great tutorial! I had to install a lot of packages for the autogen.sh and ./configure process, but it was pretty self-explanatory. However, now I am stuck in the make process, this is what I get:
> 
bas@ComputerBas:/opt/cinelerra_cvs/hvirtual$ sudo make
make  all-recursive
make[1]: Entering directory `/opt/cinelerra_cvs/hvirtual'
Making all in libmpeg3
make[2]: Entering directory `/opt/cinelerra_cvs/hvirtual/libmpeg3'
Making all in audio
make[3]: Entering directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/audio'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/audio'
Making all in video
make[3]: Entering directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/video'
/bin/sh ../../libtool --tag=CC --mode=link gcc -DHAVE_MMX -DUSE_MMX -DX86_CPU  -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2   -o libmpeg3_video.la   getpicture.lo headers.lo idct.lo macroblocks.lo mmxtest.lo motion.lo mpeg3video.lo output.lo reconstruct.lo seek.lo slice.lo vlc.lo mmxidct.lo reconmmx.lo   -lm -ldl -lpthread
ar cru .libs/libmpeg3_video.a .libs/getpicture.o .libs/headers.o .libs/idct.o .libs/macroblocks.o .libs/mmxtest.o .libs/motion.o .libs/mpeg3video.o .libs/output.o .libs/reconstruct.o .libs/seek.o .libs/slice.o .libs/vlc.o .libs/mmxidct.o .libs/reconmmx.o
ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1
make[3]: Leaving directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/cinelerra_cvs/hvirtual/libmpeg3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/cinelerra_cvs/hvirtual'
make: *** [all] Error 2

I tried to install libmpeg3 but it didn't work. Is there a solution to this?

---

### Post by lprofil on 2006-06-04
**@chainzz**
[QUOTE=chainzz]I tried to install libmpeg3 but it didn't work. Is there a solution to this?[/QUOTE]

Well, if you type:
```
apt-cache search libmpeg3
```

you find tree packages: mpeg3-utils libmpeg3-dev libmpeg3-1

Install them and we will see. I already added them to my first post.

**@eqisow**
[QUOTE=eqisow]However, this is not the appropriate place for Howto's.[/QUOTE] Your absolutely right! 
But i had some difficulties to post this thread anyhow, so i was just lucky to had it posted. If you are a admin **please move this thread**!

[QUOTE=eqisow]They go to the [howto forum]("http://www.ubuntuforums.org/forumdisplay.php?f=100") and the [wiki]("http://wiki.ubuntu.com/").[/QUOTE]

Thanks mate. I will take a look.

/lprofil

---

### Post by chainzz on 2006-06-04
[QUOTE=lprofil]**@chainzz**
Well, if you type:
```
apt-cache search libmpeg3
```

you find tree packages: mpeg3-utils libmpeg3-dev libmpeg3-1

Install them and we will see. I already added them to my first post.
/lprofil[/QUOTE]

I did that but it doesn't work. It looks like it wants reconmmx.o in /opt/cinelerra_cvs/hvirtual/libmpeg3/video/.libs. There are two reconmmx files in /opt/cinelerra_cvs/hvirtual/libmpeg3/video/: reconmmx.lo and reconmmx.s. Maybe I can compile them into reconmmx.o or something?

---

### Post by lprofil on 2006-06-04
[QUOTE=chainzz]... It looks like it wants reconmmx.o in /opt/cinelerra_cvs/hvirtual/libmpeg3/video/.libs. There are two reconmmx files in /opt/cinelerra_cvs/hvirtual/libmpeg3/video/: reconmmx.lo and reconmmx.s. Maybe I can compile them into reconmmx.o or something?[/QUOTE]

I have no clue, but i posted your errror message on the **[German Ubuntuusers Forum]("http://forum.ubuntuusers.de/topic/13510/45")** 
and we will see if someone knows. 

You might not speak or read german but **[this could help you anyway]("http://wiki.ubuntuusers.de/Cinelerra/")**.

/lprofil

---

### Post by chainzz on 2006-06-04
Thank you very much, I am Dutch and I learn German at school so I think I am able to read most of it.

---

### Post by dubmusic on 2006-06-04
I actually get a failure in the make process on AMD64:

Here is where it breaks:

[INDENT].libs/libquicktimehv-1.6.0.so.1.0.0
/usr/bin/ld: /usr/local/lib/libx264.a(common.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libx264.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1[/INDENT]


ANY ideas?

---

### Post by lprofil on 2006-06-04
**@dubmusic**

have you installed these packages:
libquicktime0 libquicktime-dev quicktime-x11utils quicktime-utils
?
If not you can install them via:
```
sudo apt-get install libquicktime0 libquicktime-dev quicktime-x11utils quicktime-utils
```

Hopefully they are available for the 64-bit AMD plattform. 
You can search for any package by:
```
apt-cache search the*name*of*your*package*
```

I hope this help. Please post you progress!

/lprofil

---

### Post by Rokaz on 2006-06-04
root@ubuntu:/opt/cinelerra_cvs/hvirtual# sh autogen.sh
User defined paths to the preferred autoconf and automake versions.
Read the script if you would like to modify them.
AUTOMAKE=/usr/bin/automake-1.7
ACLOCAL=/usr/bin/aclocal-1.7
AUTOCONF=autoconf
AUTOHEADER=autoheader
Now building the ./configure script...
autogen.sh: line 61: /usr/bin/automake-1.7: No such file or directory
checking for automake version... unknown
autogen.sh: line 74: /usr/bin/aclocal-1.7: No such file or directory
checking for aclocal version... unknown
Running aclocal -I m4 ...
autogen.sh: line 88: /usr/bin/aclocal-1.7: No such file or directory
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running autoheader ...
Running automake ...
autogen.sh: line 97: /usr/bin/automake-1.7: No such file or directory

any ideas ? ](*,)

---

### Post by chainzz on 2006-06-04
[QUOTE=Rokaz]root@ubuntu:/opt/cinelerra_cvs/hvirtual# sh autogen.sh
User defined paths to the preferred autoconf and automake versions.
Read the script if you would like to modify them.
AUTOMAKE=/usr/bin/automake-1.7
ACLOCAL=/usr/bin/aclocal-1.7
AUTOCONF=autoconf
AUTOHEADER=autoheader
Now building the ./configure script...
autogen.sh: line 61: /usr/bin/automake-1.7: No such file or directory
checking for automake version... unknown
autogen.sh: line 74: /usr/bin/aclocal-1.7: No such file or directory
checking for aclocal version... unknown
Running aclocal -I m4 ...
autogen.sh: line 88: /usr/bin/aclocal-1.7: No such file or directory
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running autoheader ...
Running automake ...
autogen.sh: line 97: /usr/bin/automake-1.7: No such file or directory

any ideas ? ](*,)[/QUOTE]
I had this problem too. You need to install automake-1.7 with Synaptic or do this:
```
sudo apt-get install automake-1.7
```

---

### Post by lprofil on 2006-06-04
[QUOTE=chainzz]I had this problem too. You need to install automake-1.7 with Synaptic or do this:
```
sudo apt-get install automake-1.7
```[/QUOTE]

This is slightly wrong. The packages name is **automake1.7** not automake**-"minus"-**1.7

Type:
```
sudo apt-get install automake1.7
```

Thanks for the hint. i updated point 7 of my tutorial.

/lprofil

---

### Post by JMO707 on 2006-06-04
chainzz, have you solved that problem?
 I get exactly the same error, but with a "larger" make.

And I dont know german =(

---

### Post by remarks on 2006-06-05
I am getting the same "make" failure:

```
root@dc7100:/opt/cinelerra_cvs/hvirtual# make make  all-recursive make[1]: Entering directory `/opt/cinelerra_cvs/hvirtual' Making all in libmpeg3 make[2]: Entering directory `/opt/cinelerra_cvs/hvirtual/libmpeg3' Making all in audio make[3]: Entering directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/audio'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/audio'
Making all in video
make[3]: Entering directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/video'
/bin/sh ../../libtool --tag=CC --mode=link gcc -DHAVE_MMX -DUSE_MMX -DX86_CPU  -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2   -o libmpeg3_video.la   getpicture.lo headers.lo idct.lo macroblocks.lo mmxtest.lo motion.lo mpeg3video.lo output.lo reconstruct.lo seek.lo slice.lo vlc.lo mmxidct.lo reconmmx.lo   -lm -ldl -lpthread
ar cru .libs/libmpeg3_video.a .libs/getpicture.o .libs/headers.o .libs/idct.o .libs/macroblocks.o .libs/mmxtest.o .libs/motion.o .libs/mpeg3video.o .libs/output.o .libs/reconstruct.o .libs/seek.o .libs/slice.o .libs/vlc.o .libs/mmxidct.o .libs/reconmmx.o
ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1
make[3]: Leaving directory `/opt/cinelerra_cvs/hvirtual/libmpeg3/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/cinelerra_cvs/hvirtual/libmpeg3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/cinelerra_cvs/hvirtual'
make: *** [all] Error 2

```

and I have the following installed:
```
# apt-get install libmpeg3-1 libmpeg3-dev
Reading package lists... Done
Building dependency tree... Done
libmpeg3-1 is already the newest version.
libmpeg3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by chainzz on 2006-06-05
[QUOTE=lprofil]This is slightly wrong. The packages name is **automake1.7** not automake**-"minus"-**1.7

Type:
```
sudo apt-get install automake1.7
```

Thanks for the hint. i updated point 7 of my tutorial.

/lprofil[/QUOTE]
Oh yeah, that's right, my fault.

[QUOTE=JMO707]chainzz, have you solved that problem?
 I get exactly the same error, but with a "larger" make.

And I dont know german =([/QUOTE]
No, I haven't solved the problem yet, I also talked about it in the IRC channel that's mentioned on cvs.cinelerra.org, and they say that it's a problem that a lot of people experience and that they don't really know the solution yet.

---

### Post by JMO707 on 2006-06-05
A shame... -_-

I really need a video edition tool. My sister is over my shoulders saying to me "how bad is Linux" because I cant install what she need =P

---

### Post by lprofil on 2006-06-05
[QUOTE=JMO707]chainzz, have you solved that problem?
 I get exactly the same error, but with a "larger" make.[/QUOTE]

Please quote your "lager" make output for better understanding.

Besides - there are also other less sophisticated video-cutting tools like:

avidemux [for cutting]
acidrip     [for encodiing]
kino         [for both?]
etc.

/lprofil

---

### Post by cbudden on 2006-06-05
I am also getting the libmpeg3 error.  lprofil, could you make a .deb for us please?

---

### Post by lprofil on 2006-06-05
Have you tried:
sudo apt-get install mpeg3-utils libmpeg3-dev libmpeg3-1

---

### Post by chainzz on 2006-06-05
[QUOTE=cbudden]I am also getting the libmpeg3 error.  lprofil, could you make a .deb for us please?[/QUOTE]
Yeah, that would be great!

---

### Post by chainzz on 2006-06-06
Hello guys,
Just wanted to say that I finally found a solution to the reconmmx.o problem. You need to compile the *reconmmx.s* file that's in *hvirtual/libmpeg3/video* into *reconmmx.o* and place that in *hvirtual/libmpeg3/video/.libs*.

First you need to install a package called *nasm*:
```
sudo apt-get install nasm
```
**(thanks to jstewart from #cinelerra @ irc.freenode.net for advising me to install nasm)**

Then open a console and *cd* to *hvirtual/libmpeg3/video*. Then execute the following command:
```
sudo nasm -f elf reconmmx.s -o reconmmx.o
```
Then copy the freshly compiled *reconmmx.o* into *hvirtual/libmpeg3/video/.libs*:
```
sudo cp reconmmx.o .libs/
```

This will solve the problem. After this I encountered another problem, something with xf86, I don't know the exact errormessage anymore but I solved it by doing this:
```
sudo apt-get install libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev
```

---

### Post by chainzz on 2006-06-06
I managed to build a Debian package without any dependencies with checkinstall, if anybody wants it just say it and I will try to get it hosted somewhere.

---

### Post by strikeforce on 2006-06-07
[QUOTE=chainzz]I managed to build a Debian package without any dependencies with checkinstall, if anybody wants it just say it and I will try to get it hosted somewhere.[/QUOTE]


I would be interested in this.

---

### Post by chainzz on 2006-06-07
I uploaded the Debian package here: [http://www.filefactory.com/?e71231](http://www.filefactory.com/?e71231)
Does somebody know if it's possible to contribute this to cvs.cinelerra.org? The current Ubuntu repository there isn't working for 99% of the people. If enough people want it, I can make Debian packages of Cinelerra-CVS every month or so, I only need a good place to host them.

---

### Post by lprofil on 2006-06-07
Hi chainzz,

[QUOTE=chainzz]Hello guys,
Just wanted to say that I finally found a solution to the reconmmx.o problem. [/QUOTE]

Thanks a lot. I totally forgot about the **nams** and **yasm** issue. 
I updated my first post and of course mentioned your great work and the help of jstewart from #cinelerra @ irc.freenode.net.

This is what i call community! Thanks for all of you.

/lprofil

---

### Post by chainzz on 2006-06-07
Thank you for mentioning it in the openingpost. I will try to compile a new Debian package as often as possible because the CVS is changing everyday. I will ask in the Cinelerra IRC channel if they need somebody to compile working Debian packages, the packages I compile don't have any dependencies, the Ubuntu repository on cvs.cinelerra.org has a lot of dependencies and that's why a lot of people have a hard time installing it (including me).

edit: I uploaded the Debian package to a better place: [http://s7.quicksharing.com/v/7553351/cinelerra_cvs_2.0.0_3svn20060606_1_i386.deb.html](http://s7.quicksharing.com/v/7553351/cinelerra_cvs_2.0.0_3svn20060606_1_i386.deb.html)
Iprofil, can you put this in your openingpost? You can leave the Filefactory link there too in case one of the 2 hosts is down.

---

### Post by lprofil on 2006-06-08
[QUOTE=chainzz]Thank you for mentioning it in the openingpost.[/QUOTE]

You are very welcome!

[QUOTE=chainzz]
edit: I uploaded the Debian package to a better place ... Iprofil, can you put this in your openingpost?[/QUOTE]

Done!

---

### Post by chainzz on 2006-06-08
Thank you very much!

---

### Post by napthali on 2006-06-19
I'm have the same trouble that dubmusic had a little while back in the thread. Namely, this error during make: 

```
/usr/bin/ld: /usr/lib/libx264.a(common.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libx264.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/opt/cinelerra/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/cinelerra/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/cinelerra/hvirtual'
make: *** [all] Error 2

```

When I try to update to ensure I have the write libraries: 

```
$ /opt/cinelerra/hvirtual$ sudo apt-get install libquicktime0 libquicktime-dev quicktime-x11utils quicktime-utils
Reading package lists... Done
Building dependency tree... Done
libquicktime0 is already the newest version.
libquicktime-dev is already the newest version.
quicktime-x11utils is already the newest version.
quicktime-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any other thoughts on what might be causing this? It looks like adding a flag to the compilation might help, but this is a pretty complex program and I'm hesitant to muck about in the makefile. 

I'm running Dapper on AMD-64, if that makes a difference.

---

### Post by lprofil on 2006-06-20
Hi,

[QUOTE=napthali]I'm running Dapper on AMD-64, if that makes a difference.[/QUOTE]

Have you installed the 64-bit version of Dapper Drake?

Chainz did also had some dependecy problems with the latest Cinelerra Compilations. Me too - so i just sticked to the "old" deb-file of him.

/lprofil

---

### Post by napthali on 2006-06-20
I am using the 64-bit version of Dapper -- is that a mistake? 

I tried the deb file, but it's only for 32-bit systems. :-(

---

### Post by lprofil on 2006-06-20
not a misstake, but you might have some difficulties because of the 64-bit Version you are using.

---

### Post by napthali on 2006-06-20
Hmmm. Should I consider dropping back to the 32-bit version, then? I thought Cinelerra was much more stable under 64?

---

### Post by lprofil on 2006-06-20
[QUOTE=napthali]Hmmm. Should I consider dropping back to the 32-bit version[/QUOTE]

No, please do not! You might waste a lot of encoding perdormance with the 32-bit Version. Keep it and let us fix your problems step by step. 

i am currently searching for a site for cinelerra "Dapper Drake" deb-files for 64-bit.
As i found it i will post you the link.

Man, i envy you about your nice 64-bit AMD-Processor...  :-/

/lprofil

---

### Post by lprofil on 2006-06-20
Here you go:
[http://www.kiberpipa.org/~gandalf/ubuntu/dapper/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/)

---

### Post by lprofil on 2006-06-20
[QUOTE=napthali]/usr/bin/ld: /usr/lib/libx264.a(common.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC[/QUOTE]

To come back to your issue...

Have you tried to recompile with the -fPIC flag?

/lprofil

---

### Post by kc8hr on 2006-06-22
Thank you very much for the Cinelerra package!

I do a lot of video work, and the lack of a Cinelerra package in the repositories was disappointing when I switched from Mandriva to Ubuntu. There are few good non-linear video editing programs on the Linux platform as it is, and while Cinelerra is far from perfect, it is the best I have found.

Later--
Tim

---

### Post by lprofil on 2006-06-22
Welcome Tim,

thank you for your feedback!
I assume it worked for you right away.

What are your top video-editing suggestions for linux besides Cinelerra?

/lprofil

---

### Post by kc8hr on 2006-06-22
[QUOTE=lprofil]Welcome Tim,

thank you for your feedback!
I assume it worked for you right away.

What are your top video-editing suggestions for linux besides Cinelerra?

/lprofil[/QUOTE]I also use avidemux [http://avidemux.sourceforge.net/]("http://avidemux.sourceforge.net/"). I have also tried most of the others available including PiTiVi, kdenlive, kino, MainActor and jahshaka.

While it is poorly documented, cinelerra works the best for me.

Later--
Tim

---

### Post by werty on 2006-06-26
HI
I downloaded the cinelerra cvs package and installed it.
There was no error in the installation. but when i open cinelerra
from the teminal i get this error:

cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

What is wrong?

Thanks in advance

---

### Post by lprofil on 2006-06-27
Hi werty,

it might be that the faac libaries are missing.
To be sure try to install all faac libaries:
```
sudo apt-get install libfaac0 libfaac-dev  gstreamer0.8-faac faac 
```

and try to compile Cinelerra from sources again.

/lprofil

---

### Post by BrandonSmith15 on 2006-06-30
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../quicktime -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT bcbitmap.lo -MD -MP -MF .deps/bcbitmap.Tpo -c bcbitmap.C  -fPIC -DPIC -o .libs/bcbitmap.o
In file included from bcbitmap.C:1:
bcbitmap.h:7:33: error: X11/extensions/XShm.h: No such file or directory
bcbitmap.h:8:34: error: X11/extensions/Xvlib.h: No such file or directory
bcbitmap.h:144: error: ISO C++ forbids declaration of 'XvImage' with no type
bcbitmap.h:144: error: expected ';' before '*' token
bcbitmap.h:145: error: 'XShmSegmentInfo' does not name a type
bcbitmap.C: In member function 'int BC_Bitmap::initialize(BC_WindowBase*, int, int, int, int)':
bcbitmap.C:76: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::allocate_data()':
bcbitmap.C:142: error: 'xv_image' was not declared in this scope
bcbitmap.C:148: error: expected primary-expression before ')' token
bcbitmap.C:148: error: 'XvShmCreateImage' was not declared in this scope
bcbitmap.C:150: error: expected unqualified-id before '.' token
bcbitmap.C:153: error: expected primary-expression before '.' token
bcbitmap.C:154: error: expected primary-expression before 'unsigned'
bcbitmap.C:154: error: expected `)' before 'unsigned'
bcbitmap.C:156: error: expected primary-expression before '.' token
bcbitmap.C:157: error: expected unqualified-id before '.' token
bcbitmap.C:173: error: expected primary-expression before ')' token
bcbitmap.C:200: error: expected primary-expression before ',' token
bcbitmap.C:202: error: 'XShmCreateImage' was not declared in this scope
bcbitmap.C:205: error: expected unqualified-id before '.' token
bcbitmap.C:208: error: expected primary-expression before '.' token
bcbitmap.C:210: error: expected primary-expression before 'unsigned'
bcbitmap.C:210: error: expected `)' before 'unsigned'
bcbitmap.C:211: error: expected primary-expression before '.' token
bcbitmap.C:212: error: expected unqualified-id before '.' token
bcbitmap.C:227: error: expected primary-expression before ',' token
bcbitmap.C:236: error: expected primary-expression before ')' token
bcbitmap.C:236: error: 'XShmAttach' was not declared in this scope
bcbitmap.C:242: error: expected primary-expression before '.' token
bcbitmap.C: In member function 'int BC_Bitmap::delete_data()':
bcbitmap.C:316: error: 'XvStopVideo' was not declared in this scope
bcbitmap.C:319: error: 'xv_image' was not declared in this scope
bcbitmap.C:321: error: expected primary-expression before ')' token
bcbitmap.C:321: error: 'XShmDetach' was not declared in this scope
bcbitmap.C:322: error: 'XvUngrabPort' was not declared in this scope
bcbitmap.C:324: error: expected primary-expression before '.' token
bcbitmap.C:325: error: expected primary-expression before '.' token
bcbitmap.C:334: error: expected primary-expression before ')' token
bcbitmap.C:336: error: expected primary-expression before '.' token
bcbitmap.C:337: error: expected primary-expression before '.' token
bcbitmap.C: In member function 'int BC_Bitmap::write_drawable(Drawable&, _XGC*&, int, int, int, int, int, int, int, int, int)':
bcbitmap.C:445: error: 'xv_image' was not declared in this scope
bcbitmap.C:454: error: 'XvShmPutImage' was not declared in this scope
bcbitmap.C:479: error: 'XShmPutImage' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::read_drawable(Drawable&, int, int)':
bcbitmap.C:515: error: 'XShmGetImage' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_id()':
bcbitmap.C:624: error: expected primary-expression before '.' token
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_size()':
bcbitmap.C:629: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_offset()':
bcbitmap.C:637: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_y_shm_offset()':
bcbitmap.C:648: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_u_shm_offset()':
bcbitmap.C:656: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_v_shm_offset()':
bcbitmap.C:664: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_y_offset()':
bcbitmap.C:672: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_u_offset()':
bcbitmap.C:680: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_v_offset()':
bcbitmap.C:688: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_y_plane()':
bcbitmap.C:714: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_v_plane()':
bcbitmap.C:723: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_u_plane()':
bcbitmap.C:732: error: 'xv_image' was not declared in this scope
make[2]: *** [bcbitmap.lo] Error 1
make[2]: Leaving directory `/opt/cinelerra_cvs/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/cinelerra_cvs/hvirtual'
make: *** [all] Error 2
root@brandon-desktop:/opt/cinelerra_cvs/hvirtual#


im  geting that i need help

---

### Post by chainzz on 2006-07-03
> **napthali]I'm have the same trouble that dubmusic had a little while back in the thread. Namely, this error during make: 

```
/usr/bin/ld: /usr/lib/libx264.a(common.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object said:**
> : *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/opt/cinelerra/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/cinelerra/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/cinelerra/hvirtual'
make: *** [all] Error 2

```

When I try to update to ensure I have the write libraries: 

```
$ /opt/cinelerra/hvirtual$ sudo apt-get install libquicktime0 libquicktime-dev quicktime-x11utils quicktime-utils
Reading package lists... Done
Building dependency tree... Done
libquicktime0 is already the newest version.
libquicktime-dev is already the newest version.
quicktime-x11utils is already the newest version.
quicktime-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any other thoughts on what might be causing this? It looks like adding a flag to the compilation might help, but this is a pretty complex program and I'm hesitant to muck about in the makefile. 

I'm running Dapper on AMD-64, if that makes a difference.
I also tried to compile Cinelerra on AMD64 but after running into a lot of problems I just gave up.

---

### Post by lime4x4 on 2006-07-04
having the same error about symbolic look up here is a copy of the error and when i try to install the missing dependencies it wants to remove alot of other stuff as well esp mencoder

john@ubuntu:~$ cinelerra
cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen
john@ubuntu:~$ sudo apt-get install libfaac0 libfaac-dev  gstreamer0.8-faac faacReading package lists... Done
Building dependency tree... Done
libfaac0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfaac-dev: Depends: libmp4-dev but it is not going to be installed
E: Broken packages
john@ubuntu:~$ sudo apt-get install libmp4-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmp4-dev: Depends: libmp4-0 (= 2.0.0-0.2) but it is not going to be installed
E: Broken packages
john@ubuntu:~$ sudo apt-get install libmp4-0
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libmp4v2-0 libmp4v2-dev mencoder mencoder-686 mozilla-mplayer mplayer
  mplayer-fonts xmms-xmmplayer
The following NEW packages will be installed:
  libmp4-0
0 upgraded, 1 newly installed, 8 to remove and 2 not upgraded.
Need to get 238kB of archives.
After unpacking 25.7MB disk space will be freed.
Do you want to continue [Y/n]?

So i'm pretty sure i don't want to lose mencoder or mplayer either

---

### Post by chainzz on 2006-07-07
Cinelerra has a new release! 2.1 has been released on 7/2/06. Check [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3) for more info.

---

### Post by chainzz on 2006-07-07
BrandonSmith15,

I had this problem too, After doing a 'xv lib' search in Synaptic I found the package libxv-dev, install this and your problem is solved!

---

### Post by chainzz on 2006-07-14
I wrote a tutorial (based on this tutorial) on how to compile Cinelerra on 64-bit Ubuntu: [http://www.ubuntuforums.org/showthread.php?t=215252](http://www.ubuntuforums.org/showthread.php?t=215252)

---

### Post by hollip3020 on 2006-07-14
im running dapper on amd64 as well and i get the same quicktime errors.

chainzz: i tried your tut as well but i still get the errors.

anyone figure this out yet?

---

### Post by chainzz on 2006-07-16
Did you remove the x264 packages before compiling it yourself? Please post the error message.

---

### Post by NESFreak on 2006-07-17
Cinelerra Ubuntu Instructions
(last updated 17th June 2006)

Installing Cinelerra on Ubuntu, the new way.

Ubuntu doesn't play very well with Marillat's Debian repository. So I am
currently also providing packages that are not in Ubuntu.

Current instructions are for Ubuntu 5.10 (Breezy) and 6.06 (Dapper). 5.04 (Hoary) is not supported.

Setting up repositories:

1. Enable universe, multiverse and restricted

Make sure you have following line uncommented in your /etc/apt/sources.list

for breezy:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse restricted

for dapper:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse restricted

2. Add mjpegtools ubuntu backport

for breezy:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools) ./

for dapper:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./

3. Add cinelerra build for your arch:

for breezy:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/) ./

for dapper:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

Installation:

apt-get install cinelerra


---

This repository is being maintained by Jure Cuhalev (gandalf -at- owca.info)
(please drop me a mail if things break, I'm currently not running Ubuntu on my
workstation so I have to really on your info)

I will also announce new builds on my blog in categorie Ubuntu:
[http://www.kiberpipa.org/~gandalf/blog/?cat=11](http://www.kiberpipa.org/~gandalf/blog/?cat=11)


isn't this way easier?
just followed the link at [http://cvs.cinelerra.org/getting_cinelerra.html](http://cvs.cinelerra.org/getting_cinelerra.html)

---

### Post by lime4x4 on 2006-07-17
followed everything it said to do and this is the error i'm getting when starting it thru command line

john@ubuntu:~$ cinelerra
cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

---

### Post by chainzz on 2006-07-18
NESfreak:
The packages are not up to date most of the time, I always want the newest release, that's why I compile Cinelerra myself.

Lime4x4:
I don't know what the problem is, check the mailinglists, I'm sure somebody else must have had the problem before: [http://cvs.cinelerra.org/mailinglists.php](http://cvs.cinelerra.org/mailinglists.php)
Or ask it in the Cinelerra IRC channel, irc.freenode.net:6667 #cinelerra.

And now I will go on vacation for 3 weeks, so unfortunately I cannot respond to any questions from now on. I'm back on the 4th of August, I hope 2.1 is merged into the CVS by then!

---

### Post by hkl8324 on 2006-08-01
I got this...

```
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../guicast -I../../cinelerra -I../../quicktime -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT zoomblur.lo -MD -MP -MF .deps/zoomblur.Tpo -c zoomblur.C  -fPIC -DPIC -o .libs/zoomblur.o
/bin/sh ../../libtool --tag=CXX --mode=link g++ -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2   -o zoomblur.la -rpath /usr/local/lib/cinelerra -module -shared -avoid-version zoomblur.lo  -lm -ldl -lpthread
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.0.3/crtbeginS.o  .libs/zoomblur.o  -ldl -lpthread -L/usr/lib/gcc/i486-linux-gnu/4.0.3 -L/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib -L/usr/lib/gcc/i486-linux-gnu/4.0.3/../../.. -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.0.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crtn.o  -Wl,-soname -Wl,zoomblur.so -o .libs/zoomblur.so
creating zoomblur.la
(cd .libs && rm -f zoomblur.la && ln -s ../zoomblur.la zoomblur.la)
make[3]: Leaving directory `/home/hkl8324/hvirtual/plugins/zoomblur'
Making all in fonts
make[3]: Entering directory `/home/hkl8324/hvirtual/plugins/fonts'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/hkl8324/hvirtual/plugins/fonts'
make[3]: Entering directory `/home/hkl8324/hvirtual/plugins'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/hkl8324/hvirtual/plugins'
make[2]: Leaving directory `/home/hkl8324/hvirtual/plugins'
Making all in po
make[2]: Entering directory `/home/hkl8324/hvirtual/po'
make cinelerra.pot-update
make[3]: Entering directory `/home/hkl8324/hvirtual/po'
make[3]: *** No rule to make target `../plugins/chromakey-hsv/chromakey.C', needed by `cinelerra.pot-update'.  Stop.
make[3]: Leaving directory `/home/hkl8324/hvirtual/po'
make[2]: *** [cinelerra.pot] Error 2
make[2]: Leaving directory `/home/hkl8324/hvirtual/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hkl8324/hvirtual'
make: *** [all] Error 2

```

Any thoughts?

---

### Post by lprofil on 2006-08-01
Hello hkl8324,

could you be a bit more verbose?

What are your systemspecs?

Did you use the cvs method?
Have you gone through all steps?
Do you get this error during the make process?

/lprofil

---

### Post by hkl8324 on 2006-08-01
> **lprofil said:**
> Hello hkl8324,

could you be a bit more verbose?

What are your systemspecs?

Did you use the cvs method?
Have you gone through all steps?
Do you get this error during the make process?

/lprofil

What do you mean "more verbose"? Copy a longer CLI output:confused: 

Sysspec: Pentium M 1.4 Banius, 768MB ram, Mobility Radeon Card using the xorg "radeon" driver
 
Yes, I downloaded through CVS yestersday.
And yes, I went through all the stops but I dont have libiec61883-dev and libraw1394-5 (I dont know why, I just changed the repo URL from "de" to "jp", and apt-get said package not found)
, ./configure said I "just" will not have IEEE1394 support (and I can live without that...)

FYI, ./configure said yes to all of the "mandatory package"

Yes, I got this message during the make process

---

### Post by lprofil on 2006-08-02
```
make[3]: *** No rule to make target `../plugins/chromakey-hsv/chromakey.C', needed by `cinelerra.pot-update'.  Stop.
```

What we read here, is that the compiler is complaining about a missing c-file. 
**chromakey.C** by name.
You just have to create a folder called /plugins/chromakey-hsv in you cvs path:
```
user@whatever:~$ cd /opt/hvirtual
mkdir /plugins/chromakey-hsv

```
Now search for the file an put it into the new folder.
Use the search-option in your ubuntu menue:
Places --> Search for Files...
and select the CVS-folder e.g /opt/hvirtual.


Now you copy the file into the right folder:
[CODE]cp plugins/chromakeyhsv/* plugins/chromakey-hsv[/CODE

It should work now. With the next error of the same type. But do not worry. There are only two of that type.

Actually i descried all that in point 8 of my tutorial. 
You might flush your browser-cache because i made the last changes of my tutorial few days ago.

/lprofil

---

### Post by hkl8324 on 2006-08-02
> **lprofil said:**
> Do you mean apt-get is complaining that it does not find the packages?
If you did a:
```
sudo apt-get update
```
and it does not find the packages (because here it does) check your 
apt-get sources list first. If there is nothing wrong with it change the URI to whatever DE for example and try again.

This might already fix your problem.




If it does not work as dicrieb above, well then i really don not know. 
Chainzz should be back in a few days. Let's see if he might help us.

/lprofil

Changed to DE...and grabbed those two package...but...run ./configure again  but....I still have the exact same error....](*,)

---

### Post by lprofil on 2006-08-02
see above, i edited my replay again.
I had exactely the same error message until i added point 8 to my tutorial.

/lprofil

---

### Post by Darrious on 2006-08-08
I do ./configure and it comes up with this.

```
root@linux:/opt/hvirtual# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for linux/videodev2.h... no
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.2... not present.
configure: error: Sufficiently new version of libasound not found.
root@linux:/opt/hvirtual#

```
It says that libasound is not found. I just decided to skip that and typed make but it came up with.
```
root@linux:/opt/hvirtual# make
make: *** No targets specified and no makefile found.  Stop.
root@linux:/opt/hvirtual#

```
What do I do? ](*,) ](*,)

---

### Post by qrm on 2006-08-08
Im using the easy way, the deb package, and cant get cinelerra to work:

```
ats@zanzhu:~$ cinelerra
cinelerra: error while loading shared libraries: libIlmImf.so.2: cannot open shared object file: No such file or directory
```

while installing the dependencies it found that i had everything the newest already but: 

```
E: Couldn't find package libiec61883-dev
```

I have modified my sources.list and have everything as theyre supposed to be.

Help greatly appreciated

---

### Post by lprofil on 2006-08-08
```
apt-cache search and-here-is-the-name-of-the-missing-pakage
```


**@ qrm**
do 
```
apt-cache search libiec61883-dev
```

and it will tell you:
```
libiec61883-dev - reception and transmission for DV, MPEG2-TS, and AMDTP using raw1394
```

do
```
sudo apt-get install libiec61883-dev
```

and "configure" and "make" again


**@ Darrious**
do
```
 apt-cache search libasound

```

and it will tell you:
```
libasound2 - ALSA library
libasound2-dev - ALSA library development files
libasound2-doc - ALSA library developer documentation
libasound2-plugins - ALSA library additional plugins
gimp - The GNU Image Manipulation Program

```

What do you guess is the right pakage for you?
Yes, libasound2 and maybe libasound2-dev

Install both:
```
sudo apt-get install libasound2 libasound2-dev
```

**Fahrvergnügen**

/lprofil

ps: i updated my tutorial. Thanks for asking-->helping

---

### Post by Zyith on 2006-08-09
I'm running up against the same problem as qrm:

```
sudo apt-get install libiec61883-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libiec61883-dev

```

Sources list copied and pasted from the article, apt-get update ran and everything. :-(

---

### Post by lprofil on 2006-08-09
Go to:
[http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/)

download this package:

libiec61883-dev_1.0.0-0.1_i386.deb

and install it via:
```
sudo dpkg -i libiec*
```

Now it should work.

/lprofil

---

### Post by sblanzio on 2006-08-09
> **lime4x4 said:**
> having the same error about symbolic look up here is a copy of the error and when i try to install the missing dependencies it wants to remove alot of other stuff as well esp mencoder
...
libfaac0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfaac-dev: Depends: libmp4-dev but it is not going to be installed
E: Broken packages


go here:

[http://packages.ubuntulinux.org/dapper/libdevel/](http://packages.ubuntulinux.org/dapper/libdevel/)

download libfaac0 and libfaac-dev

then open the folder you downloaded them and click right button on libfaac-dev

select kubuntu package menu (or ubuntu equivalent) -> install

prompt your password when asked and repeat for libfaac-dev

for me this worked.

bye!

---

### Post by sblanzio on 2006-08-09
> 
**#8.** A Little Bug-Fixing
It is the 29th of July today and there is still this nasty 
bug during the compiling process. I do not want to bother you with details
but there some path-names for plugins changed and the compiler does
not find them at the right place.

To fix the **first error** type:
```
cd /opt/hvirtual
```
```
sudo mkdir plugins/chromakey-hsv && cp plugins/chromakeyhsv/* plugins/chromakey-hsv
```

To fix the **second error** type:
```
sudo mkdir plugins/seltempavg && cp plugins/denoiseseltempavg/* plugins/seltempavg
```


to me this didn't work because it said "operation not permitted" (or somthing like this)

so I did it step by step: mkdir <dir name> -> cd <dir name> -> cp ....

for both steps. it worked.

bye!

---

### Post by Darrious on 2006-08-09
For some reason make is not working

---

### Post by Zyith on 2006-08-13
I just want to give big thanks to lprofil, because I got Cinelerra working.

Thanks so much. I was like this: ](*,) and now I'm like: :-D

---

### Post by qrm on 2006-08-14
my sources file:```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://ee.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://ee.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe main restricted multiverse

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse restricted

```

when I apt-cahce 8search9 for teh libiec file it doesnt find anything. the lprofils suggested package starts to complin bout dependencies which are a bit over my head:

LOL, trying to reproduce the dependencie errors it now tells me that all dependencies are sactisfied :D dunno how that happened but ... the mysteries of linux which is alien technology 

now when i try to open up cinelerra i get the following error:

cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: NeAACDecDecode

---

### Post by AIysandra on 2006-08-16
Hi someone pls help I can't even do the first step of this tutorial

fion@Home:~$ sudo apt-get -f  install subversion
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  debootstrap: Depends: binutils but it is not going to be installed
  subversion: Depends: libapr0 (>= 2.0.55) but it is not going to be installed
              Depends: libsvn0 (>= 1.3.0) but it is not going to be installed
              Depends: libsvn0 (= 1.3.1-3ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I'm a total noob so don't know how to proceed. I tried to continue:

fion@Home:/opt$ sudo svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/ hvirtual
sudo: svn: command not found

What shd i do now :confused:

---

### Post by onesojourner on 2006-08-17
I am getting this error

svn: Can't connect to host 'cvs.cinelerra.org': Connection refused

why is this?

---

### Post by Chris Tucker on 2006-08-18
I'm using the debain file [http://s7.quicksharing.com/v/7553351/cinelerra_cvs_2.0.0_3svn20060606_1_i386.deb.html]("http://s7.quicksharing.com/v/7553351/cinelerra_cvs_2.0.0_3svn20060606_1_i386.deb.html"), and i did come across one error... ```
cinelerra: error while loading shared libraries: libmjpegutils-1.8.so.0: cannot open shared object file: No such file or directory

```
So, i got that from the repositories... i have nasm and yasm and libmpeg3 from an attempt to install from the source on the official website (which failed... it doesnt seem to like i686... even tried dropping down to 386 for the compile... still complained about i686.)
Now cinelerra runs, i can edit things and learn it all, but when i try to render, it crashes after a few frames.. no errors other than ```
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory

```
from the startup, and
```
    0x8d418d8 File::write_lock File::write_frames *
BC_Signals::dump_buffers: buffer table size=0
BC_Signals::delete_temps: deleting 0 temp files
SigHandler::signal_handler total files=1
Closing /home/kai/test1.avi
kai@kai-desktop:~/
```
are the last few lines that appear... nothing intresting in the other events that come up, they look like they came from before rendering started...
what am i missing?

edit: details:
This appears immediatly when cinelerra is run:
```
Cinelerra 2.0CV Tue Jun  6 19:59:13 CEST 2006 (C)2005 Heroine Virtual Ltd.

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory
PluginServer::open_plugin: libfftw3.so.3: cannot open shared object file: No such file or directory

```
and this appears immediatly when it tries to render:
```
signal_entry: got SIGSEGV my pid=26240 execution table size=72:
    vrender.C: process_buffer: 171
    virtualvconsole.C: process_buffer: 60
    virtualvconsole.C: process_buffer: 71
    virtualvconsole.C: process_buffer: 75
    virtualvconsole.C: process_buffer: 107
    vrender.C: process_buffer: 173
    vrender.C: process_buffer: 109
    vrender.C: process_buffer: 116
    vrender.C: get_colormodel: 323
    vrender.C: get_colormodel: 326
    vrender.C: process_buffer: 119
    vrender.C: process_buffer: 124
    vrender.C: process_buffer: 171
    virtualvconsole.C: process_buffer: 60
    virtualvconsole.C: process_buffer: 71
    virtualvconsole.C: process_buffer: 75
    virtualvconsole.C: process_buffer: 107
    vrender.C: process_buffer: 173
    vrender.C: process_buffer: 109
    vrender.C: process_buffer: 116
    vrender.C: get_colormodel: 323
    vrender.C: get_colormodel: 326
    vrender.C: process_buffer: 119
    vrender.C: process_buffer: 124
    vrender.C: process_buffer: 171
    virtualvconsole.C: process_buffer: 60
    virtualvconsole.C: process_buffer: 71
    virtualvconsole.C: process_buffer: 75
    virtualvconsole.C: process_buffer: 107
    vrender.C: process_buffer: 173
    vrender.C: process_buffer: 109
    vrender.C: process_buffer: 116
    vrender.C: get_colormodel: 323
    vrender.C: get_colormodel: 326
    vrender.C: process_buffer: 119
    vrender.C: process_buffer: 124
    vrender.C: process_buffer: 171
    virtualvconsole.C: process_buffer: 60
    virtualvconsole.C: process_buffer: 71
    virtualvconsole.C: process_buffer: 75
    virtualvnode.C: render: 137
    virtualvnode.C: render_as_module: 186
    virtualvnode.C: read_data: 86
    virtualvnode.C: read_data: 89
    module.C: update_transition: 218
    module.C: update_transition: 224
    module.C: update_transition: 234
    vmodule.C: render: 368
    vmodule.C: render: 373
    vmodule.C: render: 449
    vmodule.C: import_frame: 96
    vmodule.C: import_frame: 104
    vmodule.C: import_frame: 118
    file.C: open_file: 313
    vmodule.C: import_frame: 120
    vmodule.C: import_frame: 140
    vmodule.C: import_frame: 185
    vmodule.C: import_frame: 243
    filempeg.C: read_frame: 1023
    filempeg.C: read_frame: 1030
    filempeg.C: read_frame: 1101
    vmodule.C: import_frame: 245
    vmodule.C: import_frame: 319
    vmodule.C: render: 455
    virtualvnode.C: render_as_module: 204
    virtualvnode.C: render_as_module: 211
    virtualvnode.C: render_as_module: 221
    virtualvnode.C: render_as_module: 238
    virtualvnode.C: render_as_module: 248
    virtualvnode.C: render: 142
    virtualvconsole.C: process_buffer: 107
    vrender.C: process_buffer: 173
signal_entry: lock table size=12
    0x896d2a0 BC_WindowBase::event_condition BC_WindowBase::get_event
    0x88acad8 BC_WindowBase::event_condition BC_WindowBase::get_event
    0x894b9c8 BC_WindowBase::event_condition BC_WindowBase::get_event
    0x8aa1f80 BC_WindowBase::event_condition BC_WindowBase::get_event
    0x87c3db0 BC_WindowBase::event_condition BC_WindowBase::get_event
    0x8a10980 BC_WindowBase::event_condition BC_WindowBase::get_event
    0x8d48238 LoadPackage::completion_lock LoadServer::process_packages 1 *
    0x8d489a0 LoadClient::input_lock LoadClient::run *
    0x8d489a0 LoadClient::input_lock LoadClient::run
    0x8d48198 LoadClient::completion_lock LoadServer::process_packages 2 *
    0x8d2bc30 FileThread::file_lock FileThread::run 2 *
    0x8cdbe68 File::write_lock File::write_frames *
BC_Signals::dump_buffers: buffer table size=0
BC_Signals::delete_temps: deleting 0 temp files
SigHandler::signal_handler total files=1
Closing /home/kai/test1.avi
kai@kai-desktop:~/
```
with nothing appearing in between.

---

### Post by Chris Tucker on 2006-08-18
i followed [http://www.ubuntuforums.org/showpost.php?p=1266758&postcount=50]("http://www.ubuntuforums.org/showpost.php?p=1266758&postcount=50")
and still got the problem, i fixed it by (in the render dialog) clicking video settings, and changing it from Component to mpeg4.. dunno what other codecs work yet... but its working at least :)

---

### Post by ogami1972 on 2006-09-17
Hi all! 
Have gotten cinelerra installed...kinda... it will load an .avi, but the sound is massively distorted, and once playback begins, the controls become unresponsive, and i have to kill the app.
](*,) 
Any ideas? I tried running it via term to see if it threw any error messages, but all seemed 'normal'.

---

### Post by lprofil on 2006-09-17
Hello ogami,

first of all congrats for successfully compiling Cinelerra.
I know about your problem but this thread was started to explain 
how to COMPILE and not how to USE Cinelerra.

Take a look on Cinelerras site or sneak into their IRC-Channel.
As far as i know you first have to convert the avi-file to 
a quicktime-file for proper replay or cutting.

/lprofil

ps: i would be really interested in a video-tutorial about
    how to use Cinelerra and its funky features.
    You could upload it to e.g. Youtube.

---

### Post by bayvista on 2006-12-05
I get the following error on the MAKE. Any suggestions welcome

        -c -o audioesound.o `test -f 'audioesound.C' || echo './'`audioesound.C; \
        then mv -f ".deps/audioesound.Tpo" ".deps/audioesound.Po"; \
        else rm -f ".deps/audioesound.Tpo"; exit 1; \
        fi
audioesound.C:9:17: error: esd.h: No such file or directory
audioesound.C: In member function ‘int AudioESound::get_bit_flag(int)’:
audioesound.C:28: error: ‘ESD_BITS8’ was not declared in this scope
audioesound.C:32: error: ‘ESD_BITS16’ was not declared in this scope
audioesound.C: In member function ‘int AudioESound::get_channels_flag(int)’:
audioesound.C:47: error: ‘ESD_MONO’ was not declared in this scope
audioesound.C:51: error: ‘ESD_STEREO’ was not declared in this scope
audioesound.C: In member function ‘virtual int AudioESound::open_input()’:
audioesound.C:72: error: ‘esd_format_t’ was not declared in this scope
audioesound.C:72: error: expected `;' before ‘format’
audioesound.C:77: error: ‘format’ was not declared in this scope
audioesound.C:80: error: ‘esd_open_sound’ was not declared in this scope
audioesound.C:87: error: ‘esd_record_stream_fallback’ was not declared in this scope
audioesound.C: In member function ‘virtual int AudioESound::open_output()’:
audioesound.C:93: error: ‘esd_format_t’ was not declared in this scope
audioesound.C:93: error: expected `;' before ‘format’
audioesound.C:98: error: ‘format’ was not declared in this scope
audioesound.C:101: error: ‘esd_open_sound’ was not declared in this scope
audioesound.C:108: error: ‘esd_play_stream_fallback’ was not declared in this scope
audioesound.C:110: error: ‘esd_get_latency’ was not declared in this scope
audioesound.C: In member function ‘virtual int AudioESound::close_all()’:
audioesound.C:130: error: ‘esd_close’ was not declared in this scope
audioesound.C:136: error: ‘esd_close’ was not declared in this scope
make[3]: *** [audioesound.o] Error 1
make[3]: Leaving directory `/opt/hvirtual/cinelerra'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/hvirtual/cinelerra'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

---

### Post by cwncool on 2006-12-08
This is what just happened to me
```
audioesound.C:9:17: error: esd.h: No such file or directory
audioesound.C: In member function ‘int AudioESound::get_bit_flag(int)’:
audioesound.C:28: error: ‘ESD_BITS8’ was not declared in this scope
audioesound.C:32: error: ‘ESD_BITS16’ was not declared in this scope
audioesound.C: In member function ‘int AudioESound::get_channels_flag(int)’:
audioesound.C:47: error: ‘ESD_MONO’ was not declared in this scope
audioesound.C:51: error: ‘ESD_STEREO’ was not declared in this scope
audioesound.C: In member function ‘virtual int AudioESound::open_input()’:
audioesound.C:72: error: ‘esd_format_t’ was not declared in this scope
audioesound.C:72: error: expected `;' before ‘format’
audioesound.C:77: error: ‘format’ was not declared in this scope
audioesound.C:80: error: ‘esd_open_sound’ was not declared in this scope
audioesound.C:87: error: ‘esd_record_stream_fallback’ was not declared in this s cope
audioesound.C: In member function ‘virtual int AudioESound::open_output()’:
audioesound.C:93: error: ‘esd_format_t’ was not declared in this scope
audioesound.C:93: error: expected `;' before ‘format’
audioesound.C:98: error: ‘format’ was not declared in this scope
audioesound.C:101: error: ‘esd_open_sound’ was not declared in this scope
audioesound.C:108: error: ‘esd_play_stream_fallback’ was not declared in this sc ope
audioesound.C:110: error: ‘esd_get_latency’ was not declared in this scope
audioesound.C: In member function ‘virtual int AudioESound::close_all()’:
audioesound.C:130: error: ‘esd_close’ was not declared in this scope
audioesound.C:136: error: ‘esd_close’ was not declared in this scope
make[2]: *** [audioesound.o] Error 1
make[2]: Leaving directory `/opt/hvirtual/cinelerra'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual/cinelerra'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
do any of you guys know what do do to fix this?  It was compiling for like 15 minutes too...

---

### Post by cwncool on 2006-12-08
Actually, is there a DEB for this?  If not, PLEASE someone make one!

---

### Post by lprofil on 2006-12-09
Dear cwncool, dear bayvista,

if you jump into a thread and do not give us specific information of your system, there is not much we can do for you.

Please tell us:

[LIST][*]what release are you using? Edgy or Dapper[*]Did you try to install the deb i compiled and put on the site mentioned below?
[/LIST]


Here is the link to the old deb packages i made:
[http://ww2.fs.ei.tum.de/~dr/](http://ww2.fs.ei.tum.de/~dr/)

Besides: your error messages complain a missing esd Libary.

```
audioesound.C:9:17: error: esd.h: No such file or directory
```

esd is the name for **e**nlightment **s**ound **d**aemon 
**.h** stands for the type if the file = a libary   (please correct me if i am misstaken)

You shall look up which dev package might missing with:

apt-cache search esd | grep lib
or just 
apt-cache search esd 

and see if there is a package which might fit.


/lprofil

---

### Post by rhombus66 on 2007-04-22
For those (like me) receiving the compilation errors related to a missing esd.h file...
Install the package libesd0-dev.  This includes the "esd.h" header (plus others).
(e.g. <prompt>$ sudo apt-get install libesd0-dev)
Hope that helps.

---

### Post by lprofil on 2007-04-22
Hi rhombus66,

thank you for your contribution. I will update my tutorial
and add the libesd0-dev.

/lprofil

---

### Post by Jalke on 2007-06-09
After a lot of dependency problems I finally got it to configure properly.  It seemed all happy until I tried to *make* it.  Then I got the following error :confused::

make[2]: Leaving directory `/opt/hvirtual/toolame-02l'
Making all in guicast
make[2]: Entering directory `/opt/hvirtual/guicast'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../quicktime   -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64  -g -O2 -MT bcbitmap.lo -MD -MP -MF ".deps/bcbitmap.Tpo" \
  -c -o bcbitmap.lo `test -f 'bcbitmap.C' || echo './'`bcbitmap.C; \
then mv -f ".deps/bcbitmap.Tpo" ".deps/bcbitmap.Plo"; \
else rm -f ".deps/bcbitmap.Tpo"; exit 1; \
fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../quicktime -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT bcbitmap.lo -MD -MP -MF .deps/bcbitmap.Tpo -c bcbitmap.C  -fPIC -DPIC -o .libs/bcbitmap.o
In file included from bcbitmap.C:1:
bcbitmap.h:8:34: error: X11/extensions/Xvlib.h: No such file or directory
bcbitmap.h:144: error: ISO C++ forbids declaration of 'XvImage' with no type
bcbitmap.h:144: error: expected ';' before '*' token
bcbitmap.C: In member function 'int BC_Bitmap::initialize(BC_WindowBase*, int, int, int, int)':
bcbitmap.C:77: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::allocate_data()':
bcbitmap.C:143: error: 'xv_image' was not declared in this scope
bcbitmap.C:149: error: 'XvShmCreateImage' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::delete_data()':
bcbitmap.C:317: error: 'XvStopVideo' was not declared in this scope
bcbitmap.C:320: error: 'xv_image' was not declared in this scope
bcbitmap.C:323: error: 'XvUngrabPort' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::write_drawable(Drawable&, _XGC*&, int, int, int, int, int, int, int, int, int)':
bcbitmap.C:446: error: 'xv_image' was not declared in this scope
bcbitmap.C:455: error: 'XvShmPutImage' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_size()':
bcbitmap.C:632: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_offset()':
bcbitmap.C:640: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_y_shm_offset()':
bcbitmap.C:651: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_u_shm_offset()':
bcbitmap.C:659: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_v_shm_offset()':
bcbitmap.C:667: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_y_offset()':
bcbitmap.C:675: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_u_offset()':
bcbitmap.C:683: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_v_offset()':
bcbitmap.C:691: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_y_plane()':
bcbitmap.C:717: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_v_plane()':
bcbitmap.C:726: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_u_plane()':
bcbitmap.C:735: error: 'xv_image' was not declared in this scope
make[2]: *** [bcbitmap.lo] Error 1
make[2]: Leaving directory `/opt/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

Could someone please tell me how to get around this?  You'd make me very happy.  Thanks a lot.

Jalke 
(Feisty Fawn)

---

### Post by lprofil on 2008-05-01
> **Jalke said:**
> Last edited by Jalke; June 9th, 2007 at 07:25 AM. Reason: Edit: Sorry, I just discovered the answer in another forum: install libxv-dev. Hope it helps someone else.

It did! Thank you very much for letting us know.

/lprofil

---

### Post by demolishun on 2008-07-06
chainzz,
Your nasm info helped me get it to compile on Ubuntu 8.04.  I am hoping the latest version of Cineleraa compiled from source will not lock up like the akirad repos vesion.  That version goes into a loop when trying to open up anything whether it be a video file or an existing project.

It kind of torques me a bit because I upgraded a lot of stuff only to break everything.

---

