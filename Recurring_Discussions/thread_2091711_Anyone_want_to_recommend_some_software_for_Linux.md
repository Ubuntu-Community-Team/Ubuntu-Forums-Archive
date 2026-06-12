---
title: "Anyone want to recommend some software for Linux?"
date: 2012-12-05
forum: Recurring Discussions
---

### Post by linktopower on 2012-12-05
Well I just killed my windows on my old Toshiba Laptop. And promptly installed **Lubuntu 12.10** on it.
So far I'm liking how this Ubuntu spin off is. it works pretty fast on these specs.

Toshiba satellite Laptop 
CPU: Intel Celeron 2.40Ghz
RAM: 1.00GB DDR 
VIDEO: Intel extreme Graphics, 64MB 
HARD DRIVE: 120GB


All I'm doing right now is just messing around with it, But I was wondering. 
Does anyone have any recommendations on what software is a must have for a Linux system?

This is what Other people told me I need to get

Wine
Gimp
VLC Player 
VirtualBox
Xchat

I know that these are some things I'm going to get. But I'm wondering, Is there any more software that is must haves?.

---

### Post by agillator on 2012-12-05
That is a 'which is better, apples or blue' question. There are a million answers but none of them may be what you want.  

The first question is 'What do you want to do?' Do you do lots of word processing, spreadsheets, that sort of thing? If so, then you need an office suite. Are you more into rocket guidance or discovering new planets? Can't help you there. Are you a videographer and need to edit videos, or edit sound files, or . . . or . . . or?  Typesetting (Tex, LaTex, Lyx)? Post what you think you want to do, what your interest are, what you did when you used windows,  and you can get useful suggestions.

---

### Post by linktopower on 2012-12-05
Yeah I should'v said what I want to do with it shouldn't I :P

Anyways, Pretty much all I'm going to do is use it for just 

Browsing the internet 
Downloading stuff and torrent things
Listening to music
Watch videos.
Get on Chat rooms.
Play some minor games. Maybe emulate some things.

Pretty much do things. I like messing around with stuff.
I didn't do much with it in the first place :P

---

### Post by drawkcab on 2012-12-05
Browsing--Firefox or Chrome

Torrents--Transmission, although there are good alternatives if you need specific features.  Check out rtorrent, qtorrent and deluge among others.

Music--I prefer audacious which is simple and straightforward but you may prefer a more feature rich player like rhythmbox, clementine or banshee.

Video--I primarily use VLC and SMPlayer.  The latter enables my Nvidia card to accelerate the decoding of HD .mkv files which helps because my processor is low-end.

Games--There are a bunch in the software store.  Also steam is coming to ubuntu shortly!

IRC--xchat

---

### Post by linktopower on 2012-12-05
Sounds like some pretty good software. Thanks.
I'll be getting them this weekend!

---

### Post by DukeOfMixture on 2012-12-05
Bleachbit - keeps junk files off your system.

Here's a tutorial so you don't rub out things you need

[http://www.youtube.com/watch?v=7DRWJ7cHF9A](http://www.youtube.com/watch?v=7DRWJ7cHF9A)

UFW - Universal Firewall. It may be installed already.

I'm using apparmor, also.

> Play some minor games. Maybe emulate some things.

I use Dosbox (dos programs emulator, but will work for dosgames) and Mame (if you like video arcade games. A lot of 80's games if you're old like me.).

---

### Post by agillator on 2012-12-05
That helps. For what you have listed, you probably don't need to install much of anything. For browsing there is Firefox or Chrome. For music there are several options, but start with what is already installed. Look in the applications menu under multimedia. For videos the same recommendation although many people prefer vlc or mplayer (smplayer for the XWindows front end). For chat (I assume you mean IRC) there are several programs. If you are using Firefox, check out the chat addon. For games, you may be a little limited. Some games are available for Linux (check the games portion of Ubuntu Software Center of the Applications Menu). Some will run under wine. I understand Steam is coming out or has just come out with support for Linux so Civilization and others might be available through them. 

More generally go to the Ubuntu Software Center and browse to see what catches your interest. That is one of the good things about Linux - most of what is available is free so you can try it without cost.

Other people will, of course, have more suggestions. Look at what catches your fancy. But remember, another person's treasure may well be your trash.

---

### Post by boogerama on 2012-12-05
I agree with Agillator, pretty much everything you need  for basic use comes with the OS at first install.  You'll need to find out what your preferences are on certain apps but aside from that you'll be good to go.

The only software swap I did was remove firefox and add chrome.  Aside from that I installed Wine (for Quicken 2009), Wireshark, LuckyBackup, Gimp, Skype, Dropbox, Stellarium, and indicator-weather.

That got me up and running with everything I use.

---

### Post by linktopower on 2012-12-05
> **DukeOfMixture said:**
> Bleachbit - keeps junk files off your system.

Here's a tutorial so you don't rub out things you need

[http://www.youtube.com/watch?v=7DRWJ7cHF9A](http://www.youtube.com/watch?v=7DRWJ7cHF9A)

UFW - Universal Firewall. It may be installed already.

I'm using apparmor, also.



I use Dosbox (dos programs emulator, but will work for dosgames) and Mame (if you like video arcade games. A lot of 80's games if you're old like me.).
Thanks :) 

> **agillator said:**
> 
More generally go to the Ubuntu Software Center and browse to see what catches your interest. That is one of the good things about Linux - most of what is available is free so you can try it without cost.
Yep, That's is one thing thats great about linux. half of the software is full on free :D.
So far I've never ran into software that cost money.
> **agillator said:**
> 
Other people will, of course, have more suggestions. Look at what catches your fancy. But remember, another person's treasure may well be your trash.
Yeah I Know, But its always interesting to see what other people think is must have piece of software for a Linux system.

----------
So far these are the things I'm going to be trying this weekend.

Wine
Gimp
VLC Player 
VirtualBox
Xchat
Deluge
rhythmbox, clementine banshee.
Universal Firewall
Bleachbit
Dosbox
Mame

looks good to me so far :)

