---
title: "Cinelerra 2.1 CV for Edgy Eft 6.10 [ How To / Tutorial ]"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by lprofil on 2006-12-17
Hi folks,

you might remember my former tutorial **[[1]]("http://ubuntuforums.org/showthread.php?t=188264")** about "howto compile Cinelerra CV from source" for Dapper Drake 6.04. 
That tutorial is outdated. Take this one instead.

**Preamble**

You might just like to use Cinelerra instead of going the thorny way.
There is a **.deb package** i assebled which you can [download from this site]("http://www.fs.ei.tum.de/~dr").

Just jump to step 2 and install  the deb package afterwards - that should do the trick.



This tutorial is written for **Edgy Eft 6.10 32-Bit** but also works with **Dapper Drake 6.04 32-Bit**.
I tested my tutorial on a fresh vigin installation of Edgy Eft
with no additional packages. It worked flawless.

To shorten it up i will point out the important details only.
Some parts are quoted from the "Cinelerra CV manual"**[[2]]("http://cvs.cinelerra.org/docs/cinelerra_cv_manual_en.html")**.


**#1.** Adding "Restricted Respositories"

Make sure "Universe" and "Multiverse" repositories" are included in your respositories **[[3]]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")**.


**#2.** Get necessary packages

First become root:
```
sudo -s
```


This is a bunch of packages you will need to compile cinelerra:

```
apt-get install -y g++ libesd0-dev nasm yasm libpng12-dev libasound2-dev xorg-dev cvs subversion autotools-dev automake1.7 liba52-0.7.4-dev libx264-dev libtheora-bin libtheora0 libopenexr2c2a mjpegtools libmjpegtools0c2a libraw1394-8 libfaad2-0 liblame0 libguile-dev automake1.9 autotools-dev autoproject libtool libavc1394-0 libogg-dev libtheora-dev libvorbis-dev libvorbisenc2 libopenexr-dev libdv4-dev uuid-dev libmjpegtools-dev libffi4-dev libgmp3-dev libsndfile1-dev libfaad2-dev libfaac-dev libavc1394-dev libdc1394-13-dev libraw1394-dev libiec61883-dev liblame-dev fftw3-dev libmpeg3-dev mpeg3-utils quicktime-utils quicktime-x11utils libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev libfaac0 libfaac-dev gstreamer0.8-faac faac libmp4v2-dev libmpeg2-4-dev libxv-dev libtiff4-dev
```

   (Hint: **click four times** to mark the whole line)

You need to download 36,2 MB.
If you do not have a broadband connection you 
can ask someone to build an offline update package for you [**[4]**]("https://wiki.ubuntu.com/OfflineUpdateSpec")
and to download the debian-package **[[5]]("http://www.fs.ei.tum.de/~dr")** i build for that purpose.
You will also need the SVN-tree mentioned in #3.


**#3.** Download the Source-Tree

First change directory to the /opt folder:

```
cd /opt
```

Then download the subversion files:

```
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual
```

and change to the hvirtual directory: 

```
cd hvirtual 
```


**#4.** Creating the configure file

Create the `./configure' file by running: 

```
autoreconf -i --force
```


**#5.** Run configure

Then run the `.configure' file: 

```
./configure --with-buildinfo=svn/recompile 
```

You can have a look at all the options available by running: 
./configure --help 


**#6.** Tweak a little

To avoid this error message 
```
ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1
```
during the compiling process you have 
to type in the following commands:


```
cd libmpeg3/video
nasm -f elf reconmmx.s -o reconmmx.o
mkdir .libs
cp reconmmx.o .libs/

```


**#7.** Compile the Binary file

```

cd /opt/hvirtual
make 
```


**#8.** Install Cinelerra CV

```
make install
```


**#9.** Run Cinelerra

You have to start Cinelerra as root.
Thatfor you type in your terminal window:

```
sudo cinelerra
```


Fahrvergnügen!

/lprofil


**Documents:**

**[1]** [Cinelerra on Dapper Drake 6.04 from Sources]("http://ubuntuforums.org/showthread.php?t=188264")
**[2]** [Cinelerra CV manual]("http://cvs.cinelerra.org/docs/cinelerra_cv_manual_en.html")
**[3]** [How to activate Universe and Multiverse in your Respositories]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")
**[4]** [How to create a **Update Package** for **offline use**]("https://wiki.ubuntu.com/OfflineUpdateSpec")
**[5]** [Debian Package]("http://ubulamp.dyndns.org/") for the quick and dirty way


**Editing History:**

**Mon**, Dec 18,  17:17 /  2006 updated package list added "*g++ libesd0-dev nasm yasm libpng12-dev libasound2-dev xorg-dev cvs subversion autotools-dev automake1.7*"

