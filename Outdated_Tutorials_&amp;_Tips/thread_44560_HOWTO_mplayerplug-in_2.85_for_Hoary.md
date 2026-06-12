---
title: "HOWTO: mplayerplug-in 2.85 for Hoary"
date: 2005-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by drigloi on 2005-06-26
As you might know mplayerplug-in is a handy Mozilla/Firefox plugin for streaming media contents on webpages. Currently Hoary has the quite aged version 2.70 of this plugin. Since that version things have changed significantly - now mplayerplug-in is one of the best option for viewing streaming video on web pages under Linux.

Here is how to compile it under Hoary:

NOTE:
I have enabled the following repositories (see ubuntuguide.org on how to do it):
[U]main
restricted
universe
multiverse
hoary-backports[/U]
Because I have **backports** enabled I am able to install mplayer and the latest Mozilla browser (Hoary's Mozilla is 1.7.6 while backports has the latest stable 1.7.8 which I use). This guide is based on Mozilla 1.7.8 - I don't know if it is working with the 1.7.6.

1. Set up mplayer & w32codecs
```
sudo apt-get install mplayer w32codecs
```

2. Grab latest mplayerplug-in source from here:
```
wget http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-2.85.tar.gz
```

3. Untar the mplayerplug-in source
```
tar -xvzf mplayerplug-in-2.85.tar.gz
``` 

4. Prepare dependencies for the build:
```
sudo apt-get install mozilla-dev libxpm-dev libgtk2.0-dev

```

5. Grab gecko-sdk from here:
```
wget http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.8/gecko-sdk-i686-pc-linux-gnu-1.7.8.tar.gz
```

6. Untar gecko-sdk:
```
tar -xvzf gecko-sdk-i686-pc-linux-gnu-1.7.8.tar.gz
``` 

7. Compile mplayerplug-in:
```
cd mplayerplug-in
./configure --with-gecko-sdk=../gecko-sdk
make

```

8. the "make install" (**you should remove the old mozilla-mplayer package prior this step!**)
```
sudo cp mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in.xpt /usr/lib/mozilla-firefox/components
sudo cp mplayerplug-in.types /etc
sudo cp mplayerplug-in.conf /etc
``` 

9. Prepare the config file:
```
sudo gedit /etc/mplayerplug-in.conf
```

Edit it like this:
```
#debug=0
#logfile=$HOME/mpp.log
vo=xv,x11
ao=esd,oss,arts
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
cachesize=1024
#use-mimetypes=0
#enable-real=0
#enable-wm=1
#enable-qt=1
#enable-mpeg=1
#enable-ogg=1
#enable-smil=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
``` 

As you see we've changed "vo" to "xv,x11", "ao" to "esd,oss,arts" and "cachesize" to "1024".

10. Restart Firefox and there you are!!!

---

### Post by donar73 on 2005-06-27
Thx, works great!  :smile:

---

### Post by Knome_fan on 2005-06-27
Hi, first off, thanks for the nice howto.

Inspired by it I took a look at the available debian packages and found out that the mozilla-mplayer source package for 2.85 is available. So I figuered it would be nice to use this to install mozilla-mplayer (which is the debian name for the mplayerplug-in).

So, here it goes.

**1. Get the needed files** 

Get the files you need on the debian page:
[http://ftp.debian.org/debian/pool/contrib/m/mplayerplug-in/mplayerplug-in_2.85-1.dsc](http://ftp.debian.org/debian/pool/contrib/m/mplayerplug-in/mplayerplug-in_2.85-1.dsc)
[http://ftp.debian.org/debian/pool/contrib/m/mplayerplug-in/mplayerplug-in_2.85.orig.tar.gz](http://ftp.debian.org/debian/pool/contrib/m/mplayerplug-in/mplayerplug-in_2.85.orig.tar.gz)
[http://ftp.debian.org/debian/pool/contrib/m/mplayerplug-in/mplayerplug-in_2.85-1.diff.gz](http://ftp.debian.org/debian/pool/contrib/m/mplayerplug-in/mplayerplug-in_2.85-1.diff.gz)

and download them to one directory.

**2. Get the needed dependencies** 

Now get all the dependencies you need by running:
```
sudo apt-get build-dep mozilla-mplayer
```

This should install all you need for building and installing mplayerplug-in, with one exception I will get to in a second. (Note, I'm assuming here that you have enabled all the repositories that  drigloi mentions)

Now on to the missing dependency. We are going to build mplayerplug-in with gtk2 support, as it looks nicer and will give us nice controls. To be able to do this, we'll have to install the gtk2 development files:
```
sudo apt-get install libgtk2.0-dev
```

Finally, install fakeroot as we are going to use it later on. (We don't exactly need it,  it is simply a tool that will allow us to do things as a normal user normally only root would be able to do)
```
sudo apt-get install fakeroot
```
 
**3. Build the package** 

If you haven't already done it, change to the directory to which you downloaded the debian files and unpack the source with:
```
dpkg-source -x mplayerplug-in_2.85-1.dsc
```

This will unpack mplayerplug-in_2.85.orig.tar.gz to mplayerplug-in-2.85.

Now change into the newly created mplayerplug-in-2.85 directory and edit the file debian/rules:
```
gedit debian/rules
```

Change the line:
DEB_CONFIGURE_EXTRA_FLAGS := --enable-x

to 

DEB_CONFIGURE_EXTRA_FLAGS := --enable-gtk2

and save the file.

Finally we are ready to start to build the package with:
```
dpkg-buildpackage -rfakeroot -uc -us
```

**4. Install the package** 
If everything went well you now should have a package called mozilla-mplayer_2.85-1_i386.deb in the parent directory of your current directory, that is in ../mplayerplug-in-2.85.
Change to that directory (cd ..) and install the package with:
sudo dpkg -i mozilla-mplayer_2.85-1_i386.deb

That's it.
All that's left to do is to edit /etc/mplayerplug-in.conf the way drigloi describes it and you should be good to go.

Have fun!

---

### Post by sanji on 2005-06-27
Thanks aja laa :-?

---

### Post by crashtest on 2005-06-27
This works perfectly for me with Mozilla 1.7.8.  Firefox 1.02 still crashes if I try to use the mplayer plugin however.  Is there a way to make this work with Firefox - or should it already be working at this point?  Thanks.

---

### Post by Knome_fan on 2005-06-28
I know this doesn't really help, but for what it's worth, I also did have problems with mplayerplug-in and firefox in ubuntu, no matter what version of the plugin I'm using. It works fine with epiphany for me though.

---

### Post by frodon on 2005-06-28
[QUOTE=Knome_fan]I know this doesn't really help, but for what it's worth, I also did have problems with mplayerplug-in and firefox in ubuntu, no matter what version of the plugin I'm using. It works fine with epiphany for me though.[/QUOTE]

I think I will use mozilla because i test a lot of plugin with firefox (VLC, gxine, totem, ...) and for the moment best  plugin is mplayer-plugin and it still not work with firefox .
I'm waiting for the official totem plugin or mplayer compatibility with firefox.
Thanks for this very good HOW TO. :)

---

### Post by Grunt on 2005-06-28
Great HOWTO, thanks! I now have very nice streaming video!

---

### Post by drigloi on 2005-06-28
[QUOTE=crashtest]This works perfectly for me with Mozilla 1.7.8.  Firefox 1.02 still crashes if I try to use the mplayer plugin however.  Is there a way to make this work with Firefox - or should it already be working at this point?  Thanks.[/QUOTE]

Can you describe me this Firefox crash problem? I use Backport's new 1.0.4 Firefox and haven't experienced any crashes with mplayerplug-in yet.

But it's true that previously I experienced lockups with mplayerplug-in 2.80 and Firefox 1.0.2 while watching streaming video and pressing the browser's Back button. Is this the issue you're referring to?

---

### Post by crashtest on 2005-06-28
[QUOTE=drigloi]Can you describe me this Firefox crash problem? I use Backport's new 1.0.4 Firefox and haven't experienced any crashes with mplayerplug-in yet.

But it's true that previously I experienced lockups with mplayerplug-in 2.80 and Firefox 1.0.2 while watching streaming video and pressing the browser's Back button. Is this the issue you're referring to?[/QUOTE]

I have since upgraded to the 1.0.4 version, but when I had Firefox 1.0.2 running it would just close if I tired to use the mplayerplug-in.  Even with Mozilla 1.7.8 the behavior is a little odd - videos will play, but if I click the 'x' to close mplayer, mozilla will instantly close.

Now here's another odd thing:  I've tried the mplayerplug-in to watch the news videos on CNN.com.  Mozilla let's me play the videos, but Firefox 1.0.4 pops up "Plugin Warning" telling me I need to install Windows Media Player 9.  So at this point I need a site to test Firefox 1.0.4 with the mplayerplug-in.  Any suggestions for a site to try?

I wonder how Mozilla beats the Microsoft Censorship and lets me play the CNN videos?  Maybe it's just how the browser identifies itself.  I'll have to take a look at this.

---

### Post by drigloi on 2005-06-28
> Now here's another odd thing:  I've tried the mplayerplug-in to watch the news videos on CNN.com.  Mozilla let's me play the videos, but Firefox 1.0.4 pops up "Plugin Warning" telling me I need to install Windows Media Player 9.  So at this point I need a site to test Firefox 1.0.4 with the mplayerplug-in.  Any suggestions for a site to try?


I bet after clearing cookies from Mozilla you'll get the same Plugin Warning. I think we should play mplayerplug-in.conf's user-agent variable. I tried but no solutions yet. I couldn't find what user-agent string WMP9 sends...

Some places to test mplayerplug-in:
[http://www.apple.com/trailers/](http://www.apple.com/trailers/)
[http://mediagong.com](http://mediagong.com)
[http://www.masters.org/en_US/interactive/tv/index.html](http://www.masters.org/en_US/interactive/tv/index.html)

---

### Post by Grunt on 2005-06-28
I just have two more questions:

What do you mean with " you should remove the old mozilla-mplayer package prior this step!" (which is step 8 ).

Btw. I have Mozilla Firefox installed. When I perform these steps I also get the other Mozilla browser. Is there a way to perform the installation without installing the Mozilla browser?

---

### Post by drigloi on 2005-06-29
[QUOTE=Grunt]I just have two more questions:

What do you mean with " you should remove the old mozilla-mplayer package prior this step!" (which is step 8 ).[/QUOTE]

mplayerplug-in is already available for Ubuntu from one of the repos as mozilla-mplayer. You should apt-get remove the official - rather aged 2.70 - package instead of overwriting its files. You can do this only if you have installed this package in the past of course.

I think you need to apt-get install the mozilla-dev package only, not mozilla-browser. But if you apt-getted mozilla you can safely remove it after the build process.

---

### Post by Grunt on 2005-06-29
Hi, thanks for the tip! 

For some reason though, the mozilla web browser als get's installed when I only install the mozilla-dev package. 

I'll just manually uninstall it.

---

### Post by Grunt on 2005-06-29
I'm back with two more questions! :)

If I try to uninstall the mozilla brower files it will also try to uninstall the mozilla dev files. Is that a problem, or aren't they going to be needed anymore?

Would it be bad to increase the cache size? Would that aid video performance?

Thanks again!

---

### Post by drigloi on 2005-06-29
I think mozilla-dev is required only during the compilation. You should be able to remove it safely.

Optimal cachesize depends on your internet connection type. More cachesize will result in more downloading of the media before it starts playing - so it will run out of bandwith later on slower connections.

---

### Post by Grunt on 2005-06-29
I see, thanks for the information!

---

### Post by Rob2687 on 2005-06-30
I have the backports setup in the sources.list, I don't see any mplayer things in synaptic...
Can someone paste their backports links from the sources.list file? I wanna make sure I got it right.

---

### Post by Grunt on 2005-06-30
Look here:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

"How to add extra repositories?"

---

### Post by DarkManX4lf on 2005-06-30
yea so i installed the the plugins both ways like both how-to's say in this thread but neither one works when i use Mozilla 1.78 it just says i need to download plugins, wheni use firefox it plays audio from the video but no video....someone help me out please?

---

### Post by Knome_fan on 2005-07-01
@DarkManX4lf:

Did you install the w32codecs?
And what sites are giving you problems?

---

### Post by Grunt on 2005-07-01
By the way, what would be the correct way to uninstall the program if you no longer require it?

---

### Post by drigloi on 2005-07-01
[QUOTE=Grunt]By the way, what would be the correct way to uninstall the program if you no longer require it?[/QUOTE]

sudo rm /usr/lib/mozilla-firefox/plugins/mplayerplug-in.so
sudo rm /usr/lib/mozilla-firefox/components/mplayerplug-in.xpt
sudo rm /etc/mplayerplug-in.conf
sudo rm /etc/mplayerplug-in.types

---

### Post by i3dmaster on 2005-07-01
wonderful, thanks for sharing! Love it!

---

### Post by Grunt on 2005-07-01
Merci!

---

### Post by Mr. Electric Wizard on 2005-07-01
Ok dudes, what am I doing wrong?

```
eric@ubuntu:~/mplayerplug-in$ ./configure --with-gecko-sdk=../gecko-sdk
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

---

### Post by Grunt on 2005-07-01
I had the same problem (it's answered earlier on in the thread). You have to install "build-essential" and after that you might have to install "libgtk2.0-dev".

---

### Post by Mr. Electric Wizard on 2005-07-01
Ahh, I figured it was somthing like that... Thanks, I thought I read the whole thread carefully?

---

### Post by Mr. Electric Wizard on 2005-07-01
Fabulous!!!
You Guys Rock!!!
 :)  :)  :)

---

### Post by ghostintheshell on 2005-07-13
Could you share the final deb file?

So we (everyone) don't have to compile all that stuff every time!

dkpg -i thepackage.deb shall be cool :)

Thank you!

---

### Post by ghostintheshell on 2005-07-14
Ok, thank you guy.

I compiled all from scratch and all is ok (with FireFox 1.0.5 too, the version I use).

Some minor problems but not serious (sometimes I have to click twice on the fullscreen button to restore the display).

I think that it is trick like this that makes Linux more and more fabulous, user friendly, a day-to-day usable os.

I think too that the backport team has to consider to propose this update because it is a must-have for browsing the web :)

Thank you again for this nice how-to.

---

### Post by gammyhand on 2005-07-16
[QUOTE=ghostintheshell]Ok, thank you guy.

I compiled all from scratch and all is ok (with FireFox 1.0.5 too, the version I use).

Some minor problems but not serious (sometimes I have to click twice on the fullscreen button to restore the display).

I think that it is trick like this that makes Linux more and more fabulous, user friendly, a day-to-day usable os.

I think too that the backport team has to consider to propose this update because it is a must-have for browsing the web :)

Thank you again for this nice how-to.[/QUOTE]
 I can't download the required stuff:

sudo apt-get install mozilla-dev libxpm-dev

as the connection times out. great.

---

### Post by ghostintheshell on 2005-07-16
[QUOTE=gammyhand]I can't download the required stuff:

sudo apt-get install mozilla-dev libxpm-dev

as the connection times out. great.[/QUOTE]

Hi

try  anothers repositeries (mirrors) in the */etc/apt/sources.list* file ([color=Indigo]sudo gedit /etc/apt/sources.list[/color])
then, [color=Indigo]sudo apt-get update[/color]
and  finally [color=Indigo]sudo apt-get install mozilla-dev libxpm-dev[/color]

Then give us feedback!

---

### Post by gammyhand on 2005-07-16
[QUOTE=ghostintheshell]Hi

try  anothers repositeries (mirrors) in the */etc/apt/sources.list* file ([color=Indigo]sudo gedit /etc/apt/sources.list[/color])
then, [color=Indigo]sudo apt-get update[/color]
and  finally [color=Indigo]sudo apt-get install mozilla-dev libxpm-dev[/color]

Then give us feedback![/QUOTE]
 How do I change repositories? I added all the extra repositories from ubuntuguide so I don't know what else to add.

---

### Post by ghostintheshell on 2005-07-16
Here's mine; give its a try (make a backup of your *sources.list* before):

To backup: [color=Indigo]sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup[/color]

To edit: [color=Indigo]sudo gedit /etc/apt/sources.list
[/color]
 ```
## Ubuntu officialy supported (Restricted copyright) ##

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://fr.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary main restricted

deb http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

## Kubuntu (KDE) ##

#deb http://kubuntu.org/ hoary-updates main
#deb http://kubuntu.org/hoary-kde341/ hoary-updates main

## Ubuntu community maintained (Universe) ##

deb http://fr.archive.ubuntu.com/ubuntu hoary universe
deb-src http://fr.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Ubuntu non-free (Multiverse) ##

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports ##

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

To update: [color=Indigo]sudo apt-get update[/color]

---

### Post by gammyhand on 2005-07-21
Got it working fine now :D

---

### Post by ghostintheshell on 2005-07-21
[QUOTE=gammyhand]Got it working fine now :D[/QUOTE]

[img]http://perso.wanadoo.fr/atil/forum/super2.gif[/img]

---

### Post by oddabe19 on 2005-07-23
I dont know if anyone else has this problem, but I don't have any controls. I can't stop, play or pause. Everything else shows but that.

If i remember right, I had them back in like version .65 or something.

---

### Post by vectorian798 on 2005-08-01
I still get a crash on Mozilla and Firefox when I hit the back button, even though I went through all that stuff and it seems to be working fine (that is, I have 2.85 installed for the plugin).

Anyways, I also have no sound in the quicktime videos (I used [http://www.apple.com/trailers](http://www.apple.com/trailers) as a test), but videos at CNN ([http://www.cnn.com](http://www.cnn.com)) work fine, with sound (those videos are not quicktime format, but WMV I think).

Someone please let me know if you know how to stop browser crash. Thanks in advance  :smile:

---

### Post by christooss on 2005-08-15
When will Howto for nev mplayer plug-in 3.05 be posted ? :)

---

### Post by ghostintheshell on 2005-08-15
[QUOTE=christooss]When will Howto for nev mplayer plug-in 3.05 be posted ? :)[/QUOTE]

I followed the same instructions and it works :D

Also, I copied all *mplayerplug-in*.so* and *mplayerplug-in*.xpt* files in the /firefox/plugins directory and I have more managed formats by the mplayerplug-in !
-> Google VLC multimedia plugin 1.0
-> QuickTime Plug-in 6.0 (mov, ...)
-> RealPlayer 9 (rm, ...)
-> Windows Media Player Plugin (wma, wmv, ...)
-> Standard formats (mpg, mp3, ogg, ...)

Enjoy.

---

### Post by twowheeler on 2005-08-17
Very good addition.  The 3.05 version works great.

---

### Post by christooss on 2005-08-17
[QUOTE=twowheeler]Very good addition.  The 3.05 version works great.[/QUOTE]
 SO all I have to do is change this line

[http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-2.85.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-2.85.tar.gz)

in to

[http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.05.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.05.tar.gz)

Is this working with Firefox. BTW I have comands like play stop and fastforward in 2.70 wierd

---

### Post by ghostintheshell on 2005-08-17
[QUOTE=christooss]SO all I have to do is change this line

[http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-2.85.tar.gz]("http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-2.85.tar.gz")

in to

[http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.05.tar.gz]("http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.05.tar.gz")

Is this working with Firefox. BTW I have comands like play stop and fastforward in 2.70 wierd[/QUOTE]

*my* answer is: yes at all!

_*remarks:*_

[step 1] -> you don't have to reinstall mplayer and the codecs (already done ;))
[step 5 & 6] -> the actual version of mozilla is 1.7.10 now and not 1.7.8 -> gecko-sdk = [http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.10/gecko-sdk-i686-pc-linux-gnu-1.7.10.tar.gz]("http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.10/gecko-sdk-i686-pc-linux-gnu-1.7.10.tar.gz") (replace "1.7.8" by "1.7.10")
[step 8] you _can_ copy _all_ *mplayerplug-in*.so* and *mplayerplug-in*.xpt* files in the */firefox/plugins* directory (see my post #41), not only *mplayerplug-in.so* and *mplayerplug-in.xpt*  

cheers, great work!

---

### Post by christooss on 2005-08-17
Thanks for now I will try it and than report you guys how it went.

Bye

---

### Post by Grunt on 2005-08-19
> **ghostintheshell]*my* answer is: yes at all!

_*remarks:*_

[step 1] -> you don't have to reinstall mplayer and the codecs (already done  said:**
>  -> the actual version of mozilla is 1.7.10 now and not 1.7.8 -> gecko-sdk = [http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.10/gecko-sdk-i686-pc-linux-gnu-1.7.10.tar.gz]("http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.10/gecko-sdk-i686-pc-linux-gnu-1.7.10.tar.gz") (replace "1.7.8" by "1.7.10")
[step 8] you _can_ copy _all_ *mplayerplug-in*.so* and *mplayerplug-in*.xpt* files in the */firefox/plugins* directory (see my post #41), not only *mplayerplug-in.so* and *mplayerplug-in.xpt*  

cheers, great work!

Well, I've tried everything you said with the new versions but I'm afraid the plugin doesn't work. It doesn't recognize the plugin. I did everything from scratch because I had to reinstall my Ubuntu system, so it can't be conflict of versions.  ](*,)

---

### Post by Icaros on 2005-08-19
I followed the initial tutorial on page 1 of this thread and got streaming video to work... BUT it flickers or parts of the video disapear.  By moving the vertical scrollbars up and down a bit, I can get more stable video... but it's fairly anoying to do this.

Any fixes for this problem?  Might happen because I'm using an nvidia card?

---

### Post by ghostintheshell on 2005-08-19
[QUOTE=Grunt]Well, I've tried everything you said with the new versions but I'm afraid the plugin doesn't work. It doesn't recognize the plugin. I did everything from scratch because I had to reinstall my Ubuntu system, so it can't be conflict of versions. ](*,)[/QUOTE]

more infos?

error message?

...?

did you install mplayer + codecs? does it work?

what do you see when you type:

 ```
about:plugins
``` 

in the url bar of Firefox?

which files are in your /firefox/plugins directory?

"the plugin doesn't work" > well, it does ...

---

### Post by ghostintheshell on 2005-08-19
[QUOTE=Icaros]I followed the initial tutorial on page 1 of this thread and got streaming video to work... BUT it flickers or parts of the video disapear. By moving the vertical scrollbars up and down a bit, I can get more stable video... but it's fairly anoying to do this.

Any fixes for this problem?  Might happen because I'm using an nvidia card?[/QUOTE]

Sorry, you're in the wrong place.
Report it directly to the mplayerplug-in team here: [http://mplayerplug-in.sourceforge.net/]("http://mplayerplug-in.sourceforge.net/")
Thank you for all of people who [will] have the same problem.

---

### Post by Grunt on 2005-08-19
[QUOTE=ghostintheshell]more infos?

error message?

...?

did you install mplayer + codecs? does it work?

what do you see when you type:

 ```
about:plugins
``` 

in the url bar of Firefox?

which files are in your /firefox/plugins directory?

"the plugin doesn't work" > well, it does ...[/QUOTE]

Well that's the problem, I don't get any error messages. When I type about:plugins I get the following:

> mplayerplug-in 3.05

    File name: mplayerplug-in.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes

My browser (Firefox) just says I need the right software in order to play the media files. I also have the mplayer and w32codecs installed. 

Firefox plugins:
/usr/lib/mozilla-firefox/plugins -> mplayerplug-in.so

I completed every step the same way as I did with the 2.85 tutorial with the exception of the file versions.

---

### Post by floppy on 2005-08-19
Hey, I'm an idiot newbie. Can someone recap all this into just one new how-to? 

Frankly, I get confused by all the old versions and corrections in this thread. ](*,) 

All I want is to get Firefox and Mplayer working happily together.

Thank you! :grin:

---

### Post by ghostintheshell on 2005-08-20
[QUOTE=Grunt]My browser (Firefox) just says I need the right software in order to play the media files. I also have the mplayer and w32codecs installed. 
 
 Firefox plugins:
 /usr/lib/mozilla-firefox/plugins -> mplayerplug-in.so
 
 I completed every step the same way as I did with the 2.85 tutorial with the exception of the file versions.[/QUOTE]

The tutorial for the 2.85 is for ... the 2.85.

Now, we're talking about the 3.05.

So, if you read my posts (#41 & #44), you can see:

 [QUOTE=Me]
 [step 8] Copy [size=4]_**all**_[/size] *mplayerplug-in[size=2]*****[/size].so* and *mplayerplug-in[size=2]*****[/size].xpt* files in the */firefox/plugins* directory (not only *mplayerplug-in.so* and *mplayerplug-in.xpt*) to have more managed formats by the mplayerplug-in:
-> Standard formats (mpg, mp3, ogg, ...)
But also:
 -> Google VLC multimedia plugin 1.0
-> QuickTime Plug-in 6.0 (mov, ...)
-> RealPlayer 9 (rm, ...)
-> Windows Media Player Plugin (wma, wmv, ...)
[/QUOTE]

Can't help you more than that ...

Cheers.

---

### Post by Grunt on 2005-08-20
Thanks for the info mate, I read too hastily over some of your posts. I'm going to give it another go.

Cheers!

---

### Post by Grunt on 2005-08-20
Oke, now it recognizes the plug-in, but I have no video output.  ](*,)

---

### Post by Grunt on 2005-08-20
It just says: Playing "URL", but it doesn't show anything.

---

### Post by ghostintheshell on 2005-08-20
[QUOTE=Grunt]It just says: Playing "URL", but it doesn't show anything.[/QUOTE]

try another web sites.

for examples:
- [http://www.apple.com/trailers/](http://www.apple.com/trailers/)
- [http://www.compfused.com/](http://www.compfused.com/)
- ...

does it work?

---

### Post by Grunt on 2005-08-21
I'm afraid not. I've tried all sorts of video formats but they all show the same thing. It's very weird. I think I'm going to reinstall 2.85 again.

I did use "aptitude install" instead of "apt-get install", but I don't think that has anything to do with it.

---

### Post by ghostintheshell on 2005-08-21
[QUOTE=Grunt]I'm afraid not. I've tried all sorts of video formats but they all show the same thing. It's very weird. I think I'm going to reinstall 2.85 again.

I did use "aptitude install" instead of "apt-get install", but I don't think that has anything to do with it.[/QUOTE]

Sorry.

Perhaps you'ld have more help about this issue on the mplayerplug-in web site?

All what I can say is that it works for me ...

So, the 2.85 will do the job too :)

---

### Post by imdeemvp on 2005-08-22
I was about to start about ubuntu but this how-to pretty much took care of my needs.  Thanks to poster.

---

### Post by makisupa123 on 2005-08-22
I know this isn't the place to ask questions...but this is more of a fyi and "can you replicate this?" kinda post.

Installed 3.05 without issue and it works and looks (using gtk) alot better than the last time i had it installed --long ago when hoary was first released.  There is one interesting behavior though...if I have used mplayerplug-in and then click on a standard mpg or anything else I have firefox (1.0.6) set to open with gxine or totem the browser crashes.  Just closed all at once.  Can someone point me to debug mode where I can see what's happening here?  Is anyone else experiencing this?  

Thanks,

Mak

---

### Post by ghostintheshell on 2005-08-22
[QUOTE=imdeemvp]I was about to start about ubuntu but this how-to pretty much took care of my needs.  Thanks to poster.[/QUOTE]

you're welcome.
and you're free to do what you want with your life too, dude.

ciao!

---

### Post by makisupa123 on 2005-08-22
[QUOTE=makisupa123]I know this isn't the place to ask questions...but this is more of a fyi and "can you replicate this?" kinda post.

Installed 3.05 without issue and it works and looks (using gtk) alot better than the last time i had it installed --long ago when hoary was first released.  There is one interesting behavior though...if I have used mplayerplug-in and then click on a standard mpg or anything else I have firefox (1.0.6) set to open with gxine or totem the browser crashes.  Just closed all at once.  Can someone point me to debug mode where I can see what's happening here?  Is anyone else experiencing this?  

Thanks,

Mak[/QUOTE]

OK, running FF in terminal yields the following right before crapping out:

Warning: more than one line!
Warning: more than one line!
Segmentation fault

So, my best guess is that Mplayer is not releasing a segment of memory upon closing.  Does anyone have a way of confirming or denying this?  That first message is still making me scratch my head.

Thanks

/mak

---

### Post by sapo on 2005-08-22
thanx for the howto.. worked perfectly  :grin:

---

### Post by Tralobyte on 2005-08-22
[QUOTE=ghostintheshell]Also, I copied all *mplayerplug-in*.so* and *mplayerplug-in*.xpt* files...[/QUOTE]

Thanks. I missed the .xpt's and wound up with no sound! Now it all works great.

---

### Post by Tralobyte on 2005-08-22
recap for newbies.
(This post is partially adapted from the first thread post.)

1. Open up a terminal.
2. Follow [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) to add extra repositories.
3. Copy and paste the following into the terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mplayer w32codecs
sudo apt-get install mozilla-dev libxpm-dev libgtk2.0-dev
mkdir temp
```
4. Download [http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-3.05.tar.gz?download](http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-3.05.tar.gz?download) and save it in the temp folder we just made.
5. When it's done downloading, copy and paste the following into the terminal:
```
cd temp
tar xzvf mplayerplug-in-3.05.tar.gz
cd mplayerplug-in
./configure
make
sudo checkinstall -D

```
Press enter at each prompt until you get to "Enter a number to change any of them or press ENTER to continue:"
5.1 Type "3" without quotes. Press Enter.
5.2 Type "3.05" without quotes. Press Enter
5.3 Press Enter again.

6. Copy and paste the following into the terminal:
```

mkdir ~/.mozilla/plugins
cp mplayerplug*so ~/.mozilla/plugins/
cp mplayerplug*xpt ~/.mozilla/plugins/

```
7. Close the terminal.

Please reply with any problems so I can edit this post.

---

### Post by christooss on 2005-08-23
sudo apt-get build-essential

---

### Post by christooss on 2005-08-23
[QUOTE=christooss]sudo apt-get build-essential[/QUOTE]
 Can I after installation remove these files?

libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
libfreetype6-dev libgl1-mesa-dev libglib2.0-dev libglitz1-dev
libglu1-mesa-dev libgtk2.0-dev libice-dev libnspr-dev libpango1.0-dev
libpng12-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxext-dev
libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxpm-dev libxrandr-dev
libxrender-dev libxt-dev mesa-common-dev mozilla-browser mozilla-dev x-dev
x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
x11proto-xinerama-dev zlib1g-dev

---

### Post by christooss on 2005-08-23
matic@ubuntu:~/temp/mplayerplug-in$ sudo checkinstall -D
sudo: checkinstall: command not found
matic@ubuntu:~/temp/mplayerplug-in$

---

### Post by CHUCKYCHUCK on 2005-08-27
Hi ! I can't install mplayer plug-in, i get this error message :

chucky@vinhubuntu:~/mplayerplug-in$ ./configure --with-gecko-sdk=../gecko-sdk
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.


I made exactly what was written in th How-To  ( except that i took version 3.05 instead of 2.85 )
What should i do ??
Thx

---

### Post by christooss on 2005-08-28
[QUOTE=CHUCKYCHUCK]Hi ! I can't install mplayer plug-in, i get this error message :

chucky@vinhubuntu:~/mplayerplug-in$ ./configure --with-gecko-sdk=../gecko-sdk
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.


I made exactly what was written in th How-To  ( except that i took version 3.05 instead of 2.85 )
What should i do ??
Thx[/QUOTE]
 I think you have to install build-essential

and you have to install

checkinstall

---

### Post by christooss on 2005-08-28
New howto avalible at [This link](http://ubuntuforums.org/showthread.php?p=321861#post321861)

---

### Post by monkey89 on 2005-08-31
I made a few changes to the above instructions, and 3.05 works on breezy now, and these instructions are probably good for hoary too (and make things, IMO, a little cleaner)

1. Add the hoary-extras repository from backports.  This is where I got w32codecs.
2. sudo apt-get update
3. sudo apt-get install mplayer-586 (or 386 if you're on an older computer) w32codecs
4. sudo apt-get install firefox-dev libxpm-dev libgtk2.0-dev build-essential checkinstall

(as you can see, instead of using mozilla-dev and needing to install the whole huge mozilla web browser, this builds the plug in off of firefox, which should already be installed)

5. Download the 3.05 tar.gz as mentioned above, unpack it wherever, and enter the directory where it is unpacked.
6. To get it to use firefox instead of mozilla, do this: sed -i -e "s|mozilla-plugin|firefox-plugin|" configure (special thanks to the ebuild in gentoo's bugzilla for this idea)
7. ./configure
8. make
9. sudo checkinstall -D, do it like above where you only change the version number.
10. Then the package should be installed properly, I don't see a need to add anything to ~/.mozilla/plugins.

Hope this helps,
-Monkey

---

### Post by ghostintheshell on 2005-09-14
I just installed the 3.11 version as usual and it just works fine.

Cheers.

---

### Post by ssnkumar on 2005-10-20
Hi,

   I use Solaris OS and Firefox (1.0.7 ver) and Mozilla (1.7.12 ver).
   I use mplayer to play movie files and it works fine.

   Recently I heard about the mplayer-plugin and installed it (3.11 ver)
   After that, whenever I click on the movie file in the browser, the browser crahses!

   I followed the steps that have been given in HOWTO and still I have the problem.
   Anybody in this forum using Solaris and able to use the plugin without any problem?

   Please help me to solve this problem.

Regards,
Narendra

---

