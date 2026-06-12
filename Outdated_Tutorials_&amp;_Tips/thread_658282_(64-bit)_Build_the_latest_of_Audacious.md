---
title: "(64-bit) Build the latest of Audacious"
date: 2008-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2008-01-04
**Tested:** Ubuntu 7.10 64-bit Gnome,  Ubuntu 7.10 64-bit Gnome (should work as well on 32-bit)
**Homepage:** [http://audacious-media-player.org](http://audacious-media-player.org)
**Original Guide:** [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html)


Audacious is a fork of beep-media-player 0.9.7.1. This means that Audacious is not a fork of XMMS (it seems to be assumed that BMP classic == XMMS, that's not true either), but a continuation of a previous fork of XMMS.

This guide show how to build the latest version of Audacious and its plugins.


[LIST]
[*]Before Installation
[*]Installation
[*]Auto-play CDs
[*]Audacious Associate Media Files
[*]Skins
[*]Advance Audacious Eyecandy
[/LIST]

[[img]http://www.imageviper.com/displayimage/107294/0/Pre-Audacious.png[/img]](http://www.imageviper.com/displayimage/107295/0/Audacious.png)
[size=1]Click to enlarge[/size]



===========================================

[SIZE="5"]**Before Installation**[/SIZE]

First thing you need is to enable all the sources in your repository. You can do that by; System tab ---> Administration ---> Software Sources.
You also need to enable medibuntu which you can find here; [http://www.medibuntu.org/]("http://www.medibuntu.org/")

When that is done, open the terminal (Applications tab ---> Accessories ---> Terminal ).
To build Audacious from the source the right tools, libs and headers is needed, also the old Audacious needs to be uninstall, type this in the terminal;

For Ubuntu 8.04 and previous versions 
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential mercurial autogen automake checkinstall
sudo apt-get install libgtk2.0-dev libpng12-dev libglade2-dev libdbus-glib-1-dev bison libgconf2-dev libxml2-dev libxcomposite-dev libgnomevfs2-dev imlib11-dev
sudo apt-get install gettext libsamplerate0-dev libsidplay1-dev libsidplay2-dev libflac-dev libmad0-dev libvorbis-dev libasound2-dev libesd0-dev libpulse-dev libsndfile1-dev libmpcdec-dev liblame-dev libgtkglext1-dev
sudo apt-get install liblircclient-dev libbinio-dev libwavpack-dev libtag1-dev libjack0.100.0-dev libresid-builder-dev libfluidsynth-dev libcdio-dev libcurl4-openssl-dev libmms-dev libmtp-dev libsdl1.2-dev libimlib2-dev libcdio-cdda-dev libcddb2-dev libneon26-dev flex
```

For Ubuntu 8.10 
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential mercurial autogen automake checkinstall
sudo apt-get install libgtk2.0-dev libpng12-dev libglade2-dev libdbus-glib-1-dev bison libgconf2-dev libxml2-dev libxcomposite-dev libgnomevfs2-dev imlib11-dev
sudo apt-get install gettext libsamplerate0-dev libsidplay1-dev libsidplay2-dev libflac-dev libmad0-dev libvorbis-dev libasound2-dev libesd0-dev libpulse-dev libsndfile1-dev libmpcdec-dev libtwolame-dev libmp3lame-dev libgtkglext1-dev
sudo apt-get install liblircclient-dev libbinio-dev libwavpack-dev libtag1-dev libjack0.100.0-dev libresid-builder-dev libfluidsynth-dev libcdio-dev libcurl4-openssl-dev libmms-dev libmtp-dev libsdl1.2-dev libimlib2-dev libcdio-cdda-dev libcddb2-dev libneon26-dev flex
```


There's one lib that you need but it's not available in Ubuntu repo, therefore it needs to be build as well;


**libmowgli**

[size=1]mowgli is a development framework for C (like GLib), which provides high performance and highly flexible algorithms. It can be used as a suppliment to GLib (to add additional functions (dictionaries, hashes), or replace some of the slow GLib list manipulation functions), or stand alone. It also provides a powerful hook system and convenient logging for your code, as well as a high performance block allocator.
mowgli builds upon previous attempts, such as libmisc, and will likely become the primary development framework for most projects at Atheme.[/size]
[[Homepage]](http://www.atheme.org/)

For Ubuntu 8.04 and above
[size=1][color=red]Recommended that you build it by yourself (see For Ubuntu 7.10 (below)), to get the latest version[/color][/size]
```
sudo apt-get install libmowgli-dev
```

For Ubuntu 7.10 
```
cd ~/Desktop
hg clone http://hg.atheme-project.org/libmowgli libmowgli-devel
cd libmowgli-devel
sh autogen.sh
./configure --prefix=/usr
make
checkinstall --install=no
sudo dpkg -i *.deb

```

Remember to change option (3) to a version number(X.X.X) in checkinstall.




**libMCS**

[size=1]Modular Config System is a library and set of tools which abstract the storage of configuration settings away from userland applications.[/size]
[[Homepage]](http://www.atheme.org/)

```
cd ~/Desktop
hg clone http://hg.atheme-project.org/libmcs libmcs-devel
cd libmcs-devel
sh autogen.sh
./configure --prefix=/usr
make
checkinstall --install=no
sudo dpkg -i *.deb
```

Remember to change option (3) to a version number(X.X.X) in checkinstall.

Now you're ready to compile Audacious and its Plugin.



[SIZE="5"]**Installation**[/SIZE]


**Audacious**
The first thing that need to be build is Audacious. This is the structure of Audacious and do not contain any plugins, codecs and format.


```
sudo mkdir -p /usr/local/share/audacious/Skins
cd ~/Desktop
wget http://distfiles.atheme.org/audacious-1.5.1.tgz
tar zxfv audacious-1.5.1.tgz
cd audacious-1.5.1
./configure --enable-samplerate
make
checkinstall --addso=yes --install=no
sudo dpkg -i *.deb
cd src/libaudclient
sudo cp -r libaudclient.so /usr/lib/libaudclient.so.1

```


**Audacious Plugin**
This contains codecs, visualizer, sound enhancer etc.
[21 Decoders][5 Visualization][7 Effects][10 general plugins]

```
cd ~/Desktop
wget http://distfiles.atheme.org/audacious-plugins-1.5.1.tgz
tar zxfv audacious-plugins-1.5.1.tgz
cd audacious-plugins-1.5.1
./configure
make
checkinstall --install=no
sudo dpkg -i *.deb
```


Audacious is now installed and ready for use. You can start it by writting **audacious** in the terminal or via Applications tab ---> Sound & Video ---> Audacious.

This guide used checkinstall, so if you like to uninstall it, you can do it via synaptic. Remember if you want to build or install another version of Audacious you must uninstall the previous one that is build by checkinstall.



[SIZE="5"]**Auto-play CDs**[/SIZE]
[size=1]Only for Ubuntu 7.10 and below[/size]

You want audacious auto-play your CDs when inserted in the CD-drive?

```
gnome-volume-properties
```

Go to the **Multimedia** tab and select Audio CD Discs

fill in;

```
audacious -p /media/cdrom
```

Done.



[SIZE="5"]**Audacious Associate Media Files**[/SIZE]

If you want Audacious to associate eg. all mp3 files (when you click a mp3 file audacious will play it).

Right click on a mp3 file and select **Properties**-
Go to the **Open with** tab.
Double click **audacious**.
If it's not there, simple click the **add** button to add it to the open with option.



[SIZE="5"]**Skins**[/SIZE]

To install skins for Audacious you have to copy the skin(s) to /usr/local/share/audacious/Skins
Note you don't need to extract the skin file, just copy it to the location.

an example if you have the skin called Aqua.wsz on your Desktop;

```
cd ~/Desktop
sudo cp -r Aqua.wsz /usr/local/share/audacious/Skins
```


If you have a folder full of skins

```
cd <into your skin collection directory>
sudo cp -r * /usr/local/share/audacious/Skins
```




[SIZE="5"]**Advance Audacious Eyecandy**[/SIZE]

This is needed to be done before you start to build Audacious source, if you already build an install Audacious you need to uninstall it to accompilish this.

If you want to change the icon and the graphic like I have done (see screenshot), you have to do this;

Download Audacious&#8203;-Inner&#8203;-Theme&#8203;.tar&#8203;.gz (attached to this post) to your Desktop.

```
cd ~/Desktop
tar zxfv Audacious-Inner-Theme.tar.gz
```

copy audacious.png from image folder to **audacious-1.5.1/pixmaps**
Then move rest of the icons in the image folder to **audacious-1.5.1/src/audacious/images**
The icons in audioscrobbler folder you move to **audacious-plugins-1.5.1/src/scrobbler/images**

If you want to make your own Audacious preferences icons, here is the background for it;

[img]http://bp3.blogger.com/_-keIPI3rNgc/R0MXVirAb9I/AAAAAAAAAHA/PTxHDqryyjs/s1600/platform.png[/img]

Enjoy

Regards
A.I. Dude

===========================================
Other 64-bit guides:
[Build the  latest of Pidgin + Plugins](http://ubuntuforums.org/showthread.php?p=4072317)
[Install F-prot (anti-virus)](http://ubuntuforums.org/showthread.php?t=623665)
[Install AVG (anti-virus)](http://ubuntuforums.org/showthread.php?t=622967)

---

### Post by Technoviking on 2008-01-04
Great guide, works for me except Audacious is very CPU hungry after awhile, using 50% of my CPU.

---

### Post by Perfect Storm on 2008-01-05
Guide updated

-- added Index
-- Added Audacious Associate Media Files
-- Added Advance Audacious Eyecandy
-- Added Homepage link to libmowgli

---

### Post by Technoviking on 2008-01-09
Make sure to delete/move your ~/.config/audacious  if you are having problems after upgrading. That fixed my CPU usage problem.

Mike

---

### Post by aparigraha on 2008-02-10
XLNT how to.
thx alot

---

### Post by elamericano on 2008-03-23
Darn, I didn't save /usr/local/share/audacious/Skins before installing 8.04. Now where did I get those things...

This time I'm going to symlink it to a directory in home!

---

### Post by Perfect Storm on 2008-04-08
Guide updated.
Also tested for Ubuntu 8.04
Inner theme updated to fit audacious 1.5.0

---

### Post by elgatovolador on 2008-05-11
Hi, i have several hours trying to install audacious 64 bits once and again, but after resolving some library dependencies, i am getting this error when try install the audacious plugins..

Successfully compiled xs_init.c.
Successfully compiled xs_about.c.
Successfully compiled xs_support.c.
xs_config.c:254:2: error: #error This should not happen! No supported SIDPlay2 builders configured in!
Failed to compile xs_config.c!
make[2]: *** [xs_config.o] Error 1
make[1]: *** [install] Error 1
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


Please help me, i don't wanna surrender.. :mad:

btw, i have ubuntu 8.04 (64 bits) installed on a Dell 1721 laptop (AMD Turion 64 processors).

---

### Post by Perfect Storm on 2008-05-11
Well, you don't need to compile it at the moment. The version in the repo is the latest at the moment.

Otherwise you can disable sid2 if it's nothing you gonna use.

---

### Post by ramkumail on 2008-05-21
Can some one tell me how to install 31 band equalizer plugin for audacious? I have started a new thread here so that it gets better attention. [http://ubuntuforums.org/showthread.php?t=802131](http://ubuntuforums.org/showthread.php?t=802131) 

I am posting this here as the issue is closely related. Linux geeks, please help me do this.

---

### Post by Perfect Storm on 2008-05-29
Updated the guide to fit Audacious 1.5.1

---

### Post by Perfect Storm on 2008-06-04
Guide updated;
Change the libs installation in guide (using checkinstall with two of the libs).

---

### Post by moore.bryan on 2008-06-06
maybe you guys can answer a quick question... i have the latest hg libmcs installed, but i keep getting this:
```
libmcs version 0.5.0 was found, but libmcs >= 0.7 is required.
```
rather frustrating...

---

### Post by Perfect Storm on 2008-06-07
Check if you have an old version of libmcs (-dev) installed. Try remove it.

---

### Post by moore.bryan on 2008-06-09
yeah, first thing i tried... very strange.
========================
EDIT

so i went out on a limb and tried 
```
export PKG_CONFIG_PATH="/usr/lib/pkgconfig:/usr/local/lib/pkgconfig"
```
just in-case the issue of the compiler not reading the correct libmcs was similar to the error of not thinking libmcs was installed at all and, voila, success.

---

### Post by mustang on 2008-06-11
> **Artificial Intelligence said:**
> Updated the guide to fit Audacious 1.5.1

Hi AI. I actually didn't follow your guide but I was able to successfully build audacious and audacious-plugins both 1.5.1.

However, when I play an mp3, it does nothing. Even when I try through the terminal, all I get is:

```

manish@manish-laptop:~$ audacious Music/jay-z-blow_the_whistle.mp3 

(audacious:6569): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

```

The "open file" window comes up but when I select a file nothing happens. I made sure to select the PulseAudio output in the output section. I did not have this problem with 1.5.0 (in the repository). 

edit: I tried removing ./config/Audacious/; no dice.

---

### Post by luke16 on 2008-06-17
Would the packages made by checkinstall work on other peoples computers?
I would like to be able to use a deb package to install it, which would be easier.
I already tried building it from source as in the guide, but synaptic started saying that I had broken packages (I believe it was that I had libmcs .7 installed, while something wanted libmcs1, which wouldn't install because it conflicted with libmcs .7, and I don't know how to force synaptic to ignore a dependency). So if there was a way to get all of this on some repository or make it as deb files, I think that would just be better than everyone having to do all of this (and potentially having problems). I would be willing to try to help, but I don't think I know enough to do it right.
The developers over at the website would prolly be willing to post the debian packages, or at least post where you can get it.

---

### Post by sandrshe on 2008-06-20
everything installed fine but when i run Audacious i get the following error:


audacious: symbol lookup error: /usr/lib/mcs/libkeyfile.so: undefined symbol: mcs_list_append




Ubuntu 64 8.04 and followed your guide to the T

How do i resolve?
thanks

---

### Post by DancemasterGlenn on 2008-08-29
Totally unhelpful, but I'm experiencing the same problem as sandrshe. I think the answer to this issue used to be addressed on the audacious forums, but that post was lost after the forums went down for a couple of months...

If anyone could help out, I'd appreciate it. I haven't been able to use audacious in months because of this.

EDIT: To quote people on the audacious forums...
> Audacious require libmcs >= 0.7 (libkeyfile.so is in old libmcs-0.5)
Turned out I forgot to remove all of my old mcs packages on synaptic before going through with this whole process. Uninstalling those and redoing the mcs part of this walkthrough has solved my problems. Hope this helps people out!

---

### Post by Crafty Kisses on 2008-08-29
Thanks for the tutorial I'm really liking it, nicely typed and very smooth. :)

---

### Post by randolf_ambrose on 2010-03-02
hi... i followed this tutorial to install audacious 2.2 on my jaunty...

i made one mistake in between, in the end, i gave a different name when i saw a chance to rename audacious, i tried to put amp...

well... everything went well... but when i click audacious link, nothing comes up!!!

what could be wrong... i repeated the whole process a second time making no mistakes and still audacious is not up n running!!!

pls help!!!

---

### Post by JoZ3 on 2010-03-17
Hey try install the karmic version from this repo [https://launchpad.net/~philip5/+archive/extra]("https://launchpad.net/~philip5/+archive/extra"), in my jaunty 64 bits work fine

---

