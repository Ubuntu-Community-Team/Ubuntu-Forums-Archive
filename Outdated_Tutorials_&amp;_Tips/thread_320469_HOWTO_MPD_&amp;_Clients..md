---
title: "HOWTO: MPD &amp; Clients."
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by JMO707 on 2006-12-17
This is a traduction I made of [this guide]("http://www.ubuntuforums.org/showthread.php?t=312428") because of the request of elektronaut. Hope you like it, and forgive my language mistakes :p

***Music Player ***[***Daemon***]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29")*** (MPD)** is a music player which allows for remote access from another computer. An example would be a *[*headless*]("http://en.wikipedia.org/wiki/Headless")* computer running MPD and using one of the available front ends to control it remotely. It also makes for a good desktop *[*media player*]("http://en.wikipedia.org/wiki/Media_player")*, particularly if you either don't use or frequently restart *[*X*]("http://en.wikipedia.org/wiki/X_Window_System")[I].
It utilizes a database (like other music players) to store the basic music file information for each file. Instead of playing files from the filesystem, it plays music from the MPD library. Once the daemon is started, the database is kept entirely in-memory, and there is no disk access necessary to lookup or search for a song. The text file database is only used to maintain the contents of the database when MPD is not running.[/I] [[Wikipedia]("http://en.wikipedia.org/wiki/Music_Player_Daemon")]


 Have in mind too that it consumes very little resources. In this moment it is taking away only 1,9 Mbytes of my memory. A front-end doesnt adds enough to reach the 10 Mbytes, and how it isnt required to play music, a playlist cat be left playing, and closing it we will be back to the 1,9 Mbytes.
 

 I think that the bigest obstacule that I might have for this guide is the dependencies issue.  As we are going to install 4 programs and various plugins, this, plus that I want to try being as neutral as I can with the distros in wich this can be used, can make things complicated. I will extract them directly from the official pages. Hope you can forgive this too.
 
Now we are going to install: MPD. libmpd, ncmpc, gmpc (with: coveramazon, lyrics, wikipedia, last.fm & qosd)

This is a screen to see how gmpc looks: 

[[IMG]http://img117.imageshack.us/img117/6162/pantallazohd4.th.png[/IMG]]("http://img117.imageshack.us/my.php?image=pantallazohd4.png")

···········
[COLOR=Red]
**_MPD (Music Player Daemon)_**[/COLOR] 

Lets see firsth the dependencies [acording to the oficial MPD site]("http://www.musicpd.org/install.shtml"):
[I]
**Requirements**
1) [/I][*libao*]("http://www.xiph.org/ao")[I] libraries and headers are required!
2) [/I][*zlib*]("http://www.gzip.org/zlib")[I] libraries and headers are required!

Libs included with source (i.e. nothing needed for these): [/I][*libid3tag*]("http://mad.sf.net/")* and *[*libmad*]("http://mad.sf.net/")[I]
Optional
1) for ogg vorbis support: [/I][*libogg*]("http://www.xiph.org/ogg")* and *[*libvorbis*]("http://www.xiph.org/ogg/vorbis")[I]
2) for flac support: [/I][*flac*]("http://flac.sf.net/")[I] 1.1
3) for wave/aiff/au support: [/I][*audiofile*]("http://www.68k.org/%7Emichael/audiofile/")[I]
4) for MP4/AAC support: [/I][*FAAD2*]("http://www.audiocoding.com/")[I]
5) for Mod support: [/I][*libmikmod*]("http://mikmod.raphnet.net/")


 [LEFT]Ive tryed every link, and exempting the one of*  libvorbis* (that can be found on the *libogg* link) the rest works fine. Of course, if you got the possibility of using a package manager for this, it will be simpler. That is given like something understood from now on.

