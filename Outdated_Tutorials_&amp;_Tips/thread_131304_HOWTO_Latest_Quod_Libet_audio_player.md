---
title: "HOWTO: Latest Quod Libet audio player"
date: 2006-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by HighPlainsDrifter on 2006-02-16
An oft overlooked audio player and musical organizing tool in the Ubuntu world is Quod Libet. Personally, it ranks as my favorite audio player, even over the sacred Rhythmbox :mrgreen:. Also, QL comes bundled with a VERY powerful tagging tool, called Ex Falso, which is invaluable when your music collection literally has thousands of songs across different formats :-D 

The Ubuntu repositories have an ancient version of the QL, and Google revealed an equally old .deb file. Knowing that Quod Libet was written in Python, I knew installation had to be easy as pie - it was!

First, open up a terminal (*Applications*->*Accessories*->*Terminal*) to grab the latest and greatest source from [Quod Libet's official web site]("http://www.sacredchao.net/quodlibet").

```
# wget http://www.sacredchao.net/~piman/software/quodlibet-0.17.1.tar.gz
```

Second, extract the gzipped tar file.

```
# tar xvzf quodlibet-0.17.1.tar.gz
```

Change into the directory that tar extracted the files to.
```
cd quodlibet-0.17.1
```

Before you go further, you will probably have to install *intltool*, an XML related series of scripts that QL's makefile depends on. You can learn more about intltool by running **apt-cache show intltool**.

```
sudo apt-get install intltool
```

Allow it to install the additional files, too. One more steps to go!

```
sudo make install
```

It is now installed. If you don't see Quod Libet in the Gnome menu, run **killall gnome-panel**

Enjoy your new music player \\:D/. And if you aren't satisfied with Quod Libet's features, then maybe you can [find a plugin]("http://www.sacredchao.net/quodlibet/wiki/Plugins") that does what you need!

One more IMPORTANT thing, for mp3 support, you need to install **python-pymad**, and for ogg **python-pyvorbis**

---

### Post by Lizzy on 2006-02-27
Hi, i'm a noob and want to figure out how to actually install the Cover Plugin... There's just a textfile about that plugin, which i don't know what to do with , a little more detailed HOWTO install a plugin for newbies would be kind, cause those links are more confusing for me than helpfull  :)  :confused:

---

### Post by Abdi110 on 2006-03-26
Hello. I did the steps listed here for .18, when I try to run quodlibet I get this...

abdi110@reforgotten:~$ quodlibet
Traceback (most recent call last):
  File "/usr/local/bin/quodlibet", line 310, in ?
    import pygst
ImportError: No module named pygst
abdi110@reforgotten:~$ 

I'm running gstream 8something, I went looking for 10, downloaded, failed totally at configuring it...

error: Need libxml2 for glib2 builds

I've got a ton of packages through synaptic that seem like they'd be related to libxml2, but I'm still getting the same error. Any help in this would rock! Thanks.

---

### Post by barebones on 2006-03-26
I have Quod Libet .18 running fine, man I love this music player. Your problem is indeed gstreamer, Quod Libet won't work with .8. I checked my libs, and as far as xml2 goes, I have libxml2, libxml2-utils, python2.4-libxml2, and python-libxml2. Hope that helps.

Edit:
Also check out this page, it might help
[http://www.sacredchao.net/quodlibet/wiki/Development/GStreamer0.10]("http://www.sacredchao.net/quodlibet/wiki/Development/GStreamer0.10")

---

### Post by pranith on 2006-03-27
hi,
    I got gstream 10 working in breezy all u have to do is open up /etc/apt/sources.list
and change all the instances of breezy to dapper then in synaptic reload the package listing 
then install the following 3 packges
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
python-gst0.10
after they get installed change all the instances of dapper back to breezy

Stiill there is this error for me... 
[COLOR="Red"]Traceback (most recent call last):
  File "/usr/local/bin/quodlibet", line 309, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
[/COLOR]
PS: How do we uninstall it:confused:

---

### Post by pranith on 2006-03-27
I should have google sorry 
the problem is solved like this:
 File "/usr/bin/gnome-software-properties", line 28, in ?

 import gtk

 File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ? from _gtk import *

ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

But it's already solved by people at ubuntu stuff, as this article explains the problem is on the libfreetype6 package, to solve it just add dapper on your sources.list with

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

and then do the following command:

sudo apt-get update && sudo apt-get install libfreetype6

Then your system will continue to work normally, don't forget to remove the dapper repository from your sources.list, future updates of that non stable release can break your system!

---

### Post by barebones on 2006-03-27
By the sound of it, you've got it running and therefor won't ever want to uninstall it ;) , but if you do decide to, I think going to the directory where you extracted your quod libet files to and doing one of these

```
sudo make uninstall
```

will uninstall it.

---

### Post by pranith on 2006-03-28
[QUOTE=barebones]By the sound of it, you've got it running and therefor won't ever want to uninstall it ;) , but if you do decide to, I think going to the directory where you extracted your quod libet files to and doing one of these

```
sudo make uninstall
```

will uninstall it.[/QUOTE]
[COLOR="Red"]chinna@ubuntu:/opt/quodlibet-0.17.1$ sudo make uninstall
Password:
make: *** No rule to make target `uninstall'.  Stop.
chinna@ubuntu:/opt/quodlibet-0.17.1$[/COLOR]
:(

---

### Post by mrgnash on 2006-03-28
Worked perfectly, thanks :D

---

### Post by barebones on 2006-03-28
Pranith,
You need to be in the folder where you extracted quod libet files and ran the inital make install from. This is probabily something like ~/quodlibet-0.17.1

---

### Post by pranith on 2006-03-28
[QUOTE=barebones]Pranith,
You need to be in the folder where you extracted quod libet files and ran the inital make install from. This is probabily something like ~/quodlibet-0.17.1[/QUOTE]
I installed it in /opt/quodlibet-0.17.1 thats where I ran make install....

---

### Post by barebones on 2006-03-29
Have you deleted anything from that directory since you installed? In particular, is there anything named makefile in the directory still?

---

### Post by dartmusic on 2006-03-29
How are you folks accessing their site?  I've been trying for a week and consistently get a 403/access forbidden error.  I've tried from work and from home.  *scratches head*

---

### Post by barebones on 2006-03-29
I've had no trouble accessing their site. Which address are you using? 

Their official website is [here]("http://www.sacredchao.net/quodlibet/wiki")

---

### Post by hugmenot on 2006-03-29
[QUOTE=dartmusic]How are you folks accessing their site?  I've been trying for a week and consistently get a 403/access forbidden error.  I've tried from work and from home.  *scratches head*[/QUOTE]

Ah, I had that when I came with Opera switched to ident as IE.
I think he's blocking that.

---

### Post by dartmusic on 2006-03-29
Not sure what you mean...do you mean that he's blocking IE?  If so, that would explain.  I switched my Opera ident to Opera just last night, but haven't tried since then.  I'm on a locked XP box at work.

Thanks for that!

---

### Post by LKRaider on 2006-03-29
Any chance of making a deb package out of it? I mean, not for redistribution, but so it is better to install. I don't like "*sudo make install*".

Anyone knows if at least checkinstall will work?

---

### Post by pranith on 2006-03-29
get the rpm from their site and convert it to deb using alien

---

### Post by barebones on 2006-03-29
I tried doing a checkinstall, but didn't have any luck. I never have any luck with checkinstall :(

---

### Post by pranith on 2006-03-30
this package is not similar to the other source packages u dont nee to configure here just need to do 
make install
so it is not compatible to checkinstall

PS: for checkinstall refer to [https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29](https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29)

---

### Post by LKRaider on 2006-03-30
I just discovered v0.18 is on the Dapper repositories, so I am using that.

But I have problems making the plugins work. For example, the CDDB plugin won't appear on the pllugins list, instead, it shows an error like this:

```
File "/home/username/.quodlibet/plugins/cddb.py", line 19, in ?
    from plugins.songsmenu import SongsMenuPlugin
ImportError: No module named songsmenu
```

Anyone had luck installing this plugin? The plugin for Randum Album Playback was loaded ok.

Also, the Dapper package that includes Quod Libet plugins (quodlibet-plugins), requires a non-existent package in Dapper (python2.4-musicbrainz).

---

### Post by hugmenot on 2006-03-30
Here are packages from svn HEAD (0.19), built with dpkg-buildpackage.
I could have pointed you to [my older packages ]("http://ubuntuforums.org/showpost.php?p=821891&postcount=17")but why not just update 'em to HEAD instead?

EDIT: I realise that this thread is in the Breezy forum. These debs won't work in Breezy becasue support for the older Gstreamer 0.8 was dropped some verisons ago.

---

### Post by hugmenot on 2006-03-30
[quote=LKRaider]I just discovered v0.18 is on the Dapper repositories, so I am using that.

But I have problems making the plugins work. For example, the CDDB plugin won't appear on the pllugins list, instead, it shows an error like this:

```
File "/home/username/.quodlibet/plugins/cddb.py", line 19, in ?
    from plugins.songsmenu import SongsMenuPlugin
ImportError: No module named songsmenu
``` 
Anyone had luck installing this plugin? The plugin for Randum Album Playback was loaded ok.[/quote]


There's a new system for plugins

plugins/*.py (general purpose)
plugins/songsmenu/*.py (plugins changing selected songs)
plugins/editing/*.py (plugins that enhance the tag editor)

You can install the quodlibet-plugins pavckage from my last post. I modified the paths in the package to account for the new structure.

> Also, the Dapper package that includes Quod Libet plugins (quodlibet-plugins), requires a non-existent package in Dapper (python2.4-musicbrainz).

I think I have the breezy musicbrainz package. It works well.

---

### Post by barebones on 2006-03-30
Thanks for those debs, they all did a nice clean install on my system.

Edit:
I take that back, It appears that none of the plugins installed.

---

### Post by LKRaider on 2006-03-30
Thanks for the debs hugmenot, they are working fine!

To respond to the previous post by barebones, I figured the plugins you want to use must be copied to your /home/username/.quodlibet/plugins folder (and I think must respect the correct placement, as mentioned on Quod Libet wiki).

Anyway, it is working fine here now. :)

---

### Post by hugmenot on 2006-03-31
[QUOTE=LKRaider]Thanks for the debs hugmenot, they are working fine!

To respond to the previous post by barebones, I figured the plugins you want to use must be copied to your /home/username/.quodlibet/plugins folder (and I think must respect the correct placement, as mentioned on Quod Libet wiki).

Anyway, it is working fine here now. :)[/QUOTE]

Oh, right. Although it can't be that they *have* to be in your $home. Somehow they have to be available system-wide for any new users.

I think you have to make sure that songsmenu.py remains in /usr/share/quodlibet/plugins.

If you installed the quodlibet-plugins package copy the system-wide plugins from /usr/share/quodlibet/plugins to ~/.quodlibet/plugins until I figured out how it&#8217;s done now.

---

### Post by barebones on 2006-04-01
Ahh, thanks, they're all working now.

---

### Post by Burke on 2006-04-05
```
burke@burke:~/quodlibet-0.17.1$ make extensions
cd trayicon && make trayicon.so && cd ..
make[1]: Entering directory `/home/burke/quodlibet-0.17.1/trayicon'
pygtk-codegen-2.0 --prefix trayicon \
--register `pkg-config --variable=defsdir pygtk-2.0`/gdk-types.defs \
--register `pkg-config --variable=defsdir pygtk-2.0`/gtk-types.defs \
--override trayicon.override \
trayicon.defs > gen-tmp
/bin/sh: pygtk-codegen-2.0: command not found
make[1]: *** [trayicon.c] Error 127
make[1]: Leaving directory `/home/burke/quodlibet-0.17.1/trayicon'
make: *** [_trayicon.so] Error 2
burke@burke:~/quodlibet-0.17.1$

```

here's the important part again:
```
/bin/sh: pygtk-codegen-2.0: command not found
```

What do I install? This must be a simple apt-get install x?


EDIT: Found it: python-gtk-dev or something like that.

---

### Post by hugmenot on 2006-04-05
The packaging of plugins was officially changed:

quodlibet-plugins (20060404-0.1) unstable; urgency=low

  * Non-maintainer upload.
  * New SVN snapshot for Quod Libet 0.19.
  * Depends: exfalso (>= 0.19)
  * Remove (currently broken) ReplayGain plugin.
  * Clean up long description a bit.

 -- Joe Wreschnig <piman@debian.org>  Tue,  4 Apr 2006 15:03:56 -0500

---

### Post by hugmenot on 2006-04-06
Quodlibet 0.19.1 (or more exactly svn HEAD) packages as requested by foxy123:

---

### Post by pebe on 2006-04-06
Thank you hugmenot!! Really great player, I didn't know it existed before now. :D

---

### Post by rorzer on 2006-04-06
[QUOTE=pranith]hi,
    I got gstream 10 working in breezy all u have to do is open up /etc/apt/sources.list
and change all the instances of breezy to dapper then in synaptic reload the package listing 
then install the following 3 packges
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
python-gst0.10
after they get installed change all the instances of dapper back to breezy

Stiill there is this error for me... 
[COLOR="Red"]Traceback (most recent call last):
  File "/usr/local/bin/quodlibet", line 309, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?
    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
[/COLOR]
PS: How do we uninstall it:confused:[/QUOTE]

Warning!!!
Installing these packages on my working breezy system also installed dapper version of glib2,gconf2,libxml2, and cairo2.  The net result was that evolution stopped working.  Either dist-upgrade to breezy altogether, or wait until June!

---

### Post by hugmenot on 2006-04-11
[QUOTE=LKRaider]Also, the Dapper package that includes Quod Libet plugins (quodlibet-plugins), requires a non-existent package in Dapper (python2.4-musicbrainz).[/QUOTE]


EDIT: [nonsense deleted] See below for a repository holding python-musicbrainz.

---

### Post by bramvandijk on 2006-04-30
Thanks for these packages. They work great!
However, there is a small problem with some plugins,
these are the messages they give:

brainz

Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/songsmenu/brainz.py", line 4, in ?
    import musicbrainz, os, gtk
ImportError: No module named musicbrainz

lastfmsubmit

Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/lastfmsubmit.py", line 11, in ?
    import lastfm
ImportError: No module named lastfm



I think that I am missing something like pylastfm or something. Where can I get those?

---

### Post by hugmenot on 2006-05-01
[QUOTE=bramvandijk]
ImportError: No module named musicbrainz
[/quote]

Install the package python-musicbrainz if on Breezy, or python-tunepimp if on Dapper
> 
ImportError: No module named lastfm

I think the lastfm python module is a bit obscure, the QLScrobbler plugin does the same job.

I f you copy plugins directly from the QL page make sure that you read what dependecies the plugins use.

---

### Post by bramvandijk on 2006-05-01
Thanks, I am already using the audioscrobbler plugin, so I should be OK.:-D 
I will check for python-tunepimp, I thought that I already had it installed:-k , guess not... Thanks again!

---

### Post by bramvandijk on 2006-05-01
I have python-tunepimp installed, but still musicbrainz doesn't seem to work](*,) 
Any other bright ideas to help a n00b?

---

### Post by luks on 2006-05-01
python-tunepimp and python-musicbrainz are two completely different libraries. python-musicbrainz is not in dapper yet. if you want to get python-musicbrainz without manual installing source codes, use this repository:

```
deb http://users.musicbrainz.org/~luks/ubuntu dapper main
```

---

### Post by bramvandijk on 2006-05-02
Thanks!

---

### Post by hugmenot on 2006-05-02
[QUOTE=luks]python-tunepimp and python-musicbrainz are two completely different libraries. python-musicbrainz is not in dapper yet. if you want to get python-musicbrainz without manual installing source codes, use this repository:

```
deb http://users.musicbrainz.org/~luks/ubuntu dapper main
```[/QUOTE]

Ah, that's illuminating. I don't remember where I got that nugget of info, but when I looked at apt-cache search it made sense: the related packages were there and seemed to be just substituted with s/musicbrainz/tunepimp/.

I'll attach the reverted plugins package here and remove the one with the wrong dependency above. Also, because I just saw on the QL page that a new release is due new debs with the following:
```
0.20.1 - Thanks for the eye-opener, dinosaur zombies!
 * Vorbis/FLAC tag editing works again.

