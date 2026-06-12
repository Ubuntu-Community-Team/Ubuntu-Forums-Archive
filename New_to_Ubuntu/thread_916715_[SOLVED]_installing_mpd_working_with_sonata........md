---
title: "[SOLVED] installing mpd working with sonata......."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-11
Hi everybody, well, I thought I would carry on using this thread as it was mentioned on here. 

I tried to install mpd working with sonata, by going to :-

> [http://czarism.com/sonata-mpd-perfect-ubuntu-linux-music-client](http://czarism.com/sonata-mpd-perfect-ubuntu-linux-music-client)

I followed the instructions usng a terminal

> INSTALL

sudo aptitude install mpd python-soappy libtag1-dev

The process finished, but the webiste doesnt tell you what to do next. I cant find theinstallation. 

Can somebody help please?

Thankyou for your help.

John.

---

### Post by Nepherte on 2008-09-11
You will have to edit /etc/mpd.conf to make mpd work like it should. This article pretty much covers it all: [http://linuxowns.wordpress.com/2008/07/27/setting-up-mpd-locally/](http://linuxowns.wordpress.com/2008/07/27/setting-up-mpd-locally/)

In addition to the article you could comment out an output and a mixer in /etc/mpd.conf. If you have any other questions, feel free to post them.

---

### Post by jakewc2 on 2008-09-11
Hi, thank you so much for your quick reply. 

I only installed Ubuntu the day before yesterday, and I am not up with the language. So what you just posted didnt make an awful lot of sense, I understood the first bit though.

So what I did, was the wrong way round, yes?

I will have a go at what you suggested to get mpd working then I'll come back with my results.

Thanks again.

John.

---

### Post by jakewc2 on 2008-09-11
Hi, I have manaed to get down to 

Change mpd with your username, did that, then the next command I havent managed to understand, I entered into a new terminal, and got this error, so not sure I understood that properly..

> jakewc2@jakewc2-desktop:~$ mpd –create-db
problems opening file –create-db for reading: No such file or directory
jakewc2@jakewc2-desktop:~$ mpc update
volume:  0%   repeat: off   random: off
jakewc2@jakewc2-desktop:~$ mpc add /
jakewc2@jakewc2-desktop:~$ mpc play



Where did I go wrong?

Thank you.

John

---

### Post by Nepherte on 2008-09-11
Can you post your /etc/mpd.conf file please?
```
cat /etc/mpd.conf
```

As far as I can see, you probably have set your mpd.conf file correct, but you forgot to create the necessary files. If you sticked to the configuration file changes of the guide, you'll have to do this (but I suggest you wait a little bit untill I've seen your /etc/mpd.conf):
```
mkdir ~/.mpd
mkdir ~/.mpd/playlists
touch ~/.mpd/mpd.db
touch ~/.mpd/mpd.error
touch ~/.mpd/mpd.log

```

Note that you will also have to set the directory where your music resides. In the article they use music_directory ~/Music but you can change ~/Music to the directory where your music is located.

You probably don't want to use mpc either, which is a console player front end for mpd. Sonata is a good choice for a graphical front end.

---

### Post by jakewc2 on 2008-09-11
Hi, thanks for your message, I just went through the process again to be sure, I did everything as it suggested but still get that error.

I have taken a copy of /etc/mpd.con

> # An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
port “6600&#8243;
music_directory ~/Music
playlist_directory ~/.mpd/playlists
db_file ~/.mpd/mpd.db
log_file ~/.mpd/mpd.log
error_file ~/.mpd/mpd.error
pid_file /var/run/mpd/pid
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "jakewc2"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
# An example of an ALSA output:
#
#audio_output {
#        type                    "alsa"
#        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################

I am wondering if I am understanding what Linux means as the Home Directory. Maybe that is what I'm doing wrong.

John

---

### Post by billgoldberg on 2008-09-11
> **jakewc2 said:**
> Hi, I have manaed to get down to 

Change mpd with your username, did that, then the next command I havent managed to understand, I entered into a new terminal, and got this error, so not sure I understood that properly..



Where did I go wrong?

Thank you.

John

It's "mpd --create-db"

I thought I mentioned that in my guide.

Wordpress insists on changing -- to -

---

### Post by jakewc2 on 2008-09-11
Hi, I am so sorry, I just didnt see that, my real bad. I will go back and try again. 

Thank you for your patience.

---

### Post by jakewc2 on 2008-09-11
Hiya, went back, and changed that, and now got this error

> jakewc2@jakewc2-desktop:~$ mpd--create-db
bash: mpd--create-db: command not found
jakewc2@jakewc2-desktop:~$ 


Then I did with my username instead of mpd,just in case, and still got an error
> 
jakewc2@jakewc2-desktop:~$ jakewc2--create-db
bash: jakewc2--create-db: command not found


Do you know why that should be?

Sorry about this.:(

---

### Post by Nepherte on 2008-09-11
It's again the wrong command ;) Just copy/paste the following:
```
mpd --create-db
```

The configuration file is ok.

---

### Post by jakewc2 on 2008-09-11
Oh dear, I am so sorry, I will get this right one day. :oops:

I didnt do it that way because of this line, but it looks like i misunderstood again.

> 
Note: it&#8217;s mpd - -create-db without the space between the two -.

I just copied and pasted it and got this error now.

> jakewc2@jakewc2-desktop:~$ mpd --create-db
cannot init supplementary groups of user "jakewc2" at line 36: Operation not permitted
db file "/home/jakewc2/.mpd/mpd.db" is not a regular file
jakewc2@jakewc2-desktop:~$ 

John :(

---

### Post by Nepherte on 2008-09-11
Have you done these commands?
```
mkdir ~/.mpd
mkdir ~/.mpd/playlists
touch ~/.mpd/mpd.db
touch ~/.mpd/mpd.error
touch ~/.mpd/mpd.log
```

---

### Post by jakewc2 on 2008-09-11
Hi, I just went through all those commands and this was the result.

> jakewc2@jakewc2-desktop:~$ mpd --create-db
cannot init supplementary groups of user "jakewc2" at line 36: Operation not permitted
db file "/home/jakewc2/.mpd/mpd.db" is not a regular file
jakewc2@jakewc2-desktop:~$ mkdir ~/.mpd
mkdir: cannot create directory `/home/jakewc2/.mpd': File exists
jakewc2@jakewc2-desktop:~$ mkdir ~/.mpd/playlists
mkdir: cannot create directory `/home/jakewc2/.mpd/playlists': File exists
jakewc2@jakewc2-desktop:~$ touch ~/.mpd/mpd.db
jakewc2@jakewc2-desktop:~$ touch ~/.mpd/mpd.errortouch ~/.mpd/mpd.log


So why am I getting that error with the mpd.db file, I just dont understand it.

John

---

### Post by jakewc2 on 2008-09-11
Oh well, looks like for now I'll just have to leave it until I'm more up to date with Ubuntu, to be able to work out why this is happeneing. :(

I really appreciate you guys help you have been really patient, thank you. :)

---

### Post by vanadium on 2008-09-11
I see issues with this thread: recommendations for a system-wide install (edit /etc/mpd.conf) are mixed with actions for per user install. Here follows the most simple procedure you can have to get mpd/sonata running on Ubuntu. It will be a system-wide install: i.e. all users will see the same music, playlists etc. I actually did this on the fly on my old desktop while writing these steps, so it should work.

1) Install mpd and sonata
```
sudo apt-get update ; sudo apt-get install mpd sonata
```
2) Point mpd to your music directory. We do this by replacing the default mpd music directory by a symbolic link to your actual collection.
My collection resides under the Music directory in my home, i.e. /home/vanadium/music (or ~/Music when I am logged in). Substitute your correct path instead of ~/Music in the second command:
```
sudo rmdir /var/lib/mpd/music
sudo ln -s ~/Music /var/lib/mpd/music

```
3) Create the music database
```
sudo mpd --create-db
```
4) Reboot the computer (safest but not fastest approach for it to work!)
5) Start Sonata (Applications - Sound & Video - Sonata). On the Library tab, you should see your collection. Right-click and Add adds an item (or a whole directory tree) to the playlist. With items in the playlist, pressing the Play button should ... (hold your breath)

