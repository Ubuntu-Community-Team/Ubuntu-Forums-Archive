---
title: "HOWTO: Install and Customize Music Player Daemon in Ubuntu (v2)"
date: 2005-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Xgkkp on 2005-05-04
**Edit: This guide is ridiculously ancient, and I haven't used it in years, so take anything it says with a pinch of salt!**
*Note: This is an update of the original post [Here](http://www.ubuntuforums.org/showthread.php?t=5194&page=1&pp=10) by Zenwhen*
**What is [Music Player Daemon](http://www.musicpd.org/) ?**

> Music Player Daemon (MPD) allows remote access for playing music and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It is also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.

**Why should I use it instead of Rhythmbox or Muine?**

MPD is light on your resources, and high on [extensibility](http://www.musicpd.org/clients.shtml). The daemon is easy to interact with, develop front ends for, and configure with intuitive configuration scripts. If that doesn't convince you, perhaps the pretty screenshots and features coming later in this thread will. I personally use it mainly so that I can sit on my sofa with my laptop, yet still play music through my main speaker system using my main computer.

**How do I get Music Player Daemon?**

As log as you have [configured your repositories correctly](http://www.ubuntuguide.org/#repositories), installing mpd is as simple as typing into the console:
```
apt-get install mpd mpc gmpc
```
**How do I configure Music Player Daemon**

In these instructions, we shall be configuring mpd to run as a system service. This will mean that it will start on boot, and run as it's own user (for security). We will also have a seperate folder where it stores it's music list (we can use symbolic links to add other directories)

Type this into the console:
```
sudo dpkg-reconfigure mpd
```
This will bring up a console-interface to configure mpd. Use the keyboard to move around. Do the following:
[list=1]
[*] When it asks if you want to configure as a system service, choose <Yes>
[*] Hit Enter on the next three windows - where it asks you for the directories for the music and playlist, and the port number to use
[*] Hit <Yes> for the state file. This means that it will save your playlist and music position when you turn off the computer (or restart mpd)
[*] Choose either <Yes> or <No> for restart on upgrade. I chose <No>
[/list] 
It will then quit and start mpd for you.

Now, people have been having trouble getting this to work on Hoary (myself included) and I found that this was easily solved by adding a single line to the mpd.conf saying 'ao_driver "alsa09"'. If you type the following into the console this will be done automatically:
```
sudo  echo ao_driver \"alsa09\" >> /etc/mpd.conf
```
after this restart mpd with the following command:
```
sudo /etc/init.d/mpd restart
```

**How do I add music to Music Player Daemon**
You add music by adding symbolic links to the music directory, which is set to /usr/share/mpd/music/ with the above steps. 
Say, for example, you store your music in your home directory, under the "mp3s" folder, you would issue the following command:
```
sudo ln -s $HOME/mp3s /usr/share/mpd/music
```
you then need to tell mpd to rebuild it's music database. You can do this through the graphical client, gmpc, or using mpc by typing ```
mpc update
```

**How do I use Music Player Daemon**
The GTK client for mpd is called *gmpc*.

Using this to manage MPD and update your database will make using MPD effortless, and its playlist options are as as good as any, though not as complicated. You may have noticed a set of panel launchers there on that screenshot that look like media player controls. Those are custom application launchers added to the gnome panel with a right click that point to some commands that can be sent to mpc (the command line media player daemon client). Some of the more common commands are:

```
mpc                         Displays status
mpc play <number>           Start playing at <number> (default: 1)
mpc next                    Play the next song in the current playlist
mpc prev                    Play the previous song in the current playlist
mpc pause                   Pauses the currently playing song
mpc stop                    Stop the currently playing playlists

```

For a complete list of commands for mpc, type
```
mpc --help
```

The icons on the launchers are the same as used in gmpc, and they should be installed to the folder /usr/share/mpc/

If you decided not to install mpd as a system service, you will have to start mpd with the "mpd" command before music playing works. You can either add a launcher to run that command, run it from the terminal whenever you start up, or you can add it to "gnome-session-properties" as a startup command. 

After that, you will be able to run GMPC, have a nice pop-up window whenever the song changes, control it in a winamp like fashion with he GUI, and control it from your taskbar. You can control it from the terminal without booting into X with the mpc commands, and can control it with  [FoxyTunes](https://update.mozilla.org/extensions/moreinfo.php?application=firefox&id=219).

If you noticed that I said the word "control" a lot in that last paragraph, you are right. MPD gives you total control over your music library, and gives you the ability to control it from wherever you wish, however you wish, access it how you wish, and from any OS you wish using any desktop environment you wish. There are also clients for all of the major desktop environments; including [KDE](http://www.musicpd.org/kmp.shtml)  and even [Windows](http://www.musicpd.org/MPD-Commander.shtml). 

I will answer any questions you raise to the best of my ability. Enjoy! :)

**Troubleshooting**
Here will be a list of errors people hhve had and the possible fixes. If you have a problem not listed here, it is worth taknig a look at the /var/log/mpd/errors.log file (by default this is only accesible by root):
*When I click play on gmpc, it flickers the song title and then does nothing*
[list][*]Make sure you have the correct sound driver chosen, for me this was adding the ao_driver line to the mpd.conf[/list]


**Getting Extra Help**
As I said, I and anybody else who knows will help here, but there are a couple of other good places to ask for help:
[list]
[*][The Music Player Daemon Wiki](http://mpd.wikicities.com/wiki/Main_Page)
[*]On IRC, the #mpd channel on freenode
[*]The man page for mpd is very helpful and explains the mpd.conf file settings ( man mpd )
[/list] 
*Note: This post is mostly based off of a post by Zenwhen [Here](http://www.ubuntuforums.org/showthread.php?t=5194&page=1&pp=10) , but I thought I would re-create it in the Hoary section, and update it with hoary specifics.*

---

### Post by geearf on 2005-07-29
Hello,

thanks for this howto but I have a problem.

I installed mpg on the server, and mpd, mpc and kmp on the client.

The server should be well configurated, but I can't really say so cause I am not at home right now..

The client can connect to server, finds the files to play, plays them, but I hear nothing .. while I can listen to music with amarok.

Is there anything done wrong ?

---

### Post by Stormy Eyes on 2005-07-29
[QUOTE=geearf]The client can connect to server, finds the files to play, plays them, but I hear nothing .. while I can listen to music with amarok.

Is there anything done wrong ?[/QUOTE]

Are the speakers hooked up to the server, or to the client? MPD doesn't transmit audio across the network, it just allows you to control it remotely.

---

### Post by IdoMcFly on 2005-09-16
is there a way to do like xmms when you hit q on an item on the playlist?

it queues the song so it is play next and then revert back to where it was before the queued and you can queue many items.

---

### Post by geearf on 2005-09-16
[QUOTE=Stormy Eyes]Are the speakers hooked up to the server, or to the client? MPD doesn't transmit audio across the network, it just allows you to control it remotely.[/QUOTE]
Oops sorry I did not answer you, the yes I wanted to get music over the internet, which was not possible this way, but It helped me scaring my mother from work (without intention), so it was still fun :)

thanks

---

### Post by ZylGadis on 2005-12-20
If it does not forward the stream to the local box, then I would definitely prefer running xmms through X-forwarded ssh connection. It would be more secure, at least.
Besides, I believe there are obscure ways to make xmms work with a remote-enabled esd daemon on the client box, thus forwarding the sound too.

---

### Post by qball on 2006-01-10
[QUOTE=IdoMcFly]is there a way to do like xmms when you hit q on an item on the playlist?

it queues the song so it is play next and then revert back to where it was before the queued and you can queue many items.[/QUOTE]

This isn't availible in mpd yet. There is a patch around to support this kind of behauviour in the svn version of mpd, but that isn't intergrated yet.

It's  a shame gmpc 0.12.0 just went into dapper and isn't availible on breezy, it's been out for quiet a while. gmpc 0.12 is an improvement, stability wise, over the older version of gmpc.

---

### Post by qball on 2006-01-10
[QUOTE=Alex.P]If it does not forward the stream to the local box, then I would definitely prefer running xmms through X-forwarded ssh connection. It would be more secure, at least.
Besides, I believe there are obscure ways to make xmms work with a remote-enabled esd daemon on the client box, thus forwarding the sound too.[/QUOTE]

This trick can be done, and is done, with mpd too.
If you install the development version of mpd  you can, in combination with icecast, setup a streaming server.

---

### Post by ShinjiLeery on 2006-10-29
Hi,

When i run 

```
sudo dpkg-reconfigure mpd
```

nothing happen in the terminal ... 
All the packages are installed

Tnx, 
Luca.

---

### Post by fwwarr on 2006-11-01
Hi

I am having the same problem as ShinjiLeery. Is there a way around this? I tried modifying /etc/mpd.conf manually but I\that wasn't successful either.

I am running Ubuntu 6.10, and have mpd, mpc and gmpc installed (but not working).

Thanks

---

### Post by khaeru on 2006-11-02
I got this working in edgy:

```

# Install (or use Synaptic)
sudo apt-get install mpd mpc gmpc

# Replace mpd music directory with symlink to your own; I have my music in /home/khaeru/Music
sudo rmdir /var/lib/mpd/music
sudo ln -s ~/Music /var/lib/mpd/music

# Restart and update database
sudo /etc/init.d/mpd restart
mpc update

```

Run gmpc from the GNOME menu, click the 'Configure gmpc' button, then 'Connect'. Should be good! I also like pympd -- it tells me I have 9135 songs, 27 days 4 hours and 12 minutes of music -)

---

### Post by qball on 2006-11-06
A new gmpc is making progress nicely, and if you want to try it before it's released you can follow the following howto (just something trown together, sorry for this, I will try to improve it)

[http://musicpd.org/~qball/HowtoGmpc.html](http://musicpd.org/~qball/HowtoGmpc.html)

For a few screenshots look here:
[http://musicpd.org/~qball/Manual.chunked/](http://musicpd.org/~qball/Manual.chunked/)
and:
[http://images.qballcow.nl/gmpc/gmpc-metainfo.png](http://images.qballcow.nl/gmpc/gmpc-metainfo.png)

---

### Post by Fab on 2006-11-08
thanks, qball. worked perfectly fine (one req was missing afair, gob(2) )
I really like the new features :)

Oh yeah, which package(s) do I need for the wikipedia plugin? It says something about gtk-mozembed or similar (cant remember right now) missing..

---

### Post by qball on 2006-11-08
I indeed forgot to add gob2, I will add it...

you need firefox-dev and this: [http://wordpress.qballcow.nl/2006/06/11/weird-gtkmozembed-errors-on-dapper-heres-a-fix/](http://wordpress.qballcow.nl/2006/06/11/weird-gtkmozembed-errors-on-dapper-heres-a-fix/)

---

### Post by Fab on 2006-11-09
works! :)

---

### Post by qball on 2006-11-11
Updated document here: [http://sarine.nl/index.php?page=gmpc-compile-svn](http://sarine.nl/index.php?page=gmpc-compile-svn)

---

### Post by ShiftyPowers on 2006-11-17
> **ShinjiLeery said:**
> Hi,

When i run 

```
sudo dpkg-reconfigure mpd
```

nothing happen in the terminal ... 
All the packages are installed

Tnx, 
Luca.

I tried this as well and get nothing coming up on the terminal when doing the dpkg-reconfigure.  Also, after the sudo aptitude install mpd mpc gmpc I get absolutely no mpd.conf anywhere in my system.  Anyone have any idea?

---

### Post by elektronaut on 2006-11-29
Don't rely on information found in posts that were made a year ago! Software changes quickly, especially if it's Open Source Software :D 
Just follow [this post](http://ubuntuforums.org/showpost.php?p=1702562&postcount=11), it worked for me.

---

### Post by khaeru on 2007-02-17
> **elektronaut said:**
> Don't rely on information found in posts that were made a year ago! Software changes quickly, especially if it's Open Source Software :D 
Just follow [this post](http://ubuntuforums.org/showpost.php?p=1702562&postcount=11), it worked for me.

Thanks, elektronaut! I've since stopped using gmpc, and after having tried almost all of the [available MPD clients](http://mpd.wikia.com/wiki/Clients), I've settled on [Sonata](http://sonata.berlios.de). I asked for it to be included in the Feisty repositories - in the meantime, an Ubuntu .deb is available at [http://packages.matt-good.net](http://packages.matt-good.net)

So, in my above post, only use
```
sudo apt-get install mpd mpc
```

... then follow the rest, and finally install the Sonata .deb. You're set!

---

### Post by el_itur on 2007-02-26
Khaeru, thanks for clearing things up.

I've tried up sonata. IT ROCKS.

Good by aoudacious,  gmpc, and friends :)

---

### Post by mailbox on 2007-05-21
"Type this into the console:
    sudo dpkg-reconfigure mpd
This will bring up a console-interface to configure mpd. Use the keyboard to move around. Do the following:"

that line does nothing. is it safe to continue without going through whatever that would have done for me?

---

### Post by exchequer598 on 2007-11-02
> **khaeru said:**
> I got this working in edgy:

```

# Install (or use Synaptic)
sudo apt-get install mpd mpc gmpc

# Replace mpd music directory with symlink to your own; I have my music in /home/khaeru/Music
sudo rmdir /var/lib/mpd/music
sudo ln -s ~/Music /var/lib/mpd/music

# Restart and update database
sudo /etc/init.d/mpd restart
mpc update

```

Run gmpc from the GNOME menu, click the 'Configure gmpc' button, then 'Connect'. Should be good! I also like pympd -- it tells me I have 9135 songs, 27 days 4 hours and 12 minutes of music -)

I tried doing this, and I got this error->

```

prasannah@home:/usr/share/mpd$ sudo rmdir /var/lib/mpd/music
prasannah@home:/usr/share/mpd$ sudo ln -s /media/hdb6/English /var/lib/mpd/music
prasannah@home:/usr/share/mpd$ sudo /etc/init.d/mpd restart
Stopping Music Player Daemon: mpd.
Starting Music Player Daemon: cannot open music_directory "/var/lib/mpd/music/" (config line 8): No such file or directory
failed.

```
:confused:

---

### Post by andrek on 2007-11-02
Here's how i have installed mpd and sonata [ the greatest mpd player ;) ]
sudo apt-get install mpd sonata
rm ~/.mpdconf
sudo ln -s /where/is/your/music /var/lib/mpd/music/mp3
[ for example sudo ln -s /media/hda5/Music /var/lib/mpd/music/mp3 ]
sudo mpd --create-db [ DOUBLE dash ]
sudo killall mpd
sudo /etc/init.d/mpd start

now open sonata and in its preferences, Music dir should be /var/lib/mpd/music/

That's all.
Of course, if your actual music folder is on a ntfs partition, you've got to enable ntfs-3g [ easily by ntfs-config ].

---

### Post by foxy123 on 2007-11-03
MPD crashes on boot in Gutsy. It worked fine in Feisty but now I have to run ```
sudo mpd
``` every boot. I
I do not know where to find messages which appear on the screen during boot but it is very similar to what I have with dpkg-reconfigure:
```
$ sudo dpkg-reconfigure mpd
start-stop-daemon: --start needs --exec or --startas
Try `start-stop-daemon --help' for more information.

```

---

### Post by DarkDead on 2007-11-11
Hi all. I've installed MPD and a daemon called SCMPC which is a last.fm scrobbler that runs on background. It's great advantage is that it can scrobble any track you play no matter what client you use (you don't even need to be running any client).
Installation instructions here: [http://webadedios.net/modules/wordpress/archives/otra-de-lastfm-enviando-lo-que-escucho]("http://webadedios.net/modules/wordpress/archives/otra-de-lastfm-enviando-lo-que-escucho")

Now I need to create an init.d script to run SCMPC every time the computer is turned on. There are some examples here: [http://forums.gentoo.org/viewtopic-t-438701-postdays-0-postorder-asc-start-0.html]("http://forums.gentoo.org/viewtopic-t-438701-postdays-0-postorder-asc-start-0.html") but they are suited for Gentoo and don't work in my system.
Does anyone know how to create one script for Ubuntu?

---

### Post by Colbrac on 2008-01-04
you can add your script to /etc/rc.local.
In this file you simply state a list of commands/scripts that are the last things that are executed on boot. You don't need to 'sudo' everything, it runs as root allready. Also I think you need to specify the full path to the command, but I'm not sure about that. At least full paths never hurt. :)

---

### Post by Tu13erhead on 2008-04-07
> **mailbox said:**
> "Type this into the console:
    sudo dpkg-reconfigure mpd
This will bring up a console-interface to configure mpd. Use the keyboard to move around. Do the following:"

that line does nothing. is it safe to continue without going through whatever that would have done for me?

Like quite a few others in this thread, I get this too.

Does anyone have any input on this?

Thanks.

---

### Post by qball on 2008-04-10
See [https://launchpad.net/~qball-qballcow/+archive](https://launchpad.net/~qball-qballcow/+archive) for more  up2date package of gmpc. (gutsy and hardy)

---

### Post by brunosso on 2008-11-29
when i make the db, i have this error!

```
added Divertenti/Lillo E Greg/610 - lillo & greg - f0000442.mp3
added Divertenti/Lillo E Greg/seiunozeril del 07-09-2006.mp3
added Divertenti/Lillo E Greg/610settimana2005_04_10.mp3
added Divertenti/Lillo E Greg/610 - greg lillo2 - 14 invenzioni.mp3
added Divertenti/Lillo E Greg/610settimana2005_01_16.mp3
added Divertenti/Lillo E Greg/610 - greglillo3 - 03 storie di vita.mp3
*** glibc detected *** mpd: free(): invalid next size (normal): 0x08a43668 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x414f73f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0x414f9456]
/usr/lib/libmad.so.0(mad_stream_finish+0x29)[0x4fc14879]
mpd[0x8056fa1]
mpd[0x8056ff3]
mpd[0x8070c59]
mpd[0x8070d3b]
mpd[0x8060792]
mpd[0x80608fe]
mpd[0x806065a]
mpd[0x80606f1]
mpd[0x80608fe]
mpd[0x806065a]
mpd[0x80606f1]
mpd[0x80608fe]
mpd[0x8060989]
mpd[0x8068c75]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0x4149e685]
mpd[0x804f241]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:05 919039     /usr/bin/mpd
08081000-08082000 r--p 00038000 08:05 919039     /usr/bin/mpd
08082000-08083000 rw-p 00039000 08:05 919039     /usr/bin/mpd
08083000-08087000 rw-p 08083000 00:00 0 
0897e000-08afc000 rw-p 0897e000 00:00 0          [heap]
412e1000-412ec000 r-xp 00000000 08:05 920804     /usr/lib/libvorbisenc.so.2.0.3
412ec000-412ed000 r--p 0000a000 08:05 920804     /usr/lib/libvorbisenc.so.2.0.3
412ed000-413db000 rw-p 0000b000 08:05 920804     /usr/lib/libvorbisenc.so.2.0.3
41488000-415e0000 r-xp 00000000 08:05 942632     /lib/tls/i686/cmov/libc-2.8.90.so
415e0000-415e2000 r--p 00158000 08:05 942632     /lib/tls/i686/cmov/libc-2.8.90.so
415e2000-415e3000 rw-p 0015a000 08:05 942632     /lib/tls/i686/cmov/libc-2.8.90.so
415e3000-415e6000 rw-p 415e3000 00:00 0 
415e8000-415ea000 r-xp 00000000 08:05 943092     /lib/tls/i686/cmov/libdl-2.8.90.so
415ea000-415eb000 r--p 00001000 08:05 943092     /lib/tls/i686/cmov/libdl-2.8.90.so
415eb000-415ec000 rw-p 00002000 08:05 943092     /lib/tls/i686/cmov/libdl-2.8.90.so
415ee000-41603000 r-xp 00000000 08:05 943090     /lib/tls/i686/cmov/libpthread-2.8.90.so
41603000-41604000 r--p 00014000 08:05 943090     /lib/tls/i686/cmov/libpthread-2.8.90.so
41604000-41605000 rw-p 00015000 08:05 943090     /lib/tls/i686/cmov/libpthread-2.8.90.so
41605000-41607000 rw-p 41605000 00:00 0 
41609000-4162d000 r-xp 00000000 08:05 943096     /lib/tls/i686/cmov/libm-2.8.90.so
4162d000-4162e000 r--p 00023000 08:05 943096     /lib/tls/i686/cmov/libm-2.8.90.so
4162e000-4162f000 rw-p 00024000 08:05 943096     /lib/tls/i686/cmov/libm-2.8.90.so
41631000-41645000 r-xp 00000000 08:05 918244     /usr/lib/libz.so.1.2.3.3
41645000-41647000 rw-p 00013000 08:05 918244     /usr/lib/libz.so.1.2.3.3
41649000-4164a000 r-xp 00000000 08:05 918597     /usr/lib/libxcb-xlib.so.0.0.0
4164a000-4164b000 r--p 00000000 08:05 918597     /usr/lib/libxcb-xlib.so.0.0.0
4164b000-4164c000 rw-p 00001000 08:05 918597     /usr/lib/libxcb-xlib.so.0.0.0
4164e000-41652000 r-xp 00000000 08:05 918283     /usr/lib/libXdmcp.so.6.0.0
41652000-41653000 rw-p 00003000 08:05 918283     /usr/lib/libXdmcp.so.6.0.0
41655000-41740000 r-xp 00000000 08:05 918598     /usr/lib/libX11.so.6.2.0
41740000-41741000 r--p 000ea000 08:05 918598     /usr/lib/libX11.so.6.2.0
41741000-41743000 rw-p 000eb000 08:05 918598     /usr/lib/libX11.so.6.2.0
41743000-41744000 rw-p 41743000 00:00 0 
41746000-41748000 r-xp 00000000 08:05 918282     /usr/lib/libXau.so.6.0.0
41748000-41749000 rw-p 00001000 08:05 918282     /usr/lib/libXau.so.6.0.0
4174b000-41762000 r-xp 00000000 08:05 918456     /usr/lib/libxcb.so.1.0.0
41762000-41763000 r--p 00016000 08:05 918456     /usr/lib/libxcb.so.1.0.0
41763000-41764000 rw-p 00017000 08:05 918456     /usr/lib/libxcb.so.1.0.0
4184b000-41852000 r-xp 00000000 08:05 943091     /lib/tls/i686/cmov/librt-2.8.90.so
41852000-41853000 r--p 00007000 08:05 943091     /lib/tls/i686/cmov/librt-2.8.90.so
41853000-41854000 rw-p 00008000 08:05 943091     /lib/tls/i686/cmov/librt-2.8.90.so
41a88000-41a95000 r-xp 00000000 08:05 2367509    /lib/libgcc_s.so.1
41a95000-41a96000 r--p 0000c000 08:05 2367509    /lib/libgcc_s.so.1
41a96000-41a97000 rw-p 0000d000 08:05 2367509    /lib/libgcc_s.so.1
42129000-4213e000 r-xp 00000000 08:05 919803     /usr/lib/libICE.so.6.3.0
4213e000-4213f000 rw-p 00014000 08:05 919803     /usr/lib/libICE.so.6.3.0
4213f000-42141000 rw-p 4213f000 00:00 0 
42143000-4214a000 r-xp 00000000 08:05 919805     /usr/lib/libSM.so.6.0.0
4214a000-4214b000 r--p 00006000 08:05 919805     /usr/lib/libSM.so.6.0.0
4214b000-4214c000 rw-p 00007000 08:05 919805     /usr/lib/libSM.so.6.0.0
4f990000-4f9aa000 r-xp 00000000 08:05 2367501    /lib/ld-2.8.90.so
4f9ab000-4f9ac000 r--p 0001a000 08:05 2367501    /lib/ld-2.8.90.so
4f9ac000-4f9ad000 rw-p 0001b000 08:05 2367501    /lib/ld-2.8.90.so
4f9af000-4f9b2000 r-xp 00000000 08:05 920264     /usr/lib/libao.so.2.1.3
4f9b2000-4f9b4000 rw-p 00003000 08:05 920264     /usr/lib/libao.so.2.1.3
4f9e9000-4f9fe000 r-xp 00000000 08:05 943097     /lib/tls/i686/cmov/libnsl-2.8.90.so
4f9fe000-4f9ff000 r--p 00014000 08:05 943097     /lib/tls/i686/cmov/libnsl-2.8.90.so
4f9ff000-4fa00000 rw-p 00015000 08:05 943097     /lib/tls/i686/cmov/libnsl-2.8.90.so
4fa00000-4fa02000 rw-p 4fa00000 00:00 0 
4fa23000-4fa26000 r-xp 00000000 08:05 11698494   /lib/libcap.so.1.10
4fa26000-4fa27000 rw-p 00002000 08:05 11698494   /lib/libcap.so.1.10
4fa29000-4fa77000 r-xp 00000000 08:05 920617     /usr/lib/libpulse.so.0.4.1
4fa77000-4fa78000 r--p 0004d000 08:05 920617     /usr/lib/libpulse.so.0.4.1
4fa78000-4fa79000 rw-p 0004e000 08:05 920617     /usr/lib/libpulse.so.0.4.1
4fab8000-4fac6000 r-xp 00000000 08:05 917641     /usr/lib/libjack.so.0.0.28
4fac6000-4fac7000 r--p 0000e000 08:05 917641     /usr/lib/libjack.so.0.0.28
4fac7000-4fac9000 rw-p 0000f000 08:05 917641     /usr/lib/libjack.so.0.0.28
4fac9000-4fad1000 rw-p 4fac9000 00:00 0 
4fad7000-4fb9a000 r-xp 00000000 08:05 919588     /usr/lib/libasound.so.2.0.0
4fb9a000-4fb9c000 r--p 000c2000 08:05 919588     /usr/lib/libasound.so.2.0.0
4fb9c000-4fb9f000 rw-p 000c4000 08:05 919588     /usr/lib/libasound.so.2.0.0
4fba1000-4fbf2000 r-xp 00000000 08:05 920461     /usr/lib/libFLAC.so.8.2.0
4fbf2000-4fbf3000 r--p 00050000 08:05 920461     /usr/lib/libFLAC.so.8.2.0
4fbf3000-4fbf4000 rw-p 00051000 08:05 920461     /usr/lib/libFLAC.so.8.2.0
4fc12000-4fc28000 r-xp 00000000 08:05 920654     /usr/lib/libmad.so.0.2.1
4fc28000-4fc29000 r--p 00015000 08:05 920654     /usr/lib/libmad.so.0.2.1
4fc29000-4fc2a000 rw-p 00016000 08:05 920654     /usr/lib/libmad.so.0.2.1
4fc34000-4fc56000 r-xp 00000000 08:05 919794     /usr/lib/libaudiofile.so.0.0.2
4fc56000-4fc59000 rw-p 00021000 08:05 919794     /usr/lib/libaudiofile.so.0.0.2
4fefa000-4fefe000 r-xp 00000000 08:05 920460     /usr/lib/libogg.so.0.5.3
4fefe000-4feff000 r--p 00003000 08:05 920460     /usr/lib/libogg.so.0.5.3
4feff000-4ff00000 rw-p 00004000 08:05 920460     /usr/lib/libogg.so.0.5.3
4ff02000-5006a000 r-xp 00000000 08:05 920459     /usr/lib/libsamplerate.so.0.1.3
5006a000-5006b000 r--p 00167000 08:05 920459     /usr/lib/libsamplerate.so.0.1.3
5006b000-5006c000 rw-p 00168000 08:05 920459     /usr/lib/libsamplerate.so.0.1.3
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7c3d000-b7d3c000 rw-p b7c3d000 00:00 0 
b7d3c000-b7d46000 r-xp 00000000 08:05 11715750   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d46000-b7d47000 r--p 00009000 08:05 11715750   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d47000-b7d48000 rw-p 0000a000 08:05 11715750   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d48000-b7d51000 r-xp 00000000 08:05 11715754   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7d51000-b7d52000 r--p 00008000 08:05 11715754   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7d52000-b7d53000 rw-p 00009000 08:05 11715754   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7d53000-b7d5a000 r-xp 00000000 08:05 11715746   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7d5a000-b7d5b000 r--p 00006000 08:05 11715746   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7d5b000-b7d5c000 rw-p 00007000 08:05 11715746   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7d5c000-b7d5f000 rw-p b7d5c000 00:00 0 
b7d5f000-b7d95000 r-xp 00000000 08:05 2367505    /lib/libdbus-1.so.3.4.0
b7d95000-b7d96000 r--p 00035000 08:05 2367505    /lib/libdbus-1.so.3.4.0
b7d96000-b7d97000 rw-p 00036000 08:05 2367505    /lib/libdbus-1.so.3.4.0
b7d97000-b7d98000 rw-p b7d97000 00:00 0 
b7d98000-b7db3000 r-xp 00000000 08:05 2252829    /usr/lib/sse2/libspeex.so.1.4.0
b7db3000-b7db4000 r--p 0001a000 08:05 2252829    /usr/lib/sse2/libspeex.so.1.4.0
b7db4000-b7db5000 rw-p 0001b000 08:05 2252829    /usr/lib/sse2/libspeex.so.1.4.0
b7db5000-b7dfe000 r-xp 00000000 08:05 919967     /usr/lib/libtheora.so.0.3.3
b7dfe000-b7e00000 rw-p 00049000 08:05 919967     /usr/lib/libtheora.so.0.3.3
b7e00000-b7e01000 rw-p b7e00000 00:00 0 
b7e01000-b7e10000 r-xp 00000000 08:05 919522     /usr/lib/libavahi-client.so.3.2.4
b7e10000-b7e11000 r--p 0000e000 08:05 919522     /usr/lib/libavahi-client.so.3.2.4
b7e11000-b7e12000 rw-p 0000f000 08:05 919522     /usr/liAborted
brunosso@brunosso-laptop:~$ 

```

and the library is not make!

---

### Post by Alucard-sama on 2008-12-02
> root@kendawg-desktop:~# sudo dpkg-reconfigure mpd
 * Starting Music Player Daemon mpd                                             No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed

Now what? The instruction for adding that line to mpd.conf didn't help?

---

### Post by Eamon1 on 2009-04-08
I'm getting exactly the same error. Any ideas?

```
 * Starting Music Player Daemon mpd                                            
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
    
```

---

### Post by afrodeity on 2009-07-21
> **brunosso said:**
> when i make the db, i have this error!

```

*** glibc detected *** mpd: free(): invalid next size (normal): 0x08a43668 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x414f73f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0x414f9456]
/usr/lib/libmad.so.0(mad_stream_finish+0x29)[0x4fc14879]
mpd[0x8056fa1]
mpd[0x8056ff3]
mpd[0x8070c59]
mpd[0x8070d3b]
mpd[0x8060792]
mpd[0x80608fe]
mpd[0x806065a]
mpd[0x80606f1]
mpd[0x80608fe]
mpd[0x806065a]
mpd[0x80606f1]
mpd[0x80608fe]
mpd[0x8060989]
mpd[0x8068c75]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0x4149e685]
mpd[0x804f241]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:05 919039     /usr/bin/mpd
08081000-08082000 r--p 00038000 08:05 919039     /usr/bin/mpd
08082000-08083000 rw-p 00039000 08:05 919039     /usr/bin/mpd
08083000-08087000 rw-p 08083000 00:00 0 
0897e000-08afc000 rw-p 0897e000 00:00 0          [heap]
412e1000-412ec000 r-xp 00000000 08:05 920804     /usr/lib/libvorbisenc.so.2.0.3
412ec000-412ed000 r--p 0000a000 08:05 920804     /usr/lib/libvorbisenc.so.2.0.3
412ed000-413db000 rw-p 0000b000 08:05 920804     /usr/lib/libvorbisenc.so.2.0.3
41488000-415e0000 r-xp 00000000 08:05 942632     /lib/tls/i686/cmov/libc-2.8.90.so
415e0000-415e2000 r--p 00158000 08:05 942632     /lib/tls/i686/cmov/libc-2.8.90.so
415e2000-415e3000 rw-p 0015a000 08:05 942632     /lib/tls/i686/cmov/libc-2.8.90.so
415e3000-415e6000 rw-p 415e3000 00:00 0 
415e8000-415ea000 r-xp 00000000 08:05 943092     /lib/tls/i686/cmov/libdl-2.8.90.so
415ea000-415eb000 r--p 00001000 08:05 943092     /lib/tls/i686/cmov/libdl-2.8.90.so
415eb000-415ec000 rw-p 00002000 08:05 943092     /lib/tls/i686/cmov/libdl-2.8.90.so
415ee000-41603000 r-xp 00000000 08:05 943090     /lib/tls/i686/cmov/libpthread-2.8.90.so
41603000-41604000 r--p 00014000 08:05 943090     /lib/tls/i686/cmov/libpthread-2.8.90.so
41604000-41605000 rw-p 00015000 08:05 943090     /lib/tls/i686/cmov/libpthread-2.8.90.so
41605000-41607000 rw-p 41605000 00:00 0 
41609000-4162d000 r-xp 00000000 08:05 943096     /lib/tls/i686/cmov/libm-2.8.90.so
4162d000-4162e000 r--p 00023000 08:05 943096     /lib/tls/i686/cmov/libm-2.8.90.so
4162e000-4162f000 rw-p 00024000 08:05 943096     /lib/tls/i686/cmov/libm-2.8.90.so
41631000-41645000 r-xp 00000000 08:05 918244     /usr/lib/libz.so.1.2.3.3
41645000-41647000 rw-p 00013000 08:05 918244     /usr/lib/libz.so.1.2.3.3
41649000-4164a000 r-xp 00000000 08:05 918597     /usr/lib/libxcb-xlib.so.0.0.0
4164a000-4164b000 r--p 00000000 08:05 918597     /usr/lib/libxcb-xlib.so.0.0.0
4164b000-4164c000 rw-p 00001000 08:05 918597     /usr/lib/libxcb-xlib.so.0.0.0
4164e000-41652000 r-xp 00000000 08:05 918283     /usr/lib/libXdmcp.so.6.0.0
41652000-41653000 rw-p 00003000 08:05 918283     /usr/lib/libXdmcp.so.6.0.0
41655000-41740000 r-xp 00000000 08:05 918598     /usr/lib/libX11.so.6.2.0
41740000-41741000 r--p 000ea000 08:05 918598     /usr/lib/libX11.so.6.2.0
41741000-41743000 rw-p 000eb000 08:05 918598     /usr/lib/libX11.so.6.2.0
41743000-41744000 rw-p 41743000 00:00 0 
41746000-41748000 r-xp 00000000 08:05 918282     /usr/lib/libXau.so.6.0.0
41748000-41749000 rw-p 00001000 08:05 918282     /usr/lib/libXau.so.6.0.0
4174b000-41762000 r-xp 00000000 08:05 918456     /usr/lib/libxcb.so.1.0.0
41762000-41763000 r--p 00016000 08:05 918456     /usr/lib/libxcb.so.1.0.0
41763000-41764000 rw-p 00017000 08:05 918456     /usr/lib/libxcb.so.1.0.0
4184b000-41852000 r-xp 00000000 08:05 943091     /lib/tls/i686/cmov/librt-2.8.90.so
41852000-41853000 r--p 00007000 08:05 943091     /lib/tls/i686/cmov/librt-2.8.90.so
41853000-41854000 rw-p 00008000 08:05 943091     /lib/tls/i686/cmov/librt-2.8.90.so
41a88000-41a95000 r-xp 00000000 08:05 2367509    /lib/libgcc_s.so.1
41a95000-41a96000 r--p 0000c000 08:05 2367509    /lib/libgcc_s.so.1
41a96000-41a97000 rw-p 0000d000 08:05 2367509    /lib/libgcc_s.so.1
42129000-4213e000 r-xp 00000000 08:05 919803     /usr/lib/libICE.so.6.3.0
4213e000-4213f000 rw-p 00014000 08:05 919803     /usr/lib/libICE.so.6.3.0
4213f000-42141000 rw-p 4213f000 00:00 0 
42143000-4214a000 r-xp 00000000 08:05 919805     /usr/lib/libSM.so.6.0.0
4214a000-4214b000 r--p 00006000 08:05 919805     /usr/lib/libSM.so.6.0.0
4214b000-4214c000 rw-p 00007000 08:05 919805     /usr/lib/libSM.so.6.0.0
4f990000-4f9aa000 r-xp 00000000 08:05 2367501    /lib/ld-2.8.90.so
4f9ab000-4f9ac000 r--p 0001a000 08:05 2367501    /lib/ld-2.8.90.so
4f9ac000-4f9ad000 rw-p 0001b000 08:05 2367501    /lib/ld-2.8.90.so
4f9af000-4f9b2000 r-xp 00000000 08:05 920264     /usr/lib/libao.so.2.1.3
4f9b2000-4f9b4000 rw-p 00003000 08:05 920264     /usr/lib/libao.so.2.1.3
4f9e9000-4f9fe000 r-xp 00000000 08:05 943097     /lib/tls/i686/cmov/libnsl-2.8.90.so
4f9fe000-4f9ff000 r--p 00014000 08:05 943097     /lib/tls/i686/cmov/libnsl-2.8.90.so
4f9ff000-4fa00000 rw-p 00015000 08:05 943097     /lib/tls/i686/cmov/libnsl-2.8.90.so
4fa00000-4fa02000 rw-p 4fa00000 00:00 0 
4fa23000-4fa26000 r-xp 00000000 08:05 11698494   /lib/libcap.so.1.10
4fa26000-4fa27000 rw-p 00002000 08:05 11698494   /lib/libcap.so.1.10
4fa29000-4fa77000 r-xp 00000000 08:05 920617     /usr/lib/libpulse.so.0.4.1
4fa77000-4fa78000 r--p 0004d000 08:05 920617     /usr/lib/libpulse.so.0.4.1
4fa78000-4fa79000 rw-p 0004e000 08:05 920617     /usr/lib/libpulse.so.0.4.1
4fab8000-4fac6000 r-xp 00000000 08:05 917641     /usr/lib/libjack.so.0.0.28
4fac6000-4fac7000 r--p 0000e000 08:05 917641     /usr/lib/libjack.so.0.0.28
4fac7000-4fac9000 rw-p 0000f000 08:05 917641     /usr/lib/libjack.so.0.0.28
4fac9000-4fad1000 rw-p 4fac9000 00:00 0 
4fad7000-4fb9a000 r-xp 00000000 08:05 919588     /usr/lib/libasound.so.2.0.0
4fb9a000-4fb9c000 r--p 000c2000 08:05 919588     /usr/lib/libasound.so.2.0.0
4fb9c000-4fb9f000 rw-p 000c4000 08:05 919588     /usr/lib/libasound.so.2.0.0
4fba1000-4fbf2000 r-xp 00000000 08:05 920461     /usr/lib/libFLAC.so.8.2.0
4fbf2000-4fbf3000 r--p 00050000 08:05 920461     /usr/lib/libFLAC.so.8.2.0
4fbf3000-4fbf4000 rw-p 00051000 08:05 920461     /usr/lib/libFLAC.so.8.2.0
4fc12000-4fc28000 r-xp 00000000 08:05 920654     /usr/lib/libmad.so.0.2.1
4fc28000-4fc29000 r--p 00015000 08:05 920654     /usr/lib/libmad.so.0.2.1
4fc29000-4fc2a000 rw-p 00016000 08:05 920654     /usr/lib/libmad.so.0.2.1
4fc34000-4fc56000 r-xp 00000000 08:05 919794     /usr/lib/libaudiofile.so.0.0.2
4fc56000-4fc59000 rw-p 00021000 08:05 919794     /usr/lib/libaudiofile.so.0.0.2
4fefa000-4fefe000 r-xp 00000000 08:05 920460     /usr/lib/libogg.so.0.5.3
4fefe000-4feff000 r--p 00003000 08:05 920460     /usr/lib/libogg.so.0.5.3
4feff000-4ff00000 rw-p 00004000 08:05 920460     /usr/lib/libogg.so.0.5.3
4ff02000-5006a000 r-xp 00000000 08:05 920459     /usr/lib/libsamplerate.so.0.1.3
5006a000-5006b000 r--p 00167000 08:05 920459     /usr/lib/libsamplerate.so.0.1.3
5006b000-5006c000 rw-p 00168000 08:05 920459     /usr/lib/libsamplerate.so.0.1.3
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7c3d000-b7d3c000 rw-p b7c3d000 00:00 0 
b7d3c000-b7d46000 r-xp 00000000 08:05 11715750   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d46000-b7d47000 r--p 00009000 08:05 11715750   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d47000-b7d48000 rw-p 0000a000 08:05 11715750   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7d48000-b7d51000 r-xp 00000000 08:05 11715754   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7d51000-b7d52000 r--p 00008000 08:05 11715754   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7d52000-b7d53000 rw-p 00009000 08:05 11715754   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7d53000-b7d5a000 r-xp 00000000 08:05 11715746   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7d5a000-b7d5b000 r--p 00006000 08:05 11715746   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7d5b000-b7d5c000 rw-p 00007000 08:05 11715746   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7d5c000-b7d5f000 rw-p b7d5c000 00:00 0 
b7d5f000-b7d95000 r-xp 00000000 08:05 2367505    /lib/libdbus-1.so.3.4.0
b7d95000-b7d96000 r--p 00035000 08:05 2367505    /lib/libdbus-1.so.3.4.0
b7d96000-b7d97000 rw-p 00036000 08:05 2367505    /lib/libdbus-1.so.3.4.0
b7d97000-b7d98000 rw-p b7d97000 00:00 0 
b7d98000-b7db3000 r-xp 00000000 08:05 2252829    /usr/lib/sse2/libspeex.so.1.4.0
b7db3000-b7db4000 r--p 0001a000 08:05 2252829    /usr/lib/sse2/libspeex.so.1.4.0
b7db4000-b7db5000 rw-p 0001b000 08:05 2252829    /usr/lib/sse2/libspeex.so.1.4.0
b7db5000-b7dfe000 r-xp 00000000 08:05 919967     /usr/lib/libtheora.so.0.3.3
b7dfe000-b7e00000 rw-p 00049000 08:05 919967     /usr/lib/libtheora.so.0.3.3
b7e00000-b7e01000 rw-p b7e00000 00:00 0 
b7e01000-b7e10000 r-xp 00000000 08:05 919522     /usr/lib/libavahi-client.so.3.2.4
b7e10000-b7e11000 r--p 0000e000 08:05 919522     /usr/lib/libavahi-client.so.3.2.4
b7e11000-b7e12000 rw-p 0000f000 08:05 919522     /usr/liAborted
brunosso@brunosso-laptop:~$ 

```

and the library is not make!

Me too. Not sure what to do. Should I continue, or remove mpd? I installed it thinking a music server would be cool, but is now seems that there are conflicts and the package in the repos is old. It affects Sonata which is part of the sugar bundle, so dunno. Anyone solve this problem?

---

### Post by willthong on 2010-08-26
I followed all the steps and everything was fine and dandy.  Then I got here:

> Type this into the console:
 	Code:
 	sudo dpkg-reconfigure mpd 
This will bring up a console-interface to configure mpd.

I didn't get a console interface.  Instead the Terminal pushed out:
```

 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             listen: bind to 127.0.0.1:6600 failed: Address already in use (continuing anyway, because at least one address is bound)
                                                                         [ OK ]
```

HELP!

---

### Post by dunbrokin on 2011-07-30
I am having similar problems with MPD timing out....It was working perfectly until the latest 11.04 update...now it is broken and I cannot seem to get it to work.

music@MusicBox:~$ sudo dpkg-reconfigure mpd 
[sudo] password for music: 
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                      [ OK ] 
listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
music@MusicBox:~$ mpd
log: problem opening log file "/home/music/.mpd/mpd.log" (config line 37) for writing

My log file is not in that place....I am confused.

---

### Post by qball on 2011-07-31
> **dunbrokin said:**
> I am having similar problems with MPD timing out....It was working perfectly until the latest 11.04 update...now it is broken and I cannot seem to get it to work.

music@MusicBox:~$ sudo dpkg-reconfigure mpd 
[sudo] password for music: 
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                      [ OK ] 
listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)

Here you start MPD as a system service, and this succeeds. (it will use /etc/mpd.conf)

> 
music@MusicBox:~$ mpd
log: problem opening log file "/home/music/.mpd/mpd.log" (config line 37) for writing

My log file is not in that place....I am confused.

Here you start MPD as a user service, (using ~/.mpdconf if it exists) and obviously you misconfigured that one. 

Why do you want to run MPD twice? 
If you want help be clear what you are doing. You are complaining that it timesout (what times out, what is the error message etc), then post the output you get when starting mpd as a system service and the output you get when 2ndly trying to start it as (misconfigured) user-service.

---

### Post by afrodeity on 2011-07-31
Cant' reconfigure mpd. Seems to be a port problem

```


sudo dpkg-reconfigure mpd
 * Stopping Music Player Daemon mpd    [ OK ] 
 * Starting Music Player Daemon mpd    listen: bind to '[::1]:6666' failed: Cannot assign requested address (continuing anyway, because binding to '127.0.0.1:6666' succeeded)

```

UPDATE: Okay I got it working

```
This happens in startup sometimes when some distributions, not singling out any distributions, but some bind_to_address localhost by default. For troubleshooting's sake comment this out and restart MPD.
If this didn't happen in startup, and you cannot connect this could be a bug. Make sure your MPD_HOST and MPD_PORT are correct for your client and MPD is running on the box you think it is. Then file a bug report at MPD's bug tracker.

Or change localhost in your client to 127.0.0.1.

```

comment out bind_to_address localhost in /etc/mpd.conf

make sure localhost in client is 127.0.0.1

This is a good place to start [troubleshooting mpd ]("http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot")

To fix gmpc volume controls, add mixer_type "software" to /etc/mpd.conf
```

audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
	[COLOR="Red"]mixer_type 	"software"[/COLOR]
}

```

---

### Post by qball on 2011-07-31
> **afrodeity said:**
> Seems to be a port problem

```


sudo /etc/init.d/mpd restart
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             listen: bind to '[::1]:6666' failed: Cannot assign requested address (continuing anyway, because binding to '127.0.0.1:6666' succeeded)

```

If you try to _read_ you would see MPD started successful. This is no problem. (there is an explanation for the error but I am to tired to write a page)

---

### Post by dunbrokin on 2011-08-01
Thanks all, it seems to have righted itself without me doing anything....don't know why!

---