0.20 - Feelings are boring. Kissing is awesome!
 * Bug Fixes:
   * --play-file will use the queue. (#457)
   * Audio Feeds remember download locations. (#589)
   * Song changes don't revert tag edits. (#597)
   * Browser song activation takes precedence over the queue. (#622)
   * Albums drag-and-drop in listed order. (#623)
   * Only reset relevant parts of Information windows on song change. (#624)
   * Deleting files not in the library removes them. (#638)
   * Non-numeric disc/track numbers sort properly. (#643)
   * Paned Browser no longer adds incorrect entries. (Debian bug #361131)
   * Ex Falso no longer loads WAV or MOD files.
   * Allow more headers in Internet Radio and Audio Feeds.
   * New process launching method, util.spawn.
 * UI Changes:
   * Indicator to show when songs come from the queue. (#437)
   * Rating submenu always appears in the song list. (#598)
   * Album covers hide when clicked again. (#647)
   * Select current song when jumping to it.
 * New translations:
   * Norwegian Bokmål, by Andreas Bertheussen.
   * Swedish, by Erik Christiansson.
 * Updated translations:
   * Polish, by Tomasz Torcz.
   * Dutch, by Hans van Dok.
   * Finnish, by Jari Rahkonen.
   * French, by Olivier Gambier.
   * Galician and Spanish, by Johám-Luís Miguéns Vila.
   * Hebrew, by Roee Haimovich.
   * Portuguese, by Alexandre Passos.
```

---

### Post by gorkhal on 2006-05-14
these packages are amazing hugmenot...thanks a bunch

and all the plugins too...great stuff!!!:-D

---

### Post by hartl_vienna on 2006-05-15
Thanks for your work! It´s really great! :KS

---

### Post by Chrissss on 2006-06-10
@hugmenot
quodlibet 0.21 is out. In the mood for updated packages :D

Thanks
 Christoph

---

### Post by hugmenot on 2006-06-11
Sure, why not.

```
Quod Libet 0.21 requires Ogg Vorbis support in Mutagen. This requires
either Mutagen 1.2 and pyvorbis, or Mutagen 1.3 or later.

0.21 - Faith, AND the possibility of weaponized kissing??
 * Bug Fixes:
   * Queue behaves correctly when randomizing two songs. (#666)
   * GStreamer error messages are properly localized. (#669)
   * Tray icon is more resiliant to panel crashes. (#673)
   * "Jump..." distinguishes between identically-named albums. (#674)
   * application/ogg is recognized in audio feeds. (#682)
   * .pyo files are removed on clean. (#697)
   * util.unexpand caches the value of $HOME. (#702)
   * Fix plugin function call ordering. (#714)
 * UI Changes:
   * Improved tooltips in Preferences. (#653)
   * The Paned Browser shows song totals (#639), and has a button to
     reset all selections. (#640)
   * Saving play count / rating tags can be turned off, or adjusted
     to a different email address. (#667)
   * The last-entered directory is used for Scan Directories
     configuration. (#698)
 * pyvorbis is no longer required if you use Mutagen 1.3.
 * Event plugins were redesigned, incompatibly. (#603)
 * Test coverage data can be generated using trace.py. (#702)
 * New Simplified Chinese translation by Emfox Zhou. (#653)
 * New Hungarian translation by SZERVÁC Attila.
 * Updated translations:
   * Finnish, by Jari Rahkonen.
   * Korean, by Byung-Hee HWANG and ChangBom Yoon.
   * Galician and Spanish, by Johám-Luís Miguéns Vila.
   * Norwegian Bokmål, by Andreas Bertheussen.
   * Italian, by Filippo Pappalardo.
   * Polish, by Tomasz Torcz
   * Lithuanian, by Jonas Slivka.
   * Dutch, by Hans van Dok.
```

---

### Post by Chrissss on 2006-06-11
Thanks :)

---

### Post by Paool on 2006-06-12
thanks a lot, hugmenot :D

---

### Post by Orixyu on 2006-06-12
This program doesnt even boot up. I try to uninstall it by running sudo make uninstall and it fails like someone said before.

I dont recommend this program, doesnt even run.

---

### Post by hugmenot on 2006-06-12
[QUOTE=Orixyu]This program doesnt even boot up. I try to uninstall it by running sudo make uninstall and it fails like someone said before.

I dont recommend this program, doesnt even run.[/QUOTE]

Try the packages I posted earlier. They likely work out better for you.

---

### Post by chanders on 2006-06-13
I have used this program before and I must say it is excellent... However when trying to install it on my fresh install of Dapper I keep getting this error with ALL versions of QL posted on this thread....

Anyone? I would greatly appreciate it...
thanks

```
chanders@chanders-laptop:~$ quodlibet
Traceback (most recent call last):
  File "/usr/local/bin/quodlibet", line 315, in ?
    load_library()
  File "/usr/local/bin/quodlibet", line 250, in load_library
    import library
  File "/usr/local/share/quodlibet/library.py", line 15, in ?
    import formats
  File "/usr/local/share/quodlibet/formats/__init__.py", line 20, in ?
    format = __import__(name, globals(), locals(), self)
  File "/usr/local/share/quodlibet/formats/ape.py", line 12, in ?
    if gst.element_factory_make('monkeysdec'): extensions = [".ape"]
gst.PluginNotFoundError: monkeysdec
chanders@chanders-laptop:~$


```

---

### Post by hugmenot on 2006-06-13
[QUOTE=chanders]```
  File "/usr/local/bin/quodlibet", line 315, in ?
```[/QUOTE]

This sounds like you have a really old version installed under /usr/local which interferes with the deb installs (/usr/local always takes precedence over /usr).

Clear out everything called quodlibet below /usr/local. Monkey&#8217;s Audio support (i.e., .ape files) is long gone I think.

---

### Post by chanders on 2006-06-14
That worked. 

Note to anyone doing a re-install - ALWAYS clear out QuodLibet from /usr/local before doing any new install, as the un-installer/synaptic doesnt!

---

### Post by hugmenot on 2006-06-14
[QUOTE=chanders]That worked. 

Note to anyone doing a re-install - ALWAYS clear out QuodLibet from /usr/local before doing any new install, as the un-installer/synaptic doesnt![/QUOTE]

dpkg cannot know about what else is littered over the filesystem with manual installs.

But I&#8217;m glad it helped.

---

### Post by Chrissss on 2006-06-15
Hi hugmenot, sorry to bother again, Quod Libet 0.21.1 ist out :)

[http://gnomefiles.org/app.php?soft_id=561](http://gnomefiles.org/app.php?soft_id=561)

CU
 Christoph

---

### Post by kewldude606 on 2006-06-17
I downloaded the plugin package and I am trying to install it but I get this message: Error: dependency not satisfiable: exfalso.

I have exfalso installed, and if I enter exfalso ont he command line it pops up.

I have quod libet 0.21.  I tried to install the plugins with the .py files but it didn't work.

Thanks!

---

### Post by BrunoC on 2006-06-18
[QUOTE=kewldude606]I have quod libet 0.21.  I tried to install the plugins with the .py files but it didn't work.[/QUOTE]
Same problem here... Quod Libet 0.21.1

---

### Post by hugmenot on 2006-06-22
The plugins package I uploaded depends on exfalso (>= 0.19) which should be satisfied by installing the exfalso which is in the tarball as well.
If you install exfalso manually and the plugins package via dpkg it can&#8217;t work because exfalso wasn&#8217;t enlisted in the dpkg database, which handles the dependencies.

And, as requested by Chris:
```
0.21.1 - Dude! It's not like you can't just make your own!
 * MP3s with POPM can be loaded again (Thanks, Hans van Dok)
```

In fact it is 0.21.1 plus r3493.

---

### Post by bramvandijk on 2006-06-23
Thanks a lot!
but, the tray icon seems to have gone missing with 0.21.1
And yes, I also installed quodlibet-ext

Help?

---

### Post by hugmenot on 2006-06-23
It&#8217;s a regular plugin now you have to activate.

---

### Post by bramvandijk on 2006-06-23
:oops:  thanks!

---

### Post by oskvaz on 2006-06-23
I have installed the program but when I trie to run it, shows me this message:

Quod Libet has tried to accede to plugins &#8220;alsasink&#8221;, &#8220;ossink&#8221;  but has not been able to use none of them. Set GStreamer plugin editing:

pipeline = /nen ~/.quodlibet/config

Can you help me with this?
What must I write in pipeline?

Thanks

---

### Post by sha_man on 2006-06-25
**Thanks hugmenot!**
 It worked flawlessly :)  I like quod libet very much and was annoyed of the out-of-date version in the ubuntu repos...:( 

It would be very nice if you could keep the package up-to-date and keep on posting them in this thread. :D

---

### Post by Chrissss on 2006-07-06
Hi hugmenot!

I hate to bother you again, but your packages work great and the QuodLibet Team does a great job with each new version. :) QL 0.22 is out. Could you do your magic again :)
```
  Latest Version: 0.22
The tray icon is now optional.
A D-BUS RPC interface is available.
Tag values are autocompleted when editing.
Lyrics can be searched. Python 2.4 is required.
```
Thanks
 Christoph

---

### Post by mlind on 2006-07-06
I built ql 0.22, but strangest thing is that about dialog still shows 0.21..
Could someone confirm that this actually is 0.22 ? I haven't used this player before
so I don't notice if something has changed..

/edit
Lyrics search seems to work, I guess they just didn't update about dialog

/edit2
I did a svn checkout for the plugins, and included those too


[http://www.freefilehoster.com/uploads/1152217284quodlibet-0.22_dapper.tar.gz](http://www.freefilehoster.com/uploads/1152217284quodlibet-0.22_dapper.tar.gz)

---

### Post by feelgoodlost on 2006-07-08
I don't get the trayicon to work.

make statusicon always ends with the error that there was no rule to make statusicon.so.

any help?

---

### Post by joris1977 on 2006-07-10
Does anyone know when the repositaries will be updated, makes things so much easyer... or is this a stupid question.

---

### Post by Chrissss on 2006-07-10
Yep, it is ;) The Ubuntu repos don't get update with new versions. Only security updates find their way into  the whatever-security repo. So, to get a new version of a programm, you have to wait for the next ubuntu version.

BZW, i posted a ticket about the version numbers
[http://www.sacredchao.net/quodlibet/ticket/751](http://www.sacredchao.net/quodlibet/ticket/751)

They say, they can't do anything about it. Strange.

---

### Post by hugmenot on 2006-07-11
> **Chrissss said:**
> They say, they can't do anything about it. Strange.

Yes, strange. The version number is read from const.py, which is 0.21 in the release tarball on the website and in the [current branch]("http://www.sacredchao.net/quodlibet/browser/branches/quodlibet-library2/const.py") as well as in the [trunk]("http://www.sacredchao.net/quodlibet/browser/trunk/quodlibet/const.py"). Perhaps they cannot do anything about it because the release is already out? Or, it&#8217;s the job of the maintainer to change that?

---

### Post by mlind on 2006-07-11
> **feelgoodlost said:**
> I don't get the trayicon to work.

make statusicon always ends with the error that there was no rule to make statusicon.so.

any help?

What version did you use? with 0.22 status icon is automatically included, you just need to use "Tray Icon" plugin, if that's what you mean.

---

### Post by mlind on 2006-07-11
> **joris1977 said:**
> Does anyone know when the repositaries will be updated, makes things so much easyer... or is this a stupid question.

You could try quodlibet 0.22 from my repository
```

deb http://www.elisanet.fi/mlind/ubuntu dapper testing

```

---

### Post by joris1977 on 2006-07-11
Thanks mlind for the repo. Works real nice.

I had the same problem with azureus. It's in the repositaries but that version is real outdated, but installing manually was a hard job for me. Especially with the java requirements some trackers make. But that's of topic.

---

### Post by feelgoodlost on 2006-07-11
> **mlind said:**
> What version did you use? with 0.22 status icon is automatically included, you just need to use "Tray Icon" plugin, if that's what you mean.

thank you very much mlind. the problem is solved. the plugin trayicon.py has now to be downloaded and put in the folder /home/user/.quodlibet/plugins/events.

---

### Post by jkwarras on 2006-07-12
> **mlind said:**
> You could try quodlibet 0.22 from my repository
```

deb http://www.elisanet.fi/mlind/ubuntu dapper testing

```
mlind, I can't connect with your repository. It's this normal? :)

---

### Post by mlind on 2006-07-12
> **jkwarras said:**
> mlind, I can't connect with your repository. It's this normal? :)

No, it should work okay. I just tried installing quodlibet and quodlibet-plugins there myself.

---

### Post by lazyd2 on 2006-07-17
> **jkwarras said:**
> mlind, I can't connect with your repository. It's this normal? :)
I can't connect either...:-k

I get:
```
http://www.elisanet.fi/mlind/ubuntu/dists/dapper/Release: Unable to find expected entry  testing/binary-i386/Packages in Meta-index file (malformed Release file?)
```

---

### Post by mlind on 2006-07-17
> **lazyd2 said:**
> I can't connect either...:-k

I get:
```
http://www.elisanet.fi/mlind/ubuntu/dists/dapper/Release: Unable to find expected entry  testing/binary-i386/Packages in Meta-index file (malformed Release file?)
```

I had to change repository name from testing to main, try
```

deb http://www.elisanet.fi/mlind/ubuntu dapper **main**

```

---

### Post by lazyd2 on 2006-07-17
> **mlind said:**
> I had to change repository name from testing to main, try
```

deb http://www.elisanet.fi/mlind/ubuntu dapper **main**

```
Yeap, its working now...
Thanks!:D

---

### Post by LKRaider on 2006-07-22
Thanks mlind!

btw, what's the public key for your repository? And how do I enable it? :)

---

### Post by mlind on 2006-07-22
> **LKRaider said:**
> Thanks mlind!

btw, what's the public key for your repository? And how do I enable it? :)

The spell goes like this
```

gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -

```

---

### Post by foxy123 on 2006-07-25
thanks for the repository. I wonder why the tray icon tooltip changed? It used to be more eye-candy with a nice song progress bar, but now it's a yellow label with some static info about a song playing :(

---

### Post by hugmenot on 2006-07-25
> **foxy123 said:**
> thanks for the repository. I wonder why the tray icon tooltip changed? It used to be more eye-candy with a nice song progress bar, but now it's a yellow label with some static info about a song playing :(

That fancy Banshee tooltip was a [patch by Mathieu Cadet]("http://www.sacredchao.net/quodlibet/ticket/596") that I forgot to remove when I built the packages. It&#8217;s not the way to go to apply patches in a package maintained by the original author. I could have entered it into the changelog under my own name, though.

---

### Post by joris1977 on 2006-07-26
If you installed the musicbrainz repositary from luks earlier in this thread and want to get rid of the warning messages in synaptic

use this to import the key:

gpg --keyserver subkeys.pgp.net --recv 92132F7B
gpg --export --armor 92132F7B | sudo apt-key add -
sudo apt-get update

I found this here and maybe someone else will find this usefull:

[http://wiki.musicbrainz.org/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2](http://wiki.musicbrainz.org/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2)

---

### Post by foxy123 on 2006-07-30
does anyone know if it is possible to put bitrate info on the QL display? I tried to right-click and Edit Display, but I have not idea about how to put a right tag in right format there.

---

### Post by hugmenot on 2006-07-30
Look here [http://www.sacredchao.net/quodlibet/wiki/Guide/InternalTags](http://www.sacredchao.net/quodlibet/wiki/Guide/InternalTags)
only angle brackets make it a tag.

---

### Post by foxy123 on 2006-07-31
> **hugmenot said:**
> Look here [http://www.sacredchao.net/quodlibet/wiki/Guide/InternalTags](http://www.sacredchao.net/quodlibet/wiki/Guide/InternalTags)
only angle brackets make it a tag.

thanks a lot, but what is the right sintax? I tried
```
<~#bitrate>
```
but got an error :(

---

### Post by hugmenot on 2006-07-31
Note that the bitrate is given as the bare bit/s number.
You can also add a column.

---

### Post by maxter on 2006-07-31
withe quodlibet version 0.21 i can't play ogg files.

the quodlibet site bug tracking system reports that to solve this problem it is necessary to have  mutagen version > 1.3 installed.

the site is offline at the moment, but you can see the cached google copy of the report here:
[http://www.google.com/search?q=cache:hcjTU6yL-1EJ:www.sacredchao.net/quodlibet/ticket/747+quodlibet+ogg+site:sacredchao.net&hl=it&ct=clnk&cd=4](http://www.google.com/search?q=cache:hcjTU6yL-1EJ:www.sacredchao.net/quodlibet/ticket/747+quodlibet+ogg+site:sacredchao.net&hl=it&ct=clnk&cd=4)

the mutagen ubuntu version shipped with dapper is 1.0.

does anyone know where to find an updated version?

Max

---

### Post by maxter on 2006-07-31
solved ogg playing problem...

i installed  the python-mutagen 1.5.1 and python-central 0.5.1 (requested dependency) packages i found in launchpad into the development branch of ubuntu (edgy)

this is the url where is possible to find those packages:

[https://launchpad.net/distros/ubuntu/edgy/i386/python-mutagen/1.5.1-1](https://launchpad.net/distros/ubuntu/edgy/i386/python-mutagen/1.5.1-1)

the link to the python-central package download is in the right side 'depends on:' box 

i think this will be useful for all the people around there playing ogg (i found this problem in all the pc where i installed quodlibet version 0.21).

---

### Post by foxy123 on 2006-07-31
> **hugmenot said:**
> Note that the bitrate is given as the bare bit/s number.
You can also add a column.
thanks a lot. Is there any way to make the format more human?

---

### Post by hugmenot on 2006-08-01
> **foxy123 said:**
> thanks a lot. Is there any way to make the format more human?

I´ve no idea. The syntax is something GTK-related. Ask on IRC?

---

### Post by aweller on 2006-08-02
Quod Libet is great. I think it's just what I've been after for a while now. I was not satisfied with either Rhythmbox or Banshee, but put up with them. You can download it via:

sudo aptitude install quodlibet

(I've just checked all boxes in the source lists.)

It really is not as bloated as anything else I've used (it is currently using <10Mb memory) and has been running constantly without crashing for sometime now. (Something Rhythmbox and Banshee did frequently.)

---

### Post by aweller on 2006-08-02
Quod Libet is great :D

I think it's just what I've been after for a while now. I was not satisfied with either Rhythmbox or Banshee, but put up with them. You can download it via:

sudo aptitude install quodlibet

(I've just checked all boxes in the source lists.)

It really is not as bloated as anything else I've used (it is currently using <10Mb memory) and has been running constantly without crashing for sometime now. (Something Rhythmbox and Banshee did frequently.)

---

### Post by LKRaider on 2006-08-02
> **hugmenot said:**
> I´ve no idea. The syntax is something GTK-related. Ask on IRC?
The best you can do is apply HTML-like tags (actually, Pango tags):
[http://www.pygtk.org/pygtk2reference/pango-markup-language.html](http://www.pygtk.org/pygtk2reference/pango-markup-language.html)
[http://www.sacredchao.net/quodlibet/wiki/Guide/Player](http://www.sacredchao.net/quodlibet/wiki/Guide/Player)

Example:
```
 - \<span size='8000'\>Bit  <~#bitrate>\</span\>
```
will make the bitrate show at font size 8pt

---

### Post by LKRaider on 2006-08-02
> **hugmenot said:**
> I´ve no idea. The syntax is something GTK-related. Ask on IRC?
The best you can do is apply HTML-like tags (actually, Pango tags):
[http://www.pygtk.org/pygtk2reference/pango-markup-language.html](http://www.pygtk.org/pygtk2reference/pango-markup-language.html)
[http://www.sacredchao.net/quodlibet/wiki/Guide/Player](http://www.sacredchao.net/quodlibet/wiki/Guide/Player)

Example:
```
 - \<span size='8000'\>Bit  <~#bitrate>\</span\>
```
will make the bitrate show at font size 8pt

---

### Post by ChaKy on 2006-08-02
I have just installed Quod Libet 0.22, but for some strange reason, this player does not see any mp3 or ogg files in my music directory. I have python-pymad i python-pyvorbis installed.

```
chaky@ubuntu:/usr/local/src/quodlibet-0.22$ ./check.py
Checking Python version: 2.4
Checking for PyGTK >= 2.8: found
Checking for PyGSt >= 0.10.1: found
Checking for Mutagen >= 1.2: found
Checking for mutagen.oggvorbis: found
Checking for egg.trayicon: found
Checking for ctypes: found

Your system meets the requirements to install Quod Libet.
Type 'make install' (as root) to install it.

```

Am I missing something here?

EDIT: When I start players, it says in terminal:

```
chaky@ubuntu:~$ quodlibet
Supported formats: flac, mod, mp4, mpc, wav, wavpack
Loaded song library.
Checking /mnt/razno/glazba/live_dj_sets
Opening audio device.

```

but there is no mp3 or ogg vorbis??

---

### Post by Epperly on 2006-08-02
After adding that repository posted earlier, I get this error:
```

Reading package lists... Done
W: GPG error: http://www.elisanet.fi dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
sammy@SAMMY:~$ apt-get update

```

This is what I have added:
#Quod Libet
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main

---

### Post by mlind on 2006-08-02
> **Epperly said:**
> After adding that repository posted earlier, I get this error:
```

Reading package lists... Done
W: GPG error: http://www.elisanet.fi dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
sammy@SAMMY:~$ apt-get update

```


You probably need to add new gpg key to your APT keyring:
[http://www.ubuntuforums.org/showpost.php?p=1306661&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1306661&postcount=5)

---

### Post by Epperly on 2006-08-02
Yup, fixed the key... but now my problem is that I installed the extensions and plugins and they're not showing up in Quod Libet :( Idk why.. I had it all working before I should've just left it..

---

### Post by mlind on 2006-08-02
> **Epperly said:**
> Yup, fixed the key... but now my problem is that I installed the extensions and plugins and they're not showing up in Quod Libet :( Idk why.. I had it all working before I should've just left it..

Maybe those plugins aren't compatible anymore? Installing *quodlibet-plugins* package. It should contain most of the plugins for QL.

---

### Post by Epperly on 2006-08-02
well, quodlibet says version .21 even though the install thing said version .22, but version .21 is what I had(same thing) and just had the plugins in before anyway

---

### Post by mlind on 2006-08-02
> **Epperly said:**
> well, quodlibet says version .21 even though the install thing said version .22

That's known bug with .22 version.

---

### Post by lazyd2 on 2006-08-02
> **mlind said:**
> That's known bug with .22 version.
Yeap, but who cares:D

---

### Post by Epperly on 2006-08-03
> **mlind said:**
> That's known bug with .22 version.

Is there a plugin not going to the right folder or installing bug, too?

---

### Post by mlind on 2006-08-03
> **Epperly said:**
> Is there a plugin not going to the right folder or installing bug, too?

[Maybe]("http://www.sacredchao.net/quodlibet/report/15"). What plugin do you mean?

---

### Post by Epperly on 2006-08-03
well before I had quodlibet-ext and -plugins so all of em showed then I only had a few checked off, but now I have them installed and none of them are in the plugins dialog on quod libet, like the biggest pain is I cant minimize to tray, the only plugin thats there is one I put in manually which my friend wrote and sent to me, so its there from when I uninstalled before because it didnt get deleted.

---

### Post by mlind on 2006-08-03
> **Epperly said:**
> well before I had quodlibet-ext and -plugins so all of em showed then I only had a few checked off, but now I have them installed and none of them are in the plugins dialog on quod libet, like the biggest pain is I cant minimize to tray, the only plugin thats there is one I put in manually which my friend wrote and sent to me, so its there from when I uninstalled before because it didnt get deleted.

Must be something how you installed quodlibet. I've got installed plugins visible on plugins dialog and Tray Icon plugin is working correctly.

---

### Post by ChaKy on 2006-08-03
> **ChaKy said:**
> I have just installed Quod Libet 0.22, but for some strange reason, this player does not see any mp3 or ogg files in my music directory. I have python-pymad i python-pyvorbis installed.

```
chaky@ubuntu:/usr/local/src/quodlibet-0.22$ ./check.py
Checking Python version: 2.4
Checking for PyGTK >= 2.8: found
Checking for PyGSt >= 0.10.1: found
Checking for Mutagen >= 1.2: found
Checking for mutagen.oggvorbis: found
Checking for egg.trayicon: found
Checking for ctypes: found

Your system meets the requirements to install Quod Libet.
Type 'make install' (as root) to install it.

```

Am I missing something here?

EDIT: When I start players, it says in terminal:

```
chaky@ubuntu:~$ quodlibet
Supported formats: flac, mod, mp4, mpc, wav, wavpack
Loaded song library.
Checking /mnt/razno/glazba/live_dj_sets
Opening audio device.

```

but there is no mp3 or ogg vorbis??

And nobody have problems with playing mp3's?

---

### Post by lazyd2 on 2006-08-03
Here's what I get:
```
 quodlibet
Supported formats: flac, mod, mp3, mpc, wav, wavpack
```

---

### Post by Epperly on 2006-08-03
> **mlind said:**
> Must be something how you installed quodlibet. I've got installed plugins visible on plugins dialog and Tray Icon plugin is working correctly.
Thanks for the help, I figured it out.
It was installing the plugins to /usr/share/quodlibet/plugins/events, where the functional plugins folder was ~/.quodlibet/plugins/events, so I just moved them.

:D

---

### Post by foxy123 on 2006-08-06
> **hugmenot said:**
> That fancy Banshee tooltip was a [patch by Mathieu Cadet]("http://www.sacredchao.net/quodlibet/ticket/596") that I forgot to remove when I built the packages. It’s not the way to go to apply patches in a package maintained by the original author. I could have entered it into the changelog under my own name, though.

so I have to compile QL myself to have this nice thing?

---

### Post by jordilin on 2006-08-06
> **foxy123 said:**
> so I have to compile QL myself to have this nice thing?

You don't have to. It's made in Python :-D . Download, untar it, launch. No compilation. If you want to install it system wide, you can but not necessary.

---

### Post by foxy123 on 2006-08-06
> **jordilin said:**
> You don't have to. It's made in Python :-D . Download, untar it, launch. No compilation. If you want to install it system wide, you can but not necessary.
I can see only tooltip.r3126.patch following your link...

---

### Post by jordilin on 2006-08-06
> **foxy123 said:**
> I can see only tooltip.r3126.patch following your link...

I don't understand tooltip.r3126.patch??? Download quodlibet from [http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet) and that's all. :-D

---

### Post by foxy123 on 2006-08-06
> **jordilin said:**
> I don't understand tooltip.r3126.patch??? Download quodlibet from [http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet) and that's all. :-D

sorry I have misunderstood you... I meant a nice tooltip thing that used to 
be in hugmenot's build...

---

### Post by hugmenot on 2006-08-06
That patch was against the inbuilt tray icon that was made an independent plugin in the meantime apparently.
So, the modded tray icon would have to be made a plugin as well.
It&#8217;s beyond my own scope but you could ask the original supplier of the patch.

---

### Post by adds2one on 2006-08-09
Hi,

I just installed Quod Libet 0.22 and it is working except that I can't get any plugins to work.

Where am I supposed to put the plugins? I put the trayicon.py in ~/quodlibet/plugins/events. When I open the plugins window in QL there are no plugins but if I click on Show Errors in the plugins window I see this:

```
trayicon 
Traceback (most recent call last):
  File "/home/jjob/.quodlibet/plugins/events/trayicon.py", line 1
    <!DOCTYPE html
    ^
SyntaxError: invalid syntax
```

What am I doing wrong?

Also, I tried to access the repositories mentioned in this thread by appending:

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main

to my /etc/apt/sources.list and typing in my home directory:

```
gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -

```

but when I open Synaptic I can't find the newer quodlibet packages.

Does it matter where I type that code? (I think it is kind of like a password?? Public key?? I don't know??)

Would it matter from what directory I had installed quodlibet?

Does it matter in general for any program? Should I keep those install files or can I safely delete them?

Sorry, I am a very eager nOOb. I would be greatful if someone could help me get the QL plugins working, especially the trayicon. 

And if anyone wants to fill me in on some of my other questions I would be very happy too!;)

---

### Post by Epperly on 2006-08-09
I had that same problem, it turned out the plugins it installed went to the wrong folder, when I moved them to ~/.quodlibet/plugins/events it worked.

Also that is a public key paste the first line into the terminal then press enter then the second one and enter.

---

### Post by adds2one on 2006-08-10
I actually have my plugins in ~/.quodlibet/plugins/events but none of them show up in QL and I get the error from the trayicon and one other that gives the exact same error.

Is there a way to check what dependancies I may be missing?

Is it safe to delete those .key files or do I need to keeo them somewhere in particular? Do I have to do anything with them to be able to access the repository that has an up to date version of quodlibet?

---

### Post by adds2one on 2006-08-10
OK I just needed to reload in Synaptic and now I have access to the packages!!:D 

How do I uninstall what I already have?

---

### Post by adds2one on 2006-08-10
I just searched through my system and deleted all the quodlibet files and then installed all the 0.22 packages using Synaptic. Now most of the plugins are working. The one that isn't is the tray icon. No errors, it just doesn't come on.

---

### Post by hugmenot on 2006-08-10
> **adds2one said:**
> 
```
trayicon 
Traceback (most recent call last):
  File "/home/jjob/.quodlibet/plugins/events/trayicon.py", line 1
    <!DOCTYPE html
    ^
SyntaxError: invalid syntax
```

What am I doing wrong?

You borked the download ;)
What is inside the plugin file is really a html file; likely the redirect page that triggered the real download.

What I don&#8217;t get is why you guys don&#8217;t just install the quodlibet-plugins package that I or mlind provided. (Almost) all plugins are contained in that package and they work without any hassle (they&#8217;re placed in /usr/share/quodlibet/plugins).

If you need additional plugins that are not officially maintained place them in the .quodlibet/plugins folder. Just make sure they don&#8217;t overlap.

---

### Post by adds2one on 2006-08-10
> **hugmenot said:**
> You borked the download ;)
What is inside the plugin file is really a html

Yeah, I figured that out on my own last night. :oops: 

So I uninstalled QL and then did as you suggested and installed from your repository. :) 

I now have all the plugins installed but the trayicon still isn't working.:confused:

---

### Post by hugmenot on 2006-08-10
> **adds2one said:**
> Yeah, I figured that out on my own last night. :oops: 

So I uninstalled QL and then did as you suggested and installed from your repository. :) 

I now have all the plugins installed but the trayicon still isn't working.:confused:

It&#8217;s **mlind**&#8217;s repository.
Did you click the checkbox in front of the tray icon plugin in the plugins dialog?

---

### Post by ChaKy on 2006-08-10
I have just solved my problem described in [this thread](http://www.ubuntuforums.org/showpost.php?p=1333674&postcount=106). All I have to do was, to delete /usr/local/share/quodlibet directory, and install QuodLibet player again. Now, my mp3 collection has been recognized and played.

---

### Post by nyarla33 on 2006-08-29
Just a few words to say thanks everyone here, especially **mlind** for the useful repository and the fast updates when new version of QL are released.;)

---

### Post by joris1977 on 2006-09-29
Something went wrong... suddenly i cannot play any music in quod-libet. Mplayer seems to work fine so it might be a gstreamer problem  I get this error message in the terminal: Introspect error: The name org.gajim.dbus was not provided by any .service files

any help will be appreciated a lot....

solved
edit:  Introspect error: The name org.gajim.dbus had nothing to do with it. It is a harmless error everyone seems to have. My problem was that somehow alsa mixer was deselected in the multimedia tab. Easy to solve if you know...](*,)

---

### Post by hugmenot on 2006-10-02
People need/want to test the new devices stuff before release.
I don&#8217;t know what you have at the repo currently, mlind, this is just a one-time interlude.

File issues [here]("http://www.sacredchao.net/quodlibet/timeline?ticket=on&ticket_comments=on&changeset=on&wiki=on&milestone=on").

To install unpack the archive and install all contained debs. What I don&#8217;t know is how you have to install gpod, it isn&#8217;t documented yet. Perhaps ["Installation - Point 3." ]("http://www.sacredchao.net/quodlibet/wiki/Plugins/iPod") still applies? EDIT: it seems Edgy already holds thos gpod Python bindings: [http://packages.ubuntu.com/python-gpod](http://packages.ubuntu.com/python-gpod)

---

### Post by mlind on 2006-10-03
@ hugmenot

I'm not sure either what repo currently holds :mrgreen: 
I've started to use Edgy as my main system, so my Dapper packages are probably history.

---

### Post by hugmenot on 2006-10-03
> **mlind said:**
> @ hugmenot

I'm not sure either what repo currently holds :mrgreen: 
I've started to use Edgy as my main system, so my Dapper packages are probably history.

Does it matter in this case? I thought, well, no.

---

### Post by xthaparian on 2006-10-04
Can some one please Tell me how to Remove once

sudo make install 

is executed?

sudo make uninstall does not work..

Thanks

---

### Post by foxy123 on 2006-10-04
> **hugmenot said:**
> People need/want to test the new devices stuff before release.
I don’t know what you have at the repo currently, mlind, this is just a one-time interlude.

File issues [here]("http://www.sacredchao.net/quodlibet/timeline?ticket=on&ticket_comments=on&changeset=on&wiki=on&milestone=on").

To install unpack the archive and install all contained debs. What I don’t know is how you have to install gpod, it isn’t documented yet. Perhaps ["Installation - Point 3." ]("http://www.sacredchao.net/quodlibet/wiki/Plugins/iPod") still applies? EDIT: it seems Edgy already holds thos gpod Python bindings: [http://packages.ubuntu.com/python-gpod](http://packages.ubuntu.com/python-gpod)

it is for Edgy :(

---

### Post by egmar on 2006-10-13
How to enable equalizer in Quod Libet. I use Quod Libet 0.23.1.

---

### Post by hugmenot on 2006-10-13
> **egmar said:**
> How to enable equalizer in Quod Libet. I use Quod Libet 0.23.1.

There&#8217;s none. I know there are legitimate uses for one but I&#8217;m usually fine with a flat response.

---

### Post by angrykeyboarder on 2006-10-13
> **HighPlainsDrifter said:**
> An oft overlooked audio player and musical organizing tool in the Ubuntu world is Quod Libet. Personally, it ranks as my favorite audio player, even over the sacred Rhythmbox :mrgreen:. Also, QL comes bundled with a VERY powerful tagging tool, called Ex Falso, which is invaluable when your music collection literally has thousands of songs across different formats :-D 

The Ubuntu repositories have an ancient version of the QL, and Google revealed an equally old .deb file. Knowing that Quod Libet was written in Python, I knew installation had to be easy as pie - it was!

First, open up a terminal (*Applications*->*Accessories*->*Terminal*) to grab the latest and greatest source from [Quod Libet's official web site]("http://www.sacredchao.net/quodlibet").

```
# wget [http://www.sacredchao.net/~piman/software/quodlibet-0.17.1.tar.gz]("http://www.sacredchao.net/%7Epiman/software/quodlibet-0.17.1.tar.gz")
```Second, extract the gzipped tar file.

```
# tar xvzf quodlibet-0.17.1.tar.gz
```Change into the directory that tar extracted the files to.
```
cd quodlibet-0.17.1
```Before you go further, you will probably have to install *intltool*, an XML related series of scripts that QL's makefile depends on. You can learn more about intltool by running **apt-cache show intltool**.

```
sudo apt-get install intltool
```Allow it to install the additional files, too. One more steps to go!

```
sudo make install
```It is now installed. If you don't see Quod Libet in the Gnome menu, run **killall gnome-panel**

Enjoy your new music player \\:D/. And if you aren't satisfied with Quod Libet's features, then maybe you can [find a plugin]("http://www.sacredchao.net/quodlibet/wiki/Plugins") that does what you need!

One more IMPORTANT thing, for mp3 support, you need to install **python-pymad**, and for ogg **python-pyvorbis**

Could I replace "make install" with "checkinstall"?

I don't install binaries that aren't in Debian Package format.

---

### Post by foxy123 on 2006-10-13
> **angrykeyboarder said:**
> Could I replace "make install" with "checkinstall"?

I don't install binaries that aren't in Debian Package format.

why do you need compiling it if there are debs availabled in this thread. Answering your question, yes you can of course.

---

### Post by angrykeyboarder on 2006-10-13
> **foxy123 said:**
> why do you need compiling it if there are debs availabled in this thread. Answering your question, yes you can of course.

I'm not that proficient at compiling from source and I've had problems in the past with python.

I didn't notice any debs listed in the thread.

---

### Post by foxy123 on 2006-10-13
> **angrykeyboarder said:**
> I'm not that proficient at compiling from source and I've had problems in the past with python.

I didn't notice any debs listed in the thread.

If you use Edgy, use this one:
[http://ubuntuforums.org/showpost.php?p=1572548&postcount=126http://ubuntuforums.org/showpost.php?p=1572548&postcount=126](http://ubuntuforums.org/showpost.php?p=1572548&postcount=126http://ubuntuforums.org/showpost.php?p=1572548&postcount=126)
If Dapper, then try mlind's repo:
[http://ubuntuforums.org/showpost.php?p=1240418&postcount=69](http://ubuntuforums.org/showpost.php?p=1240418&postcount=69)

---

### Post by robenroute on 2006-10-20
> **foxy123 said:**
> If you use Edgy, use this one:
[http://ubuntuforums.org/showpost.php?p=1572548&postcount=126http://ubuntuforums.org/showpost.php?p=1572548&postcount=126](http://ubuntuforums.org/showpost.php?p=1572548&postcount=126http://ubuntuforums.org/showpost.php?p=1572548&postcount=126)
If Dapper, then try mlind's repo:
[http://ubuntuforums.org/showpost.php?p=1240418&postcount=69](http://ubuntuforums.org/showpost.php?p=1240418&postcount=69)


The in [mlind repository]("http://ubuntuforums.org/showpost.php?p=1240418&postcount=69") mentioned repository should be:
```

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper main

```
not:
```

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) dapper testing

```

Testing doesn't work for me.... Good luck!

Rob

---

### Post by foxy123 on 2006-10-20
Does anyone know what is the main reason for not having a Stop button in Quod Libet?

---

### Post by LKRaider on 2006-10-20
There is no real gain in having a stop button on a software app is there?

If you want to stop use the pause, it will stop playing.
Now, if you REALLY want to stop, just close the app. :P

---

### Post by foxy123 on 2006-10-20
> **LKRaider said:**
> There is no real gain in having a stop button on a software app is there?

If you want to stop use the pause, it will stop playing.
Now, if you REALLY want to stop, just close the app. :P

it is not true. There are a number of situations when I would like to have a STOP button. For example I have just started listening to a song and something interrupted me (like a telephone call). After finishing dealing with the nuisance I would like to start listening to the song from the beginning again. In amarok, for example I just hit stop button and then play. But in QL I have either hit a pause button and then go to the beginning of the song or if I close it, the song will be gone from the play list. Another situation is when I want to finish listening to one album and take a break before next.

---

### Post by hugmenot on 2006-10-20
> **foxy123 said:**
> it is not true. There are a number of situations when I would like to have a STOP button. For example I have just started listening to a song and something interrupted me (like a telephone call). After finishing dealing with the nuisance I would like to start listening to the song from the beginning again. In amarok, for example I just hit stop button and then play. But in QL I have either hit a pause button and then go to the beginning of the song or if I close it, the song will be gone from the play list. Another situation is when I want to finish listening to one album and take a break before next.

You got a point there. In particular when you want to restart the song when it was played from the Queue. It has already vanished so you cannot just double click it.
The rationale is /I think/ that the playback button is a toggle. Playback/No playback. Another issue is that QL will lock the hw device via ALSA and OSS stuff like realplayer won&#8217;t work while QL is running. It&#8217;s a dilemma because stopping and restarting QL takes a real while and using Dmix gives bad SRC artifacts on my soundboard.

---

### Post by foxy123 on 2006-10-20
It is one of the main reasons why I am thinking about moving to listen of exaile, which are in my opinion very much based on QL, but cross it with amarok providing small but features I like (like a STOP button). However, I still prefer Quod Libet album art management to both aforementioned players.

Another thing that annoys me in QL is a Song List View. I rarely use it preferring Queue View, but it is enabled every time I restart Quod Libet. Also when the play list is over, QL starts playing the song from this Song List, the album which is left selected, while most of other players just stop.

---

### Post by hugmenot on 2006-10-20
Hmm, now I would hate that. I&#8217;m actually really fond of the Song List /Queues system that QL uses. I use the Queue to quickly insert tracks into the flow of playback and I appreciate when it resumes where it left off. That way you can compare different recordings of a piece and then resume playing the rest of the work. I have a global keybinding to open a new Search browser for this, I just select the desired results and hit Q. The Queue is also useful when you are erratically navigating around the album panel (e.g., while tagging stuff). 
What I appreciate most is the search bar in the Album List. You can narrow the list down to a subset with sophisticated searches and then have Random Album cycle through the subset. Rich meta-data is really great for this.

---

### Post by foxy123 on 2006-10-20
> **hugmenot said:**
> Hmm, now I would hate that. I’m actually really fond of the Song List /Queues system that QL uses. I use the Queue to quickly insert tracks into the flow of playback and I appreciate when it resumes where it left off. That way you can compare different recordings of a piece and then resume playing the rest of the work. I have a global keybinding to open a new Search browser for this, I just select the desired results and hit Q. The Queue is also useful when you are erratically navigating around the album panel (e.g., while tagging stuff). 
What I appreciate most is the search bar in the Album List. You can narrow the list down to a subset with sophisticated searches and then have Random Album cycle through the subset. Rich meta-data is really great for this.

I like Queue but I do not like that I cannot switch off Song List View permanently.

---

### Post by LKRaider on 2006-10-27
I know some people like the stop button, but I find myself never actually missing it. Maybe it's because the way I listen to my songs: always in random album mode, IDK.

The only gripe I have with the interface really is the hidden seekbar for the song. Not very useful (actually, un-useful).

---

### Post by nyarla33 on 2006-11-20
Quod Libet 0.24 released.
[http://www.sacredchao.net/quodlibet/wiki/Download](http://www.sacredchao.net/quodlibet/wiki/Download)

Please, could someone compile it for Edgy.
Thanks.

---

### Post by foxy123 on 2006-11-20
> **nyarla33 said:**
> Quod Libet 0.24 released.
[http://www.sacredchao.net/quodlibet/wiki/Download](http://www.sacredchao.net/quodlibet/wiki/Download)

Please, could someone compile it for Edgy.
Thanks.

what about Dapper as well? or at least post some instructions of a link about how to do it, please..

---

### Post by hugmenot on 2006-11-20
&#1047;&#1072;&#1087;&#1086;&#1074;&#1103;&#1076;&#1072;&#1081;&#1090;&#1077; :)

Don&#8217;t worry about the version number, it was incremented after I updated to the 0.24 final SVN.

Built on Edgy.

```
0.24 - One wonders if our conversation today would be an appropriate epitaph.
 * Media device (iPod and UMS so far) support. (Markus Koller)
 * Delete removes songs from the queue. (#0.819, sciyoshi)
 * Per-browser window memory. (#0.836)
 * Use Mutagen for WavPack and Musepack support. (#0.838)
 * Keep filenames when given invalid patterns. (#0.853, Markus Koller)
 * Don't duplicate performers in ~performers. (Martin Bergström)
 * Python 2.5 and GTK+ 2.10 compatibility.
 * Fix Rename Files support on MP4 files.
 * New Romanian translation, by Mugurel Tudor.
 * New Slovak translation, by Luká&#353; Lalinský.
 * Updated translations:
   * Traditional Chinese, by Hsin-lin Cheng.
   * Japanese, by Yasushi Iwata.
   * Galician and Spanish, by Johám-Luís Miguéns Vila.
   * Finnish, by Jari Rahkonen.
   * Hebrew, by Roee Haimovich.
   * Polish, by Tomasz Torcz
   * French, by Guillaume Ayoub.
   * German, by Rüdiger Arp.
```

---

### Post by hugmenot on 2006-11-20
In other news my music playback started so behave really, really weird. It basically slows down like a turntable would sound when slowed down, then it is back to normal speed, really erratic. It&#8217;s not QL, other players do that too.

What the hell is this???

---

### Post by urukrama on 2006-11-22
> **hugmenot said:**
> Don&#8217;t worry about the version number, it was incremented after I updated to the 0.24 final SVN.

Built on Edgy.

Will this work on Dapper?

---

### Post by foxy123 on 2006-11-24
> **urukrama said:**
> Will this work on Dapper?

here you are, backported from Feisty. Please use plugins package from hugmenot's Edgy package. Let me know if you have any problems. The archive also includes python-central package required for running it.

EDIT: I have withdrawn the package as it does not work for everyone. I will try to test it in a clean environment and post the results. Hopefully it should be fixed.

---

### Post by foxy123 on 2006-11-25
Have anyone had any issue with flac tagging. I have a few stuff in flac and I noticed that Quod Libet does not recognise the tags when I add files to the library. The albums do not show up in the album list. It looks like a mutagen issue though as the same thing happens with ex-falso and exaile, which both use mutagen for tagging.

The tags are read and written without any problem with EasyTag. Moreover, I have some flac files which were added some time ago and they are fine. Any idea?

---

### Post by LKRaider on 2006-11-25
**foxy123:** I couldn't install your package :(
It gave me an error about python-central not finding the Python-Version tag on your ExFalso package.

```
File "/usr/bin/pycentral", line 538, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
```

Info on python-central:
[http://python-modules.alioth.debian.org/python-central_howto.txt](http://python-modules.alioth.debian.org/python-central_howto.txt)

---

### Post by foxy123 on 2006-11-25
> **LKRaider said:**
> **foxy123:** I couldn't install your package :(
It gave me an error about python-central not finding the Python-Version tag on your ExFalso package.

```
File "/usr/bin/pycentral", line 538, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
```

Info on python-central:
[http://python-modules.alioth.debian.org/python-central_howto.txt](http://python-modules.alioth.debian.org/python-central_howto.txt)

here it is. Sorry I thought it was only required for building. Let me know if you run into any other dependencies.

---

### Post by hugmenot on 2006-11-26
> **foxy123 said:**
> Any idea?
[Yes, here]("http://www.ubuntuforums.org/showthread.php?t=209371")

---

### Post by urukrama on 2006-11-26
> **foxy123 said:**
> here it is. Sorry I thought it was only required for building. Let me know if you run into any other dependencies.

It still didn't work. I've tried both python-central packages. I get the same error.

---

### Post by foxy123 on 2006-11-26
> **hugmenot said:**
> [Yes, here]("http://www.ubuntuforums.org/showthread.php?t=209371")

Thanks a lot. It fixes the problem.

---

### Post by ryu kun on 2006-11-26
I have tried to install 0.24 to Dapper by using foxy123's packages. I also used hugmenot's plugins package.

I was installing packages in the written order

```
python-central_0.5.5ubuntu4~6.06prevu1_all.deb
python-mutagen_1.8-1_all.deb
exfalso_0.24-0ubuntu1~6.06prevu1_all.deb
```

but it gave this error during the latest:

```
sudo dpkg -i ex*.deb
Password:
(Reading database ... 86723 files and directories currently installed.)
Preparing to replace exfalso 0.24-0ubuntu1~6.06prevu1 (using exfalso_0.24-0ubuntu1~6.06prevu1_all.deb) ...
Unpacking replacement exfalso ...
Setting up exfalso (0.24-0ubuntu1~6.06prevu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1329, in ?
    main()
  File "/usr/bin/pycentral", line 1323, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 858, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 528, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing exfalso (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 exfalso
```

---

### Post by urukrama on 2006-11-26
> **hugmenot said:**
>  
* Per-browser window memory. (#0.836)


What does this actually mean? What does it do? It is the only item in the list that really sounds like something I could use.

---

### Post by foxy123 on 2006-11-26
**ryu kun**
**urukrama**

I will look into it. Sorry.

---

### Post by foxy123 on 2006-11-26
Interesting thing is that I do not have python-central installed at all.

---

### Post by urukrama on 2006-11-26
I run QL 0.23.1 on Dapper which doesn't require python-central. Seems it is something they introduced just recently.

---

### Post by foxy123 on 2006-11-26
> **urukrama said:**
> I run QL 0.23.1 on Dapper which doesn't require python-central. Seems it is something they introduced just recently.

python-central is a building tool. It is required only for building QL. It is not listed in the dependencies and I have got any other backported python packages on my system.

---

### Post by foxy123 on 2006-11-26
Ok, guys, sorry about any troubles. The problem was that I have python-mutagen 1.8 installed from hugmenot's Dapper package months ago, while Ubuntu has version 1.1. So I built it as well and attached together with other packages. 

I also included in the archive the plugins package from the recent hugmenot's build for your convenience. **hugmenot**, could you let me know if you have any objections.

Let me know if it works.

EDIT: it looks it does not :)

Thanks to ryu kun for providing proper packages!

---

### Post by robenroute on 2006-11-26
Nopes, not working (on my Edgy computer, that is). Still unable to configure ex falso due to:

Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing exfalso (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 exfalso

------

I do have python-central installed on my system.... Any ideas?

Rob

---

### Post by foxy123 on 2006-11-27
> **robenroute said:**
> Nopes, not working (on my Edgy computer, that is). Still unable to configure ex falso due to:

Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing exfalso (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 exfalso

------

I do have python-central installed on my system.... Any ideas?

Rob
what package are you trying to use? Mine is for Dapper and hugmenot's is for Edgy.

---

### Post by ryu kun on 2006-11-27
I unfortunately got the same error with Robenroute.

I used your latest packages, foxy123.

---

### Post by ryu kun on 2006-11-27
Ok, guys. I've compiled 0.24 for Dapper and it worked without any problem.

If you want to try, here is the package.

I also added foxy123's mutagen 1.8 package which is also needed. foxy123, please let me know if you have any objections.

There are lots of cool plugins for QL. You can find them here: [http://www.sacredchao.net/quodlibet/wiki/Plugins]("http://www.sacredchao.net/quodlibet/wiki/Plugins")

If you want all of the current plugins you can also extract attached plugins package into "~/.quodlibet".

---

### Post by robenroute on 2006-11-28
> **foxy123 said:**
> what package are you trying to use? Mine is for Dapper and hugmenot's is for Edgy.

Sensible question! I guess I'll have to rub the dirt out of my eyes before attempting this.... ;) 

Thanks anyway!

---

### Post by robenroute on 2006-11-28
> **robenroute said:**
> Sensible question! I guess I'll have to rub the dirt out of my eyes before attempting this.... ;) 

Thanks anyway!


***Oops!***, by installing (or, rather, tempting to install) the dapper packages, I may have caused a wee bit of havoc: it seems impossible to uninstall exfalso. I've tried Synaptic as well as command line (dpkg).

The error I get (after "sudo dpkg -P exfalso") is:

dpkg: error processing exfalso (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 exfalso

However, reinstalling isn't an option as it results in the problems I'm facing.... ](*,) ](*,) ](*,) 

Any help is much appreciated, thanks, Rob

---

### Post by urukrama on 2006-11-28
> **ryu kun said:**
> Ok, guys. I've compiled 0.24 for Dapper and it worked without any problem.

There are lots of cool plugins for QL. You can find them here: [http://www.sacredchao.net/quodlibet/wiki/Plugins]("http://www.sacredchao.net/quodlibet/wiki/Plugins")


Thanks. It works perfectly. Good to see that the website is updated again. :-D

---

### Post by ryu kun on 2006-12-03
You are welcome. :)

---

### Post by robenroute on 2006-12-12
Hi there,

I've installed hugmenot's Quod Libet .deb packages for Edgy (version 24.1, although in QL's About window it says it's version 25.0....). The whole install went fine, apart from the fact that when selecting plugins from the music menu, and then clicking the Errors button, there's a report of 3 plugins (of which 2 rather important ones) not working:


```
Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/songsmenu/brainz.py", line 4, in ?
    import musicbrainz, os, gtk, re
ImportError: No module named musicbrainz
```

The same for the CDDB and submitlastfm plugins. Someone out there who knows how to solve this? Thanks a lot in advance.

Rob

---

### Post by hugmenot on 2006-12-12
First, you better not cross-post. Then to use cddb and muscibrainz install python-cddb from main and python-musicbrainz from 

```
deb http://users.musicbrainz.org/~luks/ubuntu edgy main
```

lastfmsubmit doesn&#8217;t work without a certain obscure module but it&#8217;s redundant anyway. QLscrobbler does the same and works perfectly.

---

### Post by natalia on 2006-12-12
> **ryu kun said:**
> Ok, guys. I've compiled 0.24 for Dapper and it worked without any problem.


Thank you, that worked perfectly!

What about iPod support in this new version, has anyone tried it? I am still trying to figure out how to do it. I have even followed some instructions for the old iPod plugin ([http://www.sacredchao.net/quodlibet/wiki/Plugins/iPod)](http://www.sacredchao.net/quodlibet/wiki/Plugins/iPod)), without much success. My iPod is mounted and I can navigate through its directories, but Quod Libet does not seem to see any External Devices.

To robenroute: I had similar problems with exfalso. Have you tried apt-get instead of dpkg?

```
sudo apt-get remove exfalso
```

For some reason, that seems to have solved my problem, while Synaptic simply had given up.

**Update:** I should add I first removed the newly-installed QL, them removed exfalso, then installed the new QL again.

---

### Post by robenroute on 2006-12-12
> **natalia said:**
> 
To robenroute: I had similar problems with exfalso. Have you tried apt-get instead of dpkg?

```
sudo apt-get remove exfalso
```

For some reason, that seems to have solved my problem, while Synaptic simply had given up.

**Update:** I should add I first removed the newly-installed QL, them removed exfalso, then installed the new QL again.



Sincere apologies, people. I forgot to post the solution to the problems caused by my clumsy install adventure in this thread. Anyway, [this]("http://ubuntuforums.org/showthread.php?t=308544") thread explains how I finally got rid of the Dapper packages on my Edgy system. Thanks again, Ramses.

@hugmenot: sorry for cross-posting, but I thought this thread was a general feedback thread for people's experiences installing the latest Quod Libet packages.

---

### Post by robenroute on 2006-12-13
> **hugmenot said:**
> First, you better not cross-post. Then to use cddb and muscibrainz install python-cddb from main and python-musicbrainz from 

```
deb http://users.musicbrainz.org/~luks/ubuntu edgy main
```

lastfmsubmit doesn’t work without a certain obscure module but it’s redundant anyway. QLscrobbler does the same and works perfectly.


Thanks for the help hugmenot. I had problems finding the python-musicbrainz package, but when I changed the repository to:

```
deb http://users.musicbrainz.org/~luks/ubuntu edgy musicbrainz
```

.... everything installed just fine. However, the musicbrainz plugin still gives the same error. CDDB is working just fine....

Thanks again,
Rob

---

### Post by foxy123 on 2006-12-14
Since two days ago QL starts playing songs from the play-list as soon as it starts. I experienced it before but it was gone, now it is back. A bit annoying as I have to switch it off every time I boot my laptop.

---

### Post by ilkerka on 2006-12-31
hi i have done the installation with the guide at first page and didnt work so i tried the .deb file provided still the same error. Maybe its because of GTK+. I am using dapper and this is the error i get when i open the executable for quod libet:
Traceback (most recent call last):
  File "/usr/local/bin/quodlibet", line 315, in ?
    load_library()
  File "/usr/local/bin/quodlibet", line 250, in load_library
    import library
  File "/usr/local/share/quodlibet/library.py", line 15, in ?
    import formats
  File "/usr/local/share/quodlibet/formats/__init__.py", line 20, in ?
    format = __import__(name, globals(), locals(), self)
  File "/usr/local/share/quodlibet/formats/ape.py", line 12, in ?
    if gst.element_factory_make('monkeysdec'): extensions = [".ape"]
gst.PluginNotFoundError: monkeysdec

---

### Post by hugmenot on 2007-01-01
search this thread for monkeysdec.

---

### Post by tenseiken on 2007-01-20
Hi everyone, first-timer here.  Wait, don't run yet.

I've been trying to get Quod Libet to play my musepack files (it does claim to be able to do that) with no success.  I've installed the gstreamer musepack package and I've tried both the official Quod Libet version (0.23) in the repository as well as the one hugmenot linked to earlier (version 0.24).  Basically, no matter what I've done, it won't let me open a musepack file.  MP3 files open and play just fine though.

Any suggestions you could offer would be wonderful.

---

### Post by hugmenot on 2007-01-20
Is there any message when you want to play one back?
Does it really list musepack as supported when you start "quodlibet" in a terminal?

---

### Post by tenseiken on 2007-01-20
There's no message per se.  When I browse to a folder with .mpc files, they are greyed out and can't be added.  When I drag and drop files into the window, nothing happens.  Running the program from a terminal window reports compatibility with mp3, wav, and xiph.

-edit-
I installed some more gstreamer things.  Bad and ugly packs from the multiverse, to be precise.  That seems to have fixed my problem.  I've got mod, mp3, mp4, mpc, trueaudia, wav, wavpack, and xiph being reported from the terminal now.

---

### Post by hugmenot on 2007-01-20
I see.
Do you have these packages installed:
libmpcdec3
gstreamer0.10-plugins-bad

And what happens if you try this bare Gstreamer command:

gst-launch-0.10 playbin uri=file:///home/tenseiken/test.mpc
(modify the path to point to an mpc file)

EDIT: allright, problem solved!(?)

---

### Post by kiddvenom on 2007-04-03
Hi,

I get the following message when trying to open Quod Libet (v. 0.24, Mutagen v. 1.10.1 installed afterwards): Unable to open files - Quod Libet could not find the 'filesrc' GStreamer element. Check your GStreamer installation."

Could anyone help? I'm running Xubuntu Fesity Fawn 7.04.

---

### Post by joris1977 on 2007-04-07
Hé kiddvenom

This thread: 

[http://bbs.archlinux.org/viewtopic.php?id=30861](http://bbs.archlinux.org/viewtopic.php?id=30861)

suggests that to solve your issue, you need to install gstreamer0.10-gnomevfs 

I had the same problem as you in xubuntu feisty and for me it solved the problem. If you install gstreamer0.10-gnomevfs with synaptic it will install some extra packages. Since the package is gnome related i don´t  know if this will slow your xubuntu install.

---

### Post by hugmenot on 2007-04-08
Here's a nice Easter gimmick for you. A revised ReplayGain scanning plugin was commited to svn that scans all file formats with the new GStreamer rganalysis element instead of relying on external tools like vorbisgain.
[http://www.sacredchao.net/quodlibet/changeset/3999](http://www.sacredchao.net/quodlibet/changeset/3999)

I rebuild a quodlibet-plugins package with this included for your convenience.

---

### Post by robenroute on 2007-04-08
> **hugmenot said:**
> Here's a nice Easter gimmick for you. A revised ReplayGain scanning plugin was commited to svn that scans all file formats with the new GStreamer rganalysis element instead of relying on external tools like vorbisgain.
[http://www.sacredchao.net/quodlibet/changeset/3999](http://www.sacredchao.net/quodlibet/changeset/3999)

I rebuild a quodlibet-plugins package with this included for your convenience.

Hi there hugmenot,

Thanks for the rebuild. I do have a slight problem with it: after installing (I removed the previous plugins package first), the plugins dialogue in QL shows me:

```
Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/songsmenu/replaygain.py", line 236, in ?
    raise gst.PluginNotFoundError("replaygain")
PluginNotFoundError: replaygain
```

Have I missed something? Do I need to install more? Thanks.

P.S. I'm using Edgy, QL reports 0.25, all QL packages installed via your .debs

---

### Post by hugmenot on 2007-04-08
Ah, I guess Edgy has a gstreamer0.10-plugins-bad that is too old to have RGanalysis support.
What's your version?

---

### Post by robenroute on 2007-04-09
The bad flavour of the gstreamer plugins is 0.10.3+cvs20060918-0ubuntu1. September last year.... could indeed be a tad old.

---

### Post by robenroute on 2007-04-09
Does that mean I'll have to wait for Feisty?

---

### Post by hugmenot on 2007-04-09
Yes, sorry. I overlooked that Edgy is too old.

---

### Post by robenroute on 2007-04-09
> **hugmenot said:**
> Yes, sorry. I overlooked that Edgy is too old.

No worries. Just good to know for everyone. ;-)

---

### Post by sherl0k on 2007-04-13
installing gstreamer0.10-gnomevfs works on Xubuntu 7.04, thanks!

---

### Post by maxter on 2007-04-19
to activate musicbrainz plugin in feisty is still needed a package from 
[http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu)

i used the python-musicbrainz_2.1.4-1_all.deb  package of the edgy repository, because the python-musicbrainz_2.1.4-2_all.deb  has some dependecy problem, and the feisty repository actually does not show any package other than those picard related.

---

### Post by joris1977 on 2007-04-28
Some friends pointed me to last fm. I tried  This [http://www.sacredchao.net/quodlibet/wiki/Plugins](http://www.sacredchao.net/quodlibet/wiki/Plugins) list suggests that it is defunct. Is it? Is there some work around?

---

### Post by hugmenot on 2007-04-28
> **joris1977 said:**
> Some friends pointed me to last fm. I tried  This [http://www.sacredchao.net/quodlibet/wiki/Plugins](http://www.sacredchao.net/quodlibet/wiki/Plugins) list suggests that it is defunct. Is it? Is there some work around?

Use The QLScrobbler plugin, it does the same thing. AudioScrobbler and last.fm were merged.

---

### Post by LKRaider on 2007-05-01
I was using Quod Libet 0.20 that had a nice notification patch, now Feisty upgraded my Quod Libet to 0.24 that only shows a yellow box with the current song name... quite ugly indeed. Is that pacth still available for this version?

---

### Post by nyarla33 on 2007-05-05
Quod Libet 1.0 is out!

Please, can someone build a deb file with mutagen and the plugins (for Feisty)?

[http://www.sacredchao.net/quodlibet/wiki/Download](http://www.sacredchao.net/quodlibet/wiki/Download)

1.0 - Yeah they just showed up one day -- staring.

    * Use Mutagen for ASF/WMA and MP4 support.
    * Add IsPlaying and GetPosition to the D-Bus API. (Mickael Royer)
    * Default "No Cover" image. (Jakub Steiner)
    * Add --unfilter to reset browser filters.
    * Sort --enqueued files, and add --unqueue.
    * Basic SPC (SNES ROM audio) support.
    * Paned Browser speed improvements. (Robert Muth)
    * Errors when playing a song are now logged to a special ~errors tag. It is visible from the Information screen, and can be reset.
    * APEv2 tags can now override Musepack stream Replay Gain settings.
    * Numerous bug fixes, especially in media device handling.
    * Translation Updates:
          o Hungarian. (SZERVÁC Attila)
          o Finnish. (Jari Rahkonen)
          o Galician and Spanish. (Johám-Luís Miguéns Vila)
          o French. (Guillaume Ayoub)
          o Dutch. (Hans van Dok)
          o Japanese. (Yasushi Iwata)

---

### Post by hugmenot on 2007-05-05
> **LKRaider said:**
> I was using Quod Libet 0.20 that had a nice notification patch, now Feisty upgraded my Quod Libet to 0.24 that only shows a yellow box with the current song name... quite ugly indeed. Is that pacth still available for this version?

I ported the patch to serve as a replacement to the "trayicon" plugin.
You can drop the attached file into the plugins/events directory.

I also made new packages with the 1.0 release of Quod Libet. See next post for that, the quodlibet-plugins package includes the plugin as well.

---

### Post by hugmenot on 2007-05-05
Here is a tarball of .deb packages for Quod Libet 1.0 and Mutagen 1.11.
Built on Feisty; I have no idea whether this works on Edgy and earlier.

One significant fix not in the NEWS file is that media keys (Play, Pause) work again.

Here's the NEWS for Mutagen:

1.11 - 2007.04.26
 * New Features:
   * mid3v2 can now set URL frames. (Vladislav Naumov)
   * Musepack: Skip ID3v2 tags. (Luká&#353; Lalinský)
 * Bug Fixes:
   * mid3iconv: Skip all timestamp frames. (Luká&#353; Lalinský)
   * WavPack: More accurate length calculation. ('ak')
   * PairedTextFrame: Fix typo in documentation. (Luká&#353; Lalinský)
   * ID3: Fixed incorrect TDAT conversion. The format is DDMM, not
     MMDD. (Luká&#353; Lalinský)
 * API:
   * Metadata no longer inherits from dict.
   * Relatedly, the MRO has changed on several types.
   * More documentation for MP4 atoms. (Luká&#353; Lalinský)
   * Prefer MP3 for files with unknown extensions and ID3 tags.

---

### Post by nyarla33 on 2007-05-05
Thank you for being so fast!

---

### Post by mudfly on 2007-05-06
thanks for the 1.0 packages!

---

### Post by bramvandijk on 2007-05-08
Thanks!

I have 1 problem however. The musicbrainz plugin is not working anymore. I installed feisty from scratch, and now I don't have python-musicbrainz anymore. There is a package python-musicbrainz2, but installing that one does not help. So is there someone with a .deb for feisty?

---

### Post by gantengx on 2007-05-09
thanks for the package! it's a lot faster than the previous version yay!!! =D

btw, when will it be in the repository?

---

### Post by vinibagio on 2007-05-14
I'm having a strange trouble with this release, tray icon doesn't work anymore:

Traceback (most recent call last):
  File "/home/vini/.quodlibet/plugins/events/fancy-trayicon.py", line 18, in <module>
    import _trayicon as trayicon
ImportError: No module named _trayicon

I also had to symlink my plug-ins directory with /usr/share/quodlibet to my home one, because plug-ins weren't 
detected. My multimedia keys doesn't work either and they're been detected correctly:

  state 0x0, keycode 144 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,

Maybe I'm missing libegg? I'm on Xubuntu.

Should I post a ticket on quodlibet's trac? (I'm not sure they'll support these packages)

---

### Post by hugmenot on 2007-05-14
> **vinibagio said:**
> I'm having a strange trouble with this release, tray icon doesn't work anymore:

Traceback (most recent call last):
  File "/home/vini/.quodlibet/plugins/events/fancy-trayicon.py", line 18, in <module>
    import _trayicon as trayicon
ImportError: No module named _trayicon

Did you install quodlibet-ext? The trayicon itself is wrapped C code.
> 
I also had to symlink my plug-ins directory with /usr/share/quodlibet to my home one, because plug-ins weren't 
detected. 

that sounds weird. They should be picked up from both your home directory and from /usr/share/quodlibet/plugins.
Your path "/home/vini/.quodlibet/plugins/events/" sounds correct
> 
My multimedia keys doesn't work either and they're been detected correctly:

  state 0x0, keycode 144 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,

Maybe I'm missing libegg? I'm on Xubuntu.

No, you need quodlibet-ext for the icon, it replicates libegg. For the MM keys, there's this item in the FAQ:

[COLOR="DimGray"]**My multimedia keys no longer work under GNOME ¶**

GNOME 2.18 implemented an undocumented and crappy D-Bus-based interface that takes control of the multimedia keys on your keyboard while you're running GNOME. [Ronny Haryanto wrote a plugin to support this interface.]("http://www.sacredchao.net/quodlibet/browser/trunk/plugins/events/dbusmmkey.py?format=raw")[/COLOR]
> 
Should I post a ticket on quodlibet's trac? (I'm not sure they'll support these packages)

---

### Post by vinibagio on 2007-05-14
First of all, thanks for the response!! :)

Secondly, thanks for the plugin. Unfortunately, as I don't have Gnome installed, DBUS complains:
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files

I'll try a workaround when I have the time

And, about quodlibet-ext, I do have it (I'm translating the output from DPKG so It may not be exactly the same from the english DPKG) as you can see:

Preparing to substitute quodlibet-ext 1.0-1 (using quodlibet-ext_1.0-1_i386.deb) ...

Unpacking substitute quodlibet-ext ...
Installing quodlibet-ext (1.0-1) ...

I also had trouble trying to install quodlibet from source, but that I'll try to solve myself!

Thanks!

---

### Post by vinibagio on 2007-05-14
I solved all my problems by installing quodlibet from source and, since  the dbmmkeys.py plugin is gnome dependant i made my mmkeys working by setting XFCE's keyboard shortcuts.

But thanks anyways!

---

### Post by bramvandijk on 2007-05-15
> **bramvandijk said:**
> The musicbrainz plugin is not working anymore. I installed feisty from scratch, and now I don't have python-musicbrainz anymore. There is a package python-musicbrainz2, but installing that one does not help. So is there someone with a .deb for feisty?

Installing python-musicbrainz from debian has solved the issue. Still wondering why this package is not in ubuntu:confused:

---

### Post by antiplex on 2007-05-16
> **bramvandijk said:**
> Installing python-musicbrainz from debian has solved the issue. Still wondering why this package is not in ubuntu:confused:

i guess thats because python-musicbrainz is depreciated as they state [[COLOR="DarkOrange"]_*here*_[/COLOR]]("http://wiki.musicbrainz.org/PythonMusicbrainz"). the way i understood it, the depreciated module uses the rdf web-service of musicbrainz which will be shut down soon. 
PythonMusicBrainz2  should use the xml web-service of musicbrainz and therefore will work / be the way to use musicbrainz once the deactivate the 'old' webservice.

but as bramvandijk pointed out earlier, PythonMusicBrainz2 (which is available as a package called 'python-musicbrainz2' for feisty) is not working with the plugin. guess someone with a decent python/PythonMusicBrainz2 experience has to re-write/fix the original musicbrainz-plugin.

bad i have no clue about coding with python at all :( 


different question:
how does the cddb-plugin for QL work? i installed the package 'python-cddb' and no longer get any errors from the cddb plugin. it appears correctly when i right-click some song or album in the plugins-menu as 'CDD lookup' but when i select it, nothing appears to happen... am i missing something? how's one supposed to fill missing tag-fields like trackname or discid etc by using this plugin?

---

### Post by hugmenot on 2007-05-16
> **antiplex said:**
> 
different question:
how does the cddb-plugin for QL work? i installed the package 'python-cddb' and no longer get any errors from the cddb plugin. it appears correctly when i right-click some song or album in the plugins-menu as 'CDD lookup' but when i select it, nothing appears to happen... am i missing something? how's one supposed to fill missing tag-fields like trackname or discid etc by using this plugin?

It works by computing the Disc ID of an album, which is derived from the aggregated track lenghts of all titles from a CD. So, make sure you select all tracks, they have to be in the correct order from top to  bottom, and then select the menu item. There should be a dialod popping up.

---

### Post by antiplex on 2007-05-18
> **hugmenot said:**
> ...There should be a dialog popping up.
hmmm, this is not happening in my case :confused: weird...

but anyway, i just realized that the musicbrainz plugin might be far more useful to me since some of my mp3's might have its silences removed at its ends/beginnings so the cddb lookup might not work correctly. musicbrainz should be fine though since it fingerprints the music by using the [_[COLOR="DarkOrange"]*musicdns*[/COLOR]_]("http://www.musicip.com/dns/index.jsp") standard... so hopefully someone will update the musicbrainz plugin to the python-musicbrainz2 package/version soon...

---

### Post by sadako1 on 2007-05-26
Hey, I followed Highplanesdrifter's instructions to the letter to install this file and when it completed it wouldn't run and there was no icon in the Applications menu. I've since tried to uninstall it using the instructions barebones gave and all I got was the same "no rule to make target" message. I'm definitely in the directory that the "make install" command was run in. 

I can't run the prog, I can't uninstall it and I can't install or use any later versions. I really want to use this prog - I've hear it's *almost* as good as foobar2000 in Windows and I'd like to be able to find out!

It was the 0.17.1 files (old, probably, I know, but I'm new to this and impatient :))

Thanks in anticipation!
Andrew

---

### Post by foxy123 on 2007-05-27
> **sadako1 said:**
> Hey, I followed Highplanesdrifter's instructions to the letter to install this file and when it completed it wouldn't run and there was no icon in the Applications menu. I've since tried to uninstall it using the instructions barebones gave and all I got was the same "no rule to make target" message. I'm definitely in the directory that the "make install" command was run in. 

I can't run the prog, I can't uninstall it and I can't install or use any later versions. I really want to use this prog - I've hear it's *almost* as good as foobar2000 in Windows and I'd like to be able to find out!

It was the 0.17.1 files (old, probably, I know, but I'm new to this and impatient :))

Thanks in anticipation!
Andrew

why not to use QL from repos or debs kindly provided by hugmenot?

---

### Post by sadako1 on 2007-05-27
yeah, I was impatient, like I said. This Linux migration's a heavy affair - I've been spending about 12 hours a day reading and learning. It was 4am and I really couldn't be bothered looking any harder for the files I wanted, so I just followed the first thing I saw which was the first post of this thread! Silly, really, cos it took me a lot longer and caused a lot more hassle than I would have had if I'd read to the end! Lesson learned. Anyway, I sorted it in the end and now I've got v1.0 installed and I'm quite happy with it.

Are there any upsampling modules for this like there are with foobar2000? That'd be pretty handy - my DACs work better with a higher sample rate (up to ~176kHz'd be nice).

Thanks for taking the time to comment,
Andrew

---

### Post by lo_mein_dreams on 2007-06-07
I have a question. On [http://www.sacredchao.net/quodlibet/wiki/FAQ](http://www.sacredchao.net/quodlibet/wiki/FAQ) they explain how to activate special characters, but I am unable to understand what to do. Could someone explain it to me? I'd like my Chinese characters to work.

---

### Post by Echow on 2007-06-09
I was just wondering, how d you let quodlibet open a file by just double clicking it from nautilus/thunar? I've tried using --play-file= and --play-file but they both don't seem to work.

---

### Post by loreweaver on 2007-06-19
> [SIZE="4"]Unable to open audio device[/SIZE]

Quod Libet tried to access the 'autosink' and '' drivers but could not open them. Set your GStreamer pipeline by changing the
    pipeline = 
line in ~/.quodlibet/config.

I'm getting this error message after installing it from the .deb package in getdeb.net.
Any idea what the problem is?

---

### Post by foxy123 on 2007-07-05
FreeDB pugin does work for me. I've got the following error:
```
~$ exfalso 
/usr/share/quodlibet/plugins/editing/resub.py:1: DeprecationWarning: The sre module is deprecated, please import re.
  import sre
Traceback (most recent call last):
  File "/usr/share/quodlibet/plugins/songsmenu.py", line 149, in __handle
    try: ret = map(plugin.plugin_album, albums)
  File "/home/foxy/.quodlibet/plugins/songsmenu/cddb.py", line 197, in plugin_album
    update_discinfo(box)
  File "/home/foxy/.quodlibet/plugins/songsmenu/cddb.py", line 176, in update_discinfo
    info = query(cat, discid, xcode=xcode)
  File "/home/foxy/.quodlibet/plugins/songsmenu/cddb.py", line 74, in query
    save = file(dump, 'wU')
ValueError: universal newline mode can only be used with modes starting with 'r'

```
any idea what is it?

---

### Post by hugmenot on 2007-07-06
The plugin has been updated to fix this:

[https://svn.sacredchao.net/svn/quodlibet/trunk/plugins/songsmenu/cddb.py](https://svn.sacredchao.net/svn/quodlibet/trunk/plugins/songsmenu/cddb.py)

---

### Post by foxy123 on 2007-07-06
> **hugmenot said:**
> The plugin has been updated to fix this:

[https://svn.sacredchao.net/svn/quodlibet/trunk/plugins/songsmenu/cddb.py](https://svn.sacredchao.net/svn/quodlibet/trunk/plugins/songsmenu/cddb.py)

no, it does not :( I've got the same error...

---

### Post by hugmenot on 2007-07-06
Hm, not? Then go into the file and insert an r in front of the w in that line. Does that help?

---

### Post by foxy123 on 2007-07-06
> **hugmenot said:**
> Hm, not? Then go into the file and insert an r in front of the w in that line. Does that help?

yes, great! cheers a lot.

---

### Post by mroven on 2007-07-31
I got version 1.0 installed on Xubuntu Fiesty - thanks to this thread.

I cannot see a way of listening to internet radio stations.  Any suggestions?

TIA

---

### Post by QwUo173Hy on 2007-08-06
Thank you! I have 1.0 installed with Tray Icon and Multimedia Keys thanks to this post! I'll look into the music brainz in the future. It sounds interesting.

---

### Post by Ashly on 2007-08-11
Hi all. Just wondering, how do you use the Audio Feeds view?

I've Just installed Quod Libet 1.0, and can't find it. The view menu only has:
[LIST]
[*]Disable Browser
[*]Search Library
[*]Playlists
[*]Paned Browser
[*]Album List
[*]File System
[*]Internet Radio
[*]Media Devices
[/LIST]

Thanks. :-)

---

### Post by hugmenot on 2007-08-11
You need "*python-feedparser*" It seems to be not a hard dependency, that is why the browser doesn't show up.

---

### Post by Claire on 2007-08-24
For some reason, every time I try running Quod Libet, it refuses to run and instead spits this out at me:

:~$ quodlibet
Supported formats: mod, mp3, mp4, mpc, trueaudio, wav, wavpack, wma, xiph
Traceback (most recent call last):
  File "/usr/local/bin/quodlibet", line 304, in <module>
    main()
  File "/usr/local/bin/quodlibet", line 33, in main
    library = load_library()
  File "/usr/local/bin/quodlibet", line 258, in load_library
    lib = library.init(const.LIBRARY)
  File "/usr/local/share/quodlibet/library/__init__.py", line 38, in init
    library.load(cache_fn, skip=formats.supported)
  File "/usr/local/share/quodlibet/library/_library.py", line 124, in load
    try: items = pickle.load(fileobj)
EOFError

Does anyone know why this is??  At one point, it worked for me (back on Edgy, maybe, or perhaps it was Dapper).  All I know is I'm sick of Rhythmbox and I want Quod Libet back . . .

---

### Post by hugmenot on 2007-08-24
pickle.load is the function loading your songs library and EOFError (end of file) tells you it is truncated or otherwise corrupt. Try moving it to another place and then start QL again.
You can find it in your home dir at ~/.quodlibet/songs.

You might also want to install a newer QL package from further up in this thread. Your script based install in /usr/local will rot forever and never be updated. You'd need to purge it from /usr/local by hand, however.

---

### Post by Canada3332 on 2007-08-25
I get the following python error when I try and import my [large] MP3 library into Quodlibet.

Traceback (most recent call last):
  File "/usr/share/quodlibet/formats/__init__.py", line 52, in MusicFile
    return _infos[ext](filename)
  File "/usr/share/quodlibet/formats/_id3.py", line 86, in __init__
    audio = self.Kind(filename, ID3=ID3hack)
  File "/usr/lib/python2.4/site-packages/mutagen/__init__.py", line 74, in __init__
    self.load(filename, *args, **kwargs)
  File "/usr/lib/python2.4/site-packages/mutagen/id3.py", line 1914, in load
    self.info = self._Info(fileobj, offset)
  File "/usr/lib/python2.4/site-packages/mutagen/mp3.py", line 97, in __init__
    self.__try(fileobj, offset, size - offset, False)
  File "/usr/lib/python2.4/site-packages/mutagen/mp3.py", line 134, in __try
    raise HeaderNotFoundError("can't sync to an MPEG frame")
HeaderNotFoundError: can't sync to an MPEG frame

---

### Post by Mr_Arne on 2007-08-26
Hello,
Just a little question before I get to work with this; is qoud libet supporting DAAP as a distribution protocol on LAN? I have a MSS disk on my LAN, with mt-daapd running. Rhythmbox works like a charm with this (15700 tracks and growing...:D), but the tagging tool sounds as a good reason to try it.

Cheers
Ola

---

### Post by hugmenot on 2007-08-26
> **Mr_Arne said:**
> Hello,
Just a little question before I get to work with this; is qoud libet supporting DAAP as a distribution protocol on LAN? I have a MSS disk on my LAN, with mt-daapd running. Rhythmbox works like a charm with this (15700 tracks and growing...:D), but the tagging tool sounds as a good reason to try it.


In short, no.

---

### Post by Echow on 2007-09-05
Hey all, has anyone noticed that the quodlibet site is down atm? Have they moved website or something?

---

### Post by urukrama on 2007-09-05
Works fine here. You're trying to reach [http://www.sacredchao.net/quodlibet/](http://www.sacredchao.net/quodlibet/) right?

---

### Post by hugmenot on 2007-09-05
Try a browser other than IE.

---

### Post by Echow on 2007-09-07
Ahhh nice one. I had Opera pretending to be IE. Thanks.

---

### Post by jofre on 2007-09-30
Hi everyone, 

I just discover this audio player and looks promising, but I have problems with the fist plug in I downloaded, the FreeDB plugin, i get the following error message(I just compile the 1.0version):

traceback (most recent call last):
  File "/home/tango/.quodlibet/plugins/songsmenu/cddb.py", line 9, in <module>
    import CDDB
ImportError: No module named CDDB:(

I install the cddb from synaptic, thinking I had to install something, but I still get the same error message.

thanks folks,:)
Jofre

---

### Post by doris.houng on 2007-09-30
> **jofre said:**
> I install the cddb from synaptic, thinking I had to install something, but I still get the same error message.

The package you need to install is **python-cddb**. :)

---

### Post by jofre on 2007-09-30
Thanks! no problems now!

Well, kind of...

I have spend the whole bloody weekend working on this things and I still do not have what I wanted.

I am trying to put all my cds in to the pc. So after looking a fair bit around, seems that the best lossless format is wavpack. 

The problem is that Grip does not rip to WavPack. So I could use it to ripped and then from command line transform the *.wav to *.wv but all the tagging information was gone, and also I do not really like the way that Grip puts the taggs...

I try Easytag, but it did not want to see my *.wv files for some reason.

Then I put Banshee, which is quite cool but seem very heavy and slow. But it has a nice ripper utility, and the tagging is just perfect, so I thought, that's it, I use Banshee to rip and QuodLibet to actually manage and listen my music.
But when I tried to load the freshly created *.wv files with QL I get:

WavPackHeaderError: not a WavPack file

But I have no problem playing the files with Banshee!

(I use the very high compression, with check sum MD5)

If anybody has an idea of the possible "why", I would appreciated as QL seems much well done inside(good code=speed), while Banshee seems too focus in "looking good".

Thanks a million,
Jofre

---

### Post by hugmenot on 2007-09-30
Run mutagen-inspect on a .wv file in a terminal and look whether it contains the appropriate APEv2 tags.

Other rippers are abcde and RubyRipper, which has a GTK GUI.

---

### Post by jofre on 2007-09-30
Thanks.

Rubyripper seems quite good, but I am doing something wrong because there is no output file!

In "Codecs", I choose "Other = /usr/bin/wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%g" -w "Year=%y" -w "Track=%n" -w "Genre=%m" -f %i.wav"

I am not sure about the %i.wav, anybody knows what is the correct way? There is no encoding happening!

I tried as well with just %i, but without luck.

Any ideas?

Thanks again,
Jofre

---

### Post by jofre on 2007-10-01
Well, after a while still I have not find how to use rubyripper.

But, I found a post ([http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)) that explain what I need to do using Grip.

And yes, I tried to do the same in RubyRipper, changing:

-o %m %w

by:

-o %i %o

which I understand as the equivalent command.

So well, I will sleep better now (here in Paris is 22.39) knowing that I finally can build up my music library.

Goodnight,
Jofre

---

### Post by nyarla33 on 2008-09-10
Hello all 
A new version is out.

**Quod Libet**

1.999 - It has been a memorable day
 * Fix playlist error when loading songs.
 * Unlock device when "stop" mmkey is pressed. (Javier Kohen, I#6)
 * Restart song when rewinding and > 0.5s in. (Javier Kohen, I#7)
 * Updated Galician and Spanish translations. (Johám-Luís Miguéns Vila)
 * Make requirements consistent across all documentation.

1.99 - It is impossible to know if my dream came true
 * New distutils-based build/test/install system.
 * Multiple audio backend support.
   * Xine-based audio backend.
   * "Null" backend for Ex Falso.
 * Tag Editing:
   * Tags From Path: "<~>" will eat a string but not save it.
   * Track Numbers: Allow numbering up to 999.
 * Show image files in Ex Falso.
 * Direct output to console and to a debugging window.
   * Functions are accessible to plugins as print_d, print_e, and print_w.
 * default_rating configuration option. (Robert Muth)
 * Many bug fixes and performance improvements.


[http://code.google.com/p/quodlibet/](http://code.google.com/p/quodlibet/)

Please, can someone build a deb file with mutagen and the plugins?

---

### Post by sexcopter on 2008-09-16
> **nyarla33 said:**
> Hello all 
A new version is out.

In fact, I've just seen that version 2.0 has just been released!

I too would like to see a deb for this. I tried downloading their tar.gz, and can run it from that folder, but cannot see how to install it (I think they assume a greater level of understanding than what I have).

Even better would be for this to appear in backports.

Thanks,
James.

---

### Post by hugmenot on 2008-09-17
> **sexcopter said:**
> In fact, I've just seen that version 2.0 has just been released!

I too would like to see a deb for this. I tried downloading their tar.gz, and can run it from that folder, but cannot see how to install it (I think they assume a greater level of understanding than what I have).


Well, they use the regular install mechanism for Python software. Did you bother to read the README?

./setup.py build
sudo ./setup.py install

But this will clutter your /usr/local/ tree with files untracked by dpkg. And there is nothing equivalent to &#8220;make uninstall&#8221;. Many have spammed the forums and mailing lists with weird problems before because they had stray files cluttering their system.
Don&#8217;t do it.

Perhaps I&#8217;ll give packaging a shot soonish. But I expect that it will pop up in Debian in a few days, so I can save some work.

---

### Post by davidw89 on 2008-09-17
Set by Step guide to install this please

---

### Post by sexcopter on 2008-09-17
> **hugmenot said:**
> Well, they use the regular install mechanism for Python software. Did you bother to read the README?

./setup.py build
sudo ./setup.py install


I did read the README, and I quote:

> Quod Libet requires the PyGTK development libraries, intltool, and the
Python distutils suite to build and install. You can do this with
 $ ./setup.py build
 $ ./setup.py install


Which sounds to me as if it doesn't install quodlibet itself, but rather those dependencies it requires. Either the README isn't clear, or ./setup.py isn't for installing quodlibet itself. In any case, I tried it and got an error with status 1, so I didn't bother trying to install it.

If it appears in the Debian repos in the coming days, can we simply download it and install in Ubuntu with dpkg? Also, do you think the dependencies will be available in deb as well?

Thanks,
James.

---

### Post by hugmenot on 2008-09-17
> **sexcopter said:**
> 
Which sounds to me as if it doesn't install quodlibet itself, but rather those dependencies it requires. Either the README isn't clear, or ./setup.py isn't for installing quodlibet itself. In any case, I tried it and got an error with status 1, so I didn't bother trying to install it.

But this is how you install it manually. It&#8217;s the equivalent of make; make install.
> 
If it appears in the Debian repos in the coming days, can we simply download it and install in Ubuntu with dpkg? Also, do you think the dependencies will be available in deb as well?

It remains to be seen when this gets uploaded to Debian. I&#8217;ve seen that some stuff was refactored, so I would just re-use the updated packaging. If the debs are binary compatible with your Ubuntu version is unclear. It might very well not, because there&#8217;s some binary code in Quodlibet.


EDIT: try apt-get build-dep quodlibet

---

### Post by QwUo173Hy on 2008-09-17
I've been to their freshmeat page as well as their google page and I can't find any info on the new features in version 2.0. I looked in the tarball and just found these changes since 1.0. Is there anything noticeable different in 2.0 since 1.0?

> .0 - Once upon a time there was a radical guy!
 * Make Escape a synonym for Ctrl+W in QLTK Windows. (I#8)
 * Actually fix playlist error.
 * Fix Xine backend "Stop" behavior.

1.999 - It has been a memorable day
 * Fix playlist error when loading songs.
 * Unlock device when "stop" mmkey is pressed. (Javier Kohen, I#6)
 * Restart song when rewinding and > 0.5s in. (Javier Kohen, I#7)
 * Updated Galician and Spanish translations. (Johám-Luís Miguéns Vila)
 * Make requirements consistent across all documentation.

1.99 - It is impossible to know if my dream came true
 * New distutils-based build/test/install system.
 * Multiple audio backend support.
   * Xine-based audio backend.
   * "Null" backend for Ex Falso.
 * Tag Editing:
   * Tags From Path: "<~>" will eat a string but not save it.
   * Track Numbers: Allow numbering up to 999.
 * Show image files in Ex Falso.
 * Direct output to console and to a debugging window.
   * Functions are accessible to plugins as print_d, print_e, and print_w.
 * default_rating configuration option. (Robert Muth)
 * Many bug fixes and performance improvements.

---

### Post by sexcopter on 2008-09-17
> **hugmenot said:**
> 
EDIT: try apt-get build-dep quodlibet

I tried this and there was a ton of stuff to install. Then tried build and install and it worked! It installed quodlibet 2.0 and it works fine so far.

Now I just hope I don't run into too much trouble with files scattered around the filesystem.

Thanks,

James.

---

### Post by hugmenot on 2008-09-18
> **sexcopter said:**
> I tried this and there was a ton of stuff to install. Then tried build and install and it worked! It installed quodlibet 2.0 and it works fine so far.

Now I just hope I don't run into too much trouble with files scattered around the filesystem.


I case you ever want to go back to the official version, you would need to clean out the manual install first because it would be found with precedence in the /usr/local tree. Finding the folders of the manual install would go like this:

```
find /usr/local -name quodlibet
```
you could even directly delete them in one go. But that is a bit **more risky**:
```
find /usr/local -name quodlibet | xargs sudo rm -rf 
```
only run &#8593; after you determined all output of the first command is safe to delete.

---

### Post by sojusnik on 2008-09-26
I'm searching for a .deb package for hardy 64-bit of quod libet 2.0.

---

### Post by moopoo on 2008-10-30
Semi Bump.

I really am looking forward to a 32 bit deb-package of ql 2.0, since I am unable to install it via the script. But that is another story.

---

### Post by BrunoC on 2008-10-30
yes, it would be very nice to have 32 bit deb package of quodlibet 2.0 for ubuntu 8.10.

---

### Post by KhaaL on 2008-11-05
adding my vote for a .deb!

---

### Post by moopoo on 2008-11-11
about the deb for ql 2.0:

is that the point where people start a poll? i already contacted getdeb.net but they didn't respond.

---

### Post by jsteinhart on 2008-11-26
FYI, I've made UNOFFICIAL, *UNSUPPORTED* packages of this for my own jollies, and placed them in my PPA here (for your jollies!):

deb [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main

You need to get quodlibet, quodlibet-ext, quodlibet-plugins, and exfalso

You can either download them individually (e.g. via your browser) or add the above lines to your /etc/apt/sources.list, do an update, and install/upgrade them.

Although these should be considered experimental/untested, they have been working for me for the last day or so...  but your mileage may vary.

This is based on the quodlibet-2.0 code from code.google.com, and the current quodlibet-plugins source package from debian unstable (20080601-1).

---

### Post by prismatic7 on 2008-11-27
> **jsteinhart said:**
> FYI, I've made UNOFFICIAL, *UNSUPPORTED* packages of this for my own jollies, and placed them in my PPA here (for your jollies!):

deb [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main

You need to get quodlibet, quodlibet-ext, quodlibet-plugins, and exfalso

You can either download them individually (e.g. via your browser) or add the above lines to your /etc/apt/sources.list, do an update, and install/upgrade them.

Although these should be considered experimental/untested, they have been working for me for the last day or so...  but your mileage may vary.

This is based on the quodlibet-2.0 code from code.google.com, and the current quodlibet-plugins source package from debian unstable (20080601-1).

Thanks for the PPA, but I've noticed a problem - exfalso is not available! This breaks installation...

EDIT: **Actually, no - I'm wrong... I have some kind of weird dependency thing going on... please ignore**

---

### Post by moopoo on 2008-11-28
> **jsteinhart said:**
> FYI, I've made UNOFFICIAL, *UNSUPPORTED* packages of this for my own jollies, and placed them in my PPA here (for your jollies!):

Thanks mate! Finally!

Update: Works like a charm.

---

### Post by agmk on 2008-12-02
> **prismatic7 said:**
> Thanks for the PPA, but I've noticed a problem - exfalso is not available! This breaks installation...

EDIT: **Actually, no - I'm wrong... I have some kind of weird dependency thing going on... please ignore**

I had one too, but removing quodlibet and retrying seemed to fix it :)

---

### Post by moopoo on 2008-12-07
As the title suggests, the Quod Libet tray icon has suddenly disappeared on my intrepid machine. Everything was fine until yesterday, using [jsteinhart's ppa for Quod Libet 2.0]("http://ubuntuforums.org/showpost.php?p=6254605&postcount=258"). I haven't changed anything related to Quod Libet, only installed and then purged alltray once.

Quod Libet's plugin manager spits out this message, which I hope. someone is able to interpret:

```

#trayicon
Traceback (most recent call last):
  File "/usr/share/quodlibet/quodlibet/plugins/events/trayicon.py", line 17, in <module>
    import _trayicon as trayicon
  File "/usr/share/quodlibet/quodlibet/__init__.py", line 123, in import_ql
    old_import("quodlibet." + module, *args, **kwargs)
ImportError: No module named _trayicon
```

Tried complete removal and reinstall, with no avail. Any help would be appreciated.

**Update:**
Now that I look into the plugin manager more closely, I see more references to "missing modules":

```

#brainz
Traceback (most recent call last):
  File "/usr/share/quodlibet/quodlibet/plugins/songsmenu/brainz.py", line 4, in <module>
    import musicbrainz, os, gtk, re
  File "/usr/share/quodlibet/quodlibet/__init__.py", line 123, in import_ql
    old_import("quodlibet." + module, *args, **kwargs)
ImportError: No module named musicbrainz

#cddb
Traceback (most recent call last):
  File "/usr/share/quodlibet/quodlibet/plugins/songsmenu/cddb.py", line 9, in <module>
    import CDDB
  File "/usr/share/quodlibet/quodlibet/__init__.py", line 123, in import_ql
    old_import("quodlibet." + module, *args, **kwargs)
ImportError: No module named CDDB

#lastfmsubmit
Traceback (most recent call last):
  File "/usr/share/quodlibet/quodlibet/plugins/events/lastfmsubmit.py", line 12, in <module>
    import lastfm.client, lastfm.marshaller
  File "/usr/share/quodlibet/quodlibet/__init__.py", line 123, in import_ql
    old_import("quodlibet." + module, *args, **kwargs)
ImportError: No module named lastfm.client

#trayicon
Traceback (most recent call last):
  File "/usr/share/quodlibet/quodlibet/plugins/events/trayicon.py", line 17, in <module>
    import _trayicon as trayicon
  File "/usr/share/quodlibet/quodlibet/__init__.py", line 123, in import_ql
    old_import("quodlibet." + module, *args, **kwargs)
ImportError: No module named _trayicon

```

---

### Post by lazka on 2008-12-08
the failing part is:

```
try:
    import egg.trayicon as trayicon
except ImportError:
    import _trayicon as trayicon
```

install "python-gnome2-extras" for egg.trayicon

---

### Post by moopoo on 2008-12-09
> install "python-gnome2-extras" for egg.trayicon

Thank you. That solved the tray icon problem.

---

### Post by tv0571 on 2009-01-05
> **jsteinhart said:**
> FYI, I've made UNOFFICIAL, *UNSUPPORTED* packages of this for my own jollies, and placed them in my PPA here (for your jollies!):

deb [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main

You need to get quodlibet, quodlibet-ext, quodlibet-plugins, and exfalso

You can either download them individually (e.g. via your browser) or add the above lines to your /etc/apt/sources.list, do an update, and install/upgrade them.

Although these should be considered experimental/untested, they have been working for me for the last day or so...  but your mileage may vary.

This is based on the quodlibet-2.0 code from code.google.com, and the current quodlibet-plugins source package from debian unstable (20080601-1).
This looks like just the ticket... but I'm getting an error -- that may have nothing to do with the QL packages:
1. I upgraded to intrepid.
2. I added the PPA sources to synaptic
3. I go find the 3 QL packages and mark for upgrade.
4. Synaptic shows "4 to install/upgrade, 1 to remove"
5. *Apply* shows the package to be removed is nvidia-glx.
6. When the changes try to run, I get an error on this package removal:
E: nvidia-glx: subprocess post-removal script returned error exit status 2
The details on it indicate error checking /usr/x11R6/lib/modules/extensions/libglx.a no such file or directory.

The entire installation aborts.

I can't figure out a way to tell synaptic to ignore libglx as it can't be unmarked.  It also won't allow reinstallation.

Can someone step me through a fix?  Thanks!

---

### Post by BrunoC on 2009-02-08
> **jsteinhart said:**
> FYI, I've made UNOFFICIAL, *UNSUPPORTED* packages of this for my own jollies, and placed them in my PPA here (for your jollies!):

deb [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jsteinhart/ubuntu](http://ppa.launchpad.net/jsteinhart/ubuntu) intrepid main

You need to get quodlibet, quodlibet-ext, quodlibet-plugins, and exfalso

You can either download them individually (e.g. via your browser) or add the above lines to your /etc/apt/sources.list, do an update, and install/upgrade them.

Although these should be considered experimental/untested, they have been working for me for the last day or so...  but your mileage may vary.

This is based on the quodlibet-2.0 code from code.google.com, and the current quodlibet-plugins source package from debian unstable (20080601-1).

thank you! it worked fine. :)

---

### Post by hallu on 2010-01-05
**quodlibet-unstable      **

[https://launchpad.net/~lazka/+archive/dumpingplace]("https://launchpad.net/%7Elazka/+archive/dumpingplace")

Gapless Playback & Conditional Tags!

---

### Post by hugmenot on 2010-02-02
New version 2.2 [is out]("http://groups.google.com/group/quod-libet-development/browse_thread/thread/cb7aee4c2cbae222").

NEWS:
```
2.2 (2010-02-02) - I know you are enjoying that song but a woman DIED 
 * Saved searches extended to Album and Paned browsers [41]. 
 * Human sorting is now used in Album and Paned browsers [190]. 
 * Windows is now supported (for real this time). 
 * foobar2000's broken TXXX:DATE now supported [220]. 
 * Warnings are now printed for many missing dependencies. 
 * Fixes for device backends. 
 * Lyric downloading disabled until it can be fixed [273]. 
 * Editing both key and value with multiple keys fixed (extruded) [393]. 
 * Plugin changes: 
   * AnimOSD: major update (Andreas Bombe, Christine Spang) [387]. 
   * MusicBrainz: major update. 
   * Random Album: Changed algorithm to increase fairness. 
   * QLScrobbler: Custom patterns for title and artist. 
   * Last.fm Sync: new plugin to sync stats from Last.fm. 
   * Notify OSD, Album Art: Minor fixes. 
 * Translations: 
   * Galician, Spanish (Johám-Luís Miguéns Vila). 
   * French (Bastien Gorissen). 
2.1.98 (2010-01-04) - How are you going to convince people to use it? 
 * Christoph Reiter is now a maintainer. 
 * The GStreamer backend is now gapless [49]. 
 * Win32 is once again supported [248]. 
 * ID3 tags are removed from FLAC files upon saving [124]. 
 * File extensions are converted to lowercase upon renaming [66]. 
 * Thumbnails are now generated for artwork [140]. 
 * Inline searches in the album list can now match people [239]. 
 * Embedded album art is now supported in FLAC files [255]. 
 * Bitrates are now reported in kbps. Library reload required [79]. 
 * Additional ReplayGain settings (Nick Boultbee) [132]. 
 * Tag splitting setting is now order-sensitive [74]. 
 * Paned browser now supports patterns for panes [45]. 
 * Numeric columns have been given a few tweaks (Johan Hovold) [81]. 
 * New ratings column options (Johan Hovold, Bastien Gorissen) [82, 83]. 
 * Renaming when symlinks present no longer raises error (Philipp Weis) [353]. 
 * Xine backend uses software volume control (Markus Koller) [370]. 
 * Song positions are now saved and restored when quitting [218]. 
 * DeviceKit-Disks (UDisks) supported for device discovery [252]. 
 * Plugin changes: 
   * New playlist export plugin [30]. 
   * New queue only playorder plugin [43]. 
   * New Python console plugin. [229] 
   * Updated trayicon plugin [158]. 
   * Updated album art plugin (Eduardo Gonzalez) [139]. 
   * Updated qlscrobbler plugin (Nicholas J. Michalek) [376]. 
   * Updated lastfmsubmit plugin [292]. 
 * Translations: 
   * Russian (Anton Shestakov) [274]. 
   * Turkish (Türerkan &#304;nce). 
   * German (Rüdiger Arp). 
 * Many bug fixes and performance improvements. 
```

---

### Post by canadiandude007 on 2010-03-07
Since Karmic only has version 2.1 in dep repository, have to install this manually.

Remember to run:

```
sudo apt-get build-dep quodlibet
```

To ensure you have all the dependencies installed before installing quodlibet from source.

[http://code.google.com/p/quodlibet/wiki/Guide_Requirements](http://code.google.com/p/quodlibet/wiki/Guide_Requirements)

Then after downloading and extracting version 2.2, run ...

```
sudo ./setup.py --verbose build
```

Then with no errors, run ...

```
sudo ./setup.py --verbose install
```

All should be good, but also grab the latest plugins for 2.2 and copy them to the proper folder after you start quod libet for the first time.

---

### Post by canadiandude007 on 2010-03-07
Actually a better way to install the plugins for quod libet is to use Mercurial.

```
sudo apt-get install mercurial
```

followed by ...

```
cd ~/.quodlibet
```
```
hg clone http://quodlibet.googlecode.com/hg/ quodlibet_hg
```
```
ln -s quodlibet_hg/plugins
```

---

### Post by lazka on 2010-03-07
Or even better, just use the PPA Version I posted before..

[https://launchpad.net/~lazka/+archive/ppa](https://launchpad.net/~lazka/+archive/ppa)
[https://launchpad.net/~lazka/+archive/dumpingplace](https://launchpad.net/~lazka/+archive/dumpingplace)

---

