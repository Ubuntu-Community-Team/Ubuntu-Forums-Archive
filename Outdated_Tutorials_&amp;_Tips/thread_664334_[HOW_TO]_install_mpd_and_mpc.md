---
title: "[HOW TO] install mpd and mpc"
date: 2008-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Nolander on 2008-01-11
**HOW TO: install MPD(Music Player Daemon) and MPC.**

About MPD(taken from [here]('http://musicpd.org/info.shtml')):
Music Player Daemon (MPD) allows remote access for playing music (MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files) and managing playlists. MPD is designed for integrating a computer into a stereo system that provides control for music playback over a local network. It also makes a great desktop music player, especially if you are a console junkie, like frontend options, or restart X often.

About MPC:
A command line tool to interface MPD.

Step 1: Installing MPD and MPC
Step 2: Setting up MPD and MPC
Step 3: MPD and Conky
Step 4: MPC Keyboard Shortcuts

**Step 1: Installing MPD and MPC**

GoTo: Accessories -> Terminal.
and type: ```
sudo apt-get install MPD MPC
sudo dpkg-reconfigure mpd

```

**Step 2: Setting up MPD and MPC**

You can ether A. create a .mpdconf in ur home directory(recommended) or u can B. edit the mpd.conf file in etc/. 

A.
Type in the terminal
```

gedit ~/.mpdconf

```
and copy the text below in to the file.
```

# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/your/music"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"
################################################################

######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "root"
#
# The address and port to listen on.
#
bind_to_address                 "127.0.0.1"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################

```

Edit '/your/music' to the location of your music directory and then save the file to '~/.mpdconf'.
Edit:```
user                            "root"
```
To:```
user                            ""
```

B. Not recommended

type in to the terminal:
```

mpd --create-db
mpc update
mpc add /path/to/your/music/
mpc play 
```

you **should** here music.
```
mpc help
```
To get a list of commands and there values type:

**Step 3: Conky and MPD**

To install and setup Conky Please see [this tutorial]('http://www.google.com.au/search?hl=en&safe=off&q=How+to+install+conky+site%3Aubuntuforums.org&btnG=Search&meta=').

Open terminal and type:
```
gedit ~/.conkyrc
```
then at the bottom add:
```
${if_running mpd}$hr
${voffset -3}$alignr MPD
${voffset -5}$mpd_vol% VOL${voffset -2}$hr
$alignc::: $mpd_status :::
$alignc$mpd_artist
$alignc$mpd_title
$alignc${mpd_bar 4, 135}
${voffset -12}$mpd_elapsed$alignr$mpd_length${endif}
```

and restart conky. now you can see what song is playing.

**Step 4: MPC Keyboard Shortcuts**

If you want you can setup keyboard shortcuts...

Open terminal and type:
```
gconf-editor
```
GoTo: Apps -> metacity -> keybinding_commands.
then add the commands in the value column eg.
'command_1 | mpc <command>'.

GoTo: Apps -> metacity -> global_keybindings.
Then add the key combinations in the correct row eg.
'run_command_1 | <Super><ALT>C'.

And u can listen to music the simple way.

Change Log:
15/1/08 - Fix user privileges problem. 

If theres any think wrong or some thing that can be done easer then post it here and ill add it.

-Nolander

---

### Post by chocolatetoothpaste on 2008-01-14
I'm turning into a command line junkie.  I run openbox only on my system.  I wanted to find a CL audio player, and, while this fits the bill, I can't hear anything.  I tested my system using vlc, and I can hear mp3's through it, but no such like with mpc.  Also, when I try to run mpd --create-db, it gives me an error about "root".  If I run sudo mpd --create-db it works fine.  Not sure if this was a typo in your how to, just thought I'd share.  Can anyone offer some things to try to get mpc to work?

---

### Post by urukrama on 2008-01-14
Thanks, Nolander. I've been using MPD+GMPC for a long time now. It is a great way to manage and play music.

For those who are looking for graphical clients for mpd, have a look at the following howtos:

     * [Howto: MPD and Clients]("http://ubuntuforums.org/showthread.php?t=320469")

     * [HOWTO: Install and Customize Music Player Daemon in Ubuntu (v2)]("http://ubuntuforums.org/showthread.php?t=31763") (a bit outdated)

