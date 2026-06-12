---
title: "HOWTO: Install and Use MPD in Ubuntu V.3"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by zenwhen on 2005-10-14
What is  [Music Player Daemon](http://www.musicpd.org/)?

Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It is also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.

Why should I use it instead of Rhythmbox or Muine?

MPD is light on your resources, and high on [extensibility](http://www.musicpd.org/clients.shtml). The daemon is easy to interact with, develop front ends for, and configure with intuitive configuration scripts. If that doesn't convince you, perhaps the pretty screenshots and features coming later in this thread will. 8)

Where can I get Ubuntu compatible packages?

I took the liberty of tarring up the files needed to set MPD up in Ubuntu as I have it set up. Here are my installation instructions. Make sure you have universe enabled in apt.

Execute these commands:
```
sudo apt-get install mpd mpc gmpc
wget http://troymcferron.com/files/mpd-ubuntu.tar.gz
tar xvfz mpd-ubuntu.tar.gz
cd mpd-ubuntu
nano mpd.conf
```

Now that you have this configuration file open, edit "PATH TO YOUR MUSIC DIRECTORY" to contain the actual path to your music directory. Hit control +o then control + x, and then execute this command:

sudo cp mpd.conf /etc

Now, drop the .mpd DIR and the .gmpc.cfg FILE from mpd-ubuntu into your home dir.

Next, you will want to look at the help text for mpd.

```
zenwhen@sunball:~ $ mpd --help

usage:
mpd [options] <port> <music dir> <playlist dir> <log file> <error file>
mpd [options] <conf file>
mpd [options] (searches for ~/.mpdconf then /etc/mpd.conf)

options:
--help this usage statement
--no-daemon don't detach from console
--stdout print msgs to stdout and stderr
--create-db force (re)creation database and exit
--update-db create database and exit
--no-create-db don't create database
--verbose verbose logging
--version prints version information
```

It is always a good idea to look at the -help, --help, or -h option of any new program you install. I don't mean that to be insulting to you if you aren't quite new to Linux, but this is just a good habit to form.

The command we were looking for was "--create-db". So run:

mpd --create-db

This loads all of your music into MPD's database file. You can make playlists, and control your MPD with the application GMPC (gnome media player daemon client), which we installed earlier. You will find it in your application -> Multimedia menu, and can also run it with the command "gmpc" from the terminal.

This is what your nice GTK themed front end looks like:

[img]http://troymcferron.com/images/mpdshot.png[/img]

Using this to manage MPD and update your database will make using MPD effortless, and its playlist options are as as good as any, though not as complicated. You may have noticed a set of panel launchers there on that screenshot that look like media player controls. Those are custom application launchers added to the gnome panel with a right click that point to some of these commands that can be sent to MPC (the command line media player daemon client) :

```
mpc Displays status
mpc add <filename> Add a song to the current playlist
mpc del <playlist #> Remove a song from the current playlist
mpc play <number> Start playing at <number> (default: 1)
mpc next Play the next song in the current playlist
mpc prev Play the previous song in the current playlist
mpc pause Pauses the currently playing song
mpc stop Stop the currently playing playlists
mpc seek <0-100> Seeks to the position specified in percent
mpc clear Clear the current playlist
mpc shuffle Shuffle the current playlist
mpc move <from> <to> Move song in playlist
mpc playlist Print the current playlist
mpc listall [<song>] List all songs in the music dir
mpc ls [<dir>] List the contents of <dir>
mpc lsplaylists Lists currently available playlists
mpc load <file> Load <file> as a playlist
mpc save <file> Saves a playlist as <file>
mpc rm <file> Removes a playlist
mpc volume [+-]<num> Sets volume to <num> or adjusts by [+-]<num>
mpc repeat <on|off> Toggle repeat mode, or specify state
mpc random <on|off> Toggle random mode, or specify state
mpc search <type> <queries> Search for a song
mpc crossfade [sec] Set and display crossfade settings
mpc update Scans music directory for updates
mpc version Reports version of MPD
```

The icons are from RedHat's Bluecurve icon set. I tarred them up for your use with the launchers. You can grab them here ([http://troymcferron.com/files/bluecurve-media-icons.tar.gz](http://troymcferron.com/files/bluecurve-media-icons.tar.gz)).

You will have to start mpd with the "mpd" command before this system for music playing works. You can either add a launcher to run that command, run it from the terminal whenever you start up, or you can add it to "gnome-session-properties" as a startup command.

After that, you will be able to run GMPC, have a nice pop-up window whenever the song changes, control it in a winamp like fashion with he GUI, and control it from your taskbar. You can control it from the terminal without booting into X with the mpc commands listed above, and can control it with  [FoxyTunes](https://update.mozilla.org/extensions/moreinfo.php?application=firefox&id=219).

If you noticed that I said the word "control" a lot in that last paragraph, you are right. MPD gives you total control over your music library, and gives you the ability to control it from wherever you wish, however you wish, access it how you wish, and from any OS you wish using any desktop environment you wish. There are also clients for all of the major desktop environments; including [KDE](http://www.musicpd.org/kmp.shtml) and even [Windows](http://www.musicpd.org/MPD-Commander.shtml).

I will answer any questions you raise to the best of my ability. Enjoy! :)

I got this tip from [http://ubuntuforums.org/showthread.php?t=31763]("http://ubuntuforums.org/showthread.php?t=31763"):
 > Now, people have been having trouble getting this to work on Hoary (myself included) and I found that this was easily solved by adding a single line to the mpd.conf saying 'ao_driver "alsa09"'. If you type the following into the console this will be done automatically:
```
sudo  echo ao_driver \"alsa09\" >> /etc/mpd.conf
```

---

### Post by majikstreet on 2005-10-15
I followed these instructions *to the dot* and when I run "mpd --create-db" I get this:
```

majikstreet@oreo:~$ mpd --create-db
usage:
   mpd [options] <port> <music dir> <playlist dir> <log file> <error file>
   mpd [options] <conf file>
   mpd [options]   (searches for ~/.mpdconf then /etc/mpd.conf)

options:
   --help             this usage statement
   --no-daemon        don't detach from console
   --stdout           print msgs to stdout and stderr
   --create-db        force (re)creation database and exit
   --update-db        create database and exit
   --no-create-db     don't create database
   --verbose          verbose logging
   --version          prints version information

```

Why is that (I can connect to my computer using gmpc by the way.)

---

### Post by zenwhen on 2005-10-16
That is really odd "mpd --create-db" works perfectly for me and starts adding the files in the config files chosen folder to the DB. 

Try this:

[IMG]http://troymcferron.com/images/trythis.png[/IMG]

---

### Post by majikstreet on 2005-10-17
[QUOTE=zenwhen]That is really odd "mpd --create-db" works perfectly for me and starts adding the files in the config files chosen folder to the DB. 

Try this:

[IMG]http://troymcferron.com/images/trythis.png[/IMG][/QUOTE]
GRRR--- Now I can't connect :(

MPD is _not_ started. I don't know why I can't start it :O

---

### Post by potrick on 2006-04-18
Hey, I know this is an old howto thread but I just got MPD setup and am happy but cannot seem to make it recognize AAC files. I installed the FAAD package from the repositories ([http://packages.ubuntu.com/breezy/sound/faad](http://packages.ubuntu.com/breezy/sound/faad)) which appears to be the backend MPD would need. Any idea what I should do next?

---

### Post by potrick on 2006-04-19
okay guys, I think I know at this point getting this to work requires compiling MPD with the faad2lib package installed. I've gotten through compiling but cannot seem to make the package. The output at the end of the "make" process looks like this: 

```
mpd-aac_plugin.o: In function `getAacFloatTotalTime':
inputPlugins/aac_plugin.c:219: undefined reference to `NeAACDecOpen'
inputPlugins/aac_plugin.c:221: undefined reference to `NeAACDecGetCurrentConfiguration'
inputPlugins/aac_plugin.c:223: undefined reference to `NeAACDecSetConfiguration'
inputPlugins/aac_plugin.c:227: undefined reference to `NeAACDecInit'
inputPlugins/aac_plugin.c:234: undefined reference to `NeAACDecClose'
mpd-aac_plugin.o: In function `aac_decode':
inputPlugins/aac_plugin.c:279: undefined reference to `NeAACDecOpen'
inputPlugins/aac_plugin.c:281: undefined reference to `NeAACDecGetCurrentConfiguration'
inputPlugins/aac_plugin.c:289: undefined reference to `NeAACDecSetConfiguration'
inputPlugins/aac_plugin.c:294: undefined reference to `NeAACDecInit'
inputPlugins/aac_plugin.c:324: undefined reference to `NeAACDecDecode'
inputPlugins/aac_plugin.c:378: undefined reference to `NeAACDecClose'
inputPlugins/aac_plugin.c:332: undefined reference to `NeAACDecGetErrorMessage'
mpd-mp4_plugin.o: In function `mp4_getAACTrack':
inputPlugins/mp4_plugin.c:61: undefined reference to `NeAACDecAudioSpecificConfig'
mpd-mp4_plugin.o: In function `mp4_decode':
inputPlugins/mp4_plugin.c:144: undefined reference to `NeAACDecOpen'
inputPlugins/mp4_plugin.c:146: undefined reference to `NeAACDecGetCurrentConfiguration'
inputPlugins/mp4_plugin.c:154: undefined reference to `NeAACDecSetConfiguration'
inputPlugins/mp4_plugin.c:162: undefined reference to `NeAACDecInit2'
inputPlugins/mp4_plugin.c:295: undefined reference to `NeAACDecClose'
inputPlugins/mp4_plugin.c:240: undefined reference to `NeAACDecDecode'
inputPlugins/mp4_plugin.c:182: undefined reference to `NeAACDecClose'
inputPlugins/mp4_plugin.c:166: undefined reference to `NeAACDecClose'
inputPlugins/mp4_plugin.c:249: undefined reference to `NeAACDecGetErrorMessage'
collect2: ld returned 1 exit status
make[3]: *** [mpd] Error 1
make[3]: Leaving directory `/home/potrick/downloads/mpd-0.11.5/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/potrick/downloads/mpd-0.11.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/potrick/downloads/mpd-0.11.5'
make: *** [all] Error 2

```

I know this thread probably isn't being watched too quickly, but I'd really like to get MPD playing AAC files. It's a decent chunk of my library. Thanks for reading this, let me know if you can help.

---

### Post by daedalusman on 2006-04-19
Is there some way I can setup keyboard shortcuts to control the main playback options (play, stop, pause, next, prev) for gmpc? I ask this 'cause I have a multimedia keyboard and would like have those buttons do as intended. Another question, can I get mpd to report my played songs to last.fm? I just found out about this site about 2 weeks ago and love it 'cause it introduces me to new stuff. Other than those to quirks I love this, I've actually been wanting to try mpd out since installing conky and just never got around to it, so I greatly thank you for this short and easy how-to. And thanks for any help.

---

### Post by no1wantdthisname on 2006-05-06
Versions in Ubuntu repository are really old.  The newer versions of gmpc have cover art support and a changed ui. 
I found some debs at [http://musicpd.org/~normalperson/debian/experimental/](http://musicpd.org/~normalperson/debian/experimental/) but these needed packages with higher versions (probably from debian).
I went ahead and changed those dependencies.  Here's the altered packages.  I'm on a fully upgraded dapper so there might be more dependencies for those on breezy. 
As far as I can tell, there aren't problems from the change in dependencies.

gmpc v0.14.0~svn+r3985-1: [http://s52.yousendit.com/d.aspx?id=1WGHT9ZROMPJU1H0895CY2SGSL](http://s52.yousendit.com/d.aspx?id=1WGHT9ZROMPJU1H0895CY2SGSL)
libmpd v0.13.0~svn+r4104-1_i386: [http://s52.yousendit.com/d.aspx?id=0J90H76PH0QTU2OE5GJ5T4GSUJ](http://s52.yousendit.com/d.aspx?id=0J90H76PH0QTU2OE5GJ5T4GSUJ)
mpc v0.12.0~svn+r4133-1: [http://s52.yousendit.com/d.aspx?id=0WKPBR0NMIDIX0AY4UBXY6611X](http://s52.yousendit.com/d.aspx?id=0WKPBR0NMIDIX0AY4UBXY6611X)

---

### Post by topyli on 2006-05-07
[QUOTE=daedalusman]Is there some way I can setup keyboard shortcuts to control the main playback options (play, stop, pause, next, prev) for gmpc? I ask this 'cause I have a multimedia keyboard and would like have those buttons do as intended.[/QUOTE]
The beauty of mpd is that you're not bound to a single client, so you can control the daemon with gmpc and the command line client (mpc) simultaneously. Just bind the appopriate mpc commands to your keys.
I use keytouch ([www.keytouch.sourceforge.net](www.keytouch.sourceforge.net)) to configure my Logitech Media keyboard. Don't forget to disable these keys in the GNOME keyboard shortcut preferences :)

---