**Addendum:** It has passed to me that not everyone may have *svn* installed. This is the link to the official page: [http://subversion.tigris.org/](http://subversion.tigris.org/)

Once than the dependencies are installed, lets download MPD from the subversion repository:

*svn co *[*https://svn.musicpd.org/mpd/trunk*]("https://svn.musicpd.org/mpd/trunk")* mpd*

That from a terminal, clear in is. Next we enter to the just downloaded *mpd* folder and execute in the  terminal:

[I],/autogen.sh
make
sudo make install[/I]

Three things...
Firsth, in the output of ,*/autogen.sh* can be seen with wich libraries are MPD compiled, and therefore which things support. Its a good idea look that everything is fine before we continue.
Second, that if making *sudo make install* can be avoided, so system wide, better. If you can build packages with some tool, I recommend you to do that, if not you can always use a prefix, lets say *sudo make install &#8211;**prefix=/usr/local/*** for example. That will let you put some order in the installation. This is worth for everything we install from now on.
Third, for comfort Ill use my paths on this tutorial. Change them according to yours.

Ok. Now we got MPD, but this doesnt end here.
The next step is configure it. Start editing with root permmisions the *mpd.conf *file that is on */etc*. Example: *sudo nano /etc/mpd.conf*
You will find a lot of options, but the ones who are from our interest are:


*pid_file "/var/run/mpd/pid" *

Comment this line, putting a # in front of it. We do that because the pid file isnt created whit the installation and later MPD wouldnt start if it look for it.


[I]#mixer_type "alsa"
#mixer_device "default"
#mixer_control "PCM" [/I]

If you use ALSA, I reccomend to uncomment the lines from above and replace *PCM* by *Master*. This will avoid that the speakers turn noisy when the volume are raised too much.


*#filesystem_charset "ISO-8859-1"*

We uncomment the line and change *ISO-8859-1* by *UTF-8*, for all those who had especial characters in the tag or name of the songs. With this MPD will be able to add them to the playlist..


That is the most essential I believe. Hope I havent forgot anything. In any case, you are free to navigate and try the file later  =]

Save the changes in *mpd.conf*. Then:

*cd /var/lib/mpd/music/*
*sudo ln -s &#8220;path to our music&#8221;*

Repeat it with every place where you got music. New soft links are created that will allow MPD take the music files from multiple directories, thing that cannot be done editig the configuration file.
Its all ready. The last thing is creating a database:

*sudo mpd &#8211;create-db*

Then, to start MPD:

*sudo mpd*

And repeat the command for the database creation everytime we want to update it.

···········

[COLOR=Orange]**_libmpd (MPD library)_**[/COLOR]


[Qball website]("http://sarine.nl/gmpc-compile-svn"):
[I]
**Requirements**
- C99 Compatible C compiler (for example: gcc >= 3.0)
- autotools (automake, autoconf)
- make
- libtool
- Subversion (to fetch a copy) [/I]


Then we downloadit with::

*svn co *[*https://svn.musicpd.org/libmpd/trunk*]("https://svn.musicpd.org/libmpd/trunk")* libmpd*

We go to the folder and do:
[I]
,/autogen.sh
make
sudo make install[/I]

···········

[COLOR=DarkOrchid]**_NCMPC (Ncurses Music Player Client)_**[/COLOR]


This is my favourite client =)

[MPD official site]("http://www.musicpd.org/install.shtml"):

[I]**Requirements**
- [/I][*ncurses*]("http://www.gnu.org/software/ncurses/")[I]
- [/I][*glib-2*]("http://www.gtk.org/")


We download it with:

*svn co *[*https://svn.musicpd.org/ncmpc/branches/tradiaz*]("https://svn.musicpd.org/ncmpc/branches/tradiaz")

This is a different branch to the one indicated in the MPD site. This is because apparently the original developer as left the project, and now another person is continuing it.
Inside the downloaded folder we continue with:

[I],/autogen.sh &#8211;enable-lyrics-screen --enable-clock-screen
make
sudo make install[/I]

Later you can access to it from any teminal tipping *ncmpc*.
As a tip, you can add to your bashrc (*~/.bashrc*) an alias like *alias ncpmc=&#8221;ncmpc &#8211;colors&#8221;*, something that will put colors on it every time we start it. Here, a screen:

[[IMG]http://img138.imageshack.us/img138/9206/pantallazo2al9.th.png[/IMG]]("http://img138.imageshack.us/my.php?image=pantallazo2al9.png")

···········
[COLOR=SeaGreen]
**_GMPC (Gnome Music Player Client)_**[/COLOR] [COLOR=#006400]
[/COLOR]

This is the front-end for X that we are going to use. Towards the end of the guide Ill talk about an option, bur in my opinion this one is the more complete.
[URL="http://sarine.nl/gmpc-compile-svn"]
Qball website[/URL]:

[I]**Requirements**
- C99 Compatible C compiler (for example: gcc >= 3.0) 
- autotools (automake, autoconf) 
- Gtk+-2.8 (and dependencies) 
- libmpd from svn (see above) 
- Gob2 
- libsm 
- libglade 
- Libcurl (version 3)
- intltool 
- make 
- Subversion (te fetch a copy) [/I]

In a terminal:

*svn co *[*https://svn.musicpd.org/gmpc/trunk/*]("https://svn.musicpd.org/gmpc/trunk/")* gmpc/*

Inside the folder:

[I],/autogen.sh
make
sudo make install[/I][/LEFT]
 

 [COLOR=DeepSkyBlue][B][U]GMPC plugins

[/U][/B][/COLOR]All the avilable plugins can be seen in [https://svn.musicpd.org/gmpc/plugins/](https://svn.musicpd.org/gmpc/plugins/)

They can be downloaded in rhe next way:[I]

svn co [https://svn.musicpd.org/gmpc/plugins/"name"/trunk]("https://svn.musicpd.org/gmpc/plugins/%22nombre%22/trunk")

[/I]Installation has get a little troublesome because packiging them made the files install in wrong places*. *So this is what Ive done:[I]

,/autogen.sh
make
sudo make install

[/I]Then, I went to* /usr/local/share/gmpc/share/gmpc/plugins/ *and move the file **.so* that was there to */usr/local/share/gmpc/plugins/*. In anycase, this was for a global plugin installation. For make it local in should be moved to [I]~/.gmpc/plugins/
[/I]

 For the rest of it, I got:

**coveramazon **---> take the album covers from Amazon to show them.

**last.fm** ---> the same but whit musicians photos, and I think it sends info of the hearing habits to last.fm too.

**lyrics** ---> to recive the lyrics from LeosLyrics and LyricsTracker.

**wikipedia** ---> enable a tab where one can see the musician or band article of Wikipedia.

**qosd **---> it shows the playing song on a display with transparencies.[I]

···········

[/I]Finally I comment you of a very pleasing alternative to *gmpc*. Its *Sonata*, a client very well worked out and with the particularity of using only contextual menus.
The official page is [http://sonata.berlios.de/]("http://sonata.berlios.de/") and the way to get the latest version and install it is:[I]


svn co [http://svn.berlios.de/svnroot/repos/sonata/trunk](http://svn.berlios.de/svnroot/repos/sonata/trunk) sonata


[/I]Then we go to the folder and do:[I]


sudo python setup.py install


[/I]As *Sonata* uses distutils from Python, uninstalling it isnt a easy task, because apparently (and incredibly) distutils doesnt provides the mechanisms to uninstall it. The localization of the files are, to remove it manually:[I]


/usr/bin/sonata
/usr/lib/python2.4/site-packages/mmkeys.so
/usr/lib/python2.4/site-packages/mpdclient3.py
/usr/lib/python2.4/site-packages/mpdclient3.pyc
/usr/lib/python2.4/site-packages/sonata.py
/usr/lib/python2.4/site-packages/sonata.pyc
/usr/share/applications/sonata.desktop
/usr/share/locale/de/LC_MESSAGES/sonata.mo
/usr/share/locale/fr/LC_MESSAGES/sonata.mo
/usr/share/locale/pl/LC_MESSAGES/sonata.mo
/usr/share/locale/ru/LC_MESSAGES/sonata.mo
/usr/share/pixmaps/sonata.png
/usr/share/pixmaps/sonatacd.png
/usr/share/pixmaps/sonatacd_large.png
/usr/share/sonata/CHANGELOG
/usr/share/sonata/README
/usr/share/sonata/TODO
/usr/share/sonata/TRANSLATORS


···········

[/I]Well, I hope that this was useful to somebody. If I did it is because I sincerely consider that MPD is an excellent way to play music, and I expect that other persons known of it and appreciate it as much as I do =)

My regards.


P.D: Im open to critics. More than once I must have made a mistake =p

---

### Post by zenwhen on 2006-12-17
Great job. I used to write these for every release and had planned on doing another one. Thanks for picking up the slack. GMPC + MPD is the best music playing solution for the Linux platform.

---

### Post by qball on 2006-12-17
If you want to install the plugins in the right place, run ./autogen --prefix=/usr/local/ or where ever they are installed.

I will check if it's a bug in the autogen.sh that they get installed in the wrong location.

Q

---

### Post by lime4x4 on 2006-12-17
stupid question here but where does the mpd folder get downloaded to when using svn?

---

### Post by JMO707 on 2006-12-17
It gets downloaded to the place where you executed the command =p

---

### Post by zanglang on 2006-12-18
Nice guide, satisfied Sonata user here. :) Just curious, but what are the major feature differences of MPD currently in universe and the SVN version?

By the way, Sonata's download page does give instructions for installing via apt for people who'd like to stick with stable releases.

---

### Post by JMO707 on 2006-12-18
The differences are [the ones listed]("http://svn.musicpd.org/log.php?repname=MPD&path=%2Fmpd%2Ftrunk%2F&rev=5142&sc=0&page=1") from the revision 4895 to the 5142.

---

### Post by amgeex on 2007-01-04
Hey, if I install from the repos, will mpd be set up as a service automatically? And how do I configure it, because last time the "old" method for configuring it didn't work, it was something like "dpkg reconfigure mpd" or around those lines. Sorry, I haven't been able to find decent instructions. :mrgreen:

---

### Post by kalle314 on 2007-01-17
amgeex:I installed mpd from the repos. This is what i did to make it work:
1. Tell mpd in which directory the music is located, by editing /etc/mpd.conf (see [http://mpd.wikia.com/wiki/Configuration](http://mpd.wikia.com/wiki/Configuration))
2. Build the database and start the mpd daemon, as described above. 

mpd/mpc really is a great music player solution by the way. I just started using it, and it has already taken over the main music playing responsibility from amaroK on my computer!

---

### Post by amgeex on 2007-01-17
> **kalle314 said:**
> amgeex:I installed mpd from the repos. This is what i did to make it work:
1. Tell mpd in which directory the music is located, by editing /etc/mpd.conf (see [http://mpd.wikia.com/wiki/Configuration](http://mpd.wikia.com/wiki/Configuration))
2. Build the database and start the mpd daemon, as described above. 

mpd/mpc really is a great music player solution by the way. I just started using it, and it has already taken over the main music playing responsibility from amaroK on my computer!

Thanks, took a while to get it going, but after playing a bit with the configuration options I put together a nice and simple ~.mpdconf file. :mrgreen:

---

### Post by stalefries on 2007-01-17
Thanks for the howto. I had been planning to make a home music server, this will help a lot.

---

### Post by deadlydeathcone on 2007-01-24
Updated: packaged the plugins. The wikipedia plugin now works and the cover art fetcher is much improved.

I created some good packages for the awesome upcoming gmpc 0.14:

[gmpc_0.14-RC1.tar.gz]("http://www.box.net/shared/v1jdyzn576").  Contains the player and plugins. You only need the -dev package if you want to compile the plugins on your own.

JMO707: Thanks for the howto. I ran into some permission errors because of the symlinking tactic, and made a config file that got around it. I attached it if anyone ran into the same problem.

---

### Post by elektronaut on 2007-01-25
I just now found the time to set up my music server, so thank you a lot, JM0707! (I asked him to give us an english translation of his original spanish HowTo.) mpd is now running on my Linux router, the music is on an external hard disk attached to the router's usb port, and I can control it either from my computer with gmpc or with [my mobile phone using bluetooth](http://ubuntuforums.org/showthread.php?t=341408). Cool :cool:

---

### Post by janga on 2007-02-09
Hi.
I am using mpd and ncmpc currently on dapper server install.
Works great, but i have one last issue: How do i make mpd and mpdscribbler (for last.fm scrobbling) start automatically on startup?

When I do

```
sudo update-rc.d mpd defaults
```

it says:

```
System startup links for /etc/init.d/mpd already exist.
```


But it doesnt come up automatically on startup. Same is for mpdscribbler.

---

### Post by rggavubt on 2007-02-25
Thanks for the how to but there is an error in one of the commands.  You need to edit the original post to change "sudo mpd –create-db" to "sudo mpd --create-db" (no one reads past the main post).  Someone told me to use "man mpd" and it shows two dashs in front of create not one....this caused me many headaches!:(

---

### Post by rggavubt on 2007-02-25
> **rggavubt said:**
> Thanks for the how to but there is an error in one of the commands.  You need to edit the original post to change "sudo mpd –create-db" to "sudo mpd --create-db" (no one reads past the main post).  Someone told me to use "man mpd" and it shows two dashs in front of create not one....this caused me many headaches!:(

I just read my post and my two dashes look like one big dash....you can't see the space between the dashes on the screen.  I guess the original post was correct but didn't show up correctly on the screen.

---

### Post by foxy123 on 2007-03-21
I installed mpd, mpc and gmpc from repositories on Feisty. I made the changes in mpd.conf following this howto and ran
```
sudo mpd --create-db
``` 
which added all my songs into the database.
I launched gmpc and ticked autoconnect in teh preferences. But still I have nothing in Browse Artists in Play-list manager. Any help, please?

---

### Post by yabbadabbadont on 2007-03-21
Did you remember to restart the mpd after you updated the music database?  Changes to it won't show up until you do.

---

### Post by foxy123 on 2007-03-21
> **yabbadabbadont said:**
> Did you remember to restart the mpd after you updated the music database?  Changes to it won't show up until you do.

oh, thanks a lot, it did it.

---

### Post by urukrama on 2007-04-07
I can't get Sonata installed. I've had it running before I reinstalled Ubuntu (Dapper), but I can't get it to work now. I install from source (as the .deb clashes with some dependencies), and all goes well there. When I try to run Sonata, I get an icon in the system tray, but no player shows up.

This is what I get in the terminal:

```
Taglib and tagpy not found, tag editing support disabled.
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/sonata.py", line 3858, in trayaction
    self.trayaction_activate(None)
  File "/usr/lib/python2.4/site-packages/sonata.py", line 3823, in trayaction_activate
    if self.window.window.get_state() & gtk.gdk.WINDOW_STATE_WITHDRAWN: # window is hidden
AttributeError: 'NoneType' object has no attribute 'get_state'

```

Any suggestions? I know this should work, as I've had it running before. A bit frustrating, as it is a nice player.

EDIT: I reinstalled the package and all works fine now. Don't ask me why, though, as I have no clue. :-)

---

### Post by schmappel on 2007-04-10
I hate to ask, but what calendar is that in your screenshot?

---

### Post by digbybare on 2007-04-16
I get the following when I try to run ./autogen.sh:
```
########### MPD CONFIGURATION ############

 Playback Support:
 libao support .................disabled
 OSS support ...................enabled
 ALSA support ..................disabled
 JACK support ..................disabled
 OS X support ..................disabled
 PulseAudio support ............disabled
 Media MVP support .............disabled
 Shout streaming support .......disabled

 File Format Support:
 ID3 tag support ...............disabled
 mp3 support ...................disabled
 Ogg Vorbis support ............disabled
 FLAC support ..................disabled
 OggFLAC support ...............disabled
 Wave file support .............disabled
 MP4/AAC support ...............disabled
 Musepack (MPC) support ........disabled
 MOD support ...................disabled
configure: error: No input plugins supported!

```

I checked in synaptic, and I seem to have all the necessary packages installed, like libmad, libogg, libvorbis, etc. What should I do?

---

### Post by yabbadabbadont on 2007-04-17
> **digbybare said:**
> I checked in synaptic, and I seem to have all the necessary packages installed, like libmad, libogg, libvorbis, etc. What should I do?

Make sure that you have the development versions of those libraries installed too.  They are two different packages.

---

### Post by digbybare on 2007-04-22
> **yabbadabbadont said:**
> Make sure that you have the development versions of those libraries installed too.  They are two different packages.

Thanks, MPD's up and running now.

A couple more quick questions.

Right now, I have WinXP installed on partition, Xubuntu on a partition and a shared FAT32 partition. I have all my music on the FAT partition. I tried adding a symbolic link to my music folder in /var/lib/mpd/music. It seems to work, I can cd into it, etc. But when I try to run sudo mpd --create-db, it won't add anything to the database. I think it has something to do with the permissions. Right now, the permissions for that partition are: drwxrwx---. I tried doing sudo chmod a+rwx, and that didn't do anything. I tried actually changing into the superuser and running chmod and still didn't do anything. Also, all the files in that partition are listed in green in terminal. I have an external harddisk that's also formatted as FAT32 which seems to work fine. The file permissions are: drwxr-xr-x.

Another thing, can MPD play CDs? Do I just make a symbolic link to /media/cdrom in /var/lib/mpd/music? And, can MPD access freedb?

---

### Post by JMO707 on 2007-04-27
Sorry about not answer nothing =(

I'am really busy with other thing's right now, but if someone wants to take the tutorial and re-make it to correct stuff or update it, I give all my approval to that =)

Respect to the CD playback, it is currently not supported by MPD, but there are plans to implement it on MPD2. 

And

[QUOTE=schmappel]I hate to ask, but what calendar is that in your screenshot?[/QUOTE]

It is [gDeskCal]("http://www.pycage.de/#gdeskcal") :)

---

### Post by urukrama on 2007-05-18
Why do I not see new files I add to my music database? All my music is located in ~/Music and whenever I add new files to it, they do show up in /var/lib/mpd/music but I cannot play them. GMPC nor Sonata show those files, even if I update or restart mpd and mpc, or if I restart my computer a hundred times.

EDIT: Problem solved. I figured out that a file/folder needs to allow Read & Write privileges to all users. Once I changed that, everything appeared in GMPC.

---

### Post by andrek on 2007-06-03
I've got some problems while trying to install sonata from svn.
After sudo python setup.py install , it gives me lots of errors
> 
[...]
mmkeys.c:124: warning: implicit declaration of function ‘pygobject_register_class’
mmkeys.c:124: warning: implicit declaration of function ‘mmkeys_get_type’
mmkeys.c:125: warning: implicit declaration of function ‘pyg_set_object_has_new_constructor’
error: command 'gcc' failed with exit status 1


---

### Post by el mariachi on 2007-07-18
I've got all the libs installed (at least I think I do have the right ones) but when I compile MPD it only says to support ogg - no MP3. Is there any thing I missed? I think I have all the libraries mentioned.

---

### Post by yabbadabbadont on 2007-07-18
> **el mariachi said:**
> I've got all the libs installed (at least I think I do have the right ones) but when I compile MPD it only says to support ogg - no MP3. Is there any thing I missed? I think I have all the libraries mentioned.

What options did you use when you ran the "./configure" step?

---

### Post by el mariachi on 2007-07-18
> **yabbadabbadont said:**
> What options did you use when you ran the "./configure" step?
none. I don't know how to do that (choose options)

---

### Post by crazybilly on 2007-07-31
I'm having problems trying to mpd to work as a server on my home network.  I can get gmpc to connect to mpd locally.  

But when I try to hit it with gmpc on another computer, I get a timeout error.  I'm pretty sure I'm hitting the server (i'm just typing in the server's ip address).  I've tried going up to about 15 seconds with no luck.  

I've also made sure that the ports are open on the server.  

Any clues?

Thanks, ya'll!

---

### Post by Useff on 2007-08-21
Thanks for this. gmpc, ncmpc, and Sonata are some of the best-looking programs I've seen. The hardest part now is sticking with one.

I really love gmpc, but I wish I could get it installed from svn so I can play with all the new functionality outlined in [this post]("http://wordpress.qballcow.nl/2007/07/27/gmpc-getting-better-and-better/").

Right now, I get a syntax error while running ./configure, lines 23715.

---

### Post by crazybilly on 2007-08-21
just to update, I solved my problem by configuring the server to accept nonlocal clients.  there was a setting in the rc file for mpd on the server...can't remember where, but I think I found it earlier in this thread (or elsewhere by google).  If somebody needs it, I can find and repost the solution.

---

### Post by Useff on 2007-08-22
Fixed my problem. Had to install gob2.

---

### Post by el mariachi on 2007-08-22
I tried to compile it, like in this guide but there's no mpd.conf or /var/lib/mpd to be found... how do I remove all the garbage that this failed attempt left behind and do it right?

---

### Post by chadlewis on 2007-09-20
I'm having the same problem as this guy: [http://ubuntuforums.org/showpost.php?p=2128070&postcount=14](http://ubuntuforums.org/showpost.php?p=2128070&postcount=14)

No matter what I do, I can't get MPD to run at startup. This is in Gutsy, btw. Anyone got any suggestions?

---

### Post by secretspicy15 on 2007-10-11
Ok, I followed the how-to, eveyrthing seemed to install correctly, it built the database, great. I then type ```
 sudo mpd
``` and it gives me this:

```
unable to bind port 6600: Address already in use
maybe MPD is still running?

```

Any ideas?

---

### Post by secretspicy15 on 2007-10-11
Whew, nevermind, I got it all worked out; I just had to change the port int he config file. all better now. How exciting :-D

---

### Post by fedex1993 on 2008-01-16
okay well i got mine all setup very nicely but wheni create a data base it will only add flac files from my music folder.well there are about 500 other songs that are in the same folder ecept that they are .mp3 and .ogg  so i dont know what is going on if you could help me thanks

---

### Post by unsoiledchris on 2008-04-10
I installed MPD, but none of these directories exist.
I don't have a ~/.mpd
I looked elsewhere for them and none of them exist.
Am I missing something? or did it not install correctly?

---

### Post by crazybilly on 2008-04-11
Look in /etc.  There should be a file mpd.conf.  That's what MPD uses if it can't find anything in your local directory.  If you want to set it up for your own identityr, just copy /etc/mpd.conf to ~/.mpd.conf  ( or something like that, look through the rest of this thread) or just create a new file.  Then, when MPD starts, it'll look for that file first and use it instead of the one in /etc.  If you want to have different configurations depending on who's llgged in, you can, y creating different firesl for each person and saving them in their home directory.

---

### Post by weems on 2008-06-13
I get the following when I try to run mpd. ```
weems@mainframe:~$ sudo mpd
Error reading db, fgets
```

---

### Post by henriquemaia on 2008-06-28
Thanks a lot for this howto. Though a bit outdated, it was still helpful.

---

### Post by Elep.Repu on 2009-08-24
I gave up.
** ERROR **: problems opening file -create-db for reading: No such file or directory

---

### Post by yabbadabbadont on 2009-08-24
> **Elep.Repu said:**
> I gave up.
** ERROR **: problems opening file -create-db for reading: No such file or directory

You gave up... and yet I can find no posts by you on your issue, other than this one.  Yeah, that'll work.  :lol:

Since this is a fairly old topic, you might want to start a new support thread on your issue.  Provide the exact commands you used to produce the error that you listed above.  Just off the top of my head though, I would say that you passed the wrong option to mpd to create the database.  The option is "--create-db" (two leading dashes) and not "-created-db" (as listed in your error message).

---

### Post by Aszasz on 2011-07-15
The programms are up and running. I linked mpd in the .conf file to my home Music folder. However, mpd seems to only find the Music that is in the ~/Music folder and NOT in its subdirectories. Am i missing something here?

---