---

### Post by Nolander on 2008-01-14
@chocolatetoothpaste: Sorry bout that, i missed a bit ill change the above.

-nolander

---

### Post by BeardlessForeigner on 2008-01-20
I get the same error, but instead I used the example here [http://mpd.wikia.com/wiki/Configuration](http://mpd.wikia.com/wiki/Configuration). The big difference is you make the other paths to "~/.mpd" so that you can avoid rights conflicts and don't put in that user line. But I also can't get anything to play. Once I update my database successfully the mpc add command doesn't seem to do anything, and mpc llistall shows nothing.

---

### Post by BeardlessForeigner on 2008-01-20
ok, this is the config that worked for me:

```

bind_to_address                 "127.0.0.1"
music_directory         "~/music"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpd.db"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"

user                    "michael"

```

I also had to do a sudo killall mpd, and then restart mpd once I had the user set to me. Then I was able to add my music.

---

### Post by OZZIES on 2008-01-31
hi all ia a newbie, i have completly failed to get mpd working,
this is on of the many errors

[B]sed: can't read /etc/mpd.conf: No such file or directory
invoke-rc.d: initscript mpd, action "restart" failed.
[/B]

---

### Post by OZZIES on 2008-01-31
bump
:(

---

### Post by BeardlessForeigner on 2008-02-01
I actually don't have mpd and client working correctly either. Or rather, it works if I restart mpd after I've logged in. But if you installed from the repos and followed the instructions mentioned you should at least not be getting that error. Can you look and see if the file /etc/mpd.conf is in fact not there? If not, maybe you should reinstall mpd and mpc. Either way, once you make an .mpdconf in your home folder it should be able to use that as a config file.

---

### Post by daanemanz on 2008-02-08
Yesterday I have tried to install MPD on my server. After a few problems I finally managed to connect to it and play some music. So far, no problems any more. But when I tried to play a specific album, it wasn't even on the list, although I'm pretty sure that the music I wanted to hear resides in the directory I specified in /etc/mpd.conf. Even after subsequent 'mpd --create-db' it still didn't appear... What's wrong here? Seems like 'mpd --create-db' doesn't catch all files?

---

### Post by daanemanz on 2008-02-11
Anyone? Please?:-|

---

### Post by daanemanz on 2008-02-15
Oh well, nevermind... accidentally deleted the files... no wonder they didn't appear! :-\"

---

### Post by flybiwire on 2008-03-08
Can anyone point a noob to a HOW-TO for getting the mpd to play *AAC* (.m4a) files?  Thanks a million!

---

### Post by El_Belgicano on 2008-03-09
you need to recompile it:
in a terminal:
1) dependencies:
```
sudo apt-get install libfaad2-dev libmp4v2-dev
```
2) download mpd (tar.gz source)
3) extract in your home directory
4) move to your inside the extracted folder
```
cd ~/nameoftheextractedfolder/
```
5) run:
```
./configure
```
6) make the package
```
make
```

normally you should be done, if not, you may have a look at the music PD website for other dependencies I didn't thought of...
just ask if you have trouble.

---

### Post by flybiwire on 2008-03-09
Thanks, I somewhat got it working -- I also responded to your thread about the same thing!  Did you get everything resolved with yours?

---

### Post by El_Belgicano on 2008-03-11
I just forgot about that other thread ...
Glad it worked, I still have one issue, this [post]("http://ubuntuforums.org/showthread.php?t=716905")

---

### Post by jcr1 on 2008-08-11
Hi. Thanks for this guide. Although I am still a little confused (read stupid).

I installed mpd on my server, where my music is located. What I would like to now achieve is to be able to play music located on the server by controlling it from my laptop.

So do I install the client (gmcp or whatever) on my laptop? If so, how do I then tell the client to look at the mpd installation? As before I installed mpd, I could just open a music player and browse (via samba share) to the same location on my server).

Also...what I am ideally going to end up with, is basically a remote control (on laptop) that plays music on the server so the music is actually coming out of the server... so if i plug the server into a speaker system it comes out of that. So the laptop is merely a remote control.