---

### Post by StinkySQL on 2012-12-05
Gimp for drawing
VLC media player for movies
Thunderbird for email
Solfege for studying music
GParted for hard drives
Mono for developing

---

### Post by mike555 on 2012-12-08
To edit the menu you might want " menulibre".

---

### Post by andrew.46 on 2012-12-09
> **linktopower said:**
> 
Listening to music


If you are interested in listening to your music from your HDD you could do a lot worse than installing the commandline cd ripper abcde:

```
sudo apt-get install abcde
```

and if you are keen to rip to ogg vorbis the following ~/.abcde.conf file should prove useful:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       Ogg Vorbis using abcde version 2.5.3
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for Ogg Vorbis. In this case
# vorbize is the other choice.
OGGENCODERSYNTAX=oggenc

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/oggenc
OGGENC=oggenc

# Specify your required encoding options here. Multiple options can
# be selected as '-q 6 --another-option' etc.
OGGENCOPTS='-q 6'  

# Output type for Ogg Vorbis
OUTPUTTYPE="ogg"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

Have fun :)

---

### Post by oldgraf on 2012-12-09
@linktopower
Why is that VirtualBox ? You have celeron and only 1 GB ddr ram

---

### Post by linktopower on 2012-12-09
> **andrew.46 said:**
> If you are interested in listening to your music from your HDD you could do a lot worse than installing the commandline cd ripper abcde:

```
sudo apt-get install abcde
```

and if you are keen to rip to ogg vorbis the following ~/.abcde.conf file should prove useful:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       Ogg Vorbis using abcde version 2.5.3
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for Ogg Vorbis. In this case
# vorbize is the other choice.
OGGENCODERSYNTAX=oggenc

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/oggenc
OGGENC=oggenc

# Specify your required encoding options here. Multiple options can
# be selected as '-q 6 --another-option' etc.
OGGENCOPTS='-q 6'  

# Output type for Ogg Vorbis
OUTPUTTYPE="ogg"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

Have fun :)
Thanks, this will come in handy :)
> **oldgraf said:**
> @linktopower
Why is that VirtualBox ? You have celeron and only 1 GB ddr ram
Well I had linux on it before and I ran VB just fine.
Well maybe it helps I was running Windows 2000 in it :P

---

### Post by Sef on 2012-12-09
> That is a 'which is better, apples or blue' question. There are a million answers but none of them may be what you want. 

Exactly, which is why it belongs in Recurring Discussions.

---

### Post by Jakin on 2012-12-10
Talk of audio encoding/ ripping your own musik.
I recommend XFCA, it may take abit of time to find codecs pakages (if you need all of them) but this gui encoder is easy, has endless options :)
You'll find it in ubuntu software centre.

---

### Post by Petro Dawg on 2012-12-20
> **linktopower said:**
> Yeah I should'v said what I want to do with it shouldn't I :P

Anyways, Pretty much all I'm going to do is use it for just 

Browsing the internet 
Downloading stuff and torrent things
Listening to music
Watch videos.
Get on Chat rooms.
***Play some minor games. Maybe emulate some things***.

Pretty much do things. I like messing around with stuff.
I didn't do much with it in the first place :P

If you want to emulate some things, "**ZSNES**" is a great super NES emulator and all the great ROMS of the past are plentyfull (especially if you like RPGS).  The Nintendo 64 emulator "**mupen64plus**" is a little buggy (on my system for some ROMS anyway) but seems to play the Zelda games well.  The N64 emulator takes a little effort to get installed (installs in terminal) but is worth the time in figuring it out.  

I haven't found much in the way of easy to use stable emulators for any more recent gaming system.

---

