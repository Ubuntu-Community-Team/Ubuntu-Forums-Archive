---
title: "HOWTO: Install and Customize Music Player Daemon in Ubuntu"
date: 2004-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by zenwhen on 2004-11-16
What is [Music Player Daemon](http://www.musicpd.org/) ? 

> Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It is also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.

Why should I use it instead of Rhythmbox or Muine?

MPD is light on your resources, and high on [extensibility](http://www.musicpd.org/clients.shtml). The daemon is easy to interact with, develop front ends for, and configure with intuitive configuration scripts. If that doesn't convince you, perhaps the pretty screenshots and features coming later in this thread will. 8)

Where can I get Ubuntu compatible packages?

I took the liberty of tarring up the files needed to set MPD up in Ubuntu as I have it set up. You can get them [here](http://zenhardwhere.com/files/mpd-ubuntu.tar.gz). 
(You could also get them from the Debian unstable repos but I think the Ubuntu devs here would eat my face if I gave a HOWTO on that. :P)

Once you have that, untar it and cd into the dir. You will then need to install the three debs. Be sure you are in the dir containing mpd-ubuntu.tar.gz and execute these commands: 

```
tar xvfz mpd-ubuntu.tar.gz
cd mpd-ubuntu
dpkg -i mpd_0.11.5-1_i386.deb
dpkg -i mpc_0.11.1-2.1_i386.deb
dpkg -i gmpc_0.11.2-2_i386.deb
nano mpd.conf
```

Now that you have this configuration file open, edit "PATH TO YOUR MUSIC DIRECTORY" to contain the actual path to your music directory. Hit control +o then control + x, and then execute this command:

```
sudo cp mpd.conf /etc
```

Now, drop the .mpd DIR and the .gmpc.cfg FILE from mpd-ubuntu into your home dir.

Next, you will want to look at the help text for mpd. 

```
zenwhen@sunball:~ $ mpd --help

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

It is always a good idea to look at the -help, --help, or -h option of any new program you install. I don't mean that to be insulting to you if you aren't quite new to Linux, but this is just a good habit to form. 

The command we were looking for was "--create-db". So run:

```
mpd --create-db
```

This loads all of your music into MPD's database file. You can make playlists, and control your MPD with the application GMPC (gnome media player daemon client), which we installed earlier. You will find it in your  application -> Multimedia menu, and can also run it with the command "gmpc" from the terminal. 

This is what your nice GTK themed front end looks like:

[IMG]http://zenhardwhere.com/images/gmpc.png[/IMG]

Using this to manage MPD and update your database will make using MPD effortless, and its playlist options are as as good as any, though not as complicated. You may have noticed a set of panel   luanchers there on that screenshot that look like media player controls. Those are custom application launchers added to the gnome panel with a right click that point to some of these commands that can be sent to MPC (the command line media player daemon client) :

```
mpc                         Displays status
mpc add <filename>          Add a song to the current playlist
mpc del <playlist #>        Remove a song from the current playlist
mpc play <number>           Start playing at <number> (default: 1)
mpc next                    Play the next song in the current playlist
mpc prev                    Play the previous song in the current playlist
mpc pause                   Pauses the currently playing song
mpc stop                    Stop the currently playing playlists
mpc seek <0-100>            Seeks to the position specified in percent
mpc clear                   Clear the current playlist
mpc shuffle                 Shuffle the current playlist
mpc move <from> <to>        Move song in playlist
mpc playlist                Print the current playlist
mpc listall [<song>]        List all songs in the music dir
mpc ls [<dir>]              List the contents of <dir>
mpc lsplaylists             Lists currently available playlists
mpc load <file>             Load <file> as a playlist
mpc save <file>             Saves a playlist as <file>
mpc rm <file>               Removes a playlist
mpc volume [+-]<num>        Sets volume to <num> or adjusts by [+-]<num>
mpc repeat <on|off>         Toggle repeat mode, or specify state
mpc random <on|off>         Toggle random mode, or specify state
mpc search <type> <queries> Search for a song
mpc crossfade [sec]         Set and display crossfade settings
mpc update                  Scans music directory for updates
mpc version                 Reports version of MPD
```

The icons are from RedHat's Bluecurve icon set. I tarred them up for your use with the launchers. You can grab them [here](http://zenhardwhere.com/files/bluecurve-media-icons.tar.gz). 

You will have to start mpd with the "mpd" command before this system for music playing works. You can either add a launcher to run that command, run it from the terminal whenever you start up, or you can add it to "gnome-session-properties" as a startup command. 

After that, you will be able to run GMPC, have a nice pop-up window whenever the song changes, control it in a winamp like fashion with he GUI, and control it from your taskbar. You can control it from the terminal without booting into X with the mpc commands listed above, and can control it with  [FoxyTunes](https://update.mozilla.org/extensions/moreinfo.php?application=firefox&id=219).

If you noticed that I said the word "control" a lot in that last paragraph, you are right. MPD gives you total control over your music library, and gives you the ability to control it from wherever you wish, however you wish, access it how you wish, and from any OS you wish using any desktop environment you wish. There are also clients for all of the major desktop environments; including [KDE](http://www.musicpd.org/kmp.shtml)  and even [Windows](http://www.musicpd.org/MPD-Commander.shtml). 

I will answer any questions you raise to the best of my ability. Enjoy! :)

Edit: Made a change thanks to MPD dev shank. Hey shank. :)

---

### Post by TravisNewman on 2004-11-16
Looks pretty slick! If I get bored with rhythmbox I'll try this out ;)

---

### Post by Erikhh on 2004-11-19
I got interested in mpd and downloaded the files, but i doesnt work. Cant even do:
mpd --create-db
without getting an error message.

There are also problems with the channels. What do I do wrong?

---

### Post by zenwhen on 2004-11-19
What was the error you got when you ran the command?

Did you point the conf file to your music dir?

Could you describe your "channels" problem in more detail?

---

### Post by Erikhh on 2004-11-20
It couldn't create playlists

The problem with the channels seems to be, that mpc couldn't "connect" or what you call it.

---

### Post by zenwhen on 2004-11-25
Erikhh, come into #mpd on irc.freenode.org sometime. Your issue could likely be handled easier there.

---

### Post by Erikhh on 2004-11-26
Thanks for your concern. At the moment I have given up, because it got too complicated, but I'll try and go to the adress you mention.

---

### Post by Whippet on 2004-12-18
Thank you for you very nice How to. I finally got mpd with gmpc running  :D

---

### Post by crun on 2004-12-18
Hi Zenwhen. I really like the way MPD works so far, a great new way to organize your playlists.

Concerning the install howto: when the .mpd dir gets created, the subdirectory "playlists" isn't included. This causes an error when running "mpd --create-db". I created the dir with

$ cd .mpd
$ mkdir playlists
$ chmod -R 700 playlists

and then moved the whole .mpd dir to my home folder. After this, "mpd --create-db" runs fine.

Once again, thanks for a great program

---

### Post by AllTom on 2004-12-23
I like to use the init scripts that come with MPD so I get music as soon as I turn on my computer. Under Ubuntu, my home directory and all my folders automatically have o+r permissions set, so having all my music in /home/tom/media/audio/music/ is fine. In /etc/mpd.conf I change the following variables from their defaults:

```
music_directory         "/home/tom/media/audio/music"
playlist_directory      "/etc/mpd/playlists"
log_file                "/etc/mpd/mpd.log"
error_file              "/etc/mpd/mpd.error"
db_file         "/etc/mpd/mpd.db"
state_file              "/etc/mpd/mpdstate"
user            "mpd"
```

Then, as root, I run

```
# useradd -G audio mpd
# mkdir /etc/mpd
# mkdir /etc/mpd/playlists
# chown -R mpd:audio /etc/mpd
# /etc/init.d/mpd start-create-db
```

At this point, the database is created in /etc/mpd/mpd.db and the daemon started immediately. I can still use gmpc to control it, but now it is a service that can be started automatically on boot.. :D Have fun!

---

### Post by Nolgthorn on 2005-04-12
Hi all, this setup looks awesome. I'd love to start using the combination mpd/gmpc right away for ubuntu but I still have one problem getting it all working that's in my way.

I have installed mpd, I have it running on startup and I have sucessfully populated my playlist with music. The only problem arises when I try and play some music using gmpc it will flicker the name of the song, then stop playing immediately.

I cannot get it to play. Do you have any suggestions for me.

---

### Post by rick_hewes on 2005-04-24
This is exactly what happens for me also. (The player looks as though its going to play then doesn't). 

In the error log "problems opening audio device while playing" + mp3 file.

If I restart mpd as root it is fine. Or run mpd under my own user name.
But trying to start at boot time under the mpd user fails.

I have made sure user mpd is a member of the audio group and have added mpd as the user in mpd.conf.

Any help would be appreciated.

Rick

---

### Post by Utter on 2005-04-25
Rick,

Which Ubuntu are you using? I recently installed Hoary and setup a music server with mpd. However, after the most recent apt-get upgrade the thing broke and I also received the error you're getting in the mpd.error log.

While browsing another set of posts here someone mentioned installing alsa-oss to get Realplayer to work so I did 'sudo apt-get install alsa-oss' and restarted mpd. Checking the log I found no more errors but still couldn't get any sound out. Since I still have X running on the box I checked the volume and noticed it was set to 0. In fact now, every time I adjust mpd's volume in phpMp2 it sets Ubuntu's volume to 0 so be wary.

Maybe this is a Hoary-only problem but even if you're on Warty and have recently updated the system this might work…

---

### Post by blissfulignant on 2005-05-02
I recently installed Hoary, but I can't seem to get MPD to install... here's my console output, see if you can make any sense of it...

>dpkg -i mpd_0.11.5-1_i386.deb
Selecting previously deselected package mpd.
(Reading database ... 59629 files and directories currently installed.)
Unpacking mpd (from mpd_0.11.5-1_i386.deb) ...
dpkg: dependency problems prevent configuration of mpd:
 mpd depends on libflac4; however:
  Package libflac4 is not installed.
dpkg: error processing mpd (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mpd

I know for a fact that libflac6 is installed (Synaptic says so)...

---

### Post by Xgkkp on 2005-05-04
[QUOTE=rick_hewes]This is exactly what happens for me also. (The player looks as though its going to play then doesn't). 

In the error log "problems opening audio device while playing" + mp3 file.

If I restart mpd as root it is fine. Or run mpd under my own user name.
But trying to start at boot time under the mpd user fails.

I have made sure user mpd is a member of the audio group and have added mpd as the user in mpd.conf.

Any help would be appreciated.

Rick[/QUOTE]

I am also having this exact same problem. In fact, it's slightly different in that starting it under the mpd user name at all times means it will not play, but that it will not work on boot unless I manually restart it as root (it is running as root).

Edit: Oh, I thought this was in the hoary forums. I'll try reposting a help topic over there

---

### Post by Xgkkp on 2005-05-04
I have solved my problems with mpd on Hoary, I'm posting here as other people seem to have been having the same problem (I plan to put the info up somewhere on the hoary forums later)

Firstly, make sure that mpd is in the audio group. 
```
sudo adduser mpd audio
```
this should (normally) come up with a message saying that the user mpd is already in the group

Then for it to actually work on boot I had to specifically tell it to use ALSA for sound. This was achieved by adding the line ao_driver "also09" to the mpd.conf file. The command below should do that automatically:
```
sudo  echo ao_driver \"alsa09\" >> /etc/mpd.conf
```

Then do the command 
```
sudo /etc/init.d/mpd restart
``` to restart mpd. It should hopefully then all work fine

---

### Post by blissfulignant on 2005-05-06
I got this working by using the ubuntu version of MPD, which I found by asking the oracle for "ubuntu mpd"

[QUOTE=blissfulignant]I recently installed Hoary, but I can't seem to get MPD to install... here's my console output, see if you can make any sense of it...

>dpkg -i mpd_0.11.5-1_i386.deb
Selecting previously deselected package mpd.
(Reading database ... 59629 files and directories currently installed.)
Unpacking mpd (from mpd_0.11.5-1_i386.deb) ...
dpkg: dependency problems prevent configuration of mpd:
 mpd depends on libflac4; however:
  Package libflac4 is not installed.
dpkg: error processing mpd (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mpd

I know for a fact that libflac6 is installed (Synaptic says so)...[/QUOTE]

---

### Post by frogman on 2005-05-24
[Ampache](http://www.ampache.org)  works well with mpd.  You can play music through speakers attached to the server, or stream it to clients.

---

### Post by bryklie on 2005-07-05
[QUOTE=rick_hewes]This is exactly what happens for me also. (The player looks as though its going to play then doesn't). 

In the error log "problems opening audio device while playing" + mp3 file.

If I restart mpd as root it is fine. Or run mpd under my own user name.
But trying to start at boot time under the mpd user fails.

I have made sure user mpd is a member of the audio group and have added mpd as the user in mpd.conf.

Any help would be appreciated.

Rick[/QUOTE]

The solution is to edit the file /etc/esound/esd.conf and make sure that the following line exists:

auto_spawn=1
spawn_options=-noterminate -nobeeps -as 5

Save the config file and restart the PC.

The problem is that ESD was only being started once you logged into the PC. If like me you were running a server and connecting to it from a client then the ESD daemon would not have started, unless you were logged in.

---

### Post by mayonaise15 on 2006-10-15
Thank you very much for this how-to.  I have been looking for a system that I can use to play music in the dental office I do consulting work at.  Right now they are just using a 5 CD changer and some digital cable music system for music, but the cable company is about to terminate that service.  

It looks like with this I will be able to dump all of the CD's to a disk drive and have it be controlled through a web interface?  Also , does anybody know if this or any other program that can stream sources (net raido) from a remote interface?

---

### Post by elektronaut on 2006-11-29
> **mayonaise15 said:**
> 
It looks like with this I will be able to dump all of the CD's to a disk drive and have it be controlled through a web interface?  Also , does anybody know if this or any other program that can stream sources (net raido) from a remote interface?
Might be a bit late for an answer, but still... I'm no expert on this, but looking at [the feature list of mpd](http://www.musicpd.org/features.shtml), this should be possible. There is also [GiantDisc](http://giantdisc.org/), which should also do this. I'm just running mpd + gmpc on my laptop, but I'm about to set up a client/server solution soon. To my knowledge, both projects seem to have it's pros and cons. mpd doesn't need much resources, you can have it running on a linux router. GiantDisc comes with a very nice Palm PDA interface, but you need a 'real' computer to run it on. Of course you can't stream music to the (possibly wireless) Palm, it's just an input interface. But you could set up a (headless) streaming client to receive the stream. Or, if you don't care too much for sound quality, you could hook up a FM transmitter to the soundcard of the music server and use plain old radio receivers instead of streaming clients.

---

### Post by airtonix on 2006-12-07
please extrapolate on "real computer".....confused.

Linux runs on a imaginary computer?

---

### Post by aidanr on 2006-12-07
[http://sonata.berlios.de/](http://sonata.berlios.de/)

^ very nice frontend for mpd

---

### Post by finferflu on 2007-03-02
Is there any way I can play streaming (ogg) playlists with MPD/MPC?

Thanks!

---

### Post by tomski on 2010-01-14
why do things in linux get perpetualy dificult!!!!!
pretty soon we will all have to learn C# or C+ just to use it


mpd is a pointless application which takes 1month to a year BEFORE you actualy use it
even the wiki is as cryptic as quantum cyper

how the hell are we supposed to attract users to using linux when application like this are prolific throughout it!!!!!

---

### Post by nilarimogard on 2010-01-14
This is a very old how-to, look for a newer one :)

---

### Post by arrrghhh on 2010-04-29
I've installed this on my -server install, and it segfaults every time it tries to play a song.

Fresh 10.04 install, it was working on a 9.10 install previously.  I don't get it.  Segfaults on libavcodec...

---

### Post by Cool Javelin on 2010-07-15
arrrghhh:

Thanks for this, I just installed MPD/MPC on my new Ubuntu server 10.04. (no graphical interface)

I would like to allow my wife to control it from her XP computer, can you recommend any interfaces I can run on windoz that will allow her to do that, and also, maybe how to connect them to MPD.

Thanks.

Mark.

---

### Post by karmila on 2011-03-15
> **nilarimogard said:**
> This is a very old how-to, look for a newer one :)

Hi! I read your blog daily :D

===================

Please help me anyone... where is the up to date how-to?

---

