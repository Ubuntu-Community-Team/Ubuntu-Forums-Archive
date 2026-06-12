---
title: "Cinelerra 2.1 CV for Hardy Haron 8.04 [ How To / Tutorial ]"
date: 2008-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by lprofil on 2008-05-01
Hello again,

probably you found the .deb file for Hardy Haron on **[cinelerra.org]("http://cinelerra.org/getting_cinelerra.php")**.

But since this was not working for me right away i decided to write this Howto 
for those users who want to install Cinelerra 2.1 CV from sources.


**Preamble**

This tutorial is written for **Hardy Heron 8.04 32-Bit**.
I tested my tutorial on a fresh vigin installation of Hardy Heron
with no additional packages.


**#1.** Adding "Restricted Respositories"

Make sure "Universe" and "Multiverse" repositories" are included in your respositories **[[1]]("https://help.ubuntu.com/8.04/add-applications/C/extra-repositories.html")**.


**#2.** Get necessary packages

First become root:
```
sudo -s
```


This is a bunch of packages you will need to compile cinelerra:

```
sudo aptitude install -y g++-4.2 subversion autoconf gettext libtool xlibs-static-dev libasound2-dev nasm  liboggz1-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng12-dev libtiff4-dev libx264-dev libmjpegtools-dev uuid-dev libfftw3-dev liba52-0.7.4-dev liblame-dev libsndfile1-dev libfaac-dev libfaad-dev libraw1394-dev libiec61883-dev libxxf86vm-dev xmorph libxv-dev quicktime-x11utils quicktime-utils libarts1-mpeglib
```

   (Hint: **click four times** to mark the whole line)


**#3.** Download the Source-Tree

first change directory to the /opt folder:

```
cd /opt
```

download the subversion files:

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
./autogen.sh
```


**#5.** Run configure

Then run the `.configure' file: 

```
./configure --with-buildinfo=svn/recompile 
```


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

This error has not been fixed since it was reported in 
2007-01-21 22:58 +2


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

Start Cinelerra as root:

```
sudo cinelerra
```


Fahrvergnügen!

/lprofil


**Documents:**
[http://bugs.cinelerra.org/](http://bugs.cinelerra.org/)
[http://bugs.cinelerra.org/show_bug.cgi?id=397](http://bugs.cinelerra.org/show_bug.cgi?id=397)

**Editing History:**

**Thanks to: **
[jan_everts]("http://ubuntuforums.org/archive/index.php/t-586370.html")
[Jalke]("http://ubuntuforums.org/showthread.php?t=188264&page=9)

---

### Post by richandcreamy on 2008-05-27
I run into this error:

checking for libasound headers version >= 1.0.2... not present.
configure: error: Sufficiently new version of libasound not found.

but I have a higher version than that! =(

---

### Post by dahawk25 on 2008-05-27
Hi

(still new to Ubuntu)
I received those errors you gave fixes for but must have not done it right, 
These are the errors, i went back and tryed to redo your error fix but it still did not help any thing.  

env: g++: No such file or directory
make[2]: *** [bcbar.lo] Error 1
make[2]: Leaving directory `/opt/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

If you have any ideas or help i would greatly appreciate it Thanks

---

### Post by wyattgoettsch on 2008-05-28
> **dahawk25 said:**
> Hi

(still new to Ubuntu)
I received those errors you gave fixes for but must have not done it right, 
These are the errors, i went back and tryed to redo your error fix but it still did not help any thing.  

env: g++: No such file or directory
make[2]: *** [bcbar.lo] Error 1
make[2]: Leaving directory `/opt/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2


I also experience this problem during compilation. This is a different issue than the one he addressed in the tutorial.

Would someone help?

---

### Post by Chrisj303 on 2008-06-15
This is ridiculous.

Why don't the devs just check the.deb files before they release them?

I've been dicking around for 2 hours trying to get cinelerra installed onto my machine.

Just going to scrap the idea, and stick with Final Cut Pro on my Mac partition.

Its crap like *this* that is holding back Linux from being useable by the majority.

---

### Post by spooky655 on 2008-06-20
try this:
[http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")
 
and then search for it in synaptic

---

### Post by mateuszbaranski on 2008-06-26
> **spooky655 said:**
> try this:
[http://cinelerra.org/getting_cinelerra.php#ubuntu]("http://cinelerra.org/getting_cinelerra.php#ubuntu")
 
and then search for it in synaptic

the problem is that after installation of deb files Cinelerra doesn't respond to any click on's. No menu, no widget, no button works at all after upgrade from 7.10 (feisty) to 8.04 (hardy)

I recently find solution in my hardy installation. You could find this here:

[http://ubuntuforums.org/showthread.php?p=5267875#post5267875](http://ubuntuforums.org/showthread.php?p=5267875#post5267875)

Hope it help

---

### Post by cor2y on 2008-06-26
Question does cinlerra (at least this version on hardy) allow working with avi xvid, divx or X264 encoded files without spitting up an error or crashing?
Ever since 7.04 i have been having problems with cinelerra and editing avi files either it would crash or spit up errors or not support X264 encoded files, the only workaround is to change the fourcc of the file in question and even then there was a 60% chance the program would crash while editing/creating a project.

---

### Post by seekq on 2008-07-05
After apparently successfully installing, I got the following when I tried to run:


cinelerra: error while loading shared libraries: libquicktimehv-1.6.0.so.1: cannot open shared object file: No such file or directory



Any help appreciated.

Thanks

---

### Post by Francewhoa on 2010-03-26
**After step #7 **
```
cd /opt/hvirtual make
make
```

**Terminal returns the following error message**
```
make[2]: *** [bcbar.lo] Error 1
make[2]: Leaving directory `/opt/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2
```

---

### Post by coolime12345 on 2010-08-22
Anybody knows any NORMAL Ubuntu video editor, normally installed, normally compatible?
:confused:

---

### Post by lprofil on 2011-07-13
> **Onopoc said:**
> **After step #7 **
```
cd /opt/hvirtual make
make
```

**Terminal returns the following error message**
```
make[2]: *** [bcbar.lo] Error 1
make[2]: Leaving directory `/opt/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2
```


From this thread:
[http://comments.gmane.org/gmane.comp.video.cinelerra-cv.general/12589](http://comments.gmane.org/gmane.comp.video.cinelerra-cv.general/12589)

try to install some mesa-dev libary. It might fix it.

/lprofil

---

