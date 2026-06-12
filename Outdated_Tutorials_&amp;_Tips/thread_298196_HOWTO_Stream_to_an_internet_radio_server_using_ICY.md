---
title: "HOWTO: Stream to an internet radio server using ICY (SHOUTcast)"
date: 2006-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormx on 2006-11-12
There are a few tools out there which stream to shoutcast servers. Most are media-player plugins, a few aren't. I've yet to find one I like except for the official, closed source TRANScast client. Its not perfect, but it works for me. There are a few bugs, but my script clears up the big ID3 one.

**What this guide shows you how to do**
 - Setup TRANScast, a piece of software provided by nullsoft to stream MP3 music to a server
 - Setup a hack, which fixes the broken ID3 support in this.
 - Other nice tools

[SIZE="5"]**Okay, lets go!**[/SIZE]

```
cd ~
wget http://www.shoutcast.com/downloads/sc_trans_posix_040.tgz
```
Download the latest version of the software
```
tar -xvzf sc_trans_posix_040.tgz
```
Untar/ungzip the archive and extract.
```
mv sc_trans_040 shoutcast
```
Move the directory to something more meaningful
```
cd shoutcast
gedit sc_trans_conf
```
Use your favourite editor to edit the config file

[SIZE="5"]**Editting the config file**[/SIZE]
The config file is already pretty well annotated, but I'll go through it:

**PlaylistFile**
Set this to whatever you want your playlist file to be. You can make multiple files like metal.pls, indie.pls, electronica.pls, beatles.pls, whatever... Each file lists all the tracks in the playlist. Each track must be an MP3. The items are seperated by new lines. The software automatically misses out the first track, but the file has to exist, I think.

**ServerIP**
Doesn't actually need to be an IP. If you don't know what this is you shouldn't be reading this guide.

**ServerPort**
Pretty self-explanitory, usually 8000

**Password**
Server Password. If you have bought some shoutcast hosting you will have got this password. if you set up the server yourself, its in the config file there.

**StreamTitle, StreamURL, Genre**
This appears in the shoutcast directory, if you enable it. StreamTitle could be like, "Radio 0", StreamURL could be your website, and Genre can be multiple genres, comma seperated. e.g. House, Breakbeat, etc.

**LogFile, Shuffle** are well explained in the file itself.

**BitRate, SampleRate, Channels**
Explained in the guide. Remember that halving the amount of channels won't necessarily halve the data your transmitting.

**Quality**
This is set to 1 by default, but if you find you are getting wierd skipping then it might be worth setting it down a bit, to say, 3.

**CrossfadeMode, CrossfadeLength**
A good choice to have it on, but 8 seconds (default value) is a bit length. I have mine on 2 seconds (2000)

**UseID3**
Makes no difference.

**Public**
Well explained in the guide. 1 for submitting to shoutcast directory, 0 for not.

**AIM, ICQ, IRC**
Again, pretty obvious / well explained.

[SIZE="5"]**Creating a playlist**[/SIZE]
There are a few ways you can make the playlist. A good one is to use your favourite media player. Set everything up, then save the playlist as .M3U. It is basicly the same format. Then just move it to playlist.pls, or whatever you have in your config.

Another is just to manually edit the file.

[SIZE="5"]**Running the server**[/SIZE]
Running the server is simple:
```
cd ~/shoutcast
./sc_trans_linux
```

Be sure to do that in a terminal. Make sure everything works. Then listen to your stream for a while. Check its not lagging, and that everything is in order

[SIZE="5"]**Fun Hacks**[/SIZE]

**Fixing ID3 support**

AFAIK, ID3 support is borked in this. I wrote a small workaround, originally in BASH, and finally in PHP. The bash version was very buggy. The PHP version is nice and should work everytime, even if the code is a bit messy.

**1. ** ```
sudo apt-get install php5-cli php-getid3
```
First, install php5-cli and php-getid3
**2. ** ```
cd ~
mkdir bin
cd bin
```
It doesn't matter if bin already exists
**3. ** ```
gedit ~/.bashrc
```
If it doesn't already exist, add this:
```

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```
**4. ** ```
wget http://www.dython.net/z/hosted/stormx/shoutcast-hack-php
chmod +x shoutcast-hack-php
gedit shoutcast-hack-php

```
Edit the first variable, shoutcastbase. The rest should be fine.

**5. ** Now to launch shoutcast:

```
cd ~/shoutcast
./sc_trans_linux | shoutcast-hack-php
```

**Kill Switches**
First, find the pid of the shoutcast server. This is given when it starts up, otherwise:
```
pidof sc_trans_linux
```
Say the PID was 1000, you could do something like

```
kill -CODE 1000
```

Where CODE can be:

HUP - flush logfiles (close and reopen) -- will make console logging stop
WINCH - jump to next song
USR1 - reload playlist off disk (will not interrupt current playing stream)
USR2 - toggle shuffle on/off
TERM - normal sc_trans shutdown (clean, same as hitting Ctrl + C)

Resizing a Terminal Window gives WINCH (I think it stands for Window Change), so best make it full screen.

---

### Post by aparigraha on 2006-11-25
Thx a lot for posting this very valuable php-solution.
Got one issue that i need help with though.
When launching sc_trans with php:

```
cd ~/shoutcast
./sc_trans_linux | shoutcast-hack-php
```

I get shoutcast-hack-php Command Not Found. A bash is started and sc_trans runs as usual... ID3 still not working.

I edited the dirs "home/Barney/shoutcast" in the shoutcast-hack-php file to suit my setup in Xubuntu. Still have the "Command Not Found"-issue. Any suggestions as to where I'm going wrong, would be greatly appreciated. Could Xubuntu be the issue perhaps?

Once again. Great job!

Aparigraha

---

### Post by ultratux on 2009-06-22
Just like to share another way:

Install TunaPie via Synaptic Package Manager (easiest). It can list both Shoutcast and Icecast stations. In the preference menu, you can select the appropriate player. In my case, I use VLC.

Enjoy!

---

### Post by Jeffryvdm on 2010-02-17
Can you please update this tutorial? The download links don't work any more :(

---

