---
title: "HOWTO: Ubuntu Multimedia"
date: 2004-10-10
forum: Outdated Tutorials &amp; Tips
---

### Post by disposable on 2004-10-10
** UPDATED **
 Per post: [http://ubuntuforums.org/showpost.php?p=7156&postcount=48](http://ubuntuforums.org/showpost.php?p=7156&postcount=48)
 
 // Ubuntu Multimedia HOWTO
 //
 // by Disposable
 //
 // [http://www.oldskoolphreak.com]("http://www.oldskoolphreak.com")
 
 
 Introduction
 ------------
 "Will Warty Warthog / Ubuntu include complete multimedia support?"
 
 Ubuntu Linux [1] is a Debian-based, desktop Linux distribution whose name
 means "humanity to others."  The philosophy behind this GNU/Linux
 distribution and the great selection of packages make you feel good that
 you're using it.  The lack of multimedia support, however, leaves your
 digital media desires unsated.
 
 "We're still working out some of the difficult legal / policy issues
 involved with multimedia support. Warty Warthog will include some
 multimedia support, we just need to find out what we can safely and freely
 do."
 
 This HOWTO details the installation and configuration of applications
 essential to your media enjoyment on Ubuntu.
 
 
 Update It
 ---------
 If you've installed Ubuntu, and you should have a fresh install for this
 HOWTO, then you're already familiar with its default use of sudo.  You'll
 be using sudo a lot.
 
 The first step towards an Ubuntu multimedia powerhouse is to make sure your
 box is up-to-date [2].
 
     $ sudo apt-get update
     $ sudo apt-get upgrade
     $ sudo apt-get dist-upgrade
 
 
 MPlayer
 -------
 It's time to grab all of the packages needed to install MPlayer.  MPlayer
 is the most versatile media player available for GNU/Linux - video, audio,
 X, no X - it very well may be the only player you'll need.  Let's start with
 gcc/g++ and other dependencies, and then grab the MPlayer source.
 
     $ sudo apt-get install manpages-dev
     $ sudo apt-get install autoconf
     $ sudo apt-get install automake
     $ sudo apt-get install libtool
     $ sudo apt-get install flex
     $ sudo apt-get install bison
     $ sudo apt-get install gcc-doc
     $ sudo apt-get install g++
     $ sudo apt-get install x-window-system-dev
     $ sudo apt-get install libgtk1.2-dev
     $ sudo apt-get install libpng-dev
 
 Have your Warty Warthog CD handy and accept any extra packages, e.g. the
 libtool install will also install gcc.  We'll use a US mirror for (most of)
 the MPlayer packages and assume you're working in your home directory.
 Download MPlayer, codecs, English fonts and the default blue skin.
 Internationalization and slick graphics are up to you.
 
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2")
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2")
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2")
     $ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2]("http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2")
 
 Using the README from mplayerhq.hu [3] as a baseline, install the codecs
 with the following commands.
 
     $ tar -xjf essential-20040922.tar.bz2
     $ sudo mkdir -p /usr/local/lib/codecs
     $ sudo cp essential-20040922/* /usr/local/lib/codecs/
 
 Time to compile MPlayer.  Issue these commands.
 
     $ tar -xjf MPlayer-1.0pre5.tar.bz2
     $ cd MPlayer-1.0pre5
     $ ./configure --enable-gui
     $ make
     $ sudo make install
 
 Now install the fonts and skin.
 
     $ cd
     $ tar -xjf font-arial-iso-8859-1.tar.bz2
     $ sudo cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
     $ tar -xjf Blue-1.4.tar.bz2
     $ sudo mkdir -p /usr/local/share/mplayer/Skin/default
     $ sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/
 
 Finally, copy over the included conf files.
 
     $ sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/
 
 Test your install by launching the graphical version of MPlayer.
 
     $ gmplayer
 
 QuickTime, WindowsMedia, MPEG, avi - you should be able to play just about
 anything.  Give yourself quick access to MPlayer by adding a launcher to
 the top GNOME panel.  Right click on the panel and click Add to Panel...
 Select Custom Application Launcher and click Add.  Use the following
 information and click OK.
 
     Name: MPlayer
     Command: /usr/local/bin/gmplayer
     Icon: /usr/local/share/mplayer/Skin/default/icons/32x32.png
 
 
 Playing DVDs
 ------------
 The Ubuntu Wiki discusses restricted formats [4], which include CSS and
 DVD playback.  To add DVD playback capability to Ubuntu, use your favorite
 text editor and add the following line to your /etc/apt/sources.list file.
 
     deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") unstable main
 
 Then sync your package index and grab the infamous DeCSS.
 
     $ sudo apt-get update
     $ sudo apt-get install libdvdcss2
 
 Add a dvd link and enjoy DVDs with MPlayer and Ubuntu.
 
     $ sudo ln -s /media/cdrom0 /dev/dvd
 
 
 XMMS
 ----
 With your video needs taken care of, we can move on the audio portion of
 our show by installing XMMS.
 
     $ sudo apt-get install libmikmod2
     $ sudo apt-get install xmms
 
 Logging out and logging back in will find XMMS already in the Applications/
 Multimedia menu.  And there it is - instant Ogg/mp3/jukebox/streaming audio
 goodness.
 
 
 A Little Perl
 -------------
 For streaming internet radio, you can of course use XMMS.  Set your
 preference in Firefox and you're good to go.  I listen to a few stations
 regularly, and I always have a gnome-term open.  With those things in mind,
 I've found it much more convenient to write a Perl script that uses MPlayer
 to stream my favorite music.
 
     ```
#!/usr/bin/perl -w
 
 	# mplay.pl -
 	# command line streaming of your fav stations
 	# usage: mplay <channel>
 
 	use strict;
 
 	help() unless defined(my $chan = shift);
 
 	if ($chan =~ /bass/) {
 		system("mplayer http://us-dc1.streams.bassdrive.com:8012");
 	}
 	elsif ($chan =~ /cryo/) {
         	system("mplayer http://207.200.96.225:8022");
 	}
 	elsif ($chan =~ /di/) {
 		system("mplayer http://64.235.239.5:8006");
 	}
 	elsif ($chan =~ /ind/) {
 		system("mplayer http://130.240.207.88:9090");
 	}
 	elsif ($chan =~ /talk/) {
 		system("mplayer http://broadcast.rantradio.com:9010");
 	}
 	else { help(); }
 
 	sub help {
 
 	print <<EOF;
 
 	Usage: mplay <channel>
 
 	Channels:
 	bass - BassDrive
 	cryo - Cryosleep
 	di   - Digitally Imported
 	ind  - RantRadio Industrial
 	talk - RantRadio Talk
 
 	EOF
 
 	exit;
 	}
```
 
 "mplay ind" plays RantRadio's 128-bit industrial stream quickly and
 without a browser.  If you need your terminal, "q" stops the stream, do
 your deed, and up arrow gets the stream right back (or of course Ctrl+
 Shift+T for a new tab in gnome-terminal).
 
 
 Conclusion
 ----------
 Ubuntu Linux is an impressive distribution.  Even more impressive is the
 conviction of the developers.  "The most important thing about Ubuntu is
 not that it is available free of charge, but that it confers rights of
 software freedom on the people who install and use it."  They put their
 money where their apt is.  So as a GNU/Linux user, the tasks detailed
 above are trivial compared to the decisions made not to include such
 support.
 
 Please support free software developers.  Continue to use Ubuntu.
 Contribute to the Ubuntu Linux community.  And watch Batman: Dead End
 while you're doing it [5].
  
 
 References
 ----------
 [1] [http://www.ubuntulinux.org/]("http://www.ubuntulinux.org/")
 
 [2] I could not intuitively get Rhythmbox to play one simple Ogg file.  So
     my first step in setting up multimedia on Ubuntu is to sudo apt-get
     remove rhythmbox.
 
 [3] [http://www.mplayerhq.hu/DOCS/README]("http://www.mplayerhq.hu/DOCS/README")
 
 [4] [http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")
 
 [5] [http://www.theforce.net/theater/shortfilms/batman_deadend/]("http://www.theforce.net/theater/shortfilms/batman_deadend/")

---

### Post by eNiNjA on 2004-10-11
Very nice, thank you =)

---

### Post by metaPipe on 2004-10-11
alternatively, theres [ftp://ftp.nerim.net/debian-marillat/index.html](ftp://ftp.nerim.net/debian-marillat/index.html)

add this line to your apt sources list:
```
deb ftp&#58;//ftp.nerim.net/debian-marillat/ unstable main
```

then update apt sources and install some things like:

"gstreamer-mad" for mp3 playback in rhythmbox (yay!)

removing gstreamer-esd is also good if you are using alsa and have problems with sound skipping under system load.

theres also mplayer, xine, libcss2 and many more packages.

oh yes, and don't forget to install "w32codecs".  This will make just about any format media file play.

---

### Post by spoetnik on 2004-10-12
Thanks for this great HOWTO. Is there a way of installing mplayer as a plugin for firefox???

---

### Post by Julle on 2004-10-12
[quote=spoetnik]Thanks for this great HOWTO. Is there a way of installing mplayer as a plugin for firefox???[/quote]
You might want to try this.

[http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

Had it installed when I used Gentoo and it worked almost always.

----------
EDIT
----------

Just installed mplayerplug-in to my Ubuntu. Works like a charm. :)

---

### Post by spoetnik on 2004-10-14
I installed the plugin from source-forge but is doesn't work that good.
In 'about:plugin' it shows all the plug-ins, but firefox still ask's me what application to use.

---

### Post by wurtel on 2004-10-14
Is there a way to install mplayer without the terminal, from the synaptic package management? I ask this because I'm pretty new to linux and have no understanding of terminal commands. Since I don't understand any of it, I'm somewhat scared of it.

Also is it really necessary to install a new application? Can't there be any codecs installed for the totem video player?

---

### Post by Oolong on 2004-10-14
[quote=wurtel]Is there a way to install mplayer without the terminal, from the synaptic package management? I ask this because I'm pretty new to linux and have no understanding of terminal commands. Since I don't understand any of it, I'm somewhat scared of it.

Also is it really necessary to install a new application? Can't there be any codecs installed for the totem video player?[/quote]

You can try using mozplugger :

"Plugin allowing external viewers to be launched inside Mozilla
mozplugger allows you to seamlessly integrate external applications
to view files downloaded from the web that Mozilla can not normally
handle. The application is embedded within a Mozilla window as to act
like and feel like a true plugin.

This allows to you view PDFs, Postscript files, animations and
movies, amongst other file types all from within Mozilla (with
supporting applications)."


it is in ether universe or marillat.

---

### Post by Damon on 2004-10-16
Amazing stuff! Great write-up.. :-D

---

### Post by igster on 2004-10-19
Works great.  Thanks!

---

### Post by emperor on 2004-10-19
Mozplugger looks like an easy (no compiling) way to go. It's in the "universe" too, so you can install it using Synaptic!

---

### Post by emperor on 2004-10-20
I tried both mozplugger and the vlc plugin and neither gave me the seemless multimedia experience I wanted. For example, Media Player did not work! But ***after building and installing mplayerplug-in, everything works perfectly***, even Yahoo! Yahoo's multimeda search found all 3:  Quicktime, Media Player 9, and RealPlayer10.

So, it is worth your time to install the dependent packages, configure, make and install mplayerplug-in! I think even a newbie can do this, just give it a try!

Basicly all I have done below is fill in a few holes and adapted the information at the link below for the Ubuntu distro. The reference link is: [http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)

**How to buiild and install mplayeplug-in:**
=========================
1. Install the following using apt-get via xterm session **(sudo apt-get install *pkg*)**  or using Synaptic gui. I use the GUI when I can. I happen to like Synaptic! These packages should all be in Ubuntu's main respository.

[b]libgtk2.0-dev 
libgtk2.0-dbg[/b]   (may be optional!)

2. Download gecko-sdk: (for x86 on linux you want this one!)
[http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.6/gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.6/gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz)

3. Unpack gecko-sdk in your home "work" directory, I use "~/download"
**tar -xzvf gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz**

4. Now download the mplayer-plugin from here:
[http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-2.70.tar.gz?download](http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-2.70.tar.gz?download)

5. Unpack the source for mplayerplug-in in your "home" work directory:
**tar -xzvf mplayerplug-in-2.70.tar.gz**

6. Change to your mplayerplug-in directory, for example:
**cd mplayerplug-in    (in my case, this is: "~/download/mplayerplug-in"**
 
7. Execute "configure" with the following commandline option: (substitute  your user account name in "username" )
**./configure --with-gecko-sdk=/home/"username"/download/gecko-sdk**

8. Next compile and link together the mplayerplug-in by running make with "no" options!
**make**

9. Finally, install the component and plugin:
[b]For mozilla:
sudo cp mplayerplug-in.so /usr/lib/mozilla/plugins
sudo cp mplayerplug-in.xpt /usr/lib/mozilla/components

For firefox:
sudo cp mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in.xpt /usr/lib/mozilla-firefox/components[/b]

**Notes:**(a) I also found I had to **set Mplayer's Video driver to X11** (Preferences - Video - X11)  or Firefox/Mizilla would crash after playing a movie.

---

### Post by Julle on 2004-10-21
Just little correction. You need EITHER mozilla-dev OR gecko-sdk not both of them. So you can skip phase one of emperors instructions. And naturally you can delete the gecko-sdk and mplayerplug-in folders once you have succesfully installed the plug-in.

Then one question. Does the plug-in work correctly with you ppl? After the first test that I did I notised that for some reason there isn't any controls in my mplayerplug-in. So I can't pause the video or move it backwards or forwards. Any ideas?

---

### Post by emperor on 2004-10-21
Removed "mozilla-dev" from instructions. Thanks Julie!

---

### Post by emperor on 2004-10-21
Removed "mozilla-dev" from instructions. Thanks Julie!

---

### Post by Julle on 2004-10-21
It seems that libgtk2.0-dev was the thing I was missing. Or libgtk2.0-dbg don't know because I didn't take any changes.

My turn to say thanks.  :)

---

### Post by Perfect Storm on 2004-10-21
Works perfect, emperor!

---

### Post by natefish on 2004-10-21
Didn't need the libgtk2.0-dbg package, used gecko-sdk, and didn't need to set preferences for X11 on my set up. Seems to be working perfect. Much better user experience then the mozplugger. 

Thanks for the great directions.

---

### Post by chapterthree on 2004-10-22
Thanks for this guide!

As far as the mplayer install, the following wget isn't working, it's giving me "failed: Connection timed out"
```
 $ wget http&#58;//ftp3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5.tar.bz2
```

Are there updated links for this?

---

### Post by Rancoras on 2004-10-22
I had the same thing, it appears that their "ftp3" server may be down.  Just go to the mplayer web site and try another mirror.

[http://www.mplayerhq.hu/homepage/design7/news.html](http://www.mplayerhq.hu/homepage/design7/news.html)

---

### Post by gamehack on 2004-10-23
Hello all,

after adding the marillat repository and trying to install mplayer it gave me this:
```

The following packages have unmet dependencies:
  mplayer-586: Depends: libartsc0 (>= 1.3.0) but it is not going to be installed               Depends: libggi2 (>= 1:2.0.5) but it is not going to be installed               Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is to be installed
E: Broken packages

```

I think it's a big mistake for Ubuntu not to include mplayer in their repository. Come on, that's the best player for Linux and it's even in the repository... I like ubuntu very much but this annoys me. If there's some special package for Ubuntu for mplayer, can someone give me some links. Or some other way of installing it, but not by source. I hate whis brute force installing, although I can do it, it's not the preferred way.

Thanks

---

### Post by aledin on 2004-10-23
[QUOTE=gamehack]
I think it's a big mistake for Ubuntu not to include mplayer in their repository. Come on, that's the best player for Linux and it's even in the repository... I like ubuntu very much but this annoys me. If there's some special package for Ubuntu for mplayer, can someone give me some links. Or some other way of installing it, but not by source. I hate whis brute force installing, although I can do it, it's not the preferred way.
Thanks[/QUOTE]

mplayer package (mplayer-custom) is in the multiverse repository of Ubuntu.

---

### Post by j_baer on 2004-10-23
I'm struggling with the Firefox Quicktime. I installed MPlayer as outlined and tested. If I hit a movie trailer page the link is still looking for the Quicktime plugin.

I installed mozplugger but I have no idea how to use it.

Any help is appreciated ....

---

### Post by lean on 2004-10-23
I get this when trying to use marillat (unstable main)

apt-get install mplayer-586
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-586: Depends: libartsc0 (>= 1.3.0) but 1.2.3-1 is to be installed
               Depends: libggi2 (>= 1:2.0.5) but it is not going to be installed
               Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is to be installed

---

### Post by j_baer on 2004-10-23
All,

The HOWTO worked great. I did not do the mozillia plug but the web pages work fine  through the file association process.

Linux really needs a media program like MPlayer and this should be included as part of the base install if at all possible.

Good job everyone ...

---

### Post by Juneau on 2004-10-24
Thanks to everyone for that guide! Finally got my favourite media player on Ubuntu!

---

### Post by leeech on 2004-10-24
aren't there any ready made .deb file for mplayer and mplayer-plugin

going through all those compiling is not fun...  [-( 

reason, if i were to implement to my clients... i can't be going to all their PCs compiling 1 by 1...

---

### Post by silverkhan on 2004-10-25
[QUOTE=metaPipe]alternatively, theres [ftp://ftp.nerim.net/debian-marillat/index.html](ftp://ftp.nerim.net/debian-marillat/index.html)

add this line to your apt sources list:
```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

then update apt sources and install some things like:

"gstreamer-mad" for mp3 playback in rhythmbox (yay!)

removing gstreamer-esd is also good if you are using alsa and have problems with sound skipping under system load.

theres also mplayer, xine, libcss2 and many more packages.

oh yes, and don't forget to install "w32codecs".  This will make just about any format media file play.[/QUOTE]

I've added deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main (i did it through synaptic), but i can't seem to "gstreamer-mad". Is there any alternativ server i can use to download "gstreamer-mad"?

---

### Post by uggeli on 2004-10-25
Sorry for maybe stupid guestions, but I'm newbie so..

If mplayer-custom is in the multiverse repository of Ubuntu so what does that custom version contains (how it's costomized) and should I still do rest of steps which are on 1st message of this thread or are they ready in that customized version?

Ps. I haven't installed ubuntu yet (haven't receive CDs I ordered yet..) but just wanted to ask this allready so I can start install mplayer immediately I got ubuntu installed.

Thanks for possible answers. :)

Edit: some typos

---

### Post by gamehack on 2004-10-25
@uggeli

Yes, you can after adding the multiverse repository. But there's a slight problem... it will  only install the console version :(

Cheers,
gamehack

---

### Post by uggeli on 2004-10-25
@gamehack

Hmm I can do rest of steps mentioned in 1st post after installing mplayer from multiverse  if I got it right from you message, but do I have to do those steps or are those allready "built-in" in that "custom(ized)" version of mplayer? That word "custom" misleads me.  So is that "custom" version still normal (expect no gui :( ) mplayer?

Well maybe it's afterall easiest to just ask that does things still go like in 1st post in this thread or do I have to get mplayer (with gui) from somewhere else or what? I understood that there was some problems getting mplayer from those sources which are mentioned in 1st post, or did I misunderstood something? Howabout those other stuff (codecs etc.)?

Sorry for asking again these but as newbie I littlebit scare to try unless I'm 100% sure that things are still going the way I try to. Well I promise not to ask anymore until I got my ubuntu cd and got it installed. :)

---

### Post by j_baer on 2004-10-25
Having trouble compiling mplayerplug-in

My are my steps ...

1) apt-get libgtk2.0-dev & libgtk2.0-dbg (may be optional!) - ok

2) download gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz to ~/"username"/download - ok

3) unpacked gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz to ~/"username"/download - ok

    - this created a folder gecko-sdk in ~/"username"/download of source files
	
4) download mplayerplug-in-2.70.tar.gz to ~/"username"/download - ok

5) unpacked mplayerplug-in-2.70.tar.gz to ~/"username"/download - ok

    - this created a folder mplayerplug-in in ~/"username"/download of source files

6) changed to ~/"username"/download/mplayerplug-in directory - ok

7) configure ./configure --with-gecko-sdk=/home/"username"/download/gecko-sdk - ok

8) compile and link by "make" - failed

Questions:

Do any of the above commands need to be run as sudo?

Did the configure command really execute successfully?

Do I need to move the files from gecko-sdk to somewhere else?

Thanks ...

---

### Post by thorhr on 2004-10-26
> **disposable]Ubuntu Multimedia HOWTO


Introduction
------------------
"Will Warty Warthog / Ubuntu include complete multimedia support?"

Ubuntu Linux [1] is a Debian-based, desktop Linux distribution whose name
means "humanity to others."  The philosophy behind this GNU/Linux
distribution and the great selection of packages make you feel good that
you're using it.  The lack of multimedia support, however, leaves your
digital media desires unsated.

"We're still working out some of the difficult legal / policy issues
involved with multimedia support. Warty Warthog will include some
multimedia support, we just need to find out what we can safely and freely
do."

This HOWTO details the installation and configuration of applications
essential to your media enjoyment on Ubuntu.


Update It
--------------
If you've installed Ubuntu, and you should have a fresh install for this
HOWTO, then you're already familiar with its default use of sudo.  You'll
be using sudo a lot.

The first step towards an Ubuntu multimedia powerhouse is to make sure your
box is up-to-date [2].

	$ sudo apt-get update
	$ sudo apt-get upgrade
	$ sudo apt-get dist-upgrade


MPlayer
------------
It's time to grab all of the packages needed to install MPlayer.  MPlayer
is the most versatile media player available for GNU/Linux - video, audio,
X, no X - it very well may be the only player you'll need.  Let's start with
gcc/g++ and other dependencies, and then grab the MPlayer source.

	$ sudo apt-get install manpages-dev
	$ sudo apt-get install autoconf
	$ sudo apt-get install automake
	$ sudo apt-get install libtool
	$ sudo apt-get install flex
	$ sudo apt-get install bison
	$ sudo apt-get install gcc-doc
	$ sudo apt-get install g++
	$ sudo apt-get install x-window-system-dev
	$ sudo apt-get install libgtk1.2-dev
	$ sudo apt-get install libpng-dev

Have your Warty Warthog CD handy and accept any extra packages, e.g. the
libtool install will also install gcc.  We'll use a US mirror for the
MPlayer packages and assume you're working in your home directory.  Download
MPlayer, codecs, English fonts and the default blue skin.
Internationalization and slick graphics are up to you.

	$ wget [http://ftp3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5.tar.bz2)
	$ wget [http://ftp3.mplayerhq.hu/MPlayer/releases/codecs/essential-20040922.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/releases/codecs/essential-20040922.tar.bz2)
	$ wget [http://ftp3.mplayerhq.hu/MPlayer/releases/fonts/font-arial-iso-8859-1.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/releases/fonts/font-arial-iso-8859-1.tar.bz2)
	$ wget [http://ftp3.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)

Using the README from mplayerhq.hu [3] as a baseline, install the codecs
with the following commands.

	$ tar -xjf essential-20040922.tar.bz2
	$ sudo mkdir -p /usr/local/lib/codecs
	$ sudo cp essential-20040922/* /usr/local/lib/codecs/

Time to compile MPlayer.  Issue these commands.

	$ tar -xjf MPlayer-1.0pre5.tar.bz2
	$ cd MPlayer-1.0pre5
	$ ./configure --enable-gui
	$ make
	$ sudo make install

Now install the fonts and skin.

	$ cd
	$ tar -xjf font-arial-iso-8859-1.tar.bz2
	$ sudo cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
	$ tar -xjf Blue-1.4.tar.bz2
	$ sudo mkdir -p /usr/local/share/mplayer/Skin/default
	$ sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/

Finally, copy over the included conf files.

	$ sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/

Test your install by launching the graphical version of MPlayer.

	$ gmplayer

QuickTime, WindowsMedia, MPEG, avi - you should be able to play just about
anything.  Give yourself quick access to MPlayer by adding a launcher to
the top GNOME panel.  Right click on the panel and click Add to Panel...
Select Custom Application Launcher and click Add.  Use the following
information and click OK.

	Name: MPlayer
	Command: /usr/local/bin/gmplayer
	Icon: /usr/local/share/mplayer/Skin/default/icons/32x32.png


Playing DVDs
-------------------
The Ubuntu Wiki discusses restricted formats [4], which includes CSS and
DVD playback.  To add DVD playback capability to Ubuntu, use the Synaptics
Howto [5] to add [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) to your sources list
(unstable, main).  Then sync your package index.

	$ sudo apt-get update

Grab the infamous DeCSS.

	$ sudo apt-get install libdvdcss2

Add a dvd link and enjoy DVDs with MPlayer and Ubuntu.

	$ sudo ln -s /media/cdrom0 /dev/dvd


XMMS
---------
With your video needs taken care of, we can move on the audio portion of
our show by installing XMMS.

	$ sudo apt-get install libmikmod2
	$ sudo apt-get install xmms

Logging out and logging back in will find XMMS already in the Applications/
Multimedia menu.  And there it is - instant Ogg/mp3/jukebox/streaming audio
goodness.


A Little Perl
----------------
For streaming internet radio, you can of course use XMMS.  Set your
preference in Firefox and you're good to go.  I listen to a few stations
regularly, and I always have a gnome-term open.  With those things in mind,
I've found it much more convenient to write a Perl script that uses MPlayer
to stream my favorite music.
```
#!/usr/bin/perl -w

# mplay.pl -
# command line streaming of your fav stations
# usage&#58 said:**
> .
 

References
-----------------
[1] [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

[2] I could not intuitively get Rhythmbox to play one simple Ogg file.  So
    my first step in setting up multimedia on Ubuntu is to sudo apt-get
    remove rhythmbox.

[3] [http://www.mplayerhq.hu/DOCS/README](http://www.mplayerhq.hu/DOCS/README)

[4] [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

[5] [http://wiki.ubuntu.com/SynapticHowto](http://wiki.ubuntu.com/SynapticHowto)

[6] [http://www.theforce.net/theater/shortfilms/batman_deadend/](http://www.theforce.net/theater/shortfilms/batman_deadend/)
 These are the best instructions i have ever found on any web site. Thank you!They work!

---

### Post by senectus on 2004-10-26
I cant get down off that mirror.. is there somewhere else I can get the *.tar.bz2 files?

---

### Post by jayclark on 2004-10-26
Julle- I have the pause/play/stop buttons also the scaning bar to move forward or backwards.

---

### Post by emperor on 2004-10-26
[QUOTE=linuxbaer]Having trouble compiling mplayerplug-in

My are my steps ...

1) apt-get libgtk2.0-dev & libgtk2.0-dbg (may be optional!) - ok

2) download gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz to ~/"username"/download - ok

3) unpacked gecko-sdk-i686-pc-linux-gnu-1.6.tar.gz to ~/"username"/download - ok

    - this created a folder gecko-sdk in ~/"username"/download of source files
	
4) download mplayerplug-in-2.70.tar.gz to ~/"username"/download - ok

5) unpacked mplayerplug-in-2.70.tar.gz to ~/"username"/download - ok

    - this created a folder mplayerplug-in in ~/"username"/download of source files

6) changed to ~/"username"/download/mplayerplug-in directory - ok

7) configure ./configure --with-gecko-sdk=/home/"username"/download/gecko-sdk - ok

8) compile and link by "make" - failed

Questions:

Do any of the above commands need to be run as sudo?

Did the configure command really execute successfully?

Do I need to move the files from gecko-sdk to somewhere else?

Thanks ...[/QUOTE]

The notation "~" append's "/home/username" to the path. So "~/username/download" would become "/home/username/username/download".

Could this be your problem?

gecko-sdk does not need to be installed anywhere eles as it is just used to compile the plugin; .afterwards, you can delete it.

Use of Sudo is only required when you are copying the plugin to the final mozilla/firefox directory.

More error info would help!

BTW, "sudo -s" will create a root session in the terminal session. Use "exit" to go back to regular user. If there is a lot of "sudo-ing" going on I like to go to a root session.

---

### Post by dmatrix on 2004-10-26
Forget compiling this stuff, there is an easier way.

Make sure you have multiverse and universe in your /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted universe multiverse

Open a Terminal
sudo apt-get install mplayer-custom mozilla-mplayer
wget [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20040916-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20040916-0.0_i386.deb)
sudo dpkg -i w32codec*

Browse to [http://apple.com/trailers/](http://apple.com/trailers/)

Enjoy

---

### Post by oddabe19 on 2004-10-26
[QUOTE=dmatrix]Forget compiling this stuff, there is an easier way.

Make sure you have multiverse and universe in your /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted universe multiverse

Open a Terminal
sudo apt-get install mplayer-custom mozilla-mplayer
wget [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20040916-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20040916-0.0_i386.deb)
sudo dpkg -i w32codec*

Browse to [http://apple.com/trailers/](http://apple.com/trailers/)

Enjoy[/QUOTE]

Multiverse? What the HELL is multiverse? I was completely happy with just universe. :???:

---

### Post by jayclark on 2004-10-26
The mplayer custom has a problem. Dosen't want to work with all cpu's. It won't work on pentium 3's at all. At least thats what i'm told by a dev on the mailing list.

---

### Post by Rancoras on 2004-10-26
[QUOTE=oddabe19]Multiverse? What the HELL is multiverse? I was completely happy with just universe. :???:[/QUOTE]

Multiverse is non-free, unsupported packages

---

### Post by brschmid on 2004-10-26
i am having trouble with this part :
> Using the README from mplayerhq.hu [3] as a baseline, install the codecs
with the following commands.

$ tar -xjf essential-20040922.tar.bz2
$ sudo mkdir -p /usr/local/lib/codecs
$ sudo cp essential-20040922/* /usr/local/lib/codecs/


these are the errors, please help, i want to be able to listen to music and watch some movies. 
> me@craptop:/home $ tar -xjf essential-20040922.tar.bz2
tar: essential-20040922: Cannot mkdir: Permission denied
tar: essential-20040922/msms001.vwp: Cannot open: No such file or directory
tar: essential-20040922/ctadp32.acm: Cannot open: No such file or directory
tar: essential-20040922/mi-sc4.acm: Cannot open: No such file or directory
tar: essential-20040922/AvidQTAVUICodec.qtx: Cannot open: No such file or direct ory
tar: essential-20040922/BeHereiVideo.qtx: Cannot open: No such file or directory
tar: essential-20040922/CLRVIDDC.DLL: Cannot open: No such file or directory
tar: essential-20040922/CtWbJpg.DLL: Cannot open: No such file or directory
tar: essential-20040922/LCMW2.dll: Cannot open: No such file or directory
tar: essential-20040922/LCODCCMW2E.dll: Cannot open: No such file or directory
tar: essential-20040922/QuickTime.qts: Cannot open: No such file or directory
tar: essential-20040922/QuickTimeEssentials.qtx: Cannot open: No such file or di rectory
tar: essential-20040922/QuickTimeInternetExtras.qtx: Cannot open: No such file o r directory
tar: essential-20040922/ViVD2.dll: Cannot open: No such file or directory
tar: essential-20040922/acelpdec.ax: Cannot open: No such file or directory
tar: essential-20040922/alf2cd.acm: Cannot open: No such file or directory
tar: essential-20040922/aslcodec_dshow.dll: Cannot open: No such file or directo ry
tar: essential-20040922/atrac3.acm: Cannot open: No such file or directory
tar: essential-20040922/atrc.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/clrviddd.dll: Cannot open: No such file or directory
tar: essential-20040922/cook.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/drv3.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/drv4.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/dspr.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/iac25_32.ax: Cannot open: No such file or directory
tar: essential-20040922/icmw_32.dll: Cannot open: No such file or directory
tar: essential-20040922/imc32.acm: Cannot open: No such file or directory
tar: essential-20040922/ir41_32.dll: Cannot open: No such file or directory
tar: essential-20040922/ir50_32.dll: Cannot open: No such file or directory
tar: essential-20040922/ivvideo.dll: Cannot open: No such file or directory
tar: essential-20040922/jp2avi.dll: Cannot open: No such file or directory
tar: essential-20040922/lhacm.acm: Cannot open: No such file or directory
tar: essential-20040922/m3jp2k32.dll: Cannot open: No such file or directory
tar: essential-20040922/msh261.drv: Cannot open: No such file or directory
tar: essential-20040922/msscds32.ax: Cannot open: No such file or directory
tar: essential-20040922/nsrt2432.acm: Cannot open: No such file or directory
tar: essential-20040922/qpeg32.dll: Cannot open: No such file or directory
tar: essential-20040922/qtmlClient.dll: Cannot open: No such file or directory
tar: essential-20040922/rt32dcmp.dll: Cannot open: No such file or directory
tar: essential-20040922/sipr.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/tm20dec.ax: Cannot open: No such file or directory
tar: essential-20040922/tokf.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/tokr.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/tsccvid.dll: Cannot open: No such file or directory
tar: essential-20040922/tsd32.dll: Cannot open: No such file or directory
tar: essential-20040922/tssoft32.acm: Cannot open: No such file or directory
tar: essential-20040922/ultimo.dll: Cannot open: No such file or directory
tar: essential-20040922/vid_3ivX.xa: Cannot open: No such file or directory
tar: essential-20040922/vivog723.acm: Cannot open: No such file or directory
tar: essential-20040922/voxmsdec.ax: Cannot open: No such file or directory
tar: essential-20040922/vp4vfw.dll: Cannot open: No such file or directory
tar: essential-20040922/vp5vfw.dll: Cannot open: No such file or directory
tar: essential-20040922/vp6vfw.dll: Cannot open: No such file or directory
tar: essential-20040922/vssh264.dll: Cannot open: No such file or directory
tar: essential-20040922/vssh264core.dll: Cannot open: No such file or directory
tar: essential-20040922/vssh264dec.dll: Cannot open: No such file or directory
tar: essential-20040922/vsslight.dll: Cannot open: No such file or directory
tar: essential-20040922/vsswlt.dll: Cannot open: No such file or directory
tar: essential-20040922/wma9dmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmadmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmspdmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmv9dmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmvdmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wnvplay1.dll: Cannot open: No such file or directory
tar: essential-20040922/wnvwinx.dll: Cannot open: No such file or directory
tar: Error exit delayed from previous errors


---

### Post by j_baer on 2004-10-26
dMatrix,

Thanks, your script worked perfectly!

...

---

### Post by j_baer on 2004-10-26
Just curious,

Is there a plugin for windows media?

---

### Post by emperor on 2004-10-26
The mplayerplug-in will  handle this provided the windows codecs are installed from the mplayer "essential..." package mentioned earlier in this thread. Type the following in firefox's URL entry field to see what plugins are currently installed:  

"about:plugins"  <smiley is suppose to be a colon!>

---

### Post by BugsyMalone on 2004-10-26
I'm trying to get MPlayer set up to play DVD's. I added the marillat link to the sources list and when I run the sudo apt-get install libdvdcss2 command I get this error:

Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libdvdcss2: Depends: libdvdread2 (>= 0.9.2) but it is not installable
E: Broken packages

I don't have any idea what this means, does anybody have a translation?

---

### Post by BugsyMalone on 2004-10-26
Nevermind... I installed the unstable link and it installed. I did the sudo ln -s /media/cdrom0 /dev/dvd command and I can't get DVD's to play. AVI files play perfectly. I have a DVD/CDR drive, should I make a different entry?

---

### Post by brschmid on 2004-10-26
help!!! please

still getting errors on this part:
>  Using the README from mplayerhq.hu [3] as a baseline, install the codecs
with the following commands.

$ tar -xjf essential-20040922.tar.bz2
$ sudo mkdir -p /usr/local/lib/codecs
$ sudo cp essential-20040922/* /usr/local/lib/codecs/



>  me@craptop:/home $ tar -xjf essential-20040922.tar.bz2
tar: essential-20040922: Cannot mkdir: Permission denied
tar: essential-20040922/msms001.vwp: Cannot open: No such file or directory
tar: essential-20040922/ctadp32.acm: Cannot open: No such file or directory
tar: essential-20040922/mi-sc4.acm: Cannot open: No such file or directory
tar: essential-20040922/AvidQTAVUICodec.qtx: Cannot open: No such file or direct ory
tar: essential-20040922/BeHereiVideo.qtx: Cannot open: No such file or directory
tar: essential-20040922/CLRVIDDC.DLL: Cannot open: No such file or directory
tar: essential-20040922/CtWbJpg.DLL: Cannot open: No such file or directory
tar: essential-20040922/LCMW2.dll: Cannot open: No such file or directory
tar: essential-20040922/LCODCCMW2E.dll: Cannot open: No such file or directory
tar: essential-20040922/QuickTime.qts: Cannot open: No such file or directory
tar: essential-20040922/QuickTimeEssentials.qtx: Cannot open: No such file or di rectory
tar: essential-20040922/QuickTimeInternetExtras.qtx: Cannot open: No such file o r directory
tar: essential-20040922/ViVD2.dll: Cannot open: No such file or directory
tar: essential-20040922/acelpdec.ax: Cannot open: No such file or directory
tar: essential-20040922/alf2cd.acm: Cannot open: No such file or directory
tar: essential-20040922/aslcodec_dshow.dll: Cannot open: No such file or directo ry
tar: essential-20040922/atrac3.acm: Cannot open: No such file or directory
tar: essential-20040922/atrc.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/clrviddd.dll: Cannot open: No such file or directory
tar: essential-20040922/cook.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/drv3.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/drv4.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/dspr.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/iac25_32.ax: Cannot open: No such file or directory
tar: essential-20040922/icmw_32.dll: Cannot open: No such file or directory
tar: essential-20040922/imc32.acm: Cannot open: No such file or directory
tar: essential-20040922/ir41_32.dll: Cannot open: No such file or directory
tar: essential-20040922/ir50_32.dll: Cannot open: No such file or directory
tar: essential-20040922/ivvideo.dll: Cannot open: No such file or directory
tar: essential-20040922/jp2avi.dll: Cannot open: No such file or directory
tar: essential-20040922/lhacm.acm: Cannot open: No such file or directory
tar: essential-20040922/m3jp2k32.dll: Cannot open: No such file or directory
tar: essential-20040922/msh261.drv: Cannot open: No such file or directory
tar: essential-20040922/msscds32.ax: Cannot open: No such file or directory
tar: essential-20040922/nsrt2432.acm: Cannot open: No such file or directory
tar: essential-20040922/qpeg32.dll: Cannot open: No such file or directory
tar: essential-20040922/qtmlClient.dll: Cannot open: No such file or directory
tar: essential-20040922/rt32dcmp.dll: Cannot open: No such file or directory
tar: essential-20040922/sipr.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/tm20dec.ax: Cannot open: No such file or directory
tar: essential-20040922/tokf.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/tokr.so.6.0: Cannot open: No such file or directory
tar: essential-20040922/tsccvid.dll: Cannot open: No such file or directory
tar: essential-20040922/tsd32.dll: Cannot open: No such file or directory
tar: essential-20040922/tssoft32.acm: Cannot open: No such file or directory
tar: essential-20040922/ultimo.dll: Cannot open: No such file or directory
tar: essential-20040922/vid_3ivX.xa: Cannot open: No such file or directory
tar: essential-20040922/vivog723.acm: Cannot open: No such file or directory
tar: essential-20040922/voxmsdec.ax: Cannot open: No such file or directory
tar: essential-20040922/vp4vfw.dll: Cannot open: No such file or directory
tar: essential-20040922/vp5vfw.dll: Cannot open: No such file or directory
tar: essential-20040922/vp6vfw.dll: Cannot open: No such file or directory
tar: essential-20040922/vssh264.dll: Cannot open: No such file or directory
tar: essential-20040922/vssh264core.dll: Cannot open: No such file or directory
tar: essential-20040922/vssh264dec.dll: Cannot open: No such file or directory
tar: essential-20040922/vsslight.dll: Cannot open: No such file or directory
tar: essential-20040922/vsswlt.dll: Cannot open: No such file or directory
tar: essential-20040922/wma9dmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmadmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmspdmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmv9dmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wmvdmod.dll: Cannot open: No such file or directory
tar: essential-20040922/wnvplay1.dll: Cannot open: No such file or directory
tar: essential-20040922/wnvwinx.dll: Cannot open: No such file or directory
tar: Error exit delayed from previous errors

---

### Post by herweg on 2004-10-26
It sounds to me like for some reason you don't have permission in that directory - come to think of it, it looks like you are one level up from where you should be. Is that your personal home directory for that username? If not, you won't have adequate permission to edit it, you can do one of two things - either sudo mv the file to your username's home directory, or you can just throw a sudo in front of the tar.

---

### Post by disposable on 2004-10-27
Since vBulletin won't let me edit the original post, the latest verion of the HOWTO is located here:

[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

I implore everyone to read the conclusion and notice that capability is added without enabling universe/multiverse/negaverse. The path of least resistance leads to... windows.

---

### Post by brschmid on 2004-10-27
[QUOTE=disposable]Since vBulletin won't let me edit the original post, the latest verion of the HOWTO is located here:

[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

I implore everyone to read the conclusion and notice that capability is added without enabling universe/multiverse/negaverse. The path of least resistance leads to... windows.[/QUOTE]
 i just got it built :) finally.

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=brschmid]i am having trouble with this part :



these are the errors, please help, i want to be able to listen to music and watch some movies.[/QUOTE]


Your extracting you /home which a defaul user doesn't have access too write too.  So in this case you would have to extract it to ~/ or /home/USER_NAME.

---

### Post by plasmo on 2004-10-27
emperor: i followed your guide and yes. everything worked flawlessly :D
u da man! :)

---

### Post by DriftSK on 2004-10-28
[QUOTE=jayclark]The mplayer custom has a problem. Dosen't want to work with all cpu's. It won't work on pentium 3's at all. At least thats what i'm told by a dev on the mailing list.[/QUOTE]

I confirm that. Right now as I'm writing it seems that mplayer-custom package was compiled with P4 optimizations (arrgghhh  :-(  ). Moreover, all mplayer packages that I've got in my apt cache now refuse to install, and are redirected to mplayer-custom as default fallback... so I can't even force mplayer-386 or similar as I used to.

PLEASE, rebuild mplayer-custom as a 386 package!

A little footnote about mplayer plugin: I've tried many of them, including the infamous Marillat-available one, but the one and only that worked 100% giving me playback control buttons and all the bells & whistles is the one in Cerkinfo repository:

deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

and is named mplayerplug-in.

---

### Post by hectorvs on 2004-10-29
Thanks man, it worked excellent!

The only thing is that sound doesnt work... kinda...

Everytime I open a movie by right click --- open with gmplayer I get this message

audio_setup: Can't open audio device /dev/dsp: Device or source busy


But when I open mplayer first and then open the movie through the player, sound works ??


any help? Thanks!

---

### Post by ubuntu-geek on 2004-10-29
Updated... on the first page...
 
 [QUOTE=disposable]Since vBulletin won't let me edit the original post, the latest verion of the HOWTO is located here:
 
 [http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt]("http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt")
 
I implore everyone to read the conclusion and notice that capability is added without enabling universe/multiverse/negaverse. The path of least resistance leads to... windows.[/QUOTE]

---

### Post by moon2js on 2004-10-30
Anyone else having problems with this howto? I've followed to the letter after a fresh install twice, and no luck. Video won't display windowed (just blue screen) however I can hear the sound. In full screen mode, the the video appears, but it's aligned wrong. There is a big blue bar going down the screen and the original video's right third is displayed on the left, the left on the right.

---

### Post by DriftSK on 2004-10-30
IMHO building Mplayer from sources is NOT the right way of solving the problem. At least not for the average Ubuntu user, which I suppose is not a geek.

Ubuntu to me is a very good package-oriented distro, and should be used as such. When you need to compile something in a package-oriented distro in my opinion there's something going wrong: Ubuntu is not Gentoo and eventually should be even better than Debian GNU/Linux for its simplicity and ease of use. This should mean no hassles with installation, no cryptic configuration steps, no need to compile anything.

The universe/multiverse repository is a very good approach because it allows the user to choose up to which grade of "unofficiality" his distro can be, a bit like choosing between Debian unstable or testing. Even Fedora, which is one of the most conservative distro ever about multimedia support (they don't even provide mp3 playback in the standard configuration, you have to add it manually), allows its users to add almost any multimedia toy they want - afterwards and using only yum or apt. And IMHO so should Ubuntu.

Let's face it, many people in this thread are reporting troubles about compiling Mplayer. It's not a very easy task and the user should not be forced to do it.

Instead, I'd suggest providing mplayer and mplayerplugin in the multiverse repository - after checking the mplayer-custom package, which in current state is almost useless (as I pointed out previously) being P4-only optimized.

My two cents, huh. Sorry if I've gone a bit OT.

---

### Post by dmatrix on 2004-10-30
If you look back thru this thread you will see I suggested an easier way using multiverse packages. The mplayer-custom package and the mplayer-amd64 package work great for me on many of my systems including amd64, 686-smp and k7. Once you install the mplayer package you just need to get w32codecs and you are good to go. As a Debian user I know I do not have to compile things from scratch. If there is a package available in apt-src its really easy to compile it. ie. apt-get --compile source mplayer-custom. Which is what I did with my mplayer package since it lacked libdvdread support.

---

### Post by Magneto on 2004-10-31
Just a side note for anyone having issues compiling or using the various methods listed here. 

Ubuntu seemed to make my ck-sources 2.6.8-cko8 kernel have major issues- weird instability issues with windowing - weird swap issues - and I couldnt compile mplayer from source without error everytime- switching back to the default ubuntu kernel set me straight again

Also mplayercustom seems to be compiled without gui support but comes with gmplayer links- but if I ran gmplayer - it would die in --help mode as if I ran mplayer

I am up and running though now and add another " Great job on the howto" from me

---

### Post by marguz on 2004-11-01
Sorry, but I just have to ask.

How did you tell apt-get to use libdvdread during the --compile option ?

I've looked. but could not work it out.

Comming from FC2, so apt-get with all of it options is new to me.

Mark


[QUOTE=dmatrix]If you look back thru this thread you will see I suggested an easier way using multiverse packages. The mplayer-custom package and the mplayer-amd64 package work great for me on many of my systems including amd64, 686-smp and k7. Once you install the mplayer package you just need to get w32codecs and you are good to go. As a Debian user I know I do not have to compile things from scratch. If there is a package available in apt-src its really easy to compile it. ie. apt-get --compile source mplayer-custom. Which is what I did with my mplayer package since it lacked libdvdread support.[/QUOTE]

---

### Post by fng on 2004-11-01
I can't resize the video :/.  Whenever i go fullscreen, the video remains the original size with a black border around it, instead of enlarging the video screen.

---

### Post by DriftSK on 2004-11-02
[QUOTE=fng]I can't resize the video :/.  Whenever i go fullscreen, the video remains the original size with a black border around it, instead of enlarging the video screen.[/QUOTE]

This is usually a side effect of using x11 video output instead of xv. Try setting xv as your video overlay and see (you should notice a performance improvement too).

---

### Post by oddabe19 on 2004-11-02
Actully... I use x11 (Cause i like my screenshot with video), and it resizes just fine (except doublemode... but that doesn't work in general).

in your mplayer configfile, you just have to make sure you have zoom in there. or when you launch mplayer

mplayer -zoom

---

### Post by fng on 2004-11-02
enabling it in the config file worked. thnx

---

### Post by Verlager on 2004-11-04
root@ubuntu:/home/verlager # sudo apt-get install libpng-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.5.0-7ubuntu1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate

What do I do now?

---

### Post by mercurus on 2004-11-04
I'm concerned.

Surely totem-xine is capable of playing all the same formats as mplayer ?

They use the same codecs, and totem comes pre-installed on Ubuntu systems. Further, a totem solution would continue GTK 2.0+ packages, and mean that no GTK 1.x+ packages or libraries would be required.

I installed totem-xine and codecs and I was very happy with it.

The **sole** reason I've just begun install mplayer from Marillat is the absence of an interface between mozilla-firefox and totem-xine. If there were mozilla plugins re-directing media to totem, I would ditch mplayer completely and maintain a GTK 2.0+ Ubuntu system.

Is there any possibility of such a match-up ?

Cheers
mercurus

---

### Post by spoetnik on 2004-11-04
The easiest way to install Mplayer and the firefox player plugin is using the scripts from kanotix.

[http://www.kanotix.com/files/](http://www.kanotix.com/files/)

Look for  these scripts...

install-codecs.sh
install-mplayer.sh
install-mplayer-cvs.sh
install-kmplayer.sh

---

### Post by St-Ex on 2004-11-04
I got MPlayer working, but not with DVD; i get a "seek failed" error warning...
Any idea? I'm almost there...

Cheers,

---

### Post by moon2js on 2004-11-04
[QUOTE=DriftSK]This is usually a side effect of using x11 video output instead of xv. Try setting xv as your video overlay and see (you should notice a performance improvement too).[/QUOTE]

I've found that when I use the xv option, the video doesn't display properly. In windowed mode, the picture won't display and in fullscreen mode, the video is unwatchable because the right half of the image is spliced onto the left side of the screen, the left half of the image is spiced onto the right, and there is a wide blue bar going down the middle, slightly favoring the right.

Is there anyway to fix this?

Using x11 as the video out option works fine though. What's the difference between xv and x11 besides performance?

---

### Post by BugsyMalone on 2004-11-04
[QUOTE=Verlager]root@ubuntu:/home/verlager # sudo apt-get install libpng-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.5.0-7ubuntu1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate

What do I do now?[/QUOTE]
 Verlager, the libpng-dev files can be installed in Synaptic. Make sure you have Universe enabled then do a search for libpng-dev. Several entries come up; I didn't know which one to choose so I installed them all. That will take care of it.

---

### Post by DriftSK on 2004-11-05
[QUOTE=spoetnik]The easiest way to install Mplayer and the firefox player plugin is using the scripts from kanotix.

[http://www.kanotix.com/files/](http://www.kanotix.com/files/)

Look for  these scripts...

install-codecs.sh
install-mplayer.sh
install-mplayer-cvs.sh
install-kmplayer.sh[/QUOTE]

Did you try it before posting? It made up quite a mess on my system: the install-mplayer.sh downloaded a whole bunch of stuff including the whole mozilla suite, spit out some errors and then tried to compile something - which obviously failed since I don't have any compiler on my system. I haven't found a clue about the need of a compiler in your post :-? now I have to go and clean up things...

---

### Post by DriftSK on 2004-11-05
[QUOTE=moon2js]I've found that when I use the xv option, the video doesn't display properly... 
[...]
Is there anyway to fix this?

Using x11 as the video out option works fine though. What's the difference between xv and x11 besides performance?[/QUOTE]

Xv is supposed to take advantage of your video card hardware overlay acceleration/scaling/blitting, if any. While x11 is something more basic and failproof, blitting the video without trying to use too much hardware support - which is slower and eats more CPU, but it's also likely to work on almost any video card.

I guess your troubles with xv are due to lousy video drivers and/or something wrong in the configuration. In both cases, if x11 is working fine for you go on with it and just don't care  ;-)

---

### Post by Gehost on 2004-11-05
[QUOTE=St-Ex]I got MPlayer working, but not with DVD; i get a "seek failed" error warning...
Any idea? I'm almost there...

Cheers,[/QUOTE]


hi, MPlayer can't read DVD, so I guess you to install (In Synaptic, with Universe server enabled) gXine. It can read divx and mpeg4 like MPlayer, but DVD format too... In addition, you can have a "integrated" xine to Totem... (totem-xine)

I recommand that , cos I had this problem...  8-[

---

### Post by Gehost on 2004-11-05
So... Just forget something...

In fact, you can read DVD with MPlayer, but you have to install, I think...

libdvdcss2 (sudo apt-get install libdvdcss2); but that never worked with me... :oops:

---

### Post by wallijonn on 2004-11-05
install SPM's XINE  (xine-ui)

google search for and download [COLOR=RED]libdvdcss2_1.2.8-1_i386.deb[/COLOR]

extract the files (creates /usr/lib folder) and then start a root terminal

cd <to the folder containing the following two files>
sudo cp [COLOR=BLUE]libdvdcss.so.2 [/COLOR] /usr/lib
sudo cp [COLOR=BLUE]libdvdcss.so.2.0.7[/COLOR] /usr/lib 
exit 

Slip in a movie DVD and enjoy.


.

---

### Post by St-Ex on 2004-11-10
Thx for your replys.
In fact, as I followed strictly the procedure described in the first page, I did install the libdvd...
And it eventually worked after a reboot....  :oops: 

So everything is working for me, except CD-Audio.... I really wonder what's wrong with it. It looks like it has got sthg to do with gnome-cd. I tried to desactivate the automatic reading with gnome-cd (as it can't be uninstalled through apt), but then it is not possible anymore to mount a CD-Audio, so no way to try out with XMMS (I installed the cd-read plugin). Weird... :confused:

---

### Post by Monika on 2004-11-10
[QUOTE=Magneto]JAlso mplayercustom seems to be compiled without gui support but comes with gmplayer links- but if I ran gmplayer - it would die in --help mode as if I ran mplayer[/QUOTE]

This is what's happened to me :(

I would try and compile from sources if I could, but I cannot download mplayer file number2 (the codecs). I went to their site and tried different mirrors but none of them work for me. Each time it just says that the site or file may have been moved, that it's not there.
I also recall trying to compile mplayer on SuSE linux a few weeks ago and got stuck in exactly the same spot.

I would really appreciate any help you could give me.

---

### Post by wallijonn on 2004-11-10
[QUOTE=St-Ex]So everything is working for me, except CD-Audio.... [/QUOTE]

Do you have the little 4 wire cable installed on your CDRom drive to the motherboard?

I find that I have to install it (to use the CDRom drive to listen to CD audio) but I can just use the IDE cable for Digital audio under Windows )leaving the small thin cable out).

---

### Post by St-Ex on 2004-11-11
> Do you have the little 4 wire cable installed on your CDRom drive to the motherboard? 

Actually, my dvd-rw is linked to my Audigy Player through a digital cable (tiny 2-pins cable).

But I eventually got CD-Audio working with XMMS.

Here is what I did:

1- I installed xmms-cd-read pkg

2- For this step, I will try to translate my desktop from french to english, but I am not sure as I have never got my desktop in english...
>desktop preferences>removable drive
For CD-Audio, I changes the line "gnome-cd --unique --play --device %d" by "xmms --unique --play --device %d". And it works great, using alsa driver.
I also changed the line for DVD, & replaced totem by gmplayer... No effect on cd-Audio, but each time I inserte a DVD, mplayer plays it automatically.

Cheers ;-)

> I would really appreciate any help you could give me. 

I can send you the file through email if you like.

---

### Post by zenetics on 2004-11-11
[QUOTE=brschmid]help!!! please

still getting errors on this part:[/QUOTE]
 Hello !!
I'm not sure, but you seems to have permission to create the directory 

Check if the directory is created before copying

---

### Post by mrv on 2004-11-13
[QUOTE=gamehack]
I think it's a big mistake for Ubuntu not to include mplayer in their repository. Come on, that's the best player for Linux and it's even in the repository... I like ubuntu very much but this annoys me. If there's some special package for Ubuntu for mplayer, can someone give me some links. Or some other way of installing it, but not by source. I hate whis brute force installing, although I can do it, it's not the preferred way.[/QUOTE]

If you take all the non-free / (patent) problematic parts out of the mplayer, there isn't that much left. You can't even encode (easily) in free formats, eg. Ogg Theora (for video) and Ogg Vorbis (for audio). But I do agree that mplayer has, for example, a great audio/video filter collection. I guess it just has all the non-free stuff too integrated in the core, so that it's difficult to have it in a GNU/Linux distribution.

And as was pointed out, the full mplayer is in the non-free section (multiverse) of Ubuntu.

---

### Post by krietor on 2004-11-14
The guide in this thread for compiling and installing Mplayer worked great for me. Thanks, disposable! One note, where I had to change some commands, since the source to wget one of the files was missing. . . . 
Where disposable says to do:
> $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2)
 the link didn't work so I used the following:  
'$ wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040704.tar.bz2'
 And of course some of the other commands had to be modified too. Just put 'essential-20040704.tar.bz2' wherever he says 'essential-20040922.tar.bz2' - Although there are a few clues, I don't grok the implications. However, it worked. I hadn't been able to make MPlayer go fullscreen correctly with the package from Marrilat (sp?) even after trying oodles of suggestions from here and other forums. Now MPlayer does fullscreen well. Also the handy gui came back. I like the keyboard shortcuts a lot, tho, and they are there too. 
    Wow, compiling from source can be easy and fun, AND it makes stuff run a lot better!
    Thanks again, disposable!
    P.S. I simply checked at [http://ftp5.mplayerhq.hu/mplayer/releases/codecs](http://ftp5.mplayerhq.hu/mplayer/releases/codecs) - the first part of the url for the tarball. That's when I noticed there was a essential-20040704.tar.bz2 and no essential-20040922.tar.bz2 . I suppose it was removed.

---

### Post by krietor on 2004-11-14
update on my MPlayer experience - It works really well, but every time I go to play a file it gives an error:
Requested audio codec family [mad]  (afm=libmad) not available. enable it at compilation.
What should I do?

---

### Post by adbak on 2004-11-14
I've heard that by adding ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your /etc/apt/sources.list you can install MPlayer.

NOTE:  that was *testing* -- not stable or unstable.

I'm too chicken to try that, anyone brave and daring care to confirm it for me?

---

### Post by TravisNewman on 2004-11-14
[QUOTE=adbak]I've heard that by adding ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your /etc/apt/sources.list you can install MPlayer.

NOTE:  that was *testing* -- not stable or unstable.

I'm too chicken to try that, anyone brave and daring care to confirm it for me?[/QUOTE]
 yeah, I've gotten it to run fine with testing.

---

### Post by Linux_Noob on 2004-11-15
Im having trouble with ogm format files. When i play them using mplayer i get a no stream error message? Is there some codec or app i need in addition to the ones mentioned in this thread on how to set up mplayer?

---

### Post by DaGr8Gatzby on 2004-11-16
I Really don't like MPLayer. I don't know why, I just don't. I would rather use Totem. Is there a way to get proprietary codecs to work with it?

---

### Post by kingmob on 2004-11-17
I'm getting a compile error during a make, while i followed the complete guide here. Funny thing is it used to work the last time i did it, but now, with a fresh install, something is wrong.
Maybe i should use another gcc version? If so, how?

This is the error:
```

mplayer.c: In function `main':
mplayer.c:3804: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make: *** [mplayer.o] Error 1

```

---

### Post by mrv on 2004-11-18
[QUOTE=DaGr8Gatzby]I Really don't like MPLayer. I don't know why, I just don't. I would rather use Totem. Is there a way to get proprietary codecs to work with it?[/QUOTE]

I don't like it either much. I just use it to convert video files to Ogg Theora / Ogg Vorbis formats, so that they can be played with free software programs, like the bundled Totem.

---

### Post by noxfu on 2004-11-19
Add the following to your /etc/apt/sources.list file:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty multiverse

Run the following command:

apt-get update

Type the following command:

sudo apt-get install mozilla-mplayer mplayer-fonts

---

### Post by brhill on 2004-11-21
Absolutly FANTASIC :D  Your instructions could not be easier or operate better!

thank you, Thank You, THANK YOU !!!

---

### Post by DriftSK on 2004-11-25
[QUOTE=adbak]I've heard that by adding ```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
``` to your /etc/apt/sources.list you can install MPlayer.

NOTE:  that was *testing* -- not stable or unstable.

[/QUOTE]

I can confirm that, the package in testing works fine. The one in unstable, though, is compiled against P4. The only thing missing in mplayerplugin now are controls, but it's a minor issue. Good! 
 :grin:

---

### Post by Magneto on 2004-11-25
I had to compile mplayer from source in Hoary yesterday- very worthwhile- compiled mplayerplugin too have allcodecs -newest quicktime and I have my controls on embedded media in webpages. The testing package from marillat wouldnt work for me this time although it did in warty.  Later I will post a tarball with fonts codecs some  nice skins , ffmpeg, gecko-sdk, mplayer cvs sources and mplayer plugin sources and a few instructions. I did go through the list of prereqs on mplayerplug-in's page with a terminal open running apt-get for deps but its the least buggy install of mplayer ive had to date including going to fullscreen from a quicktime trailer.

and totem seems totally useless to me

---

### Post by easy_target on 2004-11-25
OMG IT WORKS!!!!!
I've tried many different distros and the one true love is Ubuntu. I'm in love with phylosophy and all... 

Thanks team. Now I have a complete distro. Never coming back to $indows or anything!!!!

Woooo-hooooooooo!!!!!!

---

### Post by brlmedia on 2004-11-25
fantastic howto, just installed my first mplayer by command line, lol. seems to work fine!!

---

### Post by ubuntu_demon on 2004-11-25
Hi,

Why not create a multiimedia meta-package (like ubuntu-desktop) and put it in multiverse ?

It could contain mplayer + all codecs and xmms. Maybe add some more multimedia meta-packages like : multimedia-totem to get full multimedia support for totem and multimedia-xine to get full multimediia support for xine etc.

see also :

[http://www.ubuntuforums.org/showthread.php?t=6178&highlight=idea#post24097](http://www.ubuntuforums.org/showthread.php?t=6178&highlight=idea#post24097)

---

### Post by Magneto on 2004-11-25
[QUOTE=demon666_nl]Hi,

Why not create a multiimedia meta-package (like ubuntu-desktop) and put it in multiverse ?

It could contain mplayer + all codecs and xmms. Maybe add some more multimedia meta-packages like : multimedia-totem to get full multimedia support for totem and multimedia-xine to get full multimediia support for xine etc.

see also :

[http://www.ubuntuforums.org/showthread.php?t=6178&highlight=idea#post24097](http://www.ubuntuforums.org/showthread.php?t=6178&highlight=idea#post24097)[/QUOTE]

great idea

---

### Post by shir0kuma on 2004-11-26
Has anyone run into this problem with MPlayer:  "audio_setup: Cant' open audio device /dev/dsp:  Device or resource busy"

Here is the output I get from running gmlayer from the cli:

daniel@STS-LIn:~ $ gmplayer metroid_prime_2_echoes.mov
MPlayer 1.0pre5-3.3.5 (C) 2000-2004 MPlayer Team

CPU: Intel Pentium 4/Xeon/Celeron Foster 2680 MHz (Family: 8, Stepping: 7)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

**Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directory**
Reading config file /home/daniel/.mplayer/config
[cfg] read config file: /home/daniel/.mplayer/gui.conf
Reading config file /home/daniel/.mplayer/gui.conf
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
Disabling DPMS
**Reading /home/daniel/.mplayer/codecs.conf: Can't open '/home/daniel/.mplayer/cod ecs.conf': No such file or directory**
Reading /usr/local/etc/mplayer/codecs.conf: 73 audio & 180 video codecs
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using usleep() timing
Can't open input config file /home/daniel/.mplayer/input.conf: No such file or d irectory
Input config file /usr/local/etc/mplayer/input.conf parsed: 53 binds
SKIN dir 1: '/home/daniel/.mplayer/Skin'
SKIN dir 2: '/usr/local/share/mplayer/Skin'
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)

Playing /home/daniel/metroid_prime_2_echoes.mov.
QuickTime/MOV file format detected.
--------------
MOV track #0: 216 chunks, 1618 samples
MOV: Found unknown movie atom SMI  (21)!
Image size: 480 x 360 (24 bpp)
Display size: 480 x 360
Fourcc: SVQ3  Codec: 'Sorenson Video 3'
--------------
MOV track #1: 109 chunks, 0 samples
Audio bits: 16  chans: 2  rate: 44100
MOV: Found unknown audio atom odin (543518307)!
Fourcc: ima4
--------------
MOV: longest streams: A: #1 (109 samples)  V: #0 (1618 samples)
Clip info:
 author: Nintendo of America
==========================================================================
Opening audio decoder: [imaadpcm] IMA ADPCM audio decoder
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 46856->176400 (374.8 kbit)
Selected audio codec: [imaadpcm] afm:imaadpcm (IMA ADPCM)
==========================================================================
Xv: could not grab port 62
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsvq3] vfm:ffmpeg (FFmpeg Sorenson Video v3 (SVQ3))
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
audio_setup: Can't open audio device /dev/dsp: Device or resource busy
AO: [null] 44100Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
Starting playback...
VDec: vo config request - 480 x 360 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 480x360 => 480x360 Planar YV12
A:  53.9 V:  54.0 A-V: -0.011 ct: -0.011  1618/1618   9%  7%  0.3% 7 0 0%
Successfully enabled DPMS

Exiting... (Quit)


Any assistance would greatly be appreciated.

Thanks in advance,
Daniel

---

### Post by Magneto on 2004-11-26
is esd running? is this hoary?

---

### Post by Monika on 2004-11-27
I got mplayer running :)

But still missing a codec I need... How do I get *.ogm files to run? Also, some *.rm files although they play, mplayer says the audio/video is unsupported. There's also something weird with some *.wmv files. It says that actually they're *.asf files and that I have to rename them and after renaming them they play but still a bit strangely like with the *.rm - i.e. once I press stop I only have a black screen next time I press play and only the sound runs and then it hangs and I have to force it to quit.

Oh, and the pause doesn't work at all! It works like the stop button, only after I press play again I only have sound, just a black screen (even though it starts from the beginning, wheras with the stop everything's ok).

---

### Post by Big Ed on 2004-11-27
I just installed MPlayer on Warty and didn't find the essential-20040922.tar.bz2 so I just used the essential-20040704.tar.bz2 which was in the same directory.  Then I did a quick search and found the 0922 file here: [http://www4.mplayerhq.hu/MPlayer/releases/codecs/](http://www4.mplayerhq.hu/MPlayer/releases/codecs/)

I should have done the searh before substituting files,  Is there any real benefit to updating the essential package?  If so, should I uninstall MPlayer and reinstall with the newer essential package or can I just rerun the commands from the point where I diverged?

Thanks,
Ed

---

### Post by Magneto on 2004-11-27
[QUOTE=Monika]I got mplayer running :)

But still missing a codec I need... How do I get *.ogm files to run? Also, some *.rm files although they play, mplayer says the audio/video is unsupported. There's also something weird with some *.wmv files. It says that actually they're *.asf files and that I have to rename them and after renaming them they play but still a bit strangely like with the *.rm - i.e. once I press stop I only have a black screen next time I press play and only the sound runs and then it hangs and I have to force it to quit.

Oh, and the pause doesn't work at all! It works like the stop button, only after I press play again I only have sound, just a black screen (even though it starts from the beginning, wheras with the stop everything's ok).[/QUOTE]
 .ogm is ogg media file - divx and ogg audio  install the libogg0 package

---

### Post by Magneto on 2004-11-27
[QUOTE=Big Ed]I just installed MPlayer on Warty and didn't find the essential-20040922.tar.bz2 so I just used the essential-20040704.tar.bz2 which was in the same directory.  Then I did a quick search and found the 0922 file here: [http://www4.mplayerhq.hu/MPlayer/releases/codecs/](http://www4.mplayerhq.hu/MPlayer/releases/codecs/)

I should have done the searh before substituting files,  Is there any real benefit to updating the essential package?  If so, should I uninstall MPlayer and reinstall with the newer essential package or can I just rerun the commands from the point where I diverged?

Thanks,
Ed[/QUOTE]
 There's a difference in when the codecs were released and the versions supported- like the new quicktime codec came out recently so if you had an older package you wouldnt be able to view those- I personally use the all codecs package - just place the contents in /usr/local/lib/codecs  that's where mplayer will look when it attempts to open it- you dont have to recompile mplayer but mplayerplug-in would need it I think if you built it yourself

---

### Post by Monika on 2004-11-27
[QUOTE=Magneto].ogm is ogg media file - divx and ogg audio  install the libogg0 package[/QUOTE]

It's already installed.

---

### Post by Magneto on 2004-11-27
[QUOTE=Monika]It's already installed.[/QUOTE]
 do u have the right divx codec installed? 
have you tried installing the all codecs pack from mplayer?

oh and I forgot try realplayer10 for .rm files it will handle them alot better some codecs are handled nasty

---

### Post by shir0kuma on 2004-11-27
[QUOTE=Magneto]is esd running?[/QUOTE]
**Yes** 

[QUOTE=Magneto]is this hoary?[/QUOTE]  
**Yes**

---

### Post by Magneto on 2004-11-27
[QUOTE=shir0kuma]**Yes** 

  
**Yes**[/QUOTE]
 killall esd

---

### Post by shir0kuma on 2004-11-27
Worked like a charm.  Major domo!

---

### Post by Magneto on 2004-11-27
Here's a file with all you need for mplayer to work right
[http://ubuntu.spymac.net/mplayerfiles112704.tar.bz2](http://ubuntu.spymac.net/mplayerfiles112704.tar.bz2)

Contains
all-20041107  - all codecs for mplayer  essential files + others
MPlayer-current   -  source code from latest cvs
font-arial-iso-8859-1 - font for mplayer
skins- DVDPlayer,proton,orange,osxbrushed, terminator3
ffmpeg-cvs - codec for mplayer and mplayerplug-in
gecko-sdk-i686  - gecko sdk for building mplayerplugin
mplayerplug-in source code

check out [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/) for instructions on how to compile the plugin

Proton is my favorite skin but those others i included are all nice high quality skins

---

### Post by Monika on 2004-11-28
[QUOTE=Magneto]do u have the right divx codec installed? [/quote]

I don't know... *blush* But it seems like it cause my divx videos are playing fine. Well except for not being able to pause :P Which actually for me is quite a big "except" (but as mentioned, this goes for all my videos).

> have you tried installing the all codecs pack from mplayer?

No, how do I do that? :)

> oh and I forgot try realplayer10 for .rm files it will handle them alot better some codecs are handled nasty

I once tried to install realplayer but got nowhere. In the repository there's some strange realplayer installer that doesn't work. And on their page I don't remember what there was but it didn't work either :(

---

### Post by Magneto on 2004-11-28
To install the all codecs pack from mplayer 
download this file [http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20041107.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20041107.tar.bz2)
then
tar jxvf all-20041107.tar.bz2
cp all-20041107/* /usr/local/lib/codecs/


For realplayer10 download this [http://www.real.com/R/RC.080204rpchoice_1_2_2_1_1_2.ecomm...R/forms.real.com/real/player/download.html?f=unix/RealPlayer10GOLD.bin&product=playerplus&system=linux&&src=realplayer,080204rpchoice_1_2_2_1_1_2](http://www.real.com/R/RC.080204rpchoice_1_2_2_1_1_2.ecomm...R/forms.real.com/real/player/download.html?f=unix/RealPlayer10GOLD.bin&product=playerplus&system=linux&&src=realplayer,080204rpchoice_1_2_2_1_1_2)


Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

---

### Post by Monika on 2004-11-28
Thanks, RealPlayer works really nice :)

[QUOTE=Magneto]To install the all codecs pack from mplayer 
download this file [http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20041107.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20041107.tar.bz2)
then
tar jxvf all-20041107.tar.bz2
cp all-20041107/* /usr/local/lib/codecs/[/quote]

Still can't play *.ogg files :( And have all the other problems mentioned.

Question: does Totem Xine use the same codecs as mplayer? Cause when I had it installed some time ago it seemed to work better for me (I could use the pause button ;) ). It's just that Xine is far from covering my codec needs...

---

### Post by Magneto on 2004-11-28
Xine uses the same codecs just copy the files from /usr/local/lib/codecs to /usr/lib/win32 or symlink it
xine uses the codecs differently though some mpegs and avi files look alot better for me with xine than with mplayer 
dont know why your ogg files wont work- you could try ogmtools i think thats the name of the package - it will let you change ogg files to another format

---

### Post by easy_target on 2004-11-28
[QUOTE=DaGr8Gatzby]I Really don't like MPLayer. I don't know why, I just don't. I would rather use Totem. Is there a way to get proprietary codecs to work with it?[/QUOTE]

I have the same problem. Maybe I'm too picky but I would like to see the included software to work with all media formats. I also know about the issues of including the proprietary codecs for video and audio formats, but... is there a way to get proprietary codecs working with totem? If so, where can I get them??? I tried gxine but I also like  to tweak my desktop and I have to remove the customizations. Any help?

 :confused:

---

### Post by Magneto on 2004-11-28
as far as I know totem uses gstreamer or xine as a backend - so u can play whatever files gstreamer or xine is setup to work with

---

### Post by the stranger on 2004-11-29
im having trouble finding the following file:

essential-20040922.tar.bz2 from the 1st page, does anyone have a direct link for the file?

srry im a newbie

---

### Post by Magneto on 2004-11-29
[QUOTE=the stranger]im having trouble finding the following file:

essential-20040922.tar.bz2 from the 1st page, does anyone have a direct link for the file?

srry im a newbie[/QUOTE]
 [http://www2.mplayerhq.hu/homepage/design7/dload.html](http://www2.mplayerhq.hu/homepage/design7/dload.html)

---

### Post by the stranger on 2004-11-29
srry to b a pain but which option do i click on to get the file?

---

### Post by Magneto on 2004-11-29
[QUOTE=the stranger]srry to b a pain but which option do i click on to get the file?[/QUOTE]
 Codecs

These codec packages come without installer and are unusable by normal Windows movie players. Get the essential codec package for Linux or choose from the other codec packages.
description      HTTP 	FTP
essential codecs package 	[ HU | HU2 | US | US2 | CH ] 	[ HU | US | US2 ]

---

### Post by the stranger on 2004-11-29
trying to complie MPlayer, but when i go to hit the "make" command i get the following message

> Makefile:7: config.mak: No such file or directory
make: *** No rule to make target `config.mak'.  Stop.

---

### Post by Magneto on 2004-11-29
[QUOTE=the stranger]trying to complie MPlayer, but when i go to hit the "make" command i get the following message[/QUOTE]
 ./configure 
make
sudo make install
?
have you followed all the instructions precisely?

---

### Post by LongTooth on 2004-11-29
I had problems with one step in disposable's instructions. In particular 'sudo apt-get install libpng-dev'. Apt-get could not find it and it informed me I had to make a choice. Don't ask me how I came across it but I ended up using 'sudo apt-get install libpng12-dev'. After that the rest of of the install when smoothly. You see, at first when I could not install libpng-dev I went on but at the 'make' it failed. After using libpng12-dev I encountered no problems. It did scare me when at the 'make' step apt-get just kept going and going until I thought I had done something wrong or this was going to fail again. But that was not the case. I now have Mplayer working. The fly in the oinment is that I can not play inbedded Quicktime clips as when I go to the Apple trailers site. It doesn't load (play). But if I donwload and save a .mov (Quicktime) file Mplayer works fine. One word of advice, change your audio option in Mplayer to 'oss OSS/loctl audio output' for sound. Right click Mplayer>preferences> audio>OSS. 

Now if someone can tell me how to view embedded Quicktime clips...

---

### Post by the stranger on 2004-11-29
got over the last problems, thanks for you help!

however, just stuck on this:

> sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/ 

then i go to run **gmplayer**

and get the following:

*bash: gmplayer: command not found*

any ideas?

---

### Post by Magneto on 2004-11-29
[QUOTE=the stranger]got over the last problems, thanks for you help!

however, just stuck on this:

 

then i go to run **gmplayer**

and get the following:

*bash: gmplayer: command not found*

any ideas?[/QUOTE]

Did you compile mplayer with the option --enable-gui ?

./configure --enable-gui

---

### Post by LongTooth on 2004-11-29
the stranger, to sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/  you must be in the directory where Mplayer-1.Opre5 ...is. When you extracted it, where did you do that. In most cases, folks make a folder in their home directory and lable it downloads. If you have done that and extracted Mplayer-1... in that directory, then cd to downloads. You'll be in the proper directory. Procede with sudo cp Mplay... Do a ls to see what's in a certain directory. When you find it that you can continue.

---

### Post by kris kincaid on 2004-11-29
disposable, you deserve a medal for that How-To! I tried for hours to get mplayer to work. 15 mins after reading your post and I'm in business. Thanks!  :D

---

### Post by kamstrup on 2004-11-30
Wurtel: Don't be afraid of trying this out. You are not messing with core system files here, so won't be likely to break anything ;)

One of the best ways to learn your ways through the shell is just to jump into it. If you have problems, then you have the Ubuntu forums :) When you finally get the hang of it with the shell, you'll be glad that you spent the time. Things are infinitely more faster than clicking around in your desktop, and you have a better fealing on exactly what is going on (not to begin with of course).

---

### Post by kamstrup on 2004-11-30
SUB-HOWTO :)

Installing mplayer to handle video mime types
----------------------------------------------------------------------

If you've followed disposable's (great) howto you will have a file /usr/local/etc/mplayer/mplayer.desktop . Add the following line to the bottom of this:

MimeType=video/x-msvideo;video/mpeg;video/quicktime;video/x-ms-asf;

(You could do this for example with 
'sudo gedit /usr/local/etc/mplayer/mplayer.desktop' )

After doing this run these two commands:

sudo desktop-file-install --vendor mplayer /usr/local/etc/mplayer/mplayer.desktop
sudo update-desktop-database /usr/share/applications/

There you go! Rightclicking an avi,mpg,mov,wmf-file will now give you "Open with MPlayer". Hope it works for you! :D

-------
FIXME: Might add even more mime-types in the .desktop ??
FIXME^2: Why doesn't 'make install' do this? This sub-howto might also be included in disposables howto.

---

### Post by the stranger on 2004-11-30
done it!

but for some reason it just plays in the terminal, how do i make it so it does i have a graphical display?

---

### Post by adbak on 2004-11-30
Are you typing "gmplayer" in the CLI?

---

### Post by steffen on 2004-11-30
I installed mplayer, streaming and all codecs from Marillat. I worked for ages to find out how to resize a window properly, and where my Play, Stop, FFW, Sound, etc. buttons were. I discovered through this thread that the default Marillat package doesn't have a GUI (for some odd reason).

Anyone know how I can add the GUI to my Mplayer, so that Gmplayer would work?

Also - Ubuntu put a menu icon for Mplayer in the Multimedia menu - this links to Gmplayer, which then doesn't start, because GUI isn't enabled. Very odd and confusing, indeed!

---

### Post by LongTooth on 2004-11-30
the stranger, try the alt/F2 combination. That will give you a 'Run' window. Key in gmplayer, ( or what ever program you want to run ). That should get Mplayer going.

---

### Post by adbak on 2004-11-30
Make sure that your Marillat repository is set to "testing" instead of stable or unstable.

---

### Post by the stranger on 2004-12-01
if i type gmplayer noting happens i just get a bash error message, but if i type mplayer then sumthing happens, ie it allows me to play within the terminal, and it give  me all these options aswell

---

### Post by poofyhairguy on 2004-12-01
[QUOTE=the stranger]if i type gmplayer noting happens i just get a bash error message, but if i type mplayer then sumthing happens, ie it allows me to play within the terminal, and it give  me all these options aswell[/QUOTE]

ewww. Don't use gmplayer. After trying them ALL, gxine is by far the best in ubuntu!

---

### Post by Roptaty on 2004-12-01
Steffen, I guess you installed the mplayer-custom deb package? Try installing mplayer-386 or mplayer-586. :) The mplayer-custom deb package does not provide gui, but I think the rest of the mplayer packages do. :)

---

### Post by LongTooth on 2004-12-02
puffyhairguy, will installing gxine cause any conflict? After a lot of work, I've got mplayer up and running but it has it's shortcomings. For one, when I play a clip straignt from the browser, no controls are shown. On the other hand if I first download and save the file and then open mplayer I have controls. Another annoyance is no embedded Quicktime streaming video. Once again, if I first downloand and save it, no problems. To be honest if I could get Totem to play all the types of streaming videos I'd use it. I'm thinking of trying gxine but I have concerns with any conflicts. Let us know. Thanks.

Any steps you could share with us on the installation and configuring of gxine? I'd appreciate it.

---

### Post by Infatuated_iPod on 2004-12-02
>   Have your Warty Warthog CD handy and accept any extra packages, e.g. the
libtool install will also install gcc. We'll use a US mirror for (most of)
the MPlayer packages and assume you're working in your home directory.
Download MPlayer, codecs, English fonts and the default blue skin.
Internationalization and slick graphics are up to you.

$ wget [http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2)
$ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)


I dont understand what to do there...
when i typed the code into the terminal it said host not foudnd.

---

### Post by 2fargon on 2004-12-03
[QUOTE=Infatuated_iPod]I dont understand what to do there...
when i typed the code into the terminal it said host not foudnd.[/QUOTE]

You should probably try and click those links, and copy the urls from there, using the dots (...) in the urls will not work, dude :)

Also, if that is not the problem, earlier in the thread someone said something about there being replacement urls, for when a particular download sub domain is down.

---

### Post by 2fargon on 2004-12-03
[FONT=Courier New]$ sudo apt-get install libpng-dev[/FONT] gave multiple choices so I used:
[FONT=Courier New]$ sudo apt-get install libpng12-dev[/FONT]

[FONT=Courier New]wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2) [/FONT]was down so I used:
[FONT=Courier New]wget [http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20041107.tar.bz2](http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20041107.tar.bz2)[/FONT]

Also change the icon line from :
Icon: /usr/local/share/mplayer/Skin/default/icons/32x32.png
to:
Icon: /usr/local/share/mplayer/Skin/default/icons/icon32x32.png







I followed the new version at 
[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

Thanks!

---

### Post by 2fargon on 2004-12-03
[FONT=Courier New]$ sudo apt-get install libpng-dev[/FONT] gave multiple choices so I used:
[FONT=Courier New]$ sudo apt-get install libpng12-dev[/FONT]

[FONT=Courier New]wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2) [/FONT]was down so I used:
[FONT=Courier New]wget [http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20041107.tar.bz2](http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20041107.tar.bz2)[/FONT]

I followed the new version at 
[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

Thanks!

---

### Post by Jason-X on 2004-12-04
Thanks for the HOW-TO. It worked a treat. :D

---

### Post by pavkonti on 2004-12-07
I have a problem with mplayer. It is  working fine, but it do not want save my preferences and I couldn't make subtitles to work. My subtitles are with cyrilic windows 1251 encoding.

---

### Post by Hikaru79 on 2004-12-09
I've been having a few problems with streaming video; I have an mms:// stream which is vital to my continued happiness :P If I try it with totem, the video shows up, but freezes constantly and has no audio whatsoever. If I try it in mplayer with the live.com library, it goes EXTREMELY slow with clipped audio and video. Trying it with gxine was best of all: I was able to get almost freeze-less video, but the audio seems to be several seconds behind. (or ahead, not sure-- it's Korean). Gxine seems to be the closest to what I'm after, so I'm asking -- any ideas what could be causing this slow down? In mplayer, I DO get an actual warning message that says that this file will be very slow. The most common reason stated for this (in this message) is an outdated or buggy audio driver. Their reccomended solution is using an ALSA/OSS emulator. Is this what the alsa-oss package is in Hoary/Warty? Because if it is, then I already have it. Is it not configured right? What can I do? 

Thanks in advance :D

---

### Post by GavinX on 2004-12-10
A great 'How To'. Rated as one of the very best that I have seen anywhere on the net. This article is really accessible, even to newbies of linux. You make Ubuntu as easy as eating good food!

---

### Post by sonetti on 2004-12-11
I have mplayer installed is there a way I can make it the default player for all my movie files (mpeg1&2, mpeg4, quicktime etc) at the moment Totem trys to open them unsucessfully. I'd like to be able to click on any supported movie file and have it open in mplayer, (I'm new to linux & ubuntu, thanks to all who contributed to the mplayer & mplayer plugin installation guides)

---

### Post by adbak on 2004-12-11
Open up Nautilus, which is the file explorer for Gnome.  On any movie that you have downloaded or on your computer, right click, click Properties, then click the Open With tab.  At the bottom of that window click the Add button and type in "gmplayer" without the quotation marks.  Do that to any file type you want MPlayer to open up.

---

### Post by sonetti on 2004-12-11
.... ah yes, that works a treat, many thanks!

---

### Post by mauron on 2004-12-12
Thanks for the HOWTO, worked great. 

I do however have 1 problem, and that is that whenever I play a video in Firfox (I use version 1.0), Firefox crashes shortly after thet video has finished playing. I have tried setting my video preferences to X11, but it doesn't seem to make any difference.

---

### Post by LongTooth on 2004-12-12
Disposable's HowTo was invaluable in getting my video needs met. Couldn't do without his help. Though there are a few changes I made along the way I'd like to pass on. It might help others. The most important being the substitution of  $ sudo apt-get install libpng-dev with  $ sudo apt-get install libpng12-dev. Also somewhere deep into this thread is an another link to  $ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2). Use that one as Disposable's link is down. With the exception of not being able to view embedded Quicktime (.mov) files- see  [http://www.apple.com/trailers/](http://www.apple.com/trailers/) -  , Disposable's help solved most of my problems. 

For downloaded files of all types, Mplayer did just fine. Mplayer popped up and just worked when viewing .mov, wmv, mpg, mpeg files. It worked equally well with streaming viewing with the exception of embedded .mov files. For my embbeded .mov needs, Mozpugger picked up the slack. In essence what I have is two packages working for me, Mplayer and the browser pluggin (mozplugger) which I can easily remove. At a terminal, a quick and painless sudo apt-get install mozplugger will give me browser viewing of streaming videos. When not in need, a just as quick, sudo apt-get remove mozplugger, will bring Mplayer back to usage. 

It might seem a bit too cumbersome for most but its a solution that works for me. The adding and removing Mozplugger via a terminal is quick and painless. In this case bringing Synaptic on line takes too long. CLI is a faster solution in this case. 

All which bring up a request of my own. If anyone can provide a solution for viewing embbeded .mov files without the use of Mozplugger, please feel free to post it. I'd like to check it out.

One complaint if I may. When viewing downloaded files I have full controls showing on Mplayer. When viewing files on the fly so to speak, there are no controls showing. Just the file playing. Thus no control over replay, stopping, back-up, etc. I'm looking for a solution for that as well. 

Good luck and good viewing.

---

### Post by adbak on 2004-12-12
Can anyone who has MPlayer installed from the Marillat repo please tell me their version number?  I installed something that unknowingly got rid of my MPlayer and I didn't have the version number written down.  I think I know of a way to install that version number, so any help would be appreciated.

---

### Post by kamstrup on 2004-12-13
sonetti and adbak: A few pages back I posted a howto on installing a proper .desktop file for mplayer. This would be the best solution for proper desktop integration. I don't know why mplayer doesn't install it by default...

---

### Post by sonetti on 2004-12-13
yes I saw your tip just after posting my question and it works great,  right-clicking the movie file gives you the choice to open it not just with "mplayer" but with any other media player you may have installed .... cheers kamstrup!

go to pg.13 of this thread ...
[http://ubuntuforums.org/showthread.php?t=94&page=13&pp=10](http://ubuntuforums.org/showthread.php?t=94&page=13&pp=10)

---

### Post by adbak on 2004-12-13
UPDATE:  I was relieved to find out that I still had some mplayer .debs in my /var/cache/apt/archive that worked.

---

### Post by davegod75 on 2004-12-14
[QUOTE=emperor]I 

For firefox:
sudo cp mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in.xpt /usr/lib/mozilla-firefox/components[/b]

**Notes:**(a) I also found I had to **set Mplayer's Video driver to X11** (Preferences - Video - X11)  or Firefox/Mizilla would crash after playing a movie.[/QUOTE]


I don't have these two files after doing all your steps

---

### Post by adbak on 2004-12-14
[QUOTE=davegod75]I don't have these two files after doing all your steps[/QUOTE]
 Are you sure that you are in the proper directory?

cd /home/<user>/mplayerplug-in or wherever you untarred it to.

---

### Post by almostprofound on 2004-12-16
i got mplayer installed and it loads but when i try to play a dvd it says "could not find /dev/dvd"

i ran through the dvd instructions below the mplayer walkthru, rm'ed /dev/dvd and ran thru them again. still no go. any ideas? this is on hoary.

---

### Post by Perfect Storm on 2004-12-18
Just wanna tell that a new version of Mplayer is out (1.opre5try2) and codecs, so people should take that in consideration when following the Mplayer compiling guide, so remember to change where it says eg: essential-20040922 to essential-20041107 and so on.

---

### Post by sonetti on 2004-12-18
anyone tried the new version yet ....any improvements ?

---

### Post by neighborlee on 2004-12-18
[QUOTE=spoetnik]The easiest way to install Mplayer and the firefox player plugin is using the scripts from kanotix.

[http://www.kanotix.com/files/](http://www.kanotix.com/files/)

Look for  these scripts...

install-codecs.sh
install-mplayer.sh
install-mplayer-cvs.sh
install-kmplayer.sh[/QUOTE]
------------
 I have mplayer for mozilla but when I try loading it in firefox..it starts to play ( [www.startrek.com](www.startrek.com) > current episode OR try 'next' to get to one that shows a video preview ) and then stops saying I need plugin..when I click get plugin it just shows : unknown plugin...it shows a manual install button but that does nothing either..

any idea ?

thx

---

### Post by Ubuntu Warrior on 2004-12-22
Excellent HOWTO! Was slightly peaved when I first installed Ubuntu with its basic lack of multimedia support. Followed the steps and installed the 1.0pre5try2 version of MPlayer and am overjoyed. With quality software like Ubuntu Linux, Apache, MySQL and MPlayer (just a few of my favourites) it is a wonder why people still use proprietary solutions over open source alternatives. The new Firefox browser sings!

Just a pity that software installed via APT/Synaptic seems to be so far behind versions obtainable directly from the source website...

---

### Post by Perfect Storm on 2004-12-27
New Mplayer have been released (opre6).

---

### Post by Datchew on 2004-12-27
I got all the way to the portion of the walkthrough that said...


****************************************************************
 Have your Warty Warthog CD handy and accept any extra packages, e.g. the
libtool install will also install gcc. We'll use a US mirror for (most of)
the MPlayer packages and assume you're working in your home directory.
Download MPlayer, codecs, English fonts and the default blue skin.
Internationalization and slick graphics are up to you.

$ wget [http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2)
$ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)

Using the README from mplayerhq.hu [3] as a baseline, install the codecs
with the following commands.

$ tar -xjf essential-20040922.tar.bz2
***************************************************************

then, i must have screwed up.  The 2nd link that ended in 0040922.tar.bz2 didn't work and also when I put tar -xjf essential-20040922.tar.bz2 into the terminal, it gave me the following gibberish...

"$ tar -xjf essential-20040922.tar.bz2
tar: essential-20040922.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors "


Please advise.  I'm sure it's simple, but this is about my 2nd hour ever using Linux. 
 :oops:

---

### Post by Perfect Storm on 2004-12-28
It's because, there is a newer essential, (20041107) and the old one removed. Go to mplayer site and grab the newest essential, the same thing with mplayer (1opre6). Remember to replaces the old name with new ones when you compiling.
 
 
 
 .:=The AI Dude=:.

---

### Post by Datchew on 2004-12-28
I'll try that.
Perhaps, though, I need to start somewhere else.

I'm not even sure how to begin compiling. 
Is there somewhere I can read a basic overview of what i'm doing in Linux?

So far i seem to just run commands from a terminal which seem to download, copy, and execute parts of programs from a web ftp site.   

At this part:  

$ wget [http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2)
$ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)


are those commands i'm supposed to type into the terminal window?
If i click on the links, it downloads something and opens a window that does "rollover".   I'm clueless.  Am in in too deep for my first couple days?

Thanks much.

---

### Post by snaga on 2004-12-28
[QUOTE=disposable]
 
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2")
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2")
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2")
     $ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2]("http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2")
 
 [/QUOTE]

The codecs link, the second one, should now be:

[http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2)

---

### Post by Laf on 2004-12-28
Don't forget that Marilat's Debian repository is ONLY for i386, so this HowTo (as good as it is !) will never be ok for people who have something else than a PC...

I would really like that you would do an "universal" howto :o).

---

### Post by senectus on 2004-12-28
hey can this be updated for the change in codecs..

It should now be 
```
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2
```

Also the libpng-dev should also be changed to libpng12-dev

umm and to make things easier for all, how about adding this line:
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y

Saves much time ;-)

It was fantastic help BTW.. 
Thanks

---

### Post by senectus on 2004-12-29
[QUOTE=Datchew]I'll try that.
Perhaps, though, I need to start somewhere else.

I'm not even sure how to begin compiling. 
Is there somewhere I can read a basic overview of what i'm doing in Linux?

So far i seem to just run commands from a terminal which seem to download, copy, and execute parts of programs from a web ftp site.   

At this part:  

$ wget [http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...1.0pre5.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)
$ wget [http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...-8859-1.tar.bz2)
$ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)


are those commands i'm supposed to type into the terminal window?
If i click on the links, it downloads something and opens a window that does "rollover".   I'm clueless.  Am in in too deep for my first couple days?

Thanks much.[/QUOTE]


Ok the forums are making it "easier" for you to read the links, so its no good copy and pasting the text on the screen into a shell box.. :-P 
if your going to click on the link and not use the shell (command line stuff) then you need to use the "save as" function.
The "rollover" sounds like your opening up the tar.bz2 within the GUI, (Just like when you double click on a winzip file in windows.. same thing).

try copy and paste this:
 ```
wget http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2
wget http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2

```

Do each line seperately and wait until its finished downloading before doing the next line.
wget is a pretty quick/robust download manager.. its worth learning to use it..

---

### Post by Datchew on 2004-12-29
ok. that worked wonderfully. 
Looks like i'm going to have to do some serious learning to get all those terminal commands down.  Sheesh.  At least i can copy and paste!

now i'm at this part
***********************************************

Time to compile MPlayer. Issue these commands.

$ tar -xjf MPlayer-1.0pre5.tar.bz2
$ cd MPlayer-1.0pre5
$ ./configure --enable-gui
$ make
*************************************************

it did ALL KINDS OF STUFF in teh terminal after the 3rd line there. 
But after the "make" command, it gave me this:

datchew@xxxxxLinux:~/MPlayer-1.0pre5 $ make
Makefile:7: config.mak: No such file or directory
make: *** No rule to make target `config.mak'.  Stop.

---

### Post by Perfect Storm on 2004-12-30
Do the ./configure and check the output for errors or missing liberies, that could be the reason why you can't do the 'make'.


.:=The AI Dude=:.

---

### Post by Datchew on 2004-12-30
Could you please explain that a little better?
I don't really know what that means. 

Are libraries places where you store software that you pull from repositories so that you can execute and install it locally?

---

### Post by senectus on 2004-12-30
he's asking you to do this again
cd MPlayer-1.0pre5
./configure --enable-gui


and when its finished check out what the last 15 or so lines say.. there may be some interesting error's or information in it.

---

### Post by piedamaro on 2004-12-30
> Are libraries places where you store software that you pull from repositories so that you can execute and install it locally? 
No. Libraries are binary files used to build and run applications: they provide the so-called API, a set of functions used by developers to write useful apps. (very simply speaking).

---

### Post by Perfect Storm on 2004-12-30
Okay, perhaps I didn't make it cleared enough ;)

It seems something went wrong while you did the './configure'. You can see it looking for all kind of libraries (eg: gcc ++....ok). Do you see any errors while doing the "./configure" ? Usual it says if you're missing some libraries.

---

### Post by Datchew on 2004-12-30
I'll run that again this evening and I'll post what it comes up with . 
Thanks for explaining.

---

### Post by Datchew on 2004-12-30
ok... here's what it did. 
i hope i'm not violating some rule by pasting this HUGE list into here...
please tell me how to make the little insert that scrolls inside the post. 

************************
datchew@FrogLinux:~ $ tar -xjf MPlayer-1.0pre5.tar.bz2
datchew@FrogLinux:~ $ cd MPlayer-1.0pre5
datchew@FrogLinux:~/MPlayer-1.0pre5 $ ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 3.3.4, ok
Checking for CPU vendor ... AuthenticAMD (6:4:2)
Checking for CPU type ...  AMD Athlon(tm) Processor
Checking for GCC & CPU optimization abilities ... athlon-tbird
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowex ... yes
Checking for mtrr support ... yes
Checking for assembler (as 2.14.90.0.7) ... ok
Checking for Linux kernel version ... 2.6.8.1-4-k7, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for i18n ... yes
Checking for setlocale() ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages: en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for nanosleep ... yes
Checking for socklib ... yes (using -lnsl)
Checking for inet_pton() ... yes (using -lnsl)
Checking for inttypes.h (required) ... yes
Checking for int_fastXY_t in inttypes.h ... yes
Checking for word size ... 32
Checking for stddef.h ... yes
Checking for malloc.h ... yes
Checking for memalign() ... yes
Checking for alloca.h ... yes
Checking for mman.h ... yes
Checking for dynamic loader ... yes
Checking for dynamic a/v plugins support ... no
Checking for pthread ... yes (using -lpthread)
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for BSDI dvd.h ... no
Checking for HPUX SCSI header ... no
Checking for userspace SCSI headers (Solaris) ... no
Checking for termcap ... no
Checking for termios ... yes (using sys/termios.h)
Checking for shm ... yes
Checking for linux devfs ... no
Checking for scandir() ... yes
Checking for strsep() ... yes
Checking for strlcpy() ... no
Checking for strlcat() ... no
Checking for fseeko() ... yes
Checking for localtime_r() ... yes
Checking for vsscanf() ... yes
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/X11R6/include)
Checking for X11 libs presence ... yes (using /usr/X11R6/lib)
Checking for X11 ... yes
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes
Checking for XvMC ... no
Checking for Xinerama ... yes
Checking for Xxf86vm ... yes
Checking for DGA ... yes (using DGA 2.0)
Checking for OpenGL ... yes
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... no
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=D IR)
Checking for DVB HEAD ... yes
Checking for PNG support ... no
Checking for JPEG support ... no
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... no
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for JACK ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... no
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for OggVorbis support ... no
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libmpeg2 support ... yes
Checking for Matroska support (external 0.6.0 or later OR internal) ... yes, int ernal
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for FAAD2 version ... 2.0
Checking for MacOS X SHLB (shared lib) support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformatc (static) ... no
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for DivX4linux/DivX5linux/OpenDivX decore ... no
Checking for libmp3lame (for mencoder) ... no
Checking for DivX4linux encore (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for EDL support ... yes
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... no
Checking for Video 4 Linux 2 TV interface ... no
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for byte order ... Little Endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes

Error: PNG support required for GUI compilation, please install libpng and libpn g-dev packages.

Check "configure.log" if you do not understand why it failed.
*************************************************************

so libpng and libpng-dev packages need to be installed?
i don't know the first step to get those.

---

### Post by Perfect Storm on 2004-12-31
Go to the 'synaptic package manager' (It's under computer, system configuration). Press the reload button. Then hit the 'search' button and write libpng.
Mark 'libpng 10-0', 'libpng10-dev', 'libpng12-0', 'libpng12-dev' install that should do it. Press the apply button.

or by the terminal:
```

sudo apt-get install libpng10-0

sudo apt-get install libpng10-dev

sudo apt-get install libpng12-0

sudo apt-get install libpng12-dev

```

Edit: spell error in the codes  :oops:


The problem lies in the guide 'sudo apt-get install libpng-dev' doesn't apply anymore. Perhaps the "owner" of the guide should change it.

---

### Post by senectus on 2004-12-31
[QUOTE=Artificial Intelligence]
The problem lies in the guide 'sudo apt-get install libpng-dev' doesn't apply anymore. Perhaps the "owner" of the guide should change it.[/QUOTE]

I have actually pointed this out:
[http://ubuntuforums.org/showpost.php?p=40060&postcount=164](http://ubuntuforums.org/showpost.php?p=40060&postcount=164)

And I "PM'd" that to him as well.. I guess he doesn't log in much anymore..

---

### Post by Perfect Storm on 2004-12-31
Aaahh...ok, I must have missed it.

---

### Post by hruske on 2004-12-31
Okay, this ubuntu is cool, but still lacks audio mixing. Some cards have this onboard, others need software mixing. I've managed to get alsa dmix plugin to work, this means it works transparently and in kernel (fast). 

This means you can now preview movies and listen to sounds from xmms or rhythmbox. 

So how to set up?

1. 
Make sure you have alsa supported.

2. 
Edit /etc/asound.conf
It will probably not exist, so make a new file.

(This setup works for my snd-intel8x0 module)

Put this in it:
```

 pcm.!default {
   type plug
   slave.pcm "dmixer"
 }

 pcm.dmixer  {
   type dmix
   ipc_key 1024

   slave {
     pcm "hw:0,0"
     period_time 0
     period_size 1024
     buffer_size 4096
     rate 48000
   }

   bindings {
     0 0
     1 1
   }
 }

```

You might need to edit these lines:
 pcm "hw:0,0"
and
 rate 48000

First line is for device, i've found this in my dmesg output:
 intel8x0_measure_ac97_clock: measured 49631 usecs
 intel8x0: clocking to 48000

For mplayer to work, you need to change /etc/mplayer/mplayer.conf (inf installed by apt-get) or /usr/local/etc/mplayer/mplayer.conf like this:
 ao=alsa


For xmms to work you just need to set output plugin to alsa, default device. 
Sometimes it has some problems with mmap mode (under output plugin settings) so if it does not work in first go, try changing current mmap mode.

Does it work for you?

---

### Post by Datchew on 2004-12-31
Interesting. 

In synaptic manager (what a bizarre name for a program update manager) I already had 2 of those checked and installed. 
So i did the other 2 you recommended and it's done. 
I'm going to try to pickup where i got those errors... standbye...

(10 mins later) ... ok, well, there's still tons of stuff going down the terminal window after if entered the "make" command. 

I'll post again when it's done and i do the rest of the steps. 
:-)

---

### Post by Datchew on 2004-12-31
beautiful... just got the icon installed (a nice blue triangle) and i'm about to test. 
(fingers crossed, breath held)

---

### Post by Datchew on 2004-12-31
WHOO HOO  that did it.
My dvd is playing beautifully. 
Thanks so much for your help. 

I really appreciate it. 
I think i'm gonna like Linux.

---

### Post by Perfect Storm on 2004-12-31
No problem :)

and welcome to the world of linux :)

> 
n synaptic manager (what a bizarre name for a program update manager) I already had 2 of those checked and installed.
So i did the other 2 you recommended and it's done.

They two is installed as default, but I just mention them for the safty sake.

---

### Post by vaskark on 2005-01-01
[font=Trebuchet MS]I installed MPlayer successfully, but it won't play DVD's. I get the error:
 
  > Cannot open the IFO file for DVD title 1 
 Has anyone else encountered this? I can play most media files from my harddrive fine. This is so annoying!
 
 Thanks.[/font]

---

### Post by wallijonn on 2005-01-01
[QUOTE=Datchew]please tell me how to make the little insert that scrolls inside the post. [/QUOTE]

Enclose the huge text with the word "code" in brackets before the start of the list and "/code" in brackets at the end.

This will allow us to scroll through the smaller code window.

---

### Post by wallijonn on 2005-01-01
vaskark,

You probably did not cp the libdvdcss.so.2.0.7 files to /usr/lib. (Or whatever libdvd files are necessary for MPlayer; the above are used by xine).

---

### Post by wallijonn on 2005-01-02
[QUOTE=senectus]I have actually pointed this out:
[http://ubuntuforums.org/showpost.php?p=40060&postcount=164](http://ubuntuforums.org/showpost.php?p=40060&postcount=164)

And I "PM'd" that to him as well.. I guess he doesn't log in much anymore..[/QUOTE]

You should have just as well tell them to copy
```

[COLOR=Red]apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y[/COLOR]
```
into an open editor window, then save the file as a shell script, like [COLOR=Blue]mplyr1.sh[/COLOR]

Then all they have to do is open up a root terminal,
```
sudo sh mplyr1.sh
```
and everything will scroll through their window.

---

### Post by wallijonn on 2005-01-02
If someone wants to try the latest build, highlight all the code inside the code box, right click, start gedit (or your favourite editor), paste, exit,  save it as [COLOR=Red]mplayer.sh[/COLOR]. 

```

sudo mkdir mplyr
cd mplyr
#
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y
#
# get mplayer program
wget http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre6a.tar.bz2
#
# get codecs
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2
#
# get fonts
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2 
#
# get skin 
# go to http://www.mplayerhq.hu/homepage/design7/dload.html right click 
# your favourite [HTTP] skin, Copy Link Location, 
# paste it over the following line after wget)
wget http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2 
#
tar -xjf MPlayer-1.0pre6a.tar.bz2
cd MPlayer-1.0pre6a
./configure --enable-gui
make
make install
cd ..
#
tar -xjf essential-20041107.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
#
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
#
tar -xjf phony-1.1.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
# change the word phoney with the name of your skin.
cp -r phony/* /usr/local/share/mplayer/Skin/default/
#
cp MPlayer-1.0pre6a/etc/* /usr/local/etc/mplayer/
#
cd ..
exit
# start your gmplayer program

```

You would then open a root terminal and ```
sudo sh mplayer.sh
```

I liked the [COLOR=Blue]phoney[/COLOR] skin instead of the [COLOR=Blue]Blue[/COLOR] skin, so I modified "[COLOR=Indigo]disposable[/COLOR]"'s script accordingly.

I leave getting the dvd codecs (and everything else) up to you.

---------------------------------------------------------------------------------------------------------

Now let's put it in the menu:

Applications -> Media -> (go to the right pane, right click) -> Entire Menu -> Add New Item To This Menu -> 
Name: [COLOR=Red]MPlayer[/COLOR]
Generic Name: [COLOR=Red]Media Player[/COLOR]
Comment:
Command: [COLOR=Red]/usr/local/bin/gmplayer[/Color]

Hit the "[COLOR=Red]No Icon[/COLOR]" button
Find the "[COLOR=Red]media-player-48.png[/COLOR]" picture, select it, hit the "[COLOR=Red]OK[/COLOR]" button.
Hit the "[COLOR=Red]OK[/COLOR]" button

---

### Post by Perfect Storm on 2005-01-02
Running the latest mplayer, and there is remarkable changes from MPlayer-1.0pre5.tar.bz2 to MPlayer-1.0pre6a.tar.bz2 so it's advisble to try it out :)

Perhaps someone wanna make a new HOWTO: Multimedia so we can get it up to date, as it seems the original maker of this thread isn't updating it.


.:=The AI Dude=:.

---

### Post by wallijonn on 2005-01-02
Whenever I look at a thread I always go to the end of the thread after reading the front page to see what the updated code looks like, then work my way back a page or two.

So if you run the script and it doesn't work, update it accordingly and put it at the end. 

So far I ran the script and everything installed correctly (see the note concerning the 24001108.tar.bz2 file extraction problem).

When it exited it started up MPlayer.

So, how do we test this puppy?

I inserted a DVD, it opened the DVD window, I closed that window, started up MPlayer and it plays the DVD with sound. I had the dvdcodecs installed from my xine installation when I installed xine-ui through SPM. Xine was a lot easier to install.  

The movie, "The One" played fine but when I inserted "Thunderbirds" it says "Couldn't find matching filter/ao format!"

I do notice that Xine will take me to the full menu choice screen but Mplayer starts to play the movie right away; it bypasses the Menu Screen.
.

---

### Post by wallijonn on 2005-01-02
The "5" version works better ("Thunderbirds Are Go" plays fine - no "bad audio").

Here is the shell script:
```

mkdir mplyr
cd mplyr
#
apt-get install manpages-dev automake autoconf libtool flex bison gcc-doc g++ x-window-system-dev libgtk1.2-dev libpng12-dev -y
#
# get mplayer program
wget http://www1.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre5try2.tar.bz2
#
# get codecs
wget http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20041107.tar.bz2
#
# get fonts
wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2 
#
# get skin 
wget http://ftp5.mplayerhq.hu/mplayer/Skin/phony-1.1.tar.bz2 
#
# Mplayer install
tar -xjf MPlayer-1.0pre5try2.tar.bz2
cd MPlayer-1.0pre5try2
./configure --enable-gui
make
make install
#
cd ..
tar -xjf essential-20041107.tar.bz2
mkdir -p /usr/local/lib/codecs
cp essential-20041107/* /usr/local/lib/codecs/
#
tar -xjf font-arial-iso-8859-1.tar.bz2
cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
#
tar -xjf phony-1.1.tar.bz2
mkdir -p /usr/local/share/mplayer/Skin/default
cp -r phony/* /usr/local/share/mplayer/Skin/default/
#
cp MPlayer-1.0pre5try2/etc/* /usr/local/etc/mplayer/
#
cd ..
gmplayer
exit

```

---

### Post by monkey89 on 2005-01-15
Looking at the previous scripts, don't the essential codecs have to be installed before mplayer?  Otherwise, it doesn't detect them.

I had to do ./configure --enable-gui --with-codecsdir=/usr/local/lib/codecs after they were extracted to get them to be detected.  I also added --prefix=/usr, just my personal preference.  

I'm compiling the latest version now, we'll see how it goes.

---

### Post by r0nin on 2005-01-16
Thanks for the guide! All the software works and I can watch all movies I through at mPlayer. But is there a way to tweak the imagequality? Under Windows (with FFDShow) the movies are much smoother and not as grainy as under Ubuntu. 
Any ideas?

I've got an nVidia Gefore3Ti200 card and read somewhere that nVidia cards don't have particulary imagequality under Linux - Is this true?

---

### Post by midnightfxgt on 2005-01-22
Hey guys,

I am VERY new to the linux world, and find this site great.  it seems as though I cant get to the following link: 

$ wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)

Is there an alternate site?

Thanks
~JOHN

---

### Post by Perfect Storm on 2005-01-22
Hi there, it's because there's a new version of that file (presumable). 

Perhaps you should look here: [http://www.ubuntuforums.org/showthread.php?t=9850](http://www.ubuntuforums.org/showthread.php?t=9850)
Or you could look at Mplayer's homepage, I think it's mplayer.org




.:=The AI Dude=:.

---

### Post by Ste on 2005-01-22
[QUOTE=Artificial Intelligence]Hi there, it's because there's a new version of that file (presumable). 

Perhaps you should look here: [http://www.ubuntuforums.org/showthread.php?t=9850](http://www.ubuntuforums.org/showthread.php?t=9850)
Or you could look at Mplayer's homepage, I think it's mplayer.org




.:=The AI Dude=:.[/QUOTE]
 Close ;)

[http://www.mplayerhq.hu/homepage/design7/news.html](http://www.mplayerhq.hu/homepage/design7/news.html)

---

### Post by Perfect Storm on 2005-01-22
Ah well, I can't be right everytime  :mrgreen:

---

### Post by ctt1wbw on 2005-01-24
Well, being a total newb to Linux and the bash, I followed the instructions and got MPlayer and XMML working.  I got Bittorrent working.  I love these forums here.  Thanks for the tips and how-to's, they work.

If you are a newb, don't hesitate to follow the instructions.  These guys know what they are doing.  These guys are great!  Thanks!  I'm *THIS* close to erasing my XP partion.  

BTW, this reminds me.  Can I erase the XP partition and format it to a Linux partition and give it all to the Ubuntu partition without screwing anything up?

And how about Seti at Home?  I haven't tried that yet.  Any tutorials on how to get that up and running?

---

### Post by ctt1wbw on 2005-01-24
Okay, I just download the newest version, Pre6 release.  How can I update MPLayer without going through the entire section how-to on the first page of this thread?  That's what I did and unfortunately I didn't look at the last page to see if it was updated.  DVD won't play on MPlayer now...  :)

---

### Post by ctt1wbw on 2005-01-24
Would I just retype these commands as root:

 Time to compile MPlayer. Issue these commands.

$ tar -xjf MPlayer-1.0pre5.tar.bz2
$ cd MPlayer-1.0pre5
$ ./configure --enable-gui
$ make
$ sudo make install

---

### Post by ctt1wbw on 2005-01-24
Okay, well, under the version of MPlayer that I got, I got the video portion of a DVD to come up, but the audio won't.  I keep getting this error:

"Can't open audio device /dev/dsp" doesn't exit.

Me is confused now...  :)

---

### Post by Xappe on 2005-01-24
when running the ./configure, does it find any esd? if not, try to install the libesd0-dev package and redo your config/make...then change to esd sound output in the MPlayer preferences...

---

### Post by ctt1wbw on 2005-01-24
I just installed the newest version and ran it again.  Still no audio, and now a different error message:

"Couldn't find matching filter/ao format"

What should I do now?

Oh, and I already downloaded and installed that file you just mentioned.

---

### Post by ctt1wbw on 2005-01-24
[QUOTE=Xappe]when running the ./configure, does it find any esd? if not, try to install the libesd0-dev package and redo your config/make...then change to esd sound output in the MPlayer preferences...[/QUOTE]


What is esd sound output?

---

### Post by hardcandy on 2005-01-24
Enlightened sound deamon, supposed to allow several sounds streams to take place at the same time. It is part of the Gnome project. KDE equivalent is aRts.

---

### Post by ctt1wbw on 2005-01-24
I can't find out how to enable that.  I think that's the thing holding back audio in MPlayer.

---

### Post by ctt1wbw on 2005-01-24
Okay, I rebooted and then ran MPlayer again.  This time I'm getting this error:

"Could not open/initialize audio device -> no sound"

Should I reinstall the codecs?

---

### Post by ctt1wbw on 2005-01-24
Well, I reinstalled the codecs anyway then rebooted the computer and I'm still getting this "no sound" error.  I don't really know where to look now...

Someone please get me set up straight here!   :D

---

### Post by Perfect Storm on 2005-01-24
This is a shot and this is what I read on another forum: Try to reinstall alsa-base and alsa-headers

---

### Post by ctt1wbw on 2005-01-24
Well, thanks anyway.  I did that and then rebooted and still get the same error about no sound...   :confused:

---

### Post by ctt1wbw on 2005-01-25
Here's my list of pci ports:

I see my multimedia audio controller, but I am not too sure yet how to find out if the codec is installed, or where to get it.  Is that probably the reason...?

root@WaynesWorld:/home/ctt1wbw # lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB (ICH4) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB (ICH4) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB (ICH4) USB UHCI #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BAM/CAM PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB (ICH4) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go 5200] (rev a1)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:02:03.0 Network controller: Intel Corp. Intel(R) PRO/Wireless 2200BG (rev 05)
root@WaynesWorld:/home/ctt1wbw #

---

### Post by ctt1wbw on 2005-01-26
Okay, I download the .deb package of the w32codecs.  I tried dpkg -i packagename but what other commands are after that?

---

### Post by Rule on 2005-01-26
nothing :)

---

### Post by ctt1wbw on 2005-01-26
Huh, that's weird.  This is what I typed:

root@WaynesWorld:/home/ctt1wbw # cd /home/ctt1wbw/Downloads
root@WaynesWorld:/home/ctt1wbw/Downloads # dpkg -i w32codecs_20040916-0.0_i386.deb
(Reading database ... 90413 files and directories currently installed.)
Preparing to replace w32codecs 1:20040916-0.0 (using w32codecs_20040916-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20040916-0.0) ...


And then nothing...  I was expecting fireworks or something.  Oh well.   :smile:

---

### Post by Rule on 2005-01-27
[QUOTE=ctt1wbw]
And then nothing...  I was expecting fireworks or something.  Oh well.   :smile:[/QUOTE]

[IMG]http://www.ruidoso.net/visitors/images/fireworks.jpg[/IMG] 
there ya go :D

---

### Post by ctt1wbw on 2005-01-27
I got a warm and fuzzy now!  Thanks!   :)

---

### Post by ctt1wbw on 2005-01-27
Well, I got the MPlayer plugin working for Mozilla and Firefox!  Thanks for the help!  But I still don't have sound!!!  argh!!!!   :)

---

### Post by andradelipe on 2005-01-27
[QUOTE=ctt1wbw]Well, I got the MPlayer plugin working for Mozilla and Firefox!  Thanks for the help!  But I still don't have sound!!!  argh!!!!   :)[/QUOTE]
 Os pacotes a seguir têm dependências desencontradas:
  libpng12-dev: Depende: libpng12-0 (= 1.2.5.0-7) mas 1.2.5.0-7ubuntu1 está para ser instalado
E: Pacotes quebrados

I'm having some problem with this package, and cant't install it..
please, someone tell me what's going on

---

### Post by bnutting on 2005-01-27
Is there a reason that people need to go through all this extra effort to get multimedia working when other distrobutions do it automagicly? (Mepis for example)

I hope the with the next release most of this would be taken care of.

Just my $.02

Bryan

---

### Post by mattack on 2005-01-27
when following the instructions on the very first post, i get to .configure --enable-gui and get the following error (after it checks for a whole lot of stuff)
```
Checking for GTK version ...
Error: The GUI requires GTK devel packages (which were not found).
```

Me = total n00b. 
What are the GTK devel packages, and how should I install them?
I looked in Synaptic but nothing looks obvious...

*edit
Nevermind...  I figured it out...  :grin:

---

### Post by Jad on 2005-01-27
Thats great 
one question if may I
I have encountered a problem on NLD 9.2, Suse 9.1, And mandrake 9, 10
which is when you install more than one audio/vedio player a conflict will happen.

is it the same on Ubuntu ?

---

### Post by ctt1wbw on 2005-01-27
[QUOTE=bnutting]Is there a reason that people need to go through all this extra effort to get multimedia working when other distrobutions do it automagicly? (Mepis for example)

I hope the with the next release most of this would be taken care of.

Just my $.02

Bryan[/QUOTE]

Well some multimedia apps are there, but the one I hear the most and best about is not, MPlayer.  This crap is driving me nuts with the no audio errors I keep getting.  I've tried every combo of audio driver I can think of.

---

### Post by mattack on 2005-01-27
Looks like I got mplayer *and* the plug-in working!  
Thanks! :)

---

### Post by ctt1wbw on 2005-01-27
You got audio? :-P

---

### Post by mattack on 2005-01-28
[QUOTE=ctt1wbw]You got audio? :-P[/QUOTE]
yup.  no problems at all here...   ;)

---

### Post by ctt1wbw on 2005-01-28
Dammit, Jim!   :-D

---

### Post by ctt1wbw on 2005-01-28
Tell me please!  What is your preferrences set to for audio?

---

### Post by philip41 on 2005-01-28
For the life of me i cannot get the MPlayer to install, i have followed the insructions, i have d/loaded and updated where told.

I have tried with the pre5, pre6, pre6a all to noavail.

As soon as i type phil@ubuntu:~/MPlayer-1.0pre5 $ ./configure --enable-gui , i get the following screen.

[HTML]phil@ubuntu:~/MPlayer-1.0pre5 $ ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 3.3.5, ok
Checking for CPU vendor ... AuthenticAMD (6:8:1)
Checking for CPU type ...  AMD Athlon(tm) XP 2600+
Checking for GCC & CPU optimization abilities ... athlon-4
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowex ... yes
Checking for kernel support of sse ... yes
Checking for mtrr support ... yes
Checking for assembler (as 2.15) ... ok
Checking for Linux kernel version ... 2.6.10-2-k7, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for i18n ... yes
Checking for setlocale() ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages: en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for nanosleep ... yes
Checking for socklib ... yes (using -lnsl)
Checking for inet_pton() ... yes (using -lnsl)
Checking for inttypes.h (required) ... yes
Checking for int_fastXY_t in inttypes.h ... yes
Checking for word size ... 32
Checking for stddef.h ... yes
Checking for malloc.h ... yes
Checking for memalign() ... yes
Checking for alloca.h ... yes
Checking for mman.h ... yes
Checking for dynamic loader ... yes
Checking for dynamic a/v plugins support ... no
Checking for pthread ... yes (using -lpthread)
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for BSDI dvd.h ... no
Checking for HPUX SCSI header ... no
Checking for userspace SCSI headers (Solaris) ... no
Checking for termcap ... no
Checking for termios ... yes (using sys/termios.h)
Checking for shm ... yes
Checking for linux devfs ... no
Checking for scandir() ... yes
Checking for strsep() ... yes
Checking for strlcpy() ... no
Checking for strlcat() ... no
Checking for fseeko() ... yes
Checking for localtime_r() ... yes
Checking for vsscanf() ... yes
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/X11R6/include)
Checking for X11 libs presence ... yes (using /usr/X11R6/lib)
Checking for X11 ... yes
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes
Checking for XvMC ... no
Checking for Xinerama ... no
Checking for Xxf86vm ... no
Checking for DGA ... no
Checking for OpenGL ... yes
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... no
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... yes
Checking for JPEG support ... no
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... no
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for JACK ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... no
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for OggVorbis support ... no
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libmpeg2 support ... yes
Checking for Matroska support (external 0.6.0 or later OR internal) ... yes, internal
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for FAAD2 version ... 2.0
Checking for MacOS X SHLB (shared lib) support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformatc (static) ... no
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for DivX4linux/DivX5linux/OpenDivX decore ... no
Checking for libmp3lame (for mencoder) ... no
Checking for DivX4linux encore (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for EDL support ... yes
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... no
Checking for Video 4 Linux 2 TV interface ... no
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for byte order ... Little Endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes
Checking for XShape extension ... yes
Checking for GTK version ... 1.2.10 (using gtk-config)
Checking for glib version ... 1.2.10 (using glib-config)
Creating Gui/config.mak
Checking for ftello() ... yes
Checking for VIDIX ... yes
Checking for joystick ... no
Checking for lirc ... no
Checking for lircc ... no
Creating config.mak
Creating config.h
Creating libvo/config.mak
Creating libao2/config.mak
Creating help_mp.h

Config files successfully generated by ./configure !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /usr/local/etc/mplayer

  Byte order: Little Endian
  Optimizing for: athlon-4 mmx mmx2 3dnow 3dnowex sse mtrr

  Languages:
    Messages/GUI: en
    Manual pages: en (no localization selected, use --language=all)

  Enabled optional drivers:
    Input: ftp network edl tv matroska(internal) mpdvdkit2 vcd dvb
    Codecs: qtx libavcodec real xanim dshow/dmo win32 faad2(internal) libmpeg2 liba52 mp3lib
    Audio output: oss mpegpes(dvb)
    Video output: xvidix cvidix vesa png mpegpes(dvb) opengl xv x11 xover tga
  Disabled optional drivers:
    Input: tv-v4l2 tv-v4l tv-bsdbt848 live.com cdda dvdread smb
    Codecs: opendivx xvid libdv libtheora libvorbis libmad liblzo gif
    Audio output: sgi sun alsa jack esd arts dxr2 nas win32 sdl macosx
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx sdl gif89a jpeg fbdev svga caca aa ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx quartz

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/devices.html#mtrr)


Check configure.log if you wonder why an autodetection failed (check whether
the development headers/packages are installed).

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

phil@ubuntu:~/MPlayer-1.0pre5 $[/HTML]

---

### Post by philip41 on 2005-01-28
When i type "make" the next step i get all this below.

[HTML]so -o cyberblade_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -o radeon_vid.o radeon_vid.c
cc -shared radeon_vid.o -L../../libdha -ldha -lm -lGL  -lXv    -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl -Wl,-soname,radeon_vid.so -o radeon_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -DRAGE128 -o rage128_vid.o radeon_vid.c
cc -shared rage128_vid.o -L../../libdha -ldha -lm -lGL  -lXv    -L/usr/X11R6/lib  -lXext -lX11 -lnsl -lnsl -Wl,-soname,rage128_vid.so -o rage128_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -DRAGE128 -o mach64_vid.o mach64_vid.c
cc -shared mach64_vid.o -L../../libdha -ldha -Wl,-soname,mach64_vid.so -o mach64 _vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I..  -o nvidia_vid.o nvidia_vid.c
cc -shared nvidia_vid.o -L../../libdha -ldha -lm -Wl,-soname,nvidia_vid.so -o nv idia_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -o mga_vid.o mga_vid.c
cc -shared mga_vid.o -L../../libdha -ldha -lm -Wl,-soname,mga_vid.so -o mga_vid. so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -DCRTC2 -o mga_crtc2_vid.o mga_vid.c
cc -shared mga_crtc2_vid.o -L../../libdha -ldha -lm -Wl,-soname,mga_crtc2_vid.so  -o mga_crtc2_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -o pm3_vid.o pm3_vid.c
cc -shared pm3_vid.o -L../../libdha -ldha -Wl,-soname,pm3_vid.so -o pm3_vid.so
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -o sis_vid.o sis_vid.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fPIC -I. -I.. -o sis_bridge.o sis_bridge.c
cc -shared sis_vid.o sis_bridge.o -L../../libdha -ldha -Wl,-soname,sis_vid.so -o  sis_vid.so
make[2]: Leaving directory `/home/phil/MPlayer-1.0pre5/vidix/drivers'
make[1]: Leaving directory `/home/phil/MPlayer-1.0pre5/vidix'
make -C libmpdvdkit2
make[1]: Entering directory `/home/phil/MPlayer-1.0pre5/libmpdvdkit2'
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o css.o css.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o device.o device.c[/html]

---

### Post by philip41 on 2005-01-28
And here is the rest of the "make " progress output.
[html]
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o dvd_input.o dvd_input.c
dvd_input.c: In function `DVDInputSetup':
dvd_input.c:129: warning: assignment from incompatible pointer type
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o dvd_reader.o dvd_reader.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o dvd_udf.o dvd_udf.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o error.o error.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o ifo_print.o ifo_print.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o ifo_read.o ifo_read.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o ioctl.o ioctl.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o libdvdcss.o libdvdcss.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o nav_print.o nav_print.c
cc -I. -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=a thlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib /glib/include -DHAVE_MPLAYER -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/u sr/lib/glib/include -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -c -o nav_read.o nav_read.c
ar rc libmpdvdkit.a css.o device.o dvd_input.o dvd_reader.o dvd_udf.o error.o if o_print.o ifo_read.o ioctl.o libdvdcss.o nav_print.o nav_read.o
true libmpdvdkit.a
make[1]: Leaving directory `/home/phil/MPlayer-1.0pre5/libmpdvdkit2'
make -C Gui
make[1]: Entering directory `/home/phil/MPlayer-1.0pre5/Gui'
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o wm/ws.o wm/ws.c
../postproc/rgb2rgb.h:133: warning: `yuv2rgb' defined but not used
../postproc/rgb2rgb.h:137: warning: `yuv2rgb_init' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o wm/wsxdnd.o wm/wsxdnd.c
wm/wsxdnd.c: In function `wsXDNDProcessSelection':
wm/wsxdnd.c:71: warning: dereferencing type-punned pointer will break strict-ali asing rules
wm/wsxdnd.c: In function `wsXDNDProcessClientMessage':
wm/wsxdnd.c:170: warning: dereferencing type-punned pointer will break strict-al iasing rules
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o app.o app.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o interface.o interface.c
interface.c: In function `guiLoadFont':
interface.c:415: warning: dereferencing type-punned pointer will break strict-al iasing rules
interface.c: In function `guiGetEvent':
interface.c:597: warning: implicit declaration of function `vcd_seek_to_track'
interface.c:833: warning: dereferencing type-punned pointer will break strict-al iasing rules
interface.c: In function `gtkSet':
interface.c:1039: warning: dereferencing type-punned pointer will break strict-a liasing rules
interface.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o cfg.o cfg.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o bitmap.o bitmap.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o skin/skin.o skin/skin.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o skin/font.o skin/font.c
skin/font.c: In function `fntRender':
skin/font.c:151: warning: unused variable `tmp'
skin/font.c:155: warning: unused variable `s'
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o skin/cut.o skin/cut.c
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/widgets.o mplayer/widgets.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/play.o mplayer/play.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/mw.o mplayer/mw.c
mplayer/mw.c: In function `mplMainDraw':
mplayer/mw.c:53: warning: unused variable `item'
mplayer/mw.c:54: warning: unused variable `image'
mplayer/mw.c:55: warning: unused variable `i'
mplayer/mw.c:55: warning: unused variable `type'
mplayer/mw.c: In function `mplEventHandling':
mplayer/mw.c:82: warning: unused variable `j'
mplayer/mw.c: In function `mplDandDHandler':
mplayer/mw.c:551: warning: dereferencing type-punned pointer will break strict-a liasing rules
mplayer/mw.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/sw.o mplayer/sw.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/menu.o mplayer/menu.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/pb.o mplayer/pb.c
mplayer/pb.c: In function `mplPBInit':
mplayer/pb.c:220: warning: dereferencing type-punned pointer will break strict-a liasing rules
mplayer/pb.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/common.o mplayer/common.c
mplayer/common.c: In function `TranslateFilename':
mplayer/common.c:50: warning: suggest parentheses around assignment used as trut h value
mplayer/common.c: In function `PutImage':
mplayer/common.c:188: warning: unused variable `yc'
mplayer/common.c: In function `Render':
mplayer/common.c:245: warning: unused variable `type'
mplayer/common.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/menu.o mplayer/gtk/menu.c
mplayer/gtk/menu.c: In function `create_PopUpMenu':
mplayer/gtk/menu.c:291: warning: `N' might be used uninitialized in this functio n
mplayer/gtk/menu.c:291: warning: `D' might be used uninitialized in this functio n
mplayer/gtk/menu.c:291: warning: `F' might be used uninitialized in this functio n
mplayer/gtk/menu.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/mb.o mplayer/gtk/mb.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/about.o mplayer/gtk/about.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/pl.o mplayer/gtk/pl.c
mplayer/gtk/pl.c: In function `HidePlayList':
mplayer/gtk/pl.c:180: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/pl.c:180: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/pl.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/sb.o mplayer/gtk/sb.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/fs.o mplayer/gtk/fs.c
mplayer/gtk/fs.c: In function `ShowFileSelect':
mplayer/gtk/fs.c:316: warning: unused variable `hist'
mplayer/gtk/fs.c: In function `fs_Ok_released':
mplayer/gtk/fs.c:504: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/fs.c: In function `create_FileSelect':
mplayer/gtk/fs.c:557: warning: unused variable `FSFrame'
mplayer/gtk/fs.c:558: warning: unused variable `frame2'
mplayer/gtk/fs.c:559: warning: unused variable `frame3'
mplayer/gtk/fs.c:560: warning: unused variable `frame4'
mplayer/gtk/fs.c:564: warning: unused variable `hseparator1'
mplayer/gtk/fs.c:567: warning: unused variable `label1'
mplayer/gtk/fs.c:568: warning: unused variable `hseparator2'
mplayer/gtk/fs.c:569: warning: unused variable `hseparator3'
mplayer/gtk/fs.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/opts.o mplayer/gtk/opts.c
mplayer/gtk/opts.c: In function `prButton':
mplayer/gtk/opts.c:559: warning: dereferencing type-punned pointer will break st rict-aliasing rules
mplayer/gtk/opts.c:609: warning: dereferencing type-punned pointer will break st rict-aliasing rules
mplayer/gtk/opts.c:610: warning: dereferencing type-punned pointer will break st rict-aliasing rules
mplayer/gtk/opts.c: In function `create_Preferences':
mplayer/gtk/opts.c:1179: warning: implicit declaration of function `get_video_qu ality_max'
mplayer/gtk/opts.c:767: warning: unused variable `hbuttonbox2'
mplayer/gtk/opts.c:775: warning: unused variable `hbox3'
mplayer/gtk/opts.c:779: warning: unused variable `Font_group'
mplayer/gtk/opts.c:780: warning: unused variable `CBFontEncoding_items'
mplayer/gtk/opts.c: In function `ossButton':
mplayer/gtk/opts.c:1344: warning: dereferencing type-punned pointer will break s trict-aliasing rules
mplayer/gtk/opts.c:1345: warning: dereferencing type-punned pointer will break s trict-aliasing rules
mplayer/gtk/opts.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/url.o mplayer/gtk/url.c
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/eq.o mplayer/gtk/eq.c
mplayer/gtk/eq.c: In function `eqSetBands':
mplayer/gtk/eq.c:71: warning: implicit declaration of function `get_video_colors '
mplayer/gtk/eq.c: In function `ecButtonReleased':
mplayer/gtk/eq.c:543: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/eq.c:544: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/eq.c:545: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/eq.c:546: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/eq.c:547: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/eq.c:548: warning: dereferencing type-punned pointer will break stri ct-aliasing rules
mplayer/gtk/eq.c: At top level:
../libvo/font_load.h:93: warning: `render_one_glyph' defined but not used
../libvo/font_load.h:94: warning: `kerning' defined but not used
cc -c -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=at hlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE - D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/ glib/include -fexpensive-optimizations -fschedule-insns2 -Wall -I. -I../loader - I./wm -I./skin  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/i nclude -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  - DDEBUG  -o mplayer/gtk/common.o mplayer/gtk/common.c
rm -f libgui.a
ar rc libgui.a wm/ws.o wm/wsxdnd.o app.o interface.o cfg.o bitmap.o skin/skin.o skin/font.o skin/cut.o mplayer/widgets.o mplayer/play.o mplayer/mw.o mplayer/sw. o mplayer/menu.o mplayer/pb.o mplayer/common.o mplayer/gtk/menu.o mplayer/gtk/mb .o mplayer/gtk/about.o mplayer/gtk/pl.o mplayer/gtk/sb.o mplayer/gtk/fs.o mplaye r/gtk/opts.o mplayer/gtk/url.o mplayer/gtk/eq.o mplayer/gtk/common.o
true libgui.a
make[1]: Leaving directory `/home/phil/MPlayer-1.0pre5/Gui'
cc -I../libvo -I../../libvo -I/usr/X11R6/include -O4 -march=athlon-4 -mcpu=athlo n-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_F ILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/gli b/include -Ilibmpdemux -Iloader -Ilibvo  -I/usr/include/gtk-1.2 -I/usr/include/g lib-1.2 -I/usr/lib/glib/include   -I/usr/X11R6/include       -o mplayer mplayer. o mp_msg.o cpudetect.o codec-cfg.o spudec.o playtree.o playtreeparser.o asxparse r.o vobsub.o subreader.o sub_cc.o find_sub.o m_config.o m_option.o parser-cfg.o m_struct.o unrarlib.o mixer.o parser-mpcmd.o libvo/libvo.a libao2/libao2.a  vidi x/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a mp3lib/libMP3.a liba52/liba5 2.a libmpeg2/libmpeg2.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dm o/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a input/libinput.a postpro c/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec. a          -lpng -lz -lz         -lnsl        libfaad2/libfaad2.a  -L/usr/lib -L /usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm  -L/usr/lib -lglib  -lGL  -lXv    -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl             -lpthread -ldl -rdynamic   -lm
/usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
phil@ubuntu:~/MPlayer-1.0pre5 $[/HTML]

Would some kind soul have a browse, and tell what they see is wrong.

Thanks

Phil

---

### Post by ctt1wbw on 2005-01-30
It works!!!  It works!!!  Holy crap, it took me two weeks, but I got it working!!!  I was missing some extra files, alsa-oss for one, downloaded and compiled and then recompiled MPlayer and now it works!!!

ATTENTION NEWBIES:  Linux is great, is NOT that hard.  If I  can figure it out, anyone can.  Just make sure you use concise responses when you tell people your problems.  :)

---

### Post by rapala61 on 2005-01-30
[QUOTE=ctt1wbw]It works!!!  It works!!!  Holy crap, it took me two weeks, but I got it working!!!  I was missing some extra files, alsa-oss for one, downloaded and compiled and then recompiled MPlayer and now it works!!!

ATTENTION NEWBIES:  Linux is great, is NOT that hard.  If I  can figure it out, anyone can.  Just make sure you use concise responses when you tell people your problems.  :)[/QUOTE]



 :)  did u update ur how to with this???.. i mean.. with the way u managed to make it work?

---

### Post by ctt1wbw on 2005-01-30
No, but I found a file called alsa-oss that I didn't have.  I downloaded that via synaptic, installed it and then rebooted.  Then I had to recompile and install MPlayer, then rebooted.  And it worked.

Also, I followed this thread:

[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)

I followed it to a T.  There's also someone down the thread that resolved some static issues.  I followed that as well.  Now all is perfecto!  :)

---

### Post by enquiry on 2005-02-15
[QUOTE=r0nin]Thanks for the guide! All the software works and I can watch all movies I through at mPlayer. But is there a way to tweak the imagequality? Under Windows (with FFDShow) the movies are much smoother and not as grainy as under Ubuntu. 
Any ideas?

I've got an nVidia Gefore3Ti200 card and read somewhere that nVidia cards don't have particulary imagequality under Linux - Is this true?[/QUOTE]
What you do is you add the following lines to XF86Config-4, under Section "Device" :```
	Option		"UseInternalAGPGART" 	"no"
	Option		"RenderAccel" 		"true"
	Option		"VideoOverlay"		"on"
```
Given you have installed a driver for your nVidia card, and you are using the xv driver for MPlayer (which is the default), this should work great. nVidia cards have good drivers for GNU/Linux (unlike ATI).

---

### Post by nocturn on 2005-02-16
[QUOTE=enquiry]What you do is you add the following lines to XF86Config-4, under Section "Device" :```
	Option		"UseInternalAGPGART" 	"no"
	Option		"RenderAccel" 		"true"
	Option		"VideoOverlay"		"on"
```
Given you have installed a driver for your nVidia card, and you are using the xv driver for MPlayer (which is the default), this should work great. nVidia cards have good drivers for GNU/Linux (unlike ATI).[/QUOTE]


What do these options do?
Option		"UseInternalAGPGART" 	"no"
Option		"VideoOverlay"		"on"

I am using the Nvidia AGP driver (nvAGP) because AGPGART was slow.

---

### Post by enquiry on 2005-02-16
[QUOTE=nocturn]What do these options do?
Option		"UseInternalAGPGART" 	"no"
Option		"VideoOverlay"		"on"

I am using the Nvidia AGP driver (nvAGP) because AGPGART was slow.[/QUOTE]
The line *Option "UseInternalAGPGART" "no"* is an instuction to use the external AGP Gart, which is usually faster than the internal.

The line *Option "VideoOverlay" "on"* enables Video Overlay for the Xv extension.

---

### Post by espee on 2005-02-23
Great write up!
I got one error though: 

when trying to download 
wget [http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/re...0040922.tar.bz2)
I got a 404 file does not exist. What worked is:

wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050216.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050216.tar.bz2)
It looks like they change the essential codecs every now and then!

---

### Post by ZuLuuuuuu on 2005-02-27
Hi, I followed the instructions but at this point:

 $ ./configure --enable-gui

I have an error which says I have a bad gcc version. I have installed gcc 2.95 using Synaptic but didn't uninstall the version I have (which version I have I don't know but I think 3.3 because it was checked in Synaptic) because it says that nearly 800 mb of data (included 3 important file) will be deleted! How can I solve this problem?

---

### Post by Stefan_hb on 2005-03-05
[QUOTE=disposable]I've found it much more convenient to write a Perl script that uses MPlayer to stream my favorite music.[/QUOTE]
Great idea, thank you.
I transformed this into a "gui" version, using zenity:
```

#!/bin/bash
# Radio.sh

VAR_RADIO=$(zenity --title "Webradio" --width 150 --height 200 --list --column "Please choose a channel:"  Raute_Extreme Raute_Mainstream Amped_Out)


############################

 if [ $VAR_RADIO = Raute_Extreme ]; then
   mplayer http://extremestream.musik-radio.org:10000 &
   zenity --info --text "Now playing: '$VAR_RADIO'"
   killall mplayer
   sh ~/bin/Radio.sh
       exit 0
    fi

################################
 if [ $VAR_RADIO = Raute_Mainstream ]; then
mplayer http://mainstream.musik-radio.org:8000 &
   zenity --info --text "Now playing: '$VAR_RADIO'"
   killall mplayer
   sh ~/bin/Radio.sh
       exit 0
    fi
############################

 if [ $VAR_RADIO = Amped_Out ]; then
mplayer http://216.218.254.98:9230 &
   zenity --info --text "Now playing: '$VAR_RADIO'"
   killall mplayer
   sh ~/bin/Radio.sh
       exit 0
    fi
```
Just copy this to ~/bin .
Here's a list of other stations:
[http://mainstream.musik-radio.org:8000](http://mainstream.musik-radio.org:8000)
[http://clubstream.musik-radio.org:9000](http://clubstream.musik-radio.org:9000)
[http://extremestream.musik-radio.org:10000](http://extremestream.musik-radio.org:10000)
[http://jamstream.musik-radio.org:12000](http://jamstream.musik-radio.org:12000)

rant
[http://130.240.207.88:9090](http://130.240.207.88:9090)
[http://24.207.26.60:8888](http://24.207.26.60:8888)
[http://130.243.43.95:8888](http://130.243.43.95:8888)

amped out
[http://216.218.254.98:9230](http://216.218.254.98:9230)
[http://64.202.98.51:7090](http://64.202.98.51:7090)

Radio Morituri Te Salutant
[http://80.237.204.93:8000](http://80.237.204.93:8000)

Radio Ghoul School
[http://69.57.161.20:9998](http://69.57.161.20:9998)
--- 
Cheers
 Stefan

---

### Post by Jad on 2005-03-06
cool man

---

### Post by orvalax on 2005-03-10
I followed all your instrustions and it plays every video file that I have but it plays them all in slow motion. I'm not sure if I did anything wrong though. I even did it twice.

---

### Post by Lunde on 2005-07-01
Nice howto! Thanks

---

### Post by chr1s777 on 2005-09-14
mplayer works now, but I still cannot resize movies when using X11, although "zoom" is enabled in the mplayer configfile: 

> 
## MPlayer config file
##
## This file can be copied to /etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

vo=xv,			# To specify default video driver (see -vo help for
			    # list)

ao=alsa,		# To specify default audio driver (see -ao help for
			      # list)

fs=no			# Enlarges movie window to your desktop's size.
			    # Used by drivers: all

vm=no			# Tries to change to a different videomode
			     # Used by drivers: dga2, x11, sdl

bpp=0		  # Force changing display depth.
			# Valid settings are: 0, 15, 16, 24, 32
			# may need 'vm=yes' too.
			# Used by drivers: fbdev, dga2, svga

zoom=yes		# Enable software scaling (powerful CPU needed)
			        # Used by drivers: svga, aalib

double=yes		# use double-buffering (recommended for xv with
			        # SUB/OSD usage)

# x=800			# scale movie to <x> pixels width
# y=600			# scale movie to <y> pixels height

osdlevel=1		# don't display OSD at stratup

monitoraspect=4:3	# standard monitor size, with square pixels
# monitoraspect=16:9	# use this for widescreen monitor! non-square pixels

cache = 1024		# Disk cache 1 MB

##
## Specify your preferred default skin here
## (skins are searched in /usr/share/mplayer/Skin/yourskin
##  and ~/.mplayer/Skin/yourskin)
##

skin = default


##
## Multiple languages are available :)
##
## Hungarian	igen	nem
## English	yes	no
## German	ja	nein
## Spanish	si	no
## Binary	1	0
##
## You can also use spaces and/or tabs.
##

#sound		= 1
#nosound	= nein
#mixer		= /dev/mixer

##
## resample the fonts' alphamap
## 0	plain white fonts
## 0.75	very narrow black outline (default)
## 1	narrow black outline
## 10	bold black outline
##

#ffactor = 0.75

##
## FBdev driver: 

# fb = /dev/fb0				# framebuffer device to use
# fbmode = 640x480-120			# use this mode (read from fb.modes!)
# fbmodeconfig = /etc/fb.modes		# the fb.modes file

## VESA and FBdev driver: specify your monitor's timings
## 
## (see for example /etc/X11/XF86Config for timings!)
## ** CAUTION! IF YOUR DISPLAY DOESN'T SUPPORT AUTOMATICALLY TURNING OFF WHEN
##    OVERDRIVED (AND EVEN IF IT DOES), THIS MAY CAUSE DAMAGE TO YOUR DISPLAY!
##    WE AREN'T RESPONSIBLE, IT'S YOUR DECISION! **
##
## k, K : means multiply by 1000
## m, M : means multiply by 1.000.000
##
# monitor_hfreq = 31.5k-50k,70k		# horizontal frequency range
# monitor_vfreq = 50-90			# vertical frequency range
# monitor_dotclock = 30M-300M		# dotclock (or pixelclock) range

##
## SDL driver
##

# vo = sdl:aalib	# use SDL video driver by default
			# use "vo = sdl:aalib" or "vo sdl:dga" and so on,
			# for specifying SDL subdrivers
# ao = sdl:esd		# use SDL audio driver by default
			# use "ao = sdl:esd" to use SDL's ESD driver
# noxv = no		# whether to use XVideo hardware acceleration or not
# forcexv = yes		# force XVideo even if not detected

##
## Other (preferred to be default from configfile) switches
##

framedrop=no		# drop frames, when not in sync (slow CPU, videocard,
			# etc)

#vfm=ffmpeg		# use FFmpeg's libavcodec video codec family
			# See "mplayer -vfm help" for all available codecs

#bps=yes		# use this method for playing AVIs (if have problems,
			# try removing this)

# slang= en		# DVD : display english subtitles if available
# alang= en		# DVD : play english audio tracks if available

## This is the correct way to use "subconfig" type options in the
## configuration file. In the command line you use :
## -aop list=resample:fout=44100 , but here it is :
# aop=list=resample:fout=44100

# From Fedora
# the default mpeg audio decoder is currently broken, let's try libmad
# first:
afm=libmad

# get a default OSD font from fontconfig
#fontconfig = yes
#font = "Sans"
#subfont-text-scale = 3


Any ideas...??

---

### Post by aljones15 on 2005-09-17
> **disposable]** UPDATED **
 Per post: [http://ubuntuforums.org/showpost.php?p=7156&postcount=48](http://ubuntuforums.org/showpost.php?p=7156&postcount=48)
 
 // Ubuntu Multimedia HOWTO
 //
 // by Disposable
 //
 // [http://www.oldskoolphreak.com]("http://www.oldskoolphreak.com")
 
 
 Introduction
 ------------
 "Will Warty Warthog / Ubuntu include complete multimedia support?"
 
 Ubuntu Linux [1] is a Debian-based, desktop Linux distribution whose name
 means "humanity to others."  The philosophy behind this GNU/Linux
 distribution and the great selection of packages make you feel good that
 you're using it.  The lack of multimedia support, however, leaves your
 digital media desires unsated.
 
 "We're still working out some of the difficult legal / policy issues
 involved with multimedia support. Warty Warthog will include some
 multimedia support, we just need to find out what we can safely and freely
 do."
 
 This HOWTO details the installation and configuration of applications
 essential to your media enjoyment on Ubuntu.
 
 
 Update It
 ---------
 If you've installed Ubuntu, and you should have a fresh install for this
 HOWTO, then you're already familiar with its default use of sudo.  You'll
 be using sudo a lot.
 
 The first step towards an Ubuntu multimedia powerhouse is to make sure your
 box is up-to-date [2].
 
     $ sudo apt-get update
     $ sudo apt-get upgrade
     $ sudo apt-get dist-upgrade
 
 
 MPlayer
 -------
 It's time to grab all of the packages needed to install MPlayer.  MPlayer
 is the most versatile media player available for GNU/Linux - video, audio,
 X, no X - it very well may be the only player you'll need.  Let's start with
 gcc/g++ and other dependencies, and then grab the MPlayer source.
 
     $ sudo apt-get install manpages-dev
     $ sudo apt-get install autoconf
     $ sudo apt-get install automake
     $ sudo apt-get install libtool
     $ sudo apt-get install flex
     $ sudo apt-get install bison
     $ sudo apt-get install gcc-doc
     $ sudo apt-get install g++
     $ sudo apt-get install x-window-system-dev
     $ sudo apt-get install libgtk1.2-dev
     $ sudo apt-get install libpng-dev
 
 Have your Warty Warthog CD handy and accept any extra packages, e.g. the
 libtool install will also install gcc.  We'll use a US mirror for (most of)
 the MPlayer packages and assume you're working in your home directory.
 Download MPlayer, codecs, English fonts and the default blue skin.
 Internationalization and slick graphics are up to you.
 
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/MPlayer-1.0pre5.tar.bz2")
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20040922.tar.bz2")
     $ wget [http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2]("http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2")
     $ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2]("http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2")
 
 Using the README from mplayerhq.hu [3] as a baseline, install the codecs
 with the following commands.
 
     $ tar -xjf essential-20040922.tar.bz2
     $ sudo mkdir -p /usr/local/lib/codecs
     $ sudo cp essential-20040922/* /usr/local/lib/codecs/
 
 Time to compile MPlayer.  Issue these commands.
 
     $ tar -xjf MPlayer-1.0pre5.tar.bz2
     $ cd MPlayer-1.0pre5
     $ ./configure --enable-gui
     $ make
     $ sudo make install
 
 Now install the fonts and skin.
 
     $ cd
     $ tar -xjf font-arial-iso-8859-1.tar.bz2
     $ sudo cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
     $ tar -xjf Blue-1.4.tar.bz2
     $ sudo mkdir -p /usr/local/share/mplayer/Skin/default
     $ sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/
 
 Finally, copy over the included conf files.
 
     $ sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/
 
 Test your install by launching the graphical version of MPlayer.
 
     $ gmplayer
 
 QuickTime, WindowsMedia, MPEG, avi - you should be able to play just about
 anything.  Give yourself quick access to MPlayer by adding a launcher to
 the top GNOME panel.  Right click on the panel and click Add to Panel...
 Select Custom Application Launcher and click Add.  Use the following
 information and click OK.
 
     Name: MPlayer
     Command: /usr/local/bin/gmplayer
     Icon: /usr/local/share/mplayer/Skin/default/icons/32x32.png
 
 
 Playing DVDs
 ------------
 The Ubuntu Wiki discusses restricted formats [4], which include CSS and
 DVD playback.  To add DVD playback capability to Ubuntu, use your favorite
 text editor and add the following line to your /etc/apt/sources.list file.
 
     deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") unstable main
 
 Then sync your package index and grab the infamous DeCSS.
 
     $ sudo apt-get update
     $ sudo apt-get install libdvdcss2
 
 Add a dvd link and enjoy DVDs with MPlayer and Ubuntu.
 
     $ sudo ln -s /media/cdrom0 /dev/dvd
 
 
 XMMS
 ----
 With your video needs taken care of, we can move on the audio portion of
 our show by installing XMMS.
 
     $ sudo apt-get install libmikmod2
     $ sudo apt-get install xmms
 
 Logging out and logging back in will find XMMS already in the Applications/
 Multimedia menu.  And there it is - instant Ogg/mp3/jukebox/streaming audio
 goodness.
 
 
 A Little Perl
 -------------
 For streaming internet radio, you can of course use XMMS.  Set your
 preference in Firefox and you're good to go.  I listen to a few stations
 regularly, and I always have a gnome-term open.  With those things in mind,
 I've found it much more convenient to write a Perl script that uses MPlayer
 to stream my favorite music.
 
     ```
#!/usr/bin/perl -w
 
 	# mplay.pl -
 	# command line streaming of your fav stations
 	# usage: mplay <channel>
 
 	use strict said:**
> .
  
 
 References
 ----------
 [1] [http://www.ubuntulinux.org/]("http://www.ubuntulinux.org/")
 
 [2] I could not intuitively get Rhythmbox to play one simple Ogg file.  So
     my first step in setting up multimedia on Ubuntu is to sudo apt-get
     remove rhythmbox.
 
 [3] [http://www.mplayerhq.hu/DOCS/README]("http://www.mplayerhq.hu/DOCS/README")
 
 [4] [http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")
 
 [5] [http://www.theforce.net/theater/shortfilms/batman_deadend/]("http://www.theforce.net/theater/shortfilms/batman_deadend/")
 doesn't work for me.
apt-get install keeps saying

E: Package libxrender-dev has no installation candidate


etc.
have the debian marlliat sources listed and the key too, but still can't install this stuff.

peace,
a

---

### Post by cvmostert on 2005-12-20
thanx, im not such a mplayer fan, but i sorted out my totem problem...

was a symbolic link problem.... ln -s /media/cdrom /dev/dvd

ciao

---

### Post by emperor on 2005-12-20
[quote=chr1s777]mplayer works now, but I still cannot resize movies when using X11, although "zoom" is enabled in the mplayer configfile: 
Any ideas...??[/quote]

Set to mplayer video to "xv".

---

### Post by miahfost on 2005-12-20
Hot diggity! That was just what I was looking for! Works great! Thanks for the help! w00t!

---

### Post by Epperly on 2006-08-02
Should I toss Totem? :p

---

### Post by nexus_2006 on 2007-01-04
**EDIT:  Sorry about the post, didn't notice this forum is not for asking questions.  Could someone delete this post please?**

---

### Post by bio870 on 2007-05-15
> **GavinX said:**
> A great 'How To'. Rated as one of the very best that I have seen anywhere on the net. This article is really accessible, even to newbies of linux. You make Ubuntu as easy as eating good food!


[plants music build weather weather](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