---

### Post by jakewc2 on 2008-09-11
Hi vanadium, thank you for your message. I followed you instructions, installed it the way you suggested, and I still got an error with 

> jakewc2@jakewc2-desktop:~$ mpd --create-db
cannot init supplementary groups of user "jakewc2" at line 36: Operation not permitted
db file "/home/jakewc2/.mpd/mpd.db" is not a regular file

One thing that has appeared is Sonata in Applications>Sound and Videa, plis the Icon,that looks like a music note. I can open it up, but is says its not connected, and I cant connect it either. It looks nothing like what is on the website.

I just dont know what to do now. :(

Thank you again, for all your help.

John.

---

### Post by jakewc2 on 2008-09-12
Well, I have tried everything to get this to work, and it gets to the creating music database, and I insert the code 
> 
sudo mpd --create-db

and this is all that is causing the problem now I think, but I still get the error message

> jakewc2@jakewc2-desktop:~$ sudo mpd --create-db
db file "/home/jakewc2/.mpd/mpd.db" is not a regular file
jakewc2@jakewc2-desktop:~$ 

How can I get this sorted. I cant get the program to work at all, :(

Thankyou.

John.

---

### Post by jakewc2 on 2008-09-12
Well, now all I get when I click on Sonata, it says its starting, but nothing happens. Is there anybody around that can help, and maybe even help remotley. I would much appreciate it. 

Thankyou

John.

---

### Post by Nepherte on 2008-09-12
I think mpd and sonata are all a bit messed up on your computer right now. Sonata requires mpd to work correctly so if mpd isn't working, Sonata won't either (although it should start and show you a gui). Maybe you could start all over and redo the installation.

[LIST=1]
[*]Remove the current installation and remove the configuration files:
```
sudo apt-get purge mpd sonata
```
[*]Install the music player daemon:
```
sudo apt-get install mpd
```
[*]Edit the configuration file. We will be setting mpd up for each user, not system-wide. That way you can have different music and settings for each user. Let's open up ~/.mpd:
```
gedit ~/.mpd
```
Edit the file so these changes are made:
```
port			"6600"
music_directory         "~/music"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpd.db"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"
```
You can change the music_directory. Point it to your music collection. Otherwise mpd will not find any music.
[*]Create the necessary files:
```
mkdir -p ~/.mpd/playlists
touch ~/.mpd/mpd.db
touch ~/.mpd/mpd.log
touch ~/.mpd/mpd.error
```
It will probably say the directory already exists since you already made it in a previous post, but that's nothing to worry about.

[*]Create the database file:
```
mpd --create-db
```
[*]Let's restart the mpd service, just in case ...
```
sudo /etc/init.d/mpd restart
```
[*]Install Sonata:
```
sudo apt-get install sonata
```
Run sonata and fill in your mpd port (6600) and host (localhost) and fill in the full path to your music directory.
[/LIST]
That is it in a nutshell. There's no point in continueing to the next step if the previous one gave errors (except the one with the directory that already exists). As soon as you get one, stop the instructions and post them here. Let's hope it works this time.

---

### Post by jakewc2 on 2008-09-12
Hi, thank you for you message, unfortuntely, it didnt work, I came upon an error messagem here's a copy from the Terminal:-

> jakewc2@jakewc2-desktop:~$ sudo apt-get purge mpd sonata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sonata is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libmikmod2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  mpd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 479kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 107117 files and directories currently installed.)
Removing mpd ...
 * Stopping Music Player Daemon mpd                                      [fail] 
invoke-rc.d: initscript mpd, action "stop" failed.
dpkg: error processing mpd (--purge):
 subprocess pre-removal script returned error exit status 1
action: abort-remove not supported
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
jakewc2@jakewc2-desktop:~$ 


Tried the next command, and when you open MPD, theres a huge red circle with a white line though it when it opens. 

John

---

### Post by Nepherte on 2008-09-12
Try this before removing mpd:
```
sudo /etc/init.d/mpd stop
```

Or kill the processes:
```
ps -A | grep mpd
```
That will show you a list with numbers if mpd is still running.
```
kill number1 number2 anyothernumber
```

Then try removing mpd:
```
sudo aptitude purge mpd
```

---

### Post by jakewc2 on 2008-09-12
Hi, I have started to reinstall. As I have only been using Ubuntu for about 3 days, I am a little bit lost when it comes to some things. 

I got to the part where it says 


Code:

gedit ~/.mpd


I entered it into the Terminal, and the gedit window opened, with a warning inside saying:-

/home/jakewc2/.mpd is a directory.
Please check that you typed the location correctly and try again

Now comes the next bit, the instructions are:-


Edit the file so these changes are made:
Code:

port			"6600"
music_directory         "~/music"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpd.db"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"

Do I enter those commands into the Terminal, or where? I'm stuck on this part, :(

Thankyou for you help.

John.

---

### Post by jakewc2 on 2008-09-12
I dont know, I think at this time, this might just be a little bit over my head, I just cant get my head round it at all, and its frustrating me becauase I dont know what I'm doing. 

I am so greatfull for the help, but if this doesnt work, I think I am going to give in for the moment.

John.

---

### Post by Nepherte on 2008-09-12
Great, so you were able to remove it first? I'm sorry, it wasn't ~/.mpd but ~/.mpdconf. So that means step 3 becomes:
[LIST]
[*]Open up ~/.mpdconf:
```
gedit ~/.mpdconf
```
If the file is empty, close the file and copy the system-wide configuration file to ~/.mpdconf:
```
cp /etc/mpd.conf ~/.mpdconf
```
Then edit the file .mpdconf:
```
gedit ~/.mpdconf
```
so these changes are made:
```
port "6600"
music_directory "~/music"
playlist_directory "~/.mpd/playlists"
db_file "~/.mpd/mpd.db"
log_file "~/.mpd/mpd.log"
error_file "~/.mpd/mpd.error"
```
They are not commands that have to be executed in the terminal, but you have to edit ./mpdconf with your editor so it reflects the above.
[/LIST]
Then continue with step 4.

P.S There are a lot of other music players in linux. You just managed to pick out the one console music player, which happens to be very good though. So "the juice is wort the squeeze", but if not you can also use easier programs like exaile, banshee, amarok, ...

---

### Post by jakewc2 on 2008-09-12
Hi, have tried that, and it doesnt work, the link for Sonata is in Sounds and video, but when you click on it, it doesnt open, the cirlce goes round for a short time, then dissappears. :(


Its made me really frustrated. grrr.

Thank you for your help though, I really appreciate it. :)

---

### Post by whitethorn on 2008-09-12
MPD is a music daemon.  So pretty much it gets started with your computer and runs in the background.  You then need some sort of client software (sonata) to connect to the server (mpd) and tell it what to do.  Once you get it up and running then it's pretty cool.  I had a hard time installing it, it was my first .conf file in linux.  I think I also started a thread about it, and spent some time on the their #irc b4 I got it to run properly.  So no worries.

---

### Post by jakewc2 on 2008-09-12
Well,I have tried everything, even opened

gedit ~/.mpdconf

and changed that, but for some reason, Sonata still wont open, it tried to, but it just closes. Would anybody have an idea why it wont open?

---

### Post by jakewc2 on 2008-09-12
Um, I wonder, how do I find out in Launcher Properties what the command is for Sonata. I opened up Sonata Launch Properties and fiddled with the command and pressed on the Browse button which changed the command line, so can somebody tell me what the command is?

Thank you

John

---

### Post by Nepherte on 2008-09-13
So to make it clear: everything but sonata works? You were able to create mpd --create-db? You were able to restart the mpd service?

Assuming that this is the case, you might be able to discover the problem with sonata by launching it from the console:
```
sonata
```

There are also a lot of other front-ends for mpd if you like to try them out. These are the most popular ones:
[LIST]
[*]Graphical: gmpc
[*]Console: ncmpc, mpc
[/LIST]
All of them are in the repositories.

---

### Post by jakewc2 on 2008-09-13
Hi Nepherte, as much as I feel like I want to throw my pc out the window right, being so frustrated with getting this to work, I have spent so much time on it,that I need to give it one lst try, to see if  can get it to work.

This is what I got when I tried to open Sonata in a Terminal.

> jakewc2@jakewc2-desktop:~$ sonata
Taglib and/or tagpy not found, tag editing support disabled.
ZSI not found, fetching lyrics support disabled.
Taglib and/or tagpy not found, tag editing support disabled.
ZSI not found, fetching lyrics support disabled.
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 590, in __init__
    self.connect(blocking=True)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1623, in connect
    self.connect2(blocking, force_connection)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1635, in connect2
    self.conn = Connection(self)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 146, in __init__
    if not host: host = Base.host[Base.profile_num]
IndexError: list index out of range
jakewc2@jakewc2-desktop:~$ 

Hope that helps working out what the problem is. 

I am pretty certain the database is there.

John.

---

### Post by Nepherte on 2008-09-13
I guess sonata has been messed up. The first 4 lines of the output are no errors, the errors start from traceback. There's no sonata bug I'm aware of so the only thing I can advise you is to reinstall sonata...again.
```
sudo aptitude purge sonata && sudo aptitude install sonata
```
If that doesn't work, I'm out of possible solutions.

---

### Post by jakewc2 on 2008-09-13
I did that, but I did used a root terminal, this is what happened

> root@jakewc2-desktop:/home/jakewc2# sudo aptitude purge sonata && sudo aptitude install sonata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libboost-python1.34.1 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 
  libgdl-1-common libgdl-gnome-1-0 python-gnome2-extras python-mmkeys 
  python-tagpy python-xml python-zsi 
The following packages will be REMOVED:
  sonata{p} 
0 packages upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 18.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 108027 files and directories currently installed.)
Removing python-tagpy ...
Removing libboost-python1.34.1 ...
Removing libgda3-bin ...
Removing python-gnome2-extras ...
Removing libgda3-3 ...
Removing libgda3-common ...
Removing libgdl-gnome-1-0 ...
Removing libgdl-1-0 ...
Removing libgdl-1-common ...
Removing python-mmkeys ...
Removing python-zsi ...
Removing python-xml ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 107510 files and directories currently installed.)
Removing sonata ...
Purging configuration files for sonata ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libboost-python1.34.1 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 
  libgdl-1-common libgdl-gnome-1-0 python-gnome2-extras python-mmkeys 
  python-tagpy python-xml python-zsi 
