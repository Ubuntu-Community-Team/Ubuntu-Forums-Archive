---
title: "Installing and Using MPD in Ubuntu V.3"
date: 2005-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by zenwhen on 2005-10-04
What is  [Music Player Daemon](http://www.musicpd.org/)?

Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It is also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.

Why should I use it instead of Rhythmbox or Muine?

MPD is light on your resources, and high on [extensibility](http://www.musicpd.org/clients.shtml). The daemon is easy to interact with, develop front ends for, and configure with intuitive configuration scripts. If that doesn't convince you, perhaps the pretty screenshots and features coming later in this thread will. 8)

Where can I get Ubuntu compatible packages?

I took the liberty of tarring up the files needed to set MPD up in Ubuntu as I have it set up. Here are my installation instructions.

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

