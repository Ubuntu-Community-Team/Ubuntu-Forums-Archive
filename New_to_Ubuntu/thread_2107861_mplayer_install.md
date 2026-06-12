---
title: "mplayer install"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by midwestmac on 2013-01-22
Hello, I'm using Ubuntu (mini)12.04 or(lubuntu) with Lxde desktop

I need help getting gnome mplayer to play a video (it doesn't show a video) I have read that "lubuntu" has a bug with mplayer and to use mplayer2.
So I downloaded [mplayer2-build-106bf4525ac9ef7a1cf8f1f41664d3be72121e99.tar.bz2]("http://git.mplayer2.org/mplayer2-build/snapshot/mplayer2-build-106bf4525ac9ef7a1cf8f1f41664d3be72121e99.tar.bz2")
then folowed the instructions from here:  [http://ubuntuforums.org/showthread.php?p=10996224](http://ubuntuforums.org/showthread.php?p=10996224)
 
 
$ sudo apt-get install libdvdread4 libdvdnav-dev libdvdread-dev && \ sudo /usr/share/doc/libdvdread4/install-css.sh
$ sudo apt-get build-dep mplayer 
$ sudo apt-get install build-essential subversion git-core yasm autoconf libtool  
$ git clone git://git.mplayer2.org/mplayer2-build.git  
$ cd mplayer2-build && ./enable-mt && ./init  
$ echo --prefix=$HOME >> ./mplayer_options  
$ make -j4  
$ make install  
$ mv $HOME/bin/mplayer $HOME/bin/mplayer2
 
But when I got to here-- ' $ cd mplayer2-build && ./enable-mt && ./init ' 
I got something like error 124 'libass missing'
I got frustrated and exited out  
 
I would like to start over but, I don't know what I'm doing yet. Do I need to delete all the mplayer files installed? or Does someone have a better build idea? Thanks

---

### Post by monkeybrain2012 on 2013-01-22
> **midwestmac said:**
> Hello, I'm using Ubuntu (mini)12.04 or(lubuntu) with Lxde desktop

I need help getting gnome mplayer to play a video (it doesn't show a video) I have read that "lubuntu" has a bug with mplayer and to use mplayer2.
So I downloaded [mplayer2-build-106bf4525ac9ef7a1cf8f1f41664d3be72121e99.tar.bz2]("http://git.mplayer2.org/mplayer2-build/snapshot/mplayer2-build-106bf4525ac9ef7a1cf8f1f41664d3be72121e99.tar.bz2")
then folowed the instructions from here:  [http://ubuntuforums.org/showthread.php?p=10996224](http://ubuntuforums.org/showthread.php?p=10996224)
 
 
$ sudo apt-get install libdvdread4 libdvdnav-dev libdvdread-dev && \ sudo /usr/share/doc/libdvdread4/install-css.sh
$ sudo apt-get build-dep mplayer 
$ sudo apt-get install build-essential subversion git-core yasm autoconf libtool  
$ git clone git://git.mplayer2.org/mplayer2-build.git  
$ cd mplayer2-build && ./enable-mt && ./init  
$ echo --prefix=$HOME >> ./mplayer_options  
$ make -j4  
$ make install  
$ mv $HOME/bin/mplayer $HOME/bin/mplayer2
 
But when I got to here-- ' $ cd mplayer2-build && ./enable-mt && ./init ' 
I got something like error 124 'libass missing'
I got frustrated and exited out  
 
I would like to start over but, I don't know what I'm doing yet. Do I need to delete all the mplayer files installed? or Does someone have a better build idea? Thanks


You have to install libass-dev and also you don't need to enable --mt now as ffmpeg-mt has since merged into the main trunk. you don't need to delete anything.

BTW. if you are installing from git you don't need to download the tarball. If you look into the mplayer2-build folder after finish running 
```
git clone git://git.mplayer2.org/mplayer2-build.git 
```
you would find a readme file which tells you the step to build mplayer2 and the dependencies. 

An easier way to install mplayer2 is to add the MOTU ppa and install it from the package manager. I believe mplayer from MOTU also works in Lubuntu 12.04 (don't know that there is a problem because I never install mplayer from the default repo, it is always hopelessly out of date)


[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

mplayer/mplayer2 has a nice gui frontend called SMplayer, you can get the latest version by adding the developer's ppa
[https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)

EDITED: If you install from ppa you'll get update automatically. If you install it locally by compiling yourself (the command "echo --prefix=$HOME" instructs that mplayer2 be installed in /home/usrname/bin) you need to update manually once in a while. This is how, from the terminal

```
cd mplayer2-build
./clean
./update
make
make install

cd ~/bin
mv mplayer mplayer2
```

---

### Post by midwestmac on 2013-01-23
Thanks for the info monkeybrain2012, 
 
I'll try this,  quote "mplayer/mplayer2 has a nice gui frontend called SMplayer, you can get the latest version by adding the developer's ppa"
[https://launchpad.net/~rvm/+archive/ppa/](https://launchpad.net/~rvm/+archive/ppa/)

I would rather have something that updates automatically
I'll let you know how it goes:D

---

### Post by monkeybrain2012 on 2013-01-23
> 

I would rather have something that updates automatically
I'll let you know how it goes:D

Hi, I think you misunderstood. I didn't mean it updates automatically behind your back, I meant it is "automatically" updated by the maintainer and the updates show up in synaptic like other Ubuntu software.

---

### Post by andrew.46 on 2013-01-23
Perhaps this would be useful:

[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

---

### Post by midwestmac on 2013-01-23
Thanks andrew and monkeybrain2012, 
I added the PPA , then went to package manager downloaded SMplayer.
 
It works only problem is Smplayer says " SMplayer couldn't identify the Mplayer version you're using."
 
My choices to select are: 
1:Orc1 or older
1:Orc2
1:orc3 or newer
 
Where can I find what what version of mplayer I have?, so they can work in together I guess.

---

### Post by monkeybrain2012 on 2013-01-23
> **midwestmac said:**
> Thanks andrew and monkeybrain2012, 
I added the PPA , then went to package manager downloaded SMplayer.
 
It works only problem is Smplayer says " SMplayer couldn't identify the Mplayer version you're using."
 
My choices to select are: 
1:Orc1 or older
1:Orc2
1:orc3 or newer
 
Where can I find what what version of mplayer I have?, so they can work in together I guess.

Choose the last one.

Did you compile mplayer2 yourself with those instructions? If so your executable is in your home directory (username/bin) Open Smplayer, go to Options > Preference > General and on the top there is a box where you can choose the mplayer/mplayer2 executable, click the right most button in the box and choose your mplayer executable (see screenshot)

---

### Post by midwestmac on 2013-01-23
It works!! Thankyou,  
I did this
-chose the 1: orc or newer
then
Mplayer/options/preferences/general.
Mplayer executable: /user/bin/mplayer
 
> **monkeybrain2012 said:**
> Choose the last one.
 
Did you compile mplayer2 yourself with those instructions? 
 
Well I  just have mplayer. Last night I used the Synaptic package manager and to download mplayer again hoping it might recompile things? (on its own):D
 
I never tried "andrew.46" link for mplayer2 in post above.
So it seems smplayer and mplayer are working together here, there is some pixelating in the video. 
Like its a video codec problem or my Nvidia  video card driver (I compiled myself from some intructions i found) 
For video pixelating---
What do you guys think about mplayer should I get mplayer2?
Troubleshoot nvidia vieo card driver?

---

### Post by SeijiSensei on 2013-01-23
> **monkeybrain2012 said:**
> your executable is in your home directory (username/bin)

I much prefer to install with "sudo make install" which places the executables and any related files under /usr/local.  That's the standard location for software installed by the user outside of the package management system.  This method also makes the program available to all users on the system.

---

### Post by monkeybrain2012 on 2013-01-23
If you have a Nvidia card mplayer2 is better in my experience. You can install it from synpatic if you add the MOTU ppa (installing it would remove mplayer but you don't need to reset Smplayer because the executable has the same name and in the same location)

In smplayer you should go to Options > Preference > Videos and set output to vdpau for GPU accelerated decoding, which is pretty sweet(you should do this whether you have mplayer or mplayer2)

BTW you don't need to compile the codecs yourself. Add the medibuntu repo and install nonfree-codecs and w64 codecs (or w32 if you have 32 bit) plus the Ubuntu restricted extras and you are set (and libdvdcss2 for dvd)
[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/](http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/)

Andrew's tutorials are the best if you like compiling and tweaking things, I learn a lot from them but IMO unnecessarily complicated for new users who just want to get their stuffs up and running. The point of Ubuntu is that you don't have to do this kind of work if you don't want to. :)

---

### Post by monkeybrain2012 on 2013-01-23
> **SeijiSensei said:**
> I much prefer to install with "sudo make install" which places the executables and any related files under /usr/local.  That's the standard location for software installed by the user outside of the package management system.  This method also makes the program available to all users on the system.

In that case I would recommend installing the package checkinstall and do "sudo checkinstall" instead of "sudo make install". That way you can remove it from synaptic or SC as one package if needed instead of having fragments all over the file system.

OP's instructions use the prefix=$HOME option so it would be install in the /home/username/bin, but in the end he just installed from the repo anyway. :)

In my case I prefer to install it in my home because I like to also install mplayer for comparisons and in my system there is only one user: me. :)

---

### Post by SeijiSensei on 2013-01-23
> **monkeybrain2012 said:**
> In my case I prefer to install it in my home because I like to also install mplayer for comparisons and in my system there is only one user: me. :)

You can do that by giving the full path at the command prompt.  I have both mplayer and mplayer2 installed as well.  I can use /usr/bin/mplayer to access the first one, and /usr/local/bin/mplayer to run mplayer2.

---

### Post by midwestmac on 2013-01-23
Boy thankyou very much monkeybrain,
I added MOTU ppa, 
installed mplayer2 from synpatic
 Then went and changed this Options > Preference > Videos and set output to vdpau for GPU accelerated decoding.
 
Awsome thanks for everyones help its working great. Watching "Battleship":popcorn:now.

---