The following NEW packages will be installed:
  libboost-python1.34.1 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 
  libgdl-1-common libgdl-gnome-1-0 python-gnome2-extras python-mmkeys 
  python-tagpy python-xml python-zsi sonata 
0 packages upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3431kB of archives. After unpacking 18.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package libboost-python1.34.1.
(Reading database ... 107466 files and directories currently installed.)
Unpacking libboost-python1.34.1 (from .../libboost-python1.34.1_1.34.1-4ubuntu3_amd64.deb) ...
Selecting previously deselected package libgda3-common.
Unpacking libgda3-common (from .../libgda3-common_3.0.2-2ubuntu1_all.deb) ...
Selecting previously deselected package libgda3-3.
Unpacking libgda3-3 (from .../libgda3-3_3.0.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libgda3-bin.
Unpacking libgda3-bin (from .../libgda3-bin_3.0.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libgdl-1-common.
Unpacking libgdl-1-common (from .../libgdl-1-common_0.7.11-1_all.deb) ...
Selecting previously deselected package libgdl-1-0.
Unpacking libgdl-1-0 (from .../libgdl-1-0_0.7.11-1_amd64.deb) ...
Selecting previously deselected package libgdl-gnome-1-0.
Unpacking libgdl-gnome-1-0 (from .../libgdl-gnome-1-0_0.7.11-1_amd64.deb) ...
Selecting previously deselected package python-gnome2-extras.
Unpacking python-gnome2-extras (from .../python-gnome2-extras_2.19.1-0ubuntu7_amd64.deb) ...
Selecting previously deselected package python-mmkeys.
Unpacking python-mmkeys (from .../python-mmkeys_1.4.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package python-xml.
Unpacking python-xml (from .../python-xml_0.8.4-10ubuntu2_amd64.deb) ...
Selecting previously deselected package python-zsi.
Unpacking python-zsi (from .../python-zsi_2.0-2ubuntu4_all.deb) ...
Selecting previously deselected package sonata.
Unpacking sonata (from .../sonata_1.4.2-1ubuntu1_all.deb) ...
Selecting previously deselected package python-tagpy.
Unpacking python-tagpy (from .../python-tagpy_0.93-1_amd64.deb) ...
Setting up libboost-python1.34.1 (1.34.1-4ubuntu3) ...

Setting up libgda3-common (3.0.2-2ubuntu1) ...
Setting up libgda3-3 (3.0.2-2ubuntu1) ...

Setting up libgda3-bin (3.0.2-2ubuntu1) ...
Setting up libgdl-1-common (0.7.11-1) ...
Setting up libgdl-1-0 (0.7.11-1) ...

Setting up libgdl-gnome-1-0 (0.7.11-1) ...

Setting up python-gnome2-extras (2.19.1-0ubuntu7) ...

Setting up python-mmkeys (1.4.2-1ubuntu1) ...
Setting up python-xml (0.8.4-10ubuntu2) ...

Setting up python-zsi (2.0-2ubuntu4) ...

Setting up sonata (1.4.2-1ubuntu1) ...

Setting up python-tagpy (0.93-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
root@jakewc2-desktop:/home/jakewc2# 

then I tried opening it, and same thing, it showed in the tray as trying to open, and nothing, so I tried to open it in a root terminal and this showed

jakewc2@jakewc2-desktop:~$ Sonata
bash: Sonata: command not found
jakewc2@jakewc2-desktop:~$ sonata
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 590, in __init__
    self.connect(blocking=True)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1623, in connect
    self.connect2(blocking, force_connection)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1635, in connect2
    self.conn = Connection(self)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 146, in __init__
    if not host: host = Base.host[Base.profile_num]
IndexError: list index out of range
jakewc2@jakewc2-desktop:~$ 


I just dont know.

JOhn.

---

### Post by whitethorn on 2008-09-13
I can't really make much out of the failure you're getting. You could try using another mpd client to see if it's sonata or mpd.

In a terminal

```
sudo apt-get install gmpc
```

then
```
gmpc
```

We're only going to try this to see if mpd is working properly.  If it works see if you can get some music to play.

---

### Post by jakewc2 on 2008-09-13
Sorry, that was wrong terminal, this is what I got when I tried the root terminal

Sonata opened, but I got this error message about mdp

root@jakewc2-desktop:/home/jakewc2# sonata
Cannot connect to MPD: (111, 'Connection refused')


goes on forever

I updated the database as well, which seemed to work, but it still wont connect. :(

---

### Post by jakewc2 on 2008-09-13
Hi, I just installed that, it opened, but wouldnt connect, I tried connecting, and this error appeared

an error occured: error code 15: problems getting a response from local host on port 6600. connection refused.

Now I have seen that, I think when I changed the port, that was when Sonata stopped working.

John

---

### Post by whitethorn on 2008-09-13
That sounds like it's almost there. Do you remember what number you changed the port to?  If not just have a look at your mpdconf

```
cd ~
```
```
cat .mpdconf
```

I think that's how it's called.  Then look for the port number.  Then open sonata and get into the preferences menu, and change the Port to the number you have in your mpdconf.  That should do it.  If it still doesn't work, then you might have to start mpd.

```
mpd
```
then start sonata again.

---

### Post by jakewc2 on 2008-09-13
That is what is in cat .mpdconf, but I cant remember what the origional port/settings was before it was changed. I should have made a copy. :(

I am on a router, netgear, is there a command I can use to open the port? Would that make a difference?

John

---

### Post by jakewc2 on 2008-09-13
This is what appeared in a termina

> jakewc2@jakewc2-desktop:~$ sonata
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 590, in __init__
    self.connect(blocking=True)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1623, in connect
    self.connect2(blocking, force_connection)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1635, in connect2
    self.conn = Connection(self)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 146, in __init__
    if not host: host = Base.host[Base.profile_num]
IndexError: list index out of range
jakewc2@jakewc2-desktop:~$ cat .mpdconf
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
port “6600&#8243;
music_directory ~/Music
playlist_directory ~/.mpd/playlists
db_file ~/.mpd/mpd.db
log_file ~/.mpd/mpd.log
error_file ~/.mpd/mpd.error
pid_file /var/run/mpd/pid
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "jakewc2"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
# An example of an ALSA output:
#
#audio_output {
#        type                    "alsa"
#        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################
jakewc2@jakewc2-desktop:~$ 



there still seems to be some problems with connections.

John

---

### Post by whitethorn on 2008-09-13
Well if mpd and sonata are on the same computer you don't need to do anything on the router.  Well the normal settings are 6600 (at least that's what I have in my .conf)  Try running this command

```
sudo /etc/init.d/mpd stop
```
if you get something like
>  * Stopping Music Player Daemon mpd

then 
```
mpd
```

Then start sonata again and see if it can connect. So far your mpdconf looks pretty good.  You might not be able to play any music yet since you haven't specified if it should use alsa or pulse.  See if it works without though

---

### Post by jakewc2 on 2008-09-13
well, I am getting this error

> jakewc2@jakewc2-desktop:~$ sudo /etc/init.d/mpd stop
[sudo] password for jakewc2: 
 * Stopping Music Player Daemon mpd                                      [fail] 
jakewc2@jakewc2-desktop:~$ 


then when I enter mpd

this appears

jakewc2@jakewc2-desktop:~$ mpd
port "“6600&#8243;" specified at line 8 is not a positive integerjakewc2@jakewc2-desktop:~$

---

### Post by vanadium on 2008-09-13
Correct the quotes in your .mpdconf. Currently, you did not enter normal quotes ("6600") but curly quotes (&#8220;6600&#8243;). 6600 is the default port, so you did not change that.

To play it safe, reboot your system before attempting to start sonata. It can obviously work by killing the mpd process (sometimes processes), but as a beginner facing many troubles, take the safe way.

b.t.w., you should not be using a root terminal in Ubuntu. Use the sudo command to issue commands with root privileges.

---

### Post by whitethorn on 2008-09-13
Ok let's try something else. I rewrote my mpdconf.  So it should work on your pc.

> # An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/home/jakewc2/Music/"
playlist_directory	"/home/jakewc2/.mpd/playlists"
db_file			"/home/jakewc2/.mpd/tag_cache"
log_file		"/home/jakewc2/.mpd/mpd.log"
error_file		"/home/jakewc2/.mpd/errors.log"
pid_file		"/home/jakewc2/.mpd/pid"
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/home/jakewc2/.mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "jakewc2"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
#audio_output {
#        type    "pulse"
#        name    "My MPD PulseAudio Output"
#        server  "localhost"   # optional
#        sink    "alsa_output" # optional
#}

# An example of an ALSA output:
#
audio_output {
        type                    "alsa"
        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
        format                  "44100:16:2" # optional
}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################


Now you have to replace this with what you have in your /etc/mpd.conf

```
gksudo gedit /etc/mpd.conf
```

then we're going to rename the one in your homefolder 

```
mv ~/.mpdconf ~/.mpdconf_bak
```

now we restart mpd

```
sudo /etc/init.d/mpd restart
```

and then start sonata

```
sonata
```

---

### Post by jakewc2 on 2008-09-13
Sorry, I didnt realise that about the root terminal, I wont do that again, thanks for letting me know.

I have done everything that you said to do, and tried starting Sonata via Applications, nothing happened, then tried starting it in a terminal, and got this message.

> jakewc2@jakewc2-desktop:~$ sonata
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 590, in __init__
    self.connect(blocking=True)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1623, in connect
    self.connect2(blocking, force_connection)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1635, in connect2
    self.conn = Connection(self)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 146, in __init__
    if not host: host = Base.host[Base.profile_num]
IndexError: list index out of range
jakewc2@jakewc2-desktop:~$ 

I think I must be doing something wrong here, because nothing is working.

Plus the other music player, gmpc, I tried opening that and get the same error mesage, wont connect.

---

### Post by whitethorn on 2008-09-13
have you installed gmpc?

```
sudo apt-get install gmpc
```

then to start it just type

```
gmpc
```

I don't really know what's happening with sonata.  Does mpd work now?

what do you get when you run.
```
sudo /etc/init.d/mpd restart
```
if that works then run
```
sudo /etc/init.d/mpd start-create-db
```

that might not work (didn't for me)
```
sudo mpd --create-db
```
You should see it adding songs and stuff

You might have reboot too.

---

### Post by jakewc2 on 2008-09-13
Hi, I just took a screenshot of what I get when opening gmpc, that shows the error I get.

This is what I get when I run

> sudo /etc/init.d/mpd restart



> jakewc2@jakewc2-desktop:~$ sudo /etc/init.d/mpd restart
[sudo] password for jakewc2: 
 * Stopping Music Player Daemon mpd                                      [fail] 
 * Starting Music Player Daemon mpd                                             problem opening log file "/home/jakewc2/.mpd/mpd.log" (config line 11) for writing
                                                                         [fail]
jakewc2@jakewc2-desktop:~$ 


When I run this command now
> 
sudo /etc/init.d/mpd start-create-db

this is what I get

> jakewc2@jakewc2-desktop:~$ sudo /etc/init.d/mpd start-create-db
[sudo] password for jakewc2: 
 * Starting Music Player Daemon mpd                                              * creating /home/jakewc2/.mpd/tag_cache... 
problem opening log file "/home/jakewc2/.mpd/mpd.log" (config line 11) for writing
                                                                         [fail]
jakewc2@jakewc2-desktop:~$ 


so its knackered. :lolflag:

sorry, feeling very frustrated here.

is there any way somebody can remote access my pc and take a look at it? Not sure what else can be done with this now.

I really appreciate the patience and all the help that you have given me trying to get this sorted, I never come across this before. Its persuading me to stay and try learn ubuntu over windows.

Funny though, when I entered this command.
> 
sudo mpd --create-db

the database showed.

---

### Post by whitethorn on 2008-09-13
I think you've almost got it.  Right now it can't find open the .log file

```
ls .mpd
```  

Is there a mpd.log file in there? Give me the output of

```
ls -l ~/.mpd
```

if there's is no mpd.log file in there then

```
gedit ~/.mpd/mpd.log
```

and then save it. Then try to start mpd again

```
sudo /etc/init.d/mpd restart
```

None of the create db commands will work because mpd can't start yet there are still a couple files missing I think.

---

### Post by jakewc2 on 2008-09-13
```
ls .mpd
```

> jakewc2@jakewc2-desktop:~$ ls .mpd
mpd.db  mpd.db~  mpd.error  mpd.log  playlists  tag_cache
jakewc2@jakewc2-desktop:~$ 



```
ls -l ~/.mpd
```


> jakewc2@jakewc2-desktop:~$ ls -l ~/.mpd
total 36
-rw-r--r-- 1 jakewc2 jakewc2 5770 2008-09-13 15:17 mpd.db
-rw-r--r-- 1 jakewc2 jakewc2 5770 2008-09-12 17:41 mpd.db~
drwxr-xr-x 2 jakewc2 jakewc2 4096 2008-09-13 05:39 mpd.error
drwxr-xr-x 2 jakewc2 jakewc2 4096 2008-09-13 05:39 mpd.log
drwxr-xr-x 2 jakewc2 jakewc2 4096 2008-09-11 12:50 playlists
-rw-r--r-- 1 jakewc2 jakewc2 5770 2008-09-13 16:03 tag_cache
jakewc2@jakewc2-desktop:~$ 


```
sudo /etc/init.d/mpd restart
```

> jakewc2@jakewc2-desktop:~$ sudo /etc/init.d/mpd restart
[sudo] password for jakewc2: 
 * Stopping Music Player Daemon mpd                                      [fail] 
 * Starting Music Player Daemon mpd                                             problem opening log file "/home/jakewc2/.mpd/mpd.log" (config line 11) for writing
                                                                         [fail]
jakewc2@jakewc2-desktop:~$ 


Those are the results,and I still cant open Sonata, and gmpc still has the connection error. :(

John.

---

### Post by whitethorn on 2008-09-13
ahh we have it almost now we need to change the permission for mpd to write to the mpd.log file.

Open nautilus, then press crtl + h to show hidden folders and files.  Navigate to your .mpd folder.  Right click on mpd.log, go to the permissions tab and change it so that owner has  read and write permission, and nothing else (I don't know the terminal command). Then try restarting mpd.  As soon as we get mpd working, then gmpc shouldn't be a problem.

---

### Post by jakewc2 on 2008-09-13
Hi, sorry for sounding a bit dumb, but what is Nautilus, first time I have heard of that.Sorry. :(

---

### Post by whitethorn on 2008-09-13
It's the file manager, when you click on Places -> Home Folder (that's nautilus) sry, my mistake

---

### Post by jakewc2 on 2008-09-13
ok, workied it out, tried changing permissions, but wont change, so how can I change them?

---

### Post by Nepherte on 2008-09-13
Instead of changing the permission of the files, you can override the user music player daemon uses.

Open up ~/.mpdconf:
```
gedit ~/.mpdconf
```

In the file is a text line that says:
```
user                "mpd"
```

Replace that line with:
```
user                "jakewc2"
```

Now restart mpd:
```
sudo /etc/init.d/mpd restart
```

You should be settled now.

---

### Post by jakewc2 on 2008-09-13
Um,problem, when I try to open up 

> gedit ~/.mpdconf

it opens up a blank page :( is there another command to open it?

---

### Post by whitethorn on 2008-09-13
We already changed the user name.  You mpd.conf is in /etc/mpd.conf. I had another look, I think your mpd.log is a folder?  It needs to be a file.  So in the /home/username/.mpd folder , remove the folder called mpd.log and create a file called mpd.log

If you want to look at your conf file

```
gksudo /etc/mpd.conf
```

To remove the folder and  

```
rmdir ~/.mpd/mpd.log && gedit ~/.mpd/mpd.log
```
then save and run

```
sudo /etc/init.d/mpd restart
```

---

### Post by Nepherte on 2008-09-13
Ah, I see someone advised it to move the file.

It's not a good idea to mix up user and system-wide install!
Just move it back:
```
mv ~/.mpdconf_back ~/.mpdconf
```
and continue with my previous post. Don't forget to check that this line
```
port "6600"
```
is correct.

---

### Post by whitethorn on 2008-09-13
I told him to move his conf file to /etc/mpd.conf   I was told in the mpd irc that it has to be in there otherwise the program doesn't work properly as a daemon. His old conf is at ~/.mpdconf_bak

---

### Post by vanadium on 2008-09-13
It is becoming a big mess again. Clean it all up (uninstall everything, delete /etc/mpd.conf and all mpd directories), restart your system and strictly (strictly!) follow the instructions I gave. That is the most easy way you can have to install mpd/sonata.

---

### Post by Nepherte on 2008-09-13
There are two configuration files for mpd. One system-wide /etc/mpd.conf and one user-based ~/.mpd. They can both exist simultaneously (which was the case here, the system-wide was never removed) and I told him to make a user-based as well (by copying the system-wide to his home directory) and make the changes in the user-based. When mpd start, it looks in the home directory for its configuration file. If it exists, it uses that one, if it doesn't, it goes to the system-wide. The advantage of working user-based, is that every user can have his "mpd" configured in another way than other users, such as own music directory, own log files, etc.. When something goes wrong in the user-based one, it will still be ok for the other uses.

---

### Post by Nepherte on 2008-09-13
Both my instructions and Vanadium's would work if used solely on its own. I agree that Vanadium's instructions (I believe in page 3 somewhere) are the fastest ones to set it up so that it would work.

---

### Post by jakewc2 on 2008-09-13
[center][color="red"][size="5"]yyyyyyiiiiiippppppeeeeee!!!![/size][/color]][/center]


Cant get Sonata to work still wont open, but GMPC is working, and playing. 

Thank you so much for all your patience, you are all amazing for being so understanding and helpful. Its playing in the background as I type.

Now all I have to do is work out how to copy music from cd's to the program, then I'll be fixed.

Thank you so much again.

John.

p.s. sorry for the large red fonts, but its how I'm feeling right now. still not sure how that worked,as the last two messages confused me a bit, which isnt difficult, but I entered all the commands you both gave, and they worked, which is just amazing.

---

### Post by jakewc2 on 2008-09-13
oh dear, sorry, didnt see the posts, but you can see mine. 

Is there anyway you can find out if I have system-wide /etc/mpd.conf and user-based ~/.mpd working or how it is woking. I'm the only person here, so it will only be me using it, but it would be interesting to find out how it working? Where the filesare. Especially when I do add music, and update the database.

Or do you think I should uninstall and reinstall anyway?

John

---

### Post by Nepherte on 2008-09-13
Uninstall mpd and sonata and follow vanadium's instructions: [http://ubuntuforums.org/showpost.php?p=5769110&postcount=15](http://ubuntuforums.org/showpost.php?p=5769110&postcount=15)

They will give you mpd and sonata working rightaway.

---

### Post by vanadium on 2008-09-13
... perhaps if it *does* work with gmpd, you'd better continue with your current setup for now. You will gain more experience with Linux, and later on, it will become easy for you to understand and fix things yourself. Anyway, I am glad that you have it working now after this long journey.

---

### Post by jakewc2 on 2008-09-13
Hi, um, sorry to be a bit dense, but I'm having problems trying to save music but its just not working, I can only play when the cd is inserted. Can anybody help?

---

### Post by whitethorn on 2008-09-13
Hey Congrats!  Sorry for complicating things a bit, but at least you can now listen to music.  What happens when you put a cd in your drive? I get a popup and it asks me what to open it with.  Open Audio CD Extractor then I can extract it to my computer.  If that doesn't work for you go to Applications -> Sound and Video -> Audio CD Extractor.

If you want to check out some other clients here's list of a couple.

[http://www.musicpd.org/clients.shtml](http://www.musicpd.org/clients.shtml)

---

### Post by jakewc2 on 2008-09-13
hi, thank you for your message, I tried that, but I have a various artists album, I extractedit, but have found that unlike 1 persons album, which installed into its own folder, this stored each seperate composer in their own folders, which means theres now a dozen folders with just one record in each that wont play.

Sorry about this, anybody would think I had never used a pc before, but how do you get it so that it extracts to one folder, and get them to play, they they are in the folders, but thats it.

---

### Post by jakewc2 on 2008-09-13
Checked through the files and discovered what the problem is, its the permissions, the new music I have downloaded, has no permissions, and I cant change them, just like the other music I had. Is this going to happen everytime I want to download somewthing? Why cant I change permissionsm, as I have root acess?

---

### Post by whitethorn on 2008-09-13
What kind of filesystem are you trying to write to (ntfs, fat32, ext3)?  Usually the best way would be to extract the files somewhere in your homefolder.  If you're trying to write to fat32 or ntfs, then you won't be able to change the permissions.  And in Audio CD Extractor go to Edit -> Preferences.  change under Track Names the Folder Hierarchy.  Maybe that's why it's only putting one song per folder.

---

### Post by jakewc2 on 2008-09-13
Hi, as far as file format, I'm not sure, is not something I've ever had to find out before, can you tell me how I find that out?

I changed the preferences in the Audio CD Extractor, so maybe that might help.I've deleted the album and going to try again, but what is worrying me is the fact I cant change the permissions in the Folder to Read and Write. So its not being recognised.

The other thing I've found out is that the files are being saved as .ogg never heard of that extension before,should they be saved as .ogg's?

---

### Post by jakewc2 on 2008-09-13
Also in my fiddling, when I opened GMPC, I searched for the new album, the right clicked and found a link that says Update, I clicked on that, and then went to play the music, and at last it plays. I also found in Applications, something that says NTFS config Tool, does that mean anything?

I think now, for the moment it seems to be working. I'll try another CD and see what that does.

---

### Post by jakewc2 on 2008-09-14
Hi everybody, I have managed to get Sonata working, I found out that if you delete the sonatarc file, it reverts back to its defaoutl settings which is what I did, and now Sonata works.

Just wanted to thank everybody on here for all their help and suppoert, and patience in helpng me get this sorted. I would also like to thank Scott for telling me about the last bit to delete the file.
 John.

---

### Post by Mitch72 on 2008-11-03
Hey all, I'm having trouble with this too :mad:. I've installed MPD and configured the ~/.mpdconf file as follows (my bad for the long post):



# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"~/.mpd/music"
playlist_directory	"~/.mpd/playlists"
db_file			"~/.mpd/mpd.db"
log_file		"~/.mpd/mpd.log"
error_file		"~/.mpd/mpd.error"
pid_file		"~/.mpd/pid"
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"~/.mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "mitchell"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "verbose"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
# An example of an ALSA output:
#
#audio_output {
#        type                    "alsa"
#        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################


All the files and folders specified in the "Required Paths" section are there, the "music_directory" having a link to the music directory where all my music files are on another hardrive

My problem is, when I run "sudo mpd --create-db" it only adds a few songs (almost randomly?). My music is organised as Artist/Album/Songs, and mpd takes all of one artist starting with J, then two artists from the start of the directory, then seems to freeze. 

After having a look around, I'm thinking it may be something to do with the music being on a windows hard-drive... no idea though, as it seems to grab around 40-50 songs fine, then just stops, no error message or anything, just stops midway through retrieving.

I'd appreciate any help :p cheers, Mitch

EDIT: Found the problem... I'd used winamp on my windows install, which had somehow removed the tags of the m4a files (I have no idea why...). When MPD got to those files, it couldn't read the tag, and froze. To fix it, I use mp3tag in windows to add the metadata using the filename (luckily, most my files where organized like *artist*/*album*/*track* - *title*, so it wasn't too much trouble).

---

### Post by andrewabc on 2008-11-07
I've spent 3 hours on #mpd irc getting help. finally got it working.

Have to install paprefs (from synaptic)
Then check:
Enable network access to local sound devices
Don't require authentication

Go into mpd.conf, set the music_directory to proper location, add:
audio_output {
type	"pulse"
name	"My MPD Pulseaudio Output
}
to audio section (or else get seg faults and xopendisplay errors).

Then create your database
sudo mpd --create-db

and sonata should be working. Might have to configure sonata to point to directory. not sure.

My music was on ntfs data partition on hard drive. I already had ntfs read/write capabilities, and the partitions mount when ubuntu start.

---

