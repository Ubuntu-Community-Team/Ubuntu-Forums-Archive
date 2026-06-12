---
title: "How to download and build Cinelerra on Gutsy"
date: 2007-10-20
forum: Outdated Tutorials &amp; Tips
---

### Post by blippy on 2007-10-20
I have posted instructions on how to download, build, install and run Cinelerra on a clean Gutsy box at the following link:
[http://lab.dyne.org/cinelerra/Gutsy]("http://lab.dyne.org/cinelerra/Gutsy")
That ought to save you guys hours of futzing around trying to get it working :)

I reproduce my text below

This page describes how to build Cinelerra on a brand spanking new Gutsy box, and tested with Cinelerra-CV subversion revision 1036.

**Shmmax**

Issue the following command as root:

echo "0x7fffffff" >/proc/sys/kernel/shmmax

This sorts out the weird warning you get about shmmax

**Dependencies**

In previous versions of Ubuntu, there was a reliance on external repositories, and a few other packages that you had to build yourself. Fortunately, this no longer seems necessary. The following packages should be sufficient (there may be the stray unnecessary package - but you might as well install everything anyway) to build Cinelerra from a fresh install of Gutsy:

g++
git-core
cogito
subversion
automake
libtool
nasm
x11proto-xf86vidmode-dev
libxv-dev
libxxf86vm-dev
libogg-dev
libvorbis-dev
libtheora-dev
libopenexr-dev
libdv-dev
libpng-dev
libjpeg62-dev
libtiff4-dev
libfreetype6-dev
libsndfile1-dev
uuid-dev
libasound2-dev
libavutil-dev
libmpeg3-dev
libavcodec-dev
libx264-dev
libfaac-dev
libmjpegtools-dev
fftw3
fftw3-dev
liba52-0.7.4-dev
liblame-dev
libfaad2-dev
libesd0-dev
libiec61883-dev
libavc1394-dev

The quickest way to install the dependencies is save them in a file like "apts", and then issue the following command as root:

xargs apt-get install -y <apts

**Downloading, building and running**

You don't need root privileges to perform the following.

You can download the latest version of Cinelerra by typing:

svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual

Then

cd hvirtual
./configure
make
sudo make install

You can run Cinelerra by typing

cinelerra

or start it from

Applications > Sound & Video > Cinelerra

---

### Post by carusoswi on 2007-12-22
When I do that bid about Shmmax, I get a permission denied message.  I used Sudo before the command, also tried the command without sudo . . . no joy.  Can you help?
Thanks.
Caruso

> **blippy said:**
> I have posted instructions on how to download, build, install and run Cinelerra on a clean Gutsy box at the following link:
[http://lab.dyne.org/cinelerra/Gutsy]("http://lab.dyne.org/cinelerra/Gutsy")
That ought to save you guys hours of futzing around trying to get it working :)

I reproduce my text below

This page describes how to build Cinelerra on a brand spanking new Gutsy box, and tested with Cinelerra-CV subversion revision 1036.

**Shmmax**

Issue the following command as root:

echo "0x7fffffff" >/proc/sys/kernel/shmmax

This sorts out the weird warning you get about shmmax

**Dependencies**

In previous versions of Ubuntu, there was a reliance on external repositories, and a few other packages that you had to build yourself. Fortunately, this no longer seems necessary. The following packages should be sufficient (there may be the stray unnecessary package - but you might as well install everything anyway) to build Cinelerra from a fresh install of Gutsy:

g++
git-core
cogito
subversion
automake
libtool
nasm
x11proto-xf86vidmode-dev
libxv-dev
libxxf86vm-dev
libogg-dev
libvorbis-dev
libtheora-dev
libopenexr-dev
libdv-dev
libpng-dev
libjpeg62-dev
libtiff4-dev
libfreetype6-dev
libsndfile1-dev
uuid-dev
libasound2-dev
libavutil-dev
libmpeg3-dev
libavcodec-dev
libx264-dev
libfaac-dev
libmjpegtools-dev
fftw3
fftw3-dev
liba52-0.7.4-dev
liblame-dev
libfaad2-dev
libesd0-dev
libiec61883-dev
libavc1394-dev

The quickest way to install the dependencies is save them in a file like "apts", and then issue the following command as root:

xargs apt-get install -y <apts

**Downloading, building and running**

You don't need root privileges to perform the following.

You can download the latest version of Cinelerra by typing:

svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual

Then

cd hvirtual
./configure
make
sudo make install

You can run Cinelerra by typing

cinelerra

or start it from

Applications > Sound & Video > Cinelerra

---

### Post by blippy on 2007-12-22
> **carusoswi said:**
> When I do that bid about Shmmax, I get a permission denied message.  I used Sudo before the command, also tried the command without sudo . . . no joy.  Can you help?
Thanks.
Caruso

Try 
sudo gedit /proc/sys/kernel/shmmax
and enter the value
0x7fffffff

For a permanent fix that survives reboot, do 
sudo gedit /etc/sysctl.conf
and add the line
kernel.shmmax = 2147483647

---

### Post by carusoswi on 2007-12-22
When I enter the value you have posted, I am presented with an opportunity to save.  I cannot save.  Did I do something wrong?

Caruso

---

### Post by blippy on 2007-12-22
Type 
ls -hl /proc/sys/kernel/shmmax
What is the output?

Type 
ls -hl /etc/sysctl.conf
What is the output?

---

### Post by carusoswi on 2007-12-23
> **blippy said:**
> Type 
ls -hl /proc/sys/kernel/shmmax
What is the output?

Type 
ls -hl /etc/sysctl.conf
What is the output?

Here is the output:

ls -hl /etc/sysctl.conf

When I enter that value that you suggest, I'm in a gedit screen.  Ubuntu complains as I try to exit that screen that it cannot make a backup of the file, and the only successful exit is to close without saving.

Perhaps the above output is what I am after, but, it doesn't feel right to be exiting after entering the value without saving - how would the value have any effect?

I must be missing something.

Thanks for hanging in there with me.

Caruso

---

### Post by blippy on 2007-12-23
> **carusoswi said:**
> Here is the output:

ls -hl /etc/sysctl.conf


You neglected to mention the actual output.

> **carusoswi said:**
> 
Perhaps the above output is what I am after, but, it doesn't feel right to be exiting after entering the value without saving - how would the value have any effect?

I must be missing something.


I'm guessing the file hasn't been saved. I thought it worthwhile to check your file permissions. Not sure what's wrong, because it really shouldn't be a problem.

How about trying
sudo -s # gives you ROOT access - needs password
echo "0x7fffffff" >/proc/sys/kernel/shmmax
gedit /etc/sysctl.conf

and then putting in the value 
kernel.shmmax = 2147483647

I'm really puzzled as to what the problem is. Maybe you're not getting root, the permissions are messed up, or something.

---