**Tue**, Dec 19, 01:41 / 2006 corrected error in **#6.**  
[LIST][*]**wrong:** cp reconmmx.o .libs[*]**right:  ** cp reconmmx.o .libs**/**[/LIST]
**Tue**, Dec 19, 15:15 / 2006 added link for "*Offline Update*"
**Wed**, Jan 03, 01:05 / 2007 added line "*mkdir .libs*" in step 6
**Wed**, Jan 03, 01:27 / 2007 added [URL to deb-package]("http://www.fs.ei.tum.de/~dr")
**Sun**, Jan 07, 20:45 / 2007 edited [URL to deb-package]("http://www.fs.ei.tum.de/~dr")

---

### Post by mrastas on 2006-12-18
Hi,

i am trying to get past point 2, but i get stack with the following... Any ideas how to get those packages installed nicely.

```
The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.25-0.1 is to be installed
  liblame-dev: Depends: liblame0 (= 3.96.1-2) but 3.97-0.0 is to be installed
  libmp4v2-dev: Depends: libmp4v2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) but 1:1.5.0.1-0.3 is to be installed

```

---

### Post by lprofil on 2006-12-18
Hi mrastas,

thank you very much for trying my tutorial.
I today corrected some errors.

Please try it again if it failed to compile with the error message:
```
make[3]: Entering directory `/opt/hvirtual/libmpeg3/video'
if /bin/bash ../../libtool --tag=CC --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./..   -DHAVE_MMX -DUSE_MMX -DX86_CPU  -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT getpicture.lo -MD -MP -MF ".deps/getpicture.Tpo" -c -o getpicture.lo getpicture.c; \
        then mv -f ".deps/getpicture.Tpo" ".deps/getpicture.Plo"; else rm -f ".deps/getpicture.Tpo"; exit 1; fi
rm: cannot remove `.libs/getpicture.o': Not a directory
mkdir .libs
mkdir: cannot create directory `.libs': File exists
make[3]: *** [getpicture.lo] Error 1
make[3]: Leaving directory `/opt/hvirtual/libmpeg3/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/hvirtual/libmpeg3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

```


Refering to the official Ubuntu package list, **[Edgy Eft]("http://packages.ubuntulinux.org/edgy/libs/")** and **[Feist Fawn]("http://packages.ubuntulinux.org/feisty/libs/")** should install libfaac0 (1.24clean-0ubuntu4) 

I guess you used a f***edup "*customized*" sources.list or you installed some packages which you should deinstall befor trying my tut.

[LIST][*]How does your sources list look like?[*]What Ubuntu-Version do you use?[*]Did you try to install another Cinelrra-Version before?[*]Did you try to **DE**-install all other crap before?[/LIST]


/lprofil

---

### Post by Kingsley on 2006-12-18
my friend and i were trying to figure out how to install cinelerra a week ago. vielen dank!

---

### Post by alexander1972 on 2006-12-19
Hello I followed your tutorial step by step but got stuck at step #6.  I have tried to do the following:
root@Hal1972:/opt/hvirtual# cd libmpeg3/video
root@Hal1972:/opt/hvirtual/libmpeg3/video# nasm -f elf reconmmx.s -o reconmmx.o
root@Hal1972:/opt/hvirtual/libmpeg3/video# cp reconmmx.o .libs/
cp: target `.libs/' is not a directory: No such file or directory
The copy command is going into nowehere. How can I fix thsi
Cheers
Alex

---

### Post by lprofil on 2006-12-19
Hi Kinsgsley,

> **Kingsley said:**
> my friend and i were trying to figure out how to install cinelerra a week ago. vielen dank!

Kein Problem young fellow, you are welcome!

Hello Alexander,

> **alexander1972 said:**
> Hello I followed your tutorial step by step but got stuck at step #6.  I have tried to do the following:
root@Hal1972:/opt/hvirtual# cd libmpeg3/video
root@Hal1972:/opt/hvirtual/libmpeg3/video# nasm -f elf reconmmx.s -o reconmmx.o
root@Hal1972:/opt/hvirtual/libmpeg3/video# cp reconmmx.o .libs/
cp: target `.libs/' is not a directory: No such file or directory
The copy command is going into nowehere. How can I fix thsi
Cheers
Alex

Hm, that sound strange to me. The .libs folder should be created after:
[LIST][*]checking out from SVN Sources
[*]making the configure file
[*]configure for making
[/LIST]

When nasm creates the  reconmmx.o out of the reconmmx.s file do you get any message?
If not, everything is ok. If yes - that might be the problem. Weird.

Maybe a necessary package is missing. I edited the package list yesterday (*see Editing history*).

Why now there is no folder .libs in your installation path is a miracle for me.

/lprofil

---

### Post by bdk on 2006-12-19
I've got the same problem with the copy step... Relatively new Edgy install:

```
bdk@buddha:/usr/src/hvirtual/libmpeg3/video$ sudo nasm -f elf reconmmx.s -o reconmmx.o
bdk@buddha:/usr/src/hvirtual/libmpeg3/video$ sudo cp reconmmx.o .libs/
cp: target `.libs/' is not a directory: No such file or directory
bdk@buddha:/usr/src/hvirtual/libmpeg3/video$ ls
getpicture.c  idct.h         Makefile     mmxidct.S  mpeg3cache.c  mpeg3videoprotos.h  reconmmx.s     slice.c     vlc.c
headers.c     layerdata.h    Makefile.am  mmxtest.c  mpeg3video.c  output.c            reconstruct.c  slice.h     vlc.h
idct.c        macroblocks.c  Makefile.in  motion.c   mpeg3video.h  reconmmx.o          seek.c         subtitle.c  worksheet.c
bdk@buddha:/usr/src/hvirtual/libmpeg3/video$
```

Why/how/where was the .libs directory created? I see a .debs but no .libs.

Any guidance would be appreciated...

Thank you for the nice how-to though, I was bummed when I found out that there wasn't a deb for Cinelerra for Edgy, just for Dapper.

---

### Post by bdk on 2006-12-19
I logged in remotely while at work and went ahead and ran through the steps after the copy problem that I had earlier and it looks like things went smoothly.. I went through the make & make install process and it looks good... I don't have VNC up so I can't log in remotely to see if it works or not, so when I get home I'll update this with hopefully good news that we don't need the nasm & copy commands for the latest SVN to work.

** UPDATE ** 

Sure enough, Cinelerra compiled nicely and had the correct privs to run w/o sudo.

I did get an error though that has been talked about before:

```

void MWindow::init_shm():WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low
 Before running Cinelerra do the following as root:
 echo "0x7fffffff" > /proc/sys/kernel/shmmax

```

(That is 7 f's)

I don't remember where I read about it before but the solution was to enable the root account, set shmmax, then run cinelerra. Just sudo'ing it doesn't give you enough privs to write to the /proc directory. I don't like enabling the root account so I:

```

bdk@buddha:~$ sudo -s
root@buddha:~# echo "0x7fffffff" > /proc/sys/kernel/shmmax
root@buddha:~# exit
exit
bdk@buddha:~$ cinelerra 

```

and it ran just fine... I don't mind having to do that each time I start up, after all this is linux, I'm not rebooting everyday. If it anoys me enough I'll find the perm fix for it or I'll just write a lil' script to do that and then load Cinerella.

Thanks again lprofil for the good how-to.

*-bdk*

---

### Post by mrastas on 2006-12-20
> **lprofil said:**
> 

Refering to the official Ubuntu package list, **[Edgy Eft]("http://packages.ubuntulinux.org/edgy/libs/")** and **[Feist Fawn]("http://packages.ubuntulinux.org/feisty/libs/")** should install libfaac0 (1.24clean-0ubuntu4) 

I guess you used a f***edup "*customized*" sources.list or you installed some packages which you should deinstall befor trying my tut.

[LIST][*]How does your sources list look like?[*]What Ubuntu-Version do you use?[*]Did you try to install another Cinelrra-Version before?[*]Did you try to **DE**-install all other crap before?[/LIST]

/lprofil

Hi again,

thanks for the tip. I think my packages got mixed up when i tried the other cinelerra guide, which used some debian (sid) repo. Well anyhow i got through it by removing and installing again. Hopefully there is not many other this kind of wrong packages anymore.

So i got the second step done. Now i actually have the same problem that Alex and Bdk has. In step 5. i am also missing the ./libs directory. But as bdk pointed out, it is possible to make and make install without step 5. So i went ahead and got it compiled and installed. It seems to be running OK. :-k 

Thanks for the guide!!! This one is much easier than the others... 

Hopefully cinelerra will be soon out in ubuntu repos.

Now to make some videos...

---

### Post by legolas on 2006-12-20
lprofil, thank you so much for the tutorial.  I was actually going to just "go for it" and attempt to install this on my own.  However after seeing your how-to, I realized I am in WAY over my head.  I followed your instructions step by step and it worked for my beautifully.  Thank you so much!  We all appreciate it greatly.

---

### Post by bayvista on 2006-12-20
Hi Iprofil

Thanks for all your work. I've just installed Dapper and am stuck on Step2. Can't find iec61883-dev. Any suggestions?

Dave

---

### Post by lprofil on 2006-12-21
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

### Post by lime4x4 on 2006-12-21
here the error i'm getting

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.24+cvs20060416-0.1 is to be installed
  libfaad2-dev: Depends: libfaad2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) but 2.0.0+cvs20060416-0.0 is to be installed
  liblame-dev: Depends: liblame0 (= 3.96.1-2) but 3.97-0ubuntu0seveas1 is to be installed
  xorg-dev: Depends: libxss-dev but it is not going to be installed
E: Broken packages

---

### Post by lprofil on 2006-12-22
> **lime4x4 said:**
> here the error i'm getting
E: Broken packages

This has actually nothing to do with Cinelerra, but you could try either with synaptics
to "Fix broken packages"
--> System --> Administration --> Synaptic Package Manager --> Edit  -->  "Fix broken packages"

or

in a terminal window as root:

```
apt-get install -f
```

/lprofil

---

### Post by lime4x4 on 2006-12-22
john@john-edgy:~$ sudo -s
root@john-edgy:~# apt-get install -f -y g++ libesd0-dev nasm yasm libpng12-dev libasound2-dev xorg-dev cvs subversion autotools-dev automake1.7 liba52-0.7.4-dev libx264-dev libtheora-bin libtheora0 libopenexr2c2a mjpegtools libmjpegtools0c2a libraw1394-8 libfaad2-0 liblame0 libguile-dev automake1.9 autotools-dev autoproject libtool libavc1394-0 libogg-dev libtheora-dev libvorbis-dev libvorbisenc2 libopenexr-dev libdv4-dev uuid-dev libmjpegtools-dev libffi4-dev libgmp3-dev libsndfile1-dev libfaad2-dev libfaac-dev libavc1394-dev libdc1394-13-dev libraw1394-dev libiec61883-dev liblame-dev fftw3-dev libmpeg3-dev mpeg3-utils quicktime-utils quicktime-x11utils libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev libfaac0 libfaac-dev gstreamer0.8-faac faac libmp4v2-dev libmpeg2-4-dev libxv-dev libtiff4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
libesd0-dev is already the newest version.
nasm is already the newest version.
yasm is already the newest version.
libpng12-dev is already the newest version.
libasound2-dev is already the newest version.
subversion is already the newest version.
autotools-dev is already the newest version.
automake1.7 is already the newest version.
libtheora0 is already the newest version.
libopenexr2c2a is already the newest version.
mjpegtools is already the newest version.
libmjpegtools0c2a is already the newest version.
libraw1394-8 is already the newest version.
libfaad2-0 is already the newest version.
liblame0 is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
libtool is already the newest version.
libavc1394-0 is already the newest version.
libogg-dev is already the newest version.
libvorbis-dev is already the newest version.
libvorbisenc2 is already the newest version.
libopenexr-dev is already the newest version.
libdv4-dev is already the newest version.
libgmp3-dev is already the newest version.
libavc1394-dev is already the newest version.
libraw1394-dev is already the newest version.
quicktime-utils is already the newest version.
quicktime-x11utils is already the newest version.
libfaac0 is already the newest version.
libmp4v2-dev is already the newest version.
libtiff4-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.24+cvs20060416-0.1 is to be installed
  libfaad2-dev: Depends: libfaad2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) but 2.0.0+cvs20060416-0.0 is to be installed
  liblame-dev: Depends: liblame0 (= 3.96.1-2) but 3.97-0ubuntu0seveas1 is to be installed
  xorg-dev: Depends: libxss-dev but it is not going to be installed
E: Broken packages
root@john-edgy:~#

---

### Post by mrastas on 2006-12-25
Hi lime4x4,

i had the same problem. Check out my earlier posts.

The fix was to simply remove and install the problem packages again, but be aware that removing them removes also some other packages and while installing them back i had to manually install some of them also.

Also if it seems to install the same package back again. There might be some repos in apt source list file that you might need to change or remove and run apt-get update before trying again.

---

### Post by tassoman on 2006-12-26
Some one kind enough to write .deb packages of cinelerra for Dapper and Edgy? :-?

---

### Post by linuxguy123 on 2006-12-29
When I try to download the packages needed to compile cinelerra I receive this error:

> ~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a fftw3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ronnie-laptop:~# apt-get install -y g++ libesd0-dev nasm yasm libpng12-dev libasound2-dev xorg-dev cvs subversion autotools-dev automake1.7 liba52-0.7.4-dev libx264-dev libtheora-bin libtheora0 libopenexr2c2a mjpegtools libmjpegtools0c2a libraw1394-8 libfaad2-0 liblame0 libguile-dev automake1.9 autotools-dev autoproject libtool libavc1394-0 libogg-dev libtheora-dev libvorbis-dev libvorbisenc2 libopenexr-dev libdv4-dev uuid-dev libmjpegtools-dev libffi4-dev libgmp3-dev libsndfile1-dev libfaad2-dev libfaac-dev libavc1394-dev libdc1394-13-dev libraw1394-dev libiec61883-dev liblame-dev fftw3-dev libmpeg3-dev mpeg3-utils quicktime-utils quicktime-x11utils libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev libfaac0 libfaac-dev gstreamer0.8-faac faac libmp4v2-dev libmpeg2-4-dev libxv-dev libtiff4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtheora0 is already the newest version.
libopenexr2c2a is already the newest version.
mjpegtools is already the newest version.
libmjpegtools0c2a is already the newest version.
libraw1394-8 is already the newest version.
libfaad2-0 is already the newest version.
liblame0 is already the newest version.
libavc1394-0 is already the newest version.
libvorbisenc2 is already the newest version.
libffi4-dev is already the newest version.
libfaac0 is already the newest version.
faac is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libguile-dev: Depends: guile1.4 (= 1:1.4-26) but it is not going to be installed
                Depends: libguile9 (= 1:1.4-26) but it is not going to be installed
E: Broken packages

---

### Post by tassoman on 2006-12-29
Go to HERE:

[ Gandalf Cinelerra .deb packages for Ubuntu breezy/dapper](http://www.kiberpipa.org/~gandalf/ubuntu/README)

Take a look also at his blog [http://www.kiberpipa.org/~gandalf/blog/?cat=11](http://www.kiberpipa.org/~gandalf/blog/?cat=11)

But, I still can't acquire with analog card bt878 :| 

Should work with ieee1934

---

### Post by linuxguy123 on 2006-12-29
I'm running Ubuntu 6.10 Edgy

---

### Post by Keldek on 2007-01-02
When following the instructions in step #6

```
cd libmpeg3/video
nasm -f elf reconmmx.s -o reconmmx.o
cp reconmmx.o .libs/
```

I received the same error as others:

```
cp: target `.libs/' is not a directory: No such file or directory
```

So I simply did the following:

```
cd libmpeg3/video
mkdir .libs
nasm -f elf reconmmx.s -o reconmmx.o
cp reconmmx.o .libs/
```

This solved the error for me and I had no problems installing cinelerra from that point on. I also, to this point, have received no errors when launching cinelerra and will post back later after I figure out how to use it if I run into errors

---

### Post by fsman on 2007-01-02
Humm. I'm still using the cinelerra dapper repo's with edgy just fine. cinelerra version 2.0 rather than 2.1.

Advantage is that these repo's keep my system clean and i'm not having to manually make changes or access a debian repo. So hopefully upgrading to fiesty will go smoothly.

"muzzol" is trying to build 2.1 cinelerra for edgy - but it looks like there are still problems.

My advice - use 2.0 untill Muzzol gets his edgy repo running with a stock edgy system - without having to use debian files.

---

### Post by chiklit on 2007-01-02
I'm getting this error:

```
The following NEW packages will be installed:
  mpeg3-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/17.0kB of archives.
After unpacking 73.7kB of additional disk space will be used.
(Reading database ... 139301 files and directories currently installed.)
Unpacking mpeg3-utils (from .../mpeg3-utils_1.5.4-5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mpeg3-utils_1.5.4-5_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mpeg3dump', which is also in package libmpeg3hv
Errors were encountered while processing:
 /var/cache/apt/archives/mpeg3-utils_1.5.4-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lprofil on 2007-01-02
Hello,

if you want to speed up your installation and you are satisfied with a packages which is 
about a moth old [you can download it here]("http://ubulamp.dyndns.info").

Just make sure you install the required packages mentinoned in step 2. and install  the package for edgy by doing:

```
sudo dpkg -i cine*
```

/lprofil

---

### Post by chiklit on 2007-01-02
I tried following these instructions but in trying to meet all of the dependencies something appears to have gone wrong. Now apt-get won't let me install libmjpegtools0 or uninstall libmjpegtools0c2a because it says I have unmet dependencies. But when I try to fix them it gives me this error: 

```
(Reading database ... 138336 files and directories currently installed.)
Unpacking libmjpegtools0c2a (from .../libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So now since I have unmet dependencies I can't upgrade, remove or install any software anymore.

Is there anyway to fix this without reinstalling Ubuntu?

EDIT: I fixed this. But now for no apparent reason my sound has suddenly stopped working. Going back to Windows for now.

---

### Post by fsman on 2007-01-03
> **lprofil said:**
> Hello,

if you want to speed up your installation and you are satisfied with a packages which is 
about a moth old [you can download it here]("http://ubulamp.dyndns.info").

Just make sure you install the required packages mentinoned in step 2. and install  the package for edgy by doing:

```
sudo dpkg -i cine*
```

/lprofil


Before I try this can you clarify please.

Are you saying that using this deb with the standard universe/multiverse repos will install v.2.1? No other repos required?

Also. is this the CV (community version) or herrione?

---

### Post by lprofil on 2007-01-03
> **fsman said:**
> 
Are you saying that using this deb with the standard universe/multiverse repos will install v.2.1? No other repos required?

That is how it is.

> **fsman said:**
> Also. is this the CV (community version) or herrione?

This package was build on my 32-bit system and contains **Cinelerra 2.1 CV**

/lprofil

---

### Post by fsman on 2007-01-03
> **lprofil said:**
> That is how it is.



This package was build on my 32-bit system and contains **Cinelerra 2.1 CV**

/lprofil
 cool.

can you contact the community site and get it included on their packages
[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

I think they are trying to package for egdy but looking at the mailing lists some people are having problems.

---

### Post by dorcssa on 2007-01-03
Do I have to run cinelerra as root when installing it from the repos?

---

### Post by dailer on 2007-01-06
[http://ubulamp.dyndns.info/](http://ubulamp.dyndns.info/) doesn't work. Where else can i get a deb for Cinelerra 2.1 for edgy?

---

### Post by lprofil on 2007-01-07
> **dorcssa said:**
> Do I have to run cinelerra as root when installing it from the repos?

Yes, you have to.

> **dailer said:**
> [http://ubulamp.dyndns.info/](http://ubulamp.dyndns.info/) doesn't work. Where else can i get a deb for Cinelerra 2.1 for edgy?

The server was temporaly offline.
Try [this one ]("http://www.fs.ei.tum.de/~dr")instead.

/lprofil

---

### Post by MetalMusicAddict on 2007-01-07
Just a heads up. [Ubuntu Studio]("http://www.ubuntustudio.com/") is working hard at getting Cinelerra-CV into Feisty.

---

### Post by Aphorism on 2007-01-07
Not many folks know about this pretty heavyweight tool.

Currently I am running native 64 bit on an amd64 X2 chip and am trying to get Cinelerra to compile.

Last night, I had a header file issue.  After trying the compilation steps in this tutorial, I now have the familiar problem I had before.  Perhaps someone with 32 bit experience can help to negotiate this problem:

```

/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libx264.a(common.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libx264.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/home/aphorism/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aphorism/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aphorism/hvirtual'
make: *** [all] Error 2

```

Ideas anyone?  Tried adding -fPIC to a few makefile spots, but to no avail.

Let's get this project running on amd64.

Sincerely,
TJS

---

### Post by dorcssa on 2007-01-08
> **lprofil said:**
> [QUOTE=dorcssa;1962822]Do I have to run cinelerra as root when installing it from the repos?Yes, you have to.


/lprofil[/QUOTE]

What's the difference, when I start it from tha application menu? What I can't do?

---

### Post by lprofil on 2007-01-09
> **dorcssa said:**
> What's the difference, when I start it from tha application menu? What I can't do?

Cinelerra needs to be run as root for some reason, I read it some where and i am sure you can google that. If i am not misstaken some devices (fire-wire) or filters needs to be run as root.

/Üdvözlettel lprofil


@Aphorism
[64-bit Cinelerra tutorial]("http://ubuntuforums.org/showthread.php?t=215252")

---

### Post by dorcssa on 2007-01-09
Hmm, ok, then I run it as root than. 

És köszönöm. :D

---

### Post by Aphorism on 2007-01-09
lprofil -- Thank you kindly.  I think that will resolve the issue.  Perhaps the users of Ubuntu here in this thread should contact the CVS Cinelerra folks and update their Wiki so that everyone benefits?

Once again, lprofil -- your help is greatly appreciated.

---

### Post by fsman on 2007-01-12
Check out the offical cinelerra CV mailing lists.
now it is very easy to install cinelerra 2.1 in edgy just add the following repo and install cinelerra

deb [http://labbs.net/~vale/ubuntu](http://labbs.net/~vale/ubuntu) ./ 

see the mailing list for more info
[http://e.kevb.net/lurker/message/20070110.130629.b4fc279a.en.html](http://e.kevb.net/lurker/message/20070110.130629.b4fc279a.en.html)

---

### Post by Aphorism on 2007-01-12
I would prefer to compile it from scratch.

lprofi's trick worked right up to the point of running the app -- at which point the SUV theme is not found and it bombs.

Ideas?

Tried removing the .bcast dir, to no avail.  It seems the SUV theme isn't compiled in the process due to the shared / static workarounds?

Sincerely,
TJS

---

### Post by saepia on 2007-01-13
The .deb package on your site has missing dependencies. Maybe add libopenexr-dev? (it contains missing libIlmImf.so.2). Without that cinelerra won't run and quits with following error:

cinelerra: error while loading shared libraries: libIlmImf.so.2: cannot open shared object file: No such file or directory

---

### Post by roamingfree on 2007-01-17
Hello, this is the first time I have ever posted here and alas it is with a problem, I followed the tutorial and ran cinelerra, but I get the following error:

sudo cinelerra
cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: NeAACDecDecode


I really have no idea what I'm supposed to do to make this not be broken - any help would be greatly appreciated!!!

---

### Post by hernando on 2007-01-22
Hi!
Congratulations for your tutorial cinelerra runs like a charm on my PC. Better than any binary.
Big Tanks ):P 

Only one request. I saw the .deb you post some pages back, and I want to build my own binary.
How do you make one of this??

---

### Post by jediborger on 2007-01-22
Hey i used the cvs.cinelerra repository to install, located here [http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu")

I also get a symbol error and was wondering if anybody has any suggestions since there's next to nothing as far as support for cinelerra.

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

---

### Post by nalmeth on 2007-01-23
Your instructions worked for me.
Now I just have to figure out how to use the darn thing :)

---

### Post by doundounba on 2007-01-24
Just wanted to report success (on Kubuntu Edgy 32bit) using the cinelerra.org repos (giss.tv) listed here: [http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu").  (As others have noted you need to issue "echo "0x7fffffff" > /proc/sys/kernel/shmmax" as root before launching the app.) So, no need to compile from source for me. Still, thanks for the tutorial though - it's through reading this thread that I found the repos! :D 

Now, to actually *use* the thing... ;) I must say that MainActor looks a little more friendly on first contact.

---

### Post by parallax68 on 2007-01-25
I wanted also to report success installation of cinelerra on 2 Edgy at home by following your instructions.
I also tested some other ways to get a proper cinelerra install but yours is the one that works for me.
thanks a lot

---

### Post by Jesterday on 2007-01-25
I am also getting the following error,

cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

That is using the .deb file used in this tutorial...

Anyone have any ideas?

Darren

---

### Post by doundounba on 2007-01-26
To those getting "undefined symbol: faacDecOpen": do you have libfaad2-0 installed?  If not, try to install it.  Some googling suggests that this could be the problem...  HTH.

---

### Post by Naikei on 2007-01-28
Hey, I've run into a bit of trouble at #3.
I'm getting the 
```
error svn: Unknown hostname 'svn.skolelinux.org'
```
I've been having trouble with my proxy, but would this have anything to do with it?
I can browse through the [http://svn.skolelinux.org](http://svn.skolelinux.org) (that changes to .no) in firefox.
I'm rather confused.
I expect it's my network, but is there any other way to get the checkout files?
Regards
Naikei

---

### Post by cnphch on 2007-01-29
When in get to step two i get this output

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-dev: Depends: libxcomposite-dev but it is not going to be installed
            Depends: libxss-dev but it is not going to be installed
            Depends: xserver-xorg-dev but it is not going to be installed
E: Broken packages

Anyone?

---

### Post by soholingo on 2007-01-30
Thanks SO MUCH for this howto.  I did everything exactly as you said, and it is working without a hitch.  I was so grateful, I signed up for the Ubuntu forums just to thank you.

J

---

### Post by kr0n1x on 2007-02-09
> **doundounba said:**
> To those getting "undefined symbol: faacDecOpen": do you have libfaad2-0 installed?  If not, try to install it.  Some googling suggests that this could be the problem...  HTH.

i've libfaad2-0 and libfaad2-dev installed, but i've forever the symbol error:(

any solution??

---

### Post by eqisow on 2007-02-15
Bump.

I have the symbol lookup error as well.

---

### Post by lprofil on 2007-02-18
> **soholingo said:**
> Thanks SO MUCH for this howto.  I did everything exactly as you said, and it is working without a hitch.  I was so grateful, I signed up for the Ubuntu forums just to thank you.

J

You don't use Cinelerra for model-plane-videos by coincidence?

/lprofil

---

### Post by jussipussi on 2007-02-25
I have dapper ppc. Is your tutorial usefull for my configuration ?

---

### Post by wessel_k on 2007-02-28
Hi,

I also had issues regarding the faacDecOpen error. I finally managed to find the problem. I had installed an ffmpeg-version from a repository which needed libfaad0. But to be able to install other software I also needed libfaad2-0. So I downloaded libfaad0 and libfaad2-0 version 2.5 from the developers website. The libfaad2 was only a referral to libfaad0. So by removing them and reinstalling transcode, ffmpeg using libfaad2 and then installing cinelerra I got everything working again. 
Hope this helps anybody who had the same issue?

Regards,

Wessel

---

### Post by Statik on 2007-03-04
well, how can I run cinelerra as root from the menu? Is there another way around this? Kino seems ok when I give it permission to the proper devices.

Statik

---

### Post by yodermk on 2007-03-06
Hi,

I just registered to also say thanks!!!

And to report that this tutorial works perfectly on Feisty Fawn Herd 5 with one change.

In step 2, replace "libguile-dev" with "guile-1.8-dev".  That's it!  It is now running.

---

### Post by Commodore Guff on 2007-03-10
> **wessel_k said:**
> Hi,

I also had issues regarding the faacDecOpen error. I finally managed to find the problem. I had installed an ffmpeg-version from a repository which needed libfaad0. But to be able to install other software I also needed libfaad2-0. So I downloaded libfaad0 and libfaad2-0 version 2.5 from the developers website. The libfaad2 was only a referral to libfaad0. So by removing them and reinstalling transcode, ffmpeg using libfaad2 and then installing cinelerra I got everything working again. 
Hope this helps anybody who had the same issue?

Regards,

WesselI as well had issues with the same problem, and this is the only solution I found that works.
Just be sure to use the 2.0 version of libfaad-2.0.

Though, libfaad-2.0 is now reported as being broken.  Dunno about that.  However, Cinelerra is working.

---

### Post by wessel_k on 2007-03-11
Hi,

I also had issues with libfaad or other packages being broken. But by checking all the enabled repositories I was able to find the culprit and I got rid of any broken packages.

Regards,

Wessel

---

### Post by phaidros on 2007-03-11
> **Jesterday said:**
> I am also getting the following error,

cinelerra: symbol lookup error: /usr/local/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

That is using the .deb file used in this tutorial...

Anyone have any ideas?

Darren

I got rid of this by removing libfaad2-0 and libfaad2-dev (maybe installed from another / older repo) and reinstall cinelerra from kiberpipa [1]. cinelerra-cv sources themselves [2] should work also then, imho. (cause with the debs there was the same error)

[1] deb [http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/) ./ 
or deb [http://www.kiberpipa.org/~muzzol/cinelerra/dapper/](http://www.kiberpipa.org/~muzzol/cinelerra/dapper/) ./ 
or deb [http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/) ./ 
(Version 20070901 SVN)

[2]  deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
(Also Version 20070901 SVN)

.. dunno the differences of the Repos.
[1] works for me, but I would recommend [2], because its the repository from the CV team.

---

### Post by centrinoblue on 2007-03-12
Thanks for the tutorial.  I have been trying to get Cinelerra installed for few days now.  I was following the instructions and everything was fine until step #4

#4. Creating the configure file

Create the `./configure' file by running: 
**:/opt/hvirtual# autoconf -i --force**


When I do that I get the following:

```
root@Desk-1:/opt/hvirtual# autoconf -i --force
configure.in:8: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:10: error: possibly undefined macro: AM_GNU_GETTEXT
configure.in:11: error: possibly undefined macro: AM_GNU_GETTEXT_VERSION
configure.in:12: error: possibly undefined macro: AM_PROG_AS
configure.in:18: error: possibly undefined macro: AC_ENABLE_SHARED
configure.in:19: error: possibly undefined macro: AC_DISABLE_STATIC
configure.in:20: error: possibly undefined macro: AC_PROG_LIBTOOL
configure.in:88: error: possibly undefined macro: AM_PATH_ALSA
configure.in:101: error: possibly undefined macro: AM_PATH_ESD
configure.in:233: error: possibly undefined macro: AM_CONDITIONAL
```

I am having trouble understanding what it means to 'use m4_pattern_allow'.  Any insight would be really appreciated.

cheers

---

### Post by mrfuzzemz on 2007-03-16
I wanted to make it known that this howto has worked for me in Feisty.  Danke Schön!!

---

### Post by cor2y on 2007-03-19
there seems to be two versions of cinelerra floating around.
The one from the Official Company Heroine Virtual and the version listed in this tutorial maintained by the community.
The problem is for some reason the orginal version can handle videos encoded with xvid and x264 as input files.
While the community maintained one gives a quicktime error for any sort of encoded xvid file and for x264 says there is no codec support for the file although it can render out both xvid and x264 files.
Another thing while the Heroine orginal version can except xvid and x264 it is less stable than the communtiy version so it crashes a lot.

Does anyone know of a way to get the community version to except x264 and xvid encoded files?
It will except files encoded with lavc in mpeg4 but not  xvid or x264.

---

### Post by gespertino on 2007-03-20
The problem seems to happen when an incorrect version of libfaad is installed. I checked in synaptic and fount two versions of the same library.
The problem was solved instantly when I forced libfaad to the other version I had available (the edgy official version, if I'm not wrong).

Now it works like a charm.
:guitar:

---

### Post by h4m574h on 2007-03-31
I have a problem of video lagging behind sound. (sorry if the problem was already anwsered, I'll check now.)

Now, how do I remove software I installed through SVN? I tried through aptitude, but the package cinelerra doesn't show.

Cheers.

---

### Post by charles nicholls on 2007-04-10
Sure enough, Cinelerra compiled nicely and had the correct privs to run w/o sudo.

I did get an error though that has been talked about before:

```

void MWindow::init_shm():WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low
 Before running Cinelerra do the following as root:
 echo "0x7fffffff" > /proc/sys/kernel/shmmax

```

(That is 7 f's)

I don't remember where I read about it before but the solution was to enable the root account, set shmmax, then run cinelerra. Just sudo'ing it doesn't give you enough privs to write to the /proc directory. I don't like enabling the root account so I:

```

bdk@buddha:~$ sudo -s
root@buddha:~# echo "0x7fffffff" > /proc/sys/kernel/shmmax
root@buddha:~# exit
exit
bdk@buddha:~$ cinelerra 

```

and it ran just fine... I don't mind having to do that each time I start up, after all this is linux, I'm not rebooting everyday. If it anoys me enough I'll find the perm fix for it or I'll just write a lil' script to do that and then load Cinerella.

Thanks again lprofil for the good how-to.

*-bdk*[/QUOTE]

Just for you.
 The GNU/Linux kernel only allows 32MB of shared memory to be allocated by default. This needs to be increased to do anything useful. When launched, Cinelerra may remind you that with the following error message:

The following errors occurred:
void MWindow::init_shm0: WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff">/proc/sys/kernel/shmmax

For a permanent change, add to the “`/etc/sysctl.conf’” file the following line:

kernel/shmmax=0x7fffffff

For the first time, to avoid restarting your computer, use the following command as root:

sysctl -p

---

### Post by coolguy2k on 2007-04-10
hey guys, i don't have make, i.e., "bash: make: command not found"

What do i need to do?

edit:  I ran cinelerra (skipping the make and make install steps and did sudo cinelerra) and it seemed to work just fine.  So do I need those other steps then?

---

### Post by 9a3eedi on 2007-04-15
I got an error while making
now I don't want to post a huge wall of text, so I posted the last couple of lines

```

/usr/bin/ld: ffmpeg/libavcodec/.libs/libavcodec.a(mpegvideo_mmx.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
ffmpeg/libavcodec/.libs/libavcodec.a(mpegvideo_mmx.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/opt/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

```

wierd.. 

I also got this when invoking ./configure
```

Summary of optional components:
  ESD subsystem           found
ESD (Enlightenment Sound Daemon) is enabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              found
  libiec61883             found
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is enabled
  OpenGL 2.0 libraries    missing
Hardware acceleration using OpenGL 2.0 is disabled

```

Says that OpenGL 2.0 libraries is missing and therefore hardware acceleration is not going to work.. but it's strange since I got OpenGL to work, especially since I am running beryl as I type this. It could be because of the fact that I'm using beryl? hmm..

/me goes to check the rest of the thread for any solution..


> **coolguy2k said:**
> hey guys, i don't have make, i.e., "bash: make: command not found"

What do i need to do?

edit:  I ran cinelerra (skipping the make and make install steps and did sudo cinelerra) and it seemed to work just fine.  So do I need those other steps then?

sudo apt-get install make

funny.. I would think that make would come bundled with ubuntu edgy o.O

---

### Post by costa_g on 2007-04-15
Hi guys, I am getting the following error:

cinelerra: error while loading shared libraries: libmjpegutils-1.8.so.0: cannot open shared object file: No such file or directory

Any I ideas where to get this from?

---

### Post by mrfuzzemz on 2007-04-16
> **costa_g said:**
> Hi guys, I am getting the following error:

cinelerra: error while loading shared libraries: libmjpegutils-1.8.so.0: cannot open shared object file: No such file or directory

Any I ideas where to get this from?

If you are using feisty just try this:

```
sudo apt-get install libmjpegtools0c2a libmjpegtools-dev

```

If you are using Edgy or other, search synaptic for libmjpegtools.  This package should include the library you are looking for. Hope this helps.

---

### Post by hihihi on 2007-04-20
hi there,
thanks for the tutorial.
it's highly recommended to compile yourself and not to install from repo.
you get more options. like opengl support, etc...

what helped me to avoid message: 

ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1 

during compile was to install "libmpeg3-dev" AND "nasm".
its in my synaptic manager.

bye hihihi

---

### Post by hihihi on 2007-04-20
furthermore, if you get:

bcwindowbase.h:73:38: error: X11/extensions/xf86vmode.h: No such file or directory
bcwindowbase.h:815: error: 'XF86VidModeModeInfo' does not name a type

just go to synaptic manager and install the package  "x11proto-xf86vidmode-dev" and "libxxf86vm-dev"
btw: i'm running ubuntu edgy

hihihi

---

### Post by tom-japan on 2007-05-02
Running Feisty on 64 bit machine (dell c521 dimension - junk, don't buy it)

I got Cinelerra:KS , avidemux, tovid-gui and Qdvdauthor (version .1.5) working nicely together at last. I read a lot of the posts, but ran into trouble anyway, so decided to post my own solution.

It's not pretty, but it works.

Main Problem: conflict between libmjpegtools0c2a package from ubuntu repositories and libmjpegtools0 package at [www.debian-multimedia.org](www.debian-multimedia.org) site.

Other point: qdvdauthor in ubuntu repositories is out of date, and always froze on me, hence the need for the packages from debian-multimedia repository.

Here GOES: (The order is important, if you don't do it like this, you get messed up with errors telling you to unistall avidemux, and cinelerra. Basically if 

Repositories:

All ubuntu repositories are on (universe multiverse)

add the following to /etc/apt/source.list :

1)
#deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
#deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing main contrib non-free

[INDENT][/INDENT]or line by line (strip the #) into synaptic (suggested, if you are not comfortable at the command line and editing config files)

[INDENT][/INDENT]If using synaptic, disable all non-ubuntu repositories

2)Install avidemux, qdvdauthor (.1.2 I think)

3)Enable deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./ repository and install cinelerra.

[INDENT][/INDENT]This package is made for Edgy, but works well. I first tried to compile the package myself, but I ended up completely messing up my installation with a bunch of uninstallable packages. So I don't see any problem with it- it took me a while of trying other things before this light came on.

3) Disable deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
    Enable deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
               deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing main contrib non-free

4) Install most recent version of qdvdauthor - this should only install one package. If it tries to update the libmjpegtools0, you will loose avidemux and cinelerra

5) Install all the tovid packages (4 needed, I think I downloaded them a while back for all architectures). They are not in the repositories, which is unfortunate, as they are great packages for batch conversions and such.

---

### Post by 9a3eedi on 2007-05-27
This guide worked perfectly well on my Edgy Centrino. 

lprofil.. thank you! your guide made life a lot easier.. ^_________^

---

### Post by Jalke on 2007-06-09
After a LOT of dependency issues I actually got it going!  Hurayyy!!!!  :guitar:

Jake
(Feisty Fawn)

---

### Post by Dread Knight on 2007-06-13
I have tried and tried and i couldn't get Cinelerra to work. :(

---

### Post by lprofil on 2007-06-21
> **Dread Knight said:**
> I have tried and tried and i couldn't get Cinelerra to work. :(

Did you try it on Edgy or on the Feisty release?

/lprofil

---

### Post by Dread Knight on 2007-06-22
> **lprofil said:**
> Did you try it on Edgy or on the Feisty release?

/lprofil

Gutsy. Anyway, I've followed another tutorial and managed to get 2.0 running.

---

