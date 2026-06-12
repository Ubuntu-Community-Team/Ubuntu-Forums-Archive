---
title: "Audioscobbler plugin in Rhythmbox,Muine and Xmms/BMP"
date: 2005-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Majlo on 2005-05-30
Hi ..
*Audioscrobbler builds a profile of your musical taste using a plugin for your media player (Winamp, iTunes, XMMS etc..). Plugins send the name of every song you play to the Audioscrobbler server, which updates your musical profile with the new song. Every person with a plugin has their own page on this site which shows their listening statistics. The system automatically matches you to people with a similar music taste, and generates personalised recommendations. * 

Home Page
[http://www.audioscrobbler.com/](http://www.audioscrobbler.com/)

Example my profile [http://www.audioscrobbler.com/user/Majlo/](http://www.audioscrobbler.com/user/Majlo/)

Lets do it :-)

Do to addres [http://www.audioscrobbler.com/signup.php](http://www.audioscrobbler.com/signup.php) and register
You have now Login and password

**Rhythmbox** 

Open terminal and type

sudo apt-get install libgtk2.0-dev python-gtk2-dev python2.3 python2.3-dev gcc
wget [http://members.cox.net/alexrevo/rbscrobbler-0.0.9.tar.gz](http://members.cox.net/alexrevo/rbscrobbler-0.0.9.tar.gz)
tar zxvf rbscrobbler-0.0.9.tar.gz
cd rbscrobbler-0.0.9
make
sudo make install
rbscrobbler

Right click on the icon in notification area and type login and password

System -> Preferences -> Sessions
Startup Programs Tab -> Add
Startup Command: rbscrobbler
Order: 70 
 
**Muine**

Open terminal and type

wget [http://www.informatics.sussex.ac.uk/users/mrm21/muine/muinescrobbler-0.1.5.tar.gz](http://www.informatics.sussex.ac.uk/users/mrm21/muine/muinescrobbler-0.1.5.tar.gz)
tar zxvf muinescrobbler-0.1.5.tar.gz
cd muinescrobbler-0.1.5
make
make install

Start Muine --> File --> Audioscobbler
Type Login and Password
Click OK
Restart Muine

**Beep-media-player/XMMS**

Open terminal and type

sudo apt-get install beep-media-player-dev
OR
sudo apt-get install xmms-dev

sudo apt-get install libcurl3 libcurl3-dev libmusicbrainz4 libmusicbrainz4-dev g++

wget  [http://static.audioscrobbler.com/plugins/xmms-scrobbler-0.3.6.tar.bz2](http://static.audioscrobbler.com/plugins/xmms-scrobbler-0.3.6.tar.bz2)
tar jxvf xmms-scrobbler-0.3.6.tar.bz2
cd xmms-scrobbler-0.3.6
./configure
make
sudo make install

Start Beep Media Player --> Preferences --> Plugins --> General --> Preferences 
Type Login and Password and check enable

Thats all :-)

---

### Post by Mez on 2005-05-30
and if you use amaroK

Settings -> Configure amaroK -> Scrobbler

All the settings are there ;D and you dotn ened to install anythign

---

### Post by jonny on 2005-05-30
Tempting to start a competition... who can get the naffest list of recommendations out of the system?

---

### Post by Majlo on 2005-06-06
[QUOTE=Mez]and if you use amaroK

Settings -> Configure amaroK -> Scrobbler

All the settings are there ;D and you dotn ened to install anythign[/QUOTE]


Yes Amarok is great apps but i love Gnome & Gnome-apps :-)

---

### Post by bored2k on 2005-06-10
Scrobbler is a really cool/great thing :D

You can get a deb for it here:  [http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/r/rbscrobbler/](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/r/rbscrobbler/)

---

### Post by Majlo on 2005-06-13
[QUOTE=bored2k]Scrobbler is a really cool/great thing :D

You can get a deb for it here:  [http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/r/rbscrobbler/](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/r/rbscrobbler/)[/QUOTE]

Great ...
Thanks for tip :-)

---

### Post by Breezy on 2005-07-05
Nice howto..
Thanks

---

### Post by bernardfrancois on 2005-07-07
I'd luv to make the audioscrobbler plug-in work for rhythmbox.
When I run **make**, I get an error: **package pygtk-2.0 was not found in the pkg-config search path**.

I checked synaptic, and the following (relevant) packages are installed:
[list]
[*]python-gtk2
[*]python-gtk2-dev
[*]libgtk2.0-0
[*]libgtk2.0-0-dbg
[*]libgtk2.0-0-bin
[*]libgtk2.0-0-common
[*]libgtk2.0-0-dev
[/list]

Note that I can succesfully compile the gtk examples (in C code).

Anyone who knows what I need to do or to install to make it work?

---

### Post by bernardfrancois on 2005-07-13
nobody who ever tried to make the rhythmbox audioscrobbler plug-in work?

---

### Post by Majlo on 2005-07-13
[QUOTE=bernardfrancois]nobody who ever tried to make the rhythmbox audioscrobbler plug-in work?[/QUOTE]

Hi..

Install this plugin better from [http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/r/rbscrobbler/rbscrobbler_0.0.9r-1ubuntu2_i386.deb](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/r/rbscrobbler/rbscrobbler_0.0.9r-1ubuntu2_i386.deb)

This working fine and you don't must compile plugin . .

---

### Post by bored2k on 2005-07-24
Just wanted to add that I compiled a i386 debian package for the xmms/beep-media-player scrobbler and it can be found [here](http://bored2k.cjb.net/) . After installing the package (sudo dpkg -i file.deb), enable it on beep's/xmm's preferences.

---

### Post by niels on 2005-07-25
I have tryed to install the plugin for both Rhythembox and BMP, but it doesn't seem to work. Nothing is add at my Audioscrobbler page. When I run the rbscrobbler for Rhythembox, it gives me the follwing:

> 
niels@nielspc:~ $ rbscrobbler
Unable to import eyeD3; Musicbrainz support for mp3 will be disabled.
[20050725 12:46:30] [Audioscrobbler] Plugin ID: rbx, Version 0.9 (Protocol 1.1)
[20050725 12:46:31] [Audioscrobbler] Set username to "nielsha".
[20050725 12:46:31] [Audioscrobbler] Set password.
[20050725 12:46:31] [Rhythmbox_Bonobo] Adding callback (song): __main__::__song_change
[20050725 12:46:31] [Audioscrobbler]   [!!] duration < 30 seconds; not submitting.
[20050725 12:46:31] [Rhythmbox_Bonobo] Adding callback (state): __main__::__playing_change
[20050725 12:46:31] [Rhythmbox_Bonobo] Adding callback (song): __main__::__callback_song
[20050725 12:46:31] [Audioscrobbler] Performing handshake...
[20050725 12:46:31] [Audioscrobbler]   error: <urlopen error (111, 'Opkobling n\xe6gtet')>
[20050725 12:46:31] [Audioscrobbler]   Handshake failed: <urlopen error (111, 'Opkobling n\xe6gtet')> (will retry at 13:16 CEST)


What is the thing about eyeD3? Why can't it connect? And might the problem with BMP bee that it can't connect?


Niels

---

### Post by agds on 2005-07-29
The eyeD3 error means you need to install the python-eyed3 package.  It's available in the Multimedia (universe) section.  The handshake error was probably caused by the Audioscrobbler server, not your machine.  It frequently has that problem, but the handshake always eventually succeeds.

---

### Post by rathel on 2005-08-01
Got a question, is there a plugin or something for the terminal-based players like mp3blaster?
Just Wondering.

---

### Post by agds on 2005-08-01
None that I know.  If you're feeling particularly motivated, Audioscrobbler's FAQ indicates that the source is available from their SourceForge project page.  Maybe you could work from there?

---

### Post by niels on 2005-08-03
Is it possible to start rbscrobble together with Rhythembox? I want to start rbscrobblewhen I click the Rhythembox icon - maby in the 'Command' field?!

---

### Post by agds on 2005-08-03
The easiest way is probably to write a short shell script.  There's [a thread in one of the Audioscrobbler forums](http://www.audioscrobbler.com/forum/13117/_/25282) where two Rhythmbox users have posted scripts.  I haven't tried them, so I can't guarantee they'll work.  It's certainly worth checking out, though.

---

### Post by talkingwires on 2005-08-14
[QUOTE=bored2k]Just wanted to add that I compiled a i386 debian package for the xmms/beep-media-player scrobbler and it can be found [here](http://bored2k.cjb.net/) . After installing the package (sudo dpkg -i file.deb), enable it on beep's/xmm's preferences.[/QUOTE]Or you could just run 'sudo apt-get install beep-media-player-scrobbler'. Seriously, all of the plugins mentioned so far can be installed via apt-get. Search Synaptic for 'scrobbler'.

---

### Post by bjweeks on 2005-08-14
Thanks this is great!!! :)

---

### Post by Slugger on 2005-08-14
Yea this is great thanks!!!!

---

### Post by agds on 2005-08-14
[QUOTE=talkingwires]Or you could just run 'sudo apt-get install beep-media-player-scrobbler'. Seriously, all of the plugins mentioned so far can be installed via apt-get. Search Synaptic for 'scrobbler'.[/QUOTE]I must be missing at least one repository because searching for "scrobbler" yields no results.  Could you post your /etc/apt/sources.list?

---

### Post by Majlo on 2005-08-14
[QUOTE=talkingwires]Or you could just run 'sudo apt-get install beep-media-player-scrobbler'. Seriously, all of the plugins mentioned so far can be installed via apt-get. Search Synaptic for 'scrobbler'.[/QUOTE]


Hi..

Yes this packages is in Breezy but not in Hoary..

---

### Post by redneckr1 on 2005-10-10
err the tar for Rhythmbox is out of date, can you tell me where to get the new one as i really want to use audioscrobbler :( 


Thanks

Me

---

### Post by Ibbelz on 2005-12-19
apt-get install xmms-srobbler worked nicely for my Ubuntu. Pfew, it is just amazing how easy it is to install stuff with apt. :)

---

### Post by GreatestGravity on 2006-01-06
Has anyone had trouble with xmms-scrobbler freezing xmms occasionally ? 

I can't confidently pin it down to xmms-scrobbler, since I DO have some custom scripts running with each new song (my own songstaticsics, for my IM profile, called through the SongChange plugin) but I'm pretty sure those work fine, and audioscrobbler is the only other thing I've installed to do with XMMS recently.

If I were to guess, the problem would be caused by sporadic internet connectivity - my house has wireless internet that sporadically flickers, and my wireless card only works through NDISDriver, so I've had kind of iffy wireless all the way through. 

Anyhow, anyone had any problems with stuff before or just me?

---

### Post by dimatrod on 2006-05-08
The download link for Rhythmbox scrobbler plugin isn't working...

Also, does it work for 0.9.4.1?

---

### Post by chrstphrtlbt on 2007-02-26
can anyone help me in installing the plugin for XMMS? i have downloaded the appropriate plugin, just don't know how to install it as i'm very new to all of this.

---

### Post by agds on 2007-02-26
> **chrstphrtlbt said:**
> can anyone help me in installing the plugin for XMMS? i have downloaded the appropriate plugin, just don't know how to install it as i'm very new to all of this.

If you downloaded the plugin from Last.fm, there's an easier way to do it.  Have you used apt-get, aptitude or Synaptic to install packages before?  You'll probably be using at least one of the three quite often.  Synaptic tends to be the most approachable for GNU/Linux newbies.  The other two run from the command line.  It's outside the scope of this thread to explain how to use them, but you may want to check out these links:

[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html]("http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html")
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html")

The latter comes from the Ubuntu 6.10 Desktop Guide, but it shouldn't make much difference if you're running an earlier release, such as 6.06 LTS.

In any case, there should be a package called xmms-scrobbler in the Multimedia universe repository.  Install that, and the hard part is done.  The fastest way is to enter

```
sudo apt-get install xmms-scrobbler
```

in a terminal, assuming you have the appropriate repositories selected.  Then you can enable the plugin from the preferences menu in XMMS.

---

### Post by chrstphrtlbt on 2007-02-26
ok i'm done! just playing a track to see if it's worked. thank you so much, i didn't realise it was as simple as doing that line of code. i've done it many a time before i believe.

---

### Post by chrstphrtlbt on 2007-02-26
aha, typical. last.fm are down for routine maintenance!

---

### Post by chrstphrtlbt on 2007-02-26
ok it hasn't worked. it's all installed fine, and i have it enabled and the user and pass correct, yet it still doesn't update on the site. also, if i restart i lose sound from time to time. i'm having so many problems with ubuntu argh.

---

### Post by knatten on 2007-04-25
If you have problems with xmms not scrobbling, take a look at my answer in [this thread]("http://ubuntuforums.org/showthread.php?p=2530866#post2530866").

---

### Post by MRlaith on 2007-10-14
i know how to make xmms look like winamp its not that hard
just go in here: [http://www.winamp.com/skins/details/143266](http://www.winamp.com/skins/details/143266) 
download the file thingy and put it in here : home/(user)/.xmms/skins
then open xmms and press Alt+s and choose  "Winamp5_classifield" 
and xmms will look just like winamp :lolflag:

---