Hope someone can make this a little clearer for me.

Thanks.

---

### Post by jcr1 on 2008-08-12
OK well I seem to have inadvertently achieved what I wanted. MPD is installed on the server, opening gmpc on my laptop I can see my music and when I play, it comes out the server!

But...what if I wanted it to come out the laptop?

---

### Post by i.wanna.corndog on 2008-08-12
> **jcr1 said:**
> OK well I seem to have inadvertently achieved what I wanted. MPD is installed on the server, opening gmpc on my laptop I can see my music and when I play, it comes out the server!

But...what if I wanted it to come out the laptop?

Then you need a music server like Icecast or something like that.

Check this page (down at the bottom in next to the blue bullets):
[http://packages.ubuntu.com/hardy/mpd](http://packages.ubuntu.com/hardy/mpd)

---

### Post by jcr1 on 2008-08-20
I'M CONFUSED!!!!

OK so i installed mpd on my server.

then on my laptop installed mpc.

I have to run sudo mpd on server, then gmpc on laptop. this makes music come out the server controlled from laptop, which is just what i want.

But how do i update the collection? on the laptop I type mpc update and get:

```

 mpc update
MPD_HOST and/or MPD_PORT environment variables are not set
error: problems getting a response from "localhost" on port 6600 : Connection refused

```

so i know its looking on localhost, when it isn't on localhost, its on an ip address on my lan as the music is stored on the server,...

How do i sort this out...its confusing me!

---

### Post by Nepherte on 2008-08-20
You have to update the MPD_HOST variable to point to your server and not localhost. Localhost is in this case your laptop.

Add this to your ~.bashrc file:
```
export MPD_HOST=yourserversipaddress
```

There might be another possibility.Some players like ncmpc have a --host=HOSTNAME option. I'm not sure if gmpc has this. It's worth a look.

---

### Post by jcr1 on 2008-08-23
Ah right thank you! Did I miss this bit in the HOWTO or was the HOWTO not being used like I am using it.

Still getting a problem though. I added 'export MPD_HOST=192.168.0.4' and 'export MPD_PORT=6600' right at the end of my .bashrc and when running update I get:

```

jonr@jonr-laptop:~$ mpc update
MPD_HOST and/or MPD_PORT environment variables are not set
error: problems getting a response from "192.168.0.4" on port 6600 : Connection refused

```

---

### Post by brisbin33 on 2008-10-15
for what it's worth...

i kept getting the same error because /etc/mpd.conf wasn't set up properly.  starting mpd might not have started the deamon...

do a "ps -A | grep mpd" to check, if you get nothing, you're probably having the same problem i had.

check /etc/mpd.conf for the paths specified...

mine shows:
```
 music_directory       "/path/to/music"
 playlist_directory    "~/.mpd/playlists"
 db_file               "~/.mpd/mpd.db"
 log_file              "~/.mpd/mpd.log"
 error_file            "~/.mpd/mpd.error"
 pid_file              "~/.mpd/mpd.pid"
 state_file            "~/.mpd/mpdstate"
```

therefore, i had to:
```
 mkdir .mpd
 cd .mpd
 mkdir playlists
 touch mpd.log
 touch mpd.error
 touch mpd.pid
 touch mpdstate
 mpd --create-db [**from within .mpd**]
```

if one or more of the above files doesn't exist mpd won't start and you get your error regardless of host/port set up.

hope it helps!

---

### Post by super.rad on 2008-10-15
I have MPD & Sonata setup and working fine, problem is with conky. Whenever i try to start conky i get the following over and over until i kill conky:
```
Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused
```
My .conkyrc has the following to do with MPD:
```
{mpd_smart}${color} ${mpd_bar 5,100} ${mpd_elapsed}/${mpd_length}
```
and /etc/mpd.conf:
```
music_directory        "/media/Media/benji/Music"
playlist_directory    "/home/benji/.mpd/playlists"
db_file            "/home/benji/.mpd/tag_cache"
log_file        "/home/benji/.mpd/mpd.log"
error_file        "/home/benji/.mpd/errors.log"
pid_file        "/home/benji/.mpd/pid"
bind_to_address                 "localhost"
port                            "6600"
```
anyone know how I can fix this?

---

### Post by rocknrolf77 on 2008-10-26
I'm just getting segmentation fault when trying to start mpd in 8.10. Never seen so many bugs in any of the other ubuntu releases. 

```
Segmentation fault
                                                                                           [fail]
invoke-rc.d: initscript mpd, action "start" failed.

```

---

### Post by rlorentz on 2009-07-14
I did a clean install of ubuntu on an old dell laptop that I had no better use for, installed mpd on it, and put it in a cabinet in our kitchen above the microwave (power outlet!).  It's got fairly loud speakers on it and makes an awesome stereo for kitchen/living room, dinner party, etc. I'm controlling it from MPoD on my iPhone, it's a real slick setup and was worth doing.  

HOWEVER, as I drop albums on this clean server (not nfs mounting mp3's from somewhere else..), I noticed that either A) I have mpd misconfigured (unlikely, I've read a lot of docs), or B) it is just a total pain to add new music, it won't add it to the DB automatically!!

This problem exists for all users as far as I know, I worked around it with a crontab/script and felt it worthwhile to pass it along in hopes it helps someone else (or saves frustration)

```

#!/bin/bash

if [ "`du  /var/lib/mpd/music/ | md5sum`" != "`cat /tmp/mpdlibrary.md5`" ]
then
    mpd --create-db
    /etc/init.d/mpd restart
    echo "New files added to mpd library, restarting daemon"
fi

echo "`du /var/lib/mpd/music/ | md5sum`" > /tmp/mpdlibrary.md5

```

Create something like /root/mpd_update.sh with contents above, and in root's crontab add

```

* * * * * `/root/mpd_update.sh`

```


Every minute, if your music repository has changed, update MPD's DB and restart the daemon.  Tweak as necessary for what suits you

---

### Post by xqyz on 2009-07-14
I LOVE mpd. I don't like gmpc though, so I've got my own setup: panel starters for all important functions and a custom song notify:

[IMG]http://img240.imageshack.us/img240/5948/mpc.png[/IMG]

[B].bin/notify.py
[/B]```
#!/usr/bin/python
import sys
import pynotify

if not pynotify.init("Patrick's Notify"):
    sys.exit(-1)

title = "Title"
message = "Message"
try:
   title = sys.argv[1]
   message = sys.argv[2]
except IndexError:
   pass
n = pynotify.Notification(title, message, "")
n.show()
```[B].bin/updatestatus
[/B]```
#!/bin/bash
for (( ; ; ))
do
    old="`mpc | head -n 1`"
    sleep 5
    new="`mpc | head -n 1`"
    if [ "`echo ${new} | grep volume | grep repeat | grep random`" != "" ] ; then
        if [ "$old" != "$new" ] ; then
            ~/.bin/notify.py "MPD Playback stopped" "`date +'%I:%M %p'`"
        fi
        old="$new"
    fi
    if [ "$old" != "$new" ] ; then
        /home/patrick/.bin/name_song
    fi
done
```[B].bin/name_song
[/B]```
#!/bin/bash
#gdialog --msgbox "`mpc | head -n 1`"
~/.bin/notify.py "`mpc --format '%title%' | head -n 1`" "`mpc --format '%artist%' | head -n 1`"
```

---

### Post by dannymichel on 2009-07-20
im getting
danny@danny-desktop:~$ mpd --create-db

** ERROR **: problems opening file /etc/mpd.conf for reading: Permission denied

aborting...
Aborted

ive been googling all day

---

### Post by rdrake on 2009-07-20
> **dannymichel said:**
> im getting
danny@danny-desktop:~$ mpd --create-db

** ERROR **: problems opening file /etc/mpd.conf for reading: Permission denied

aborting...
Aborted

ive been googling all day

I'm going to take a guess here and say you don't have a user-specific mpd.conf file anywhere.  If not, mpd will look at /etc/mpd.conf which you do not have access to.

Run the command as root like so:
```
sudo mpd --create-db
```

Or create a ~/.mpdconf file.

---

