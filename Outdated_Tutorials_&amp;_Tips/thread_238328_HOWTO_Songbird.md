---
title: "HOWTO: Songbird"
date: 2006-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by plb on 2006-08-17
Really simple guys........

Download this
[http://developer.songbirdnest.com/nightly/builds/linux/i386/Songbird_20060816_linux-i686.tar.gz](http://developer.songbirdnest.com/nightly/builds/linux/i386/Songbird_20060816_linux-i686.tar.gz)

tar -xfzv Songbird*

run songbird from the directory e.g. ./Songbird or add the path to your menu via alacarte

---

### Post by coastdweller on 2006-08-19
> **plb said:**
> Really simple guys........

Download this
[http://developer.songbirdnest.com/nightly/builds/linux/i386/Songbird_20060816_linux-i686.tar.gz](http://developer.songbirdnest.com/nightly/builds/linux/i386/Songbird_20060816_linux-i686.tar.gz)

tar -xfzv Songbird*

run songbird from the directory e.g. ./Songbird or add the path to your menu via alacarte

Thank you for the submission!

I was able to easily try this out.

I'm still working on my sound problems but its cool to know there is a Itunes-like categloger for music and its easy to use.

Thanks again.

---

### Post by gils0040 on 2006-08-20
crashes every few seconds for me....looks great though, i cant wait for it to go stable

---

### Post by RSX311 on 2006-08-20
yeah crashes randomly for me too, but it looks awesome, can't wait for a stable release to come out

---

### Post by mrgnash on 2006-09-06
I tried Songbird on Klik, because I thought it would be difficult to install. But this version crashes far less often :D Looks very promising so far!

---

### Post by handband2 on 2006-10-07
First I would like to thank [ArsGeek]("http://www.arsgeek.com/?p=615") for making this so easy to install!!!

Songbird is a great way to have all your media and web media in one place.  Check out the site [Songbird]("http://www.songbirdnest.com/").

Now lets intall it:

You can go here to download the file:
[http://www.songbirdnest.com/download/get/?sb_version=RC2&platform=linux-i686]("http://www.songbirdnest.com/download/get/?sb_version=RC2&platform=linux-i686")

[Click here to download Songbird!]("http://www.songbirdnest.com/thankyou/?sb_version=RC2&platform=linux-i686")

Go to where you downloaded the file and untar it:
```
tar zxvf ~/Desktop/Song*.tar.gz
```

Rename the file:
```
cd ~/Desktop

mv Songbird_20061003 Songbird
```

Move Songbird where you would like to have it.  I put it into /opt:
```
sudo cp -Rv ~/Desktop/Songbird /opt
```

Lets make sure we have use of this folder:
```
sudo chown -Rv username:username /opt/Songbird/
```

Time to run Songbird:
```
/opt/Songbird/Songbird
```

**Add and icon**.  You can download it by clicking here:
[Songbird Icon]("http://www.ubuntuforums.org/attachment.php?attachmentid=17030&stc=1&d=1160236451") - The Default icon is /Songbird/chrome/icons/default/default.xpm

More icons here:
[http://www.songbirdnest.com/getsongbird]("http://www.songbirdnest.com/getsongbird")

Move icon:
```
sudo cp ~/Desktop/sb.png /usr/share/pixmaps
```

**Adding it to the Application Menu:**
[LIST]
[*]Right click on Applications
[/LIST]
[LIST]
[*]Select Edit Menus
[/LIST]
[LIST]
[*]In Alacarte Menu Editor - Goto Sound & Video
[/LIST]
[LIST]
[*]Click on File -> New Entry
[/LIST]
[LIST]
[*]Entry Editor
[LIST]
[*]Name: **Songbird**
[/LIST] [LIST]
[*]Comment: **Songbird**
[/LIST] [LIST]
[*]Command: **/opt/Songbird/Songbird**
[/LIST]
[/LIST]
[LIST]
[*]Click on **No Icon**
[LIST]
[*]Goto /usr/share/pixmaps/sb.png
[/LIST]
[LIST]
[*]Click OK
[/LIST]
[/LIST]

**Now run it:**

*Applications -> Sound & Video -> Songbird*



I would like to say thanks again to ArsGeek.  If any of you have a chance check out the other [Ubuntu Posts]("http://www.arsgeek.com/?cat=9").  There is a lot of good stuff there!

---

### Post by franestepona on 2006-10-07
Nice How-to! Works great, but I have a problem though... How to play last.fm stream? When I click in a radio it says: last.fm is not a registered protocol.

Thanks!

---

### Post by geovino on 2006-10-07
I downloaded the file and it installed a folder in some archiver but is doesn't tell you what program it is. Where do i go from there? It looks like it is already extracted. So I don't know if your instructions will work.

---

### Post by handband2 on 2006-10-07
> **franestepona said:**
> Nice How-to! Works great, but I have a problem though... How to play last.fm stream? When I click in a radio it says: last.fm is not a registered protocol.

Thanks!

I'm glad it worked. :) 

For last.fm you have to make sure last.fm player is installed.  **reda_ea** has a good howto for the last.fm player:  
[http://www.ubuntuforums.org/showthread.php?t=213185]("http://www.ubuntuforums.org/showthread.php?t=213185")

To install last.fm player:
```
sudo apt-get install libgconf2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgdk-pixbuf-dev libgtk2.0-dev libmono-dev  libgnome2.0-cil mono-mcs mono-gac
```
or
[LIST]
[*]Open *Synaptic Package Manager*
[/LIST]
[LIST]
[*]Install these packages
[I][LIST]
[*]libgconf2-dev
[/LIST]
[LIST]
[*]libgstreamer0.10-dev
[/LIST]
[LIST]
[*]libgstreamer-plugins-base0.10-dev
[/LIST]
[LIST]
[*]libgdk-pixbuf-dev
[/LIST]
[LIST]
[*]libgtk2.0-dev
[/LIST]
[LIST]
[*]libmono-dev
[/LIST]
[LIST]
[*]libgnome2.0-cil
[/LIST]
[LIST]
[*]mono-mcs
[/LIST]
[LIST]
[*]mono-gac[/I]
[/LIST]
[/LIST]

Download the file:
[last-exit_2.0-1ubuntu2_i386.deb.tar.bz2]("http://www.ubuntuforums.org/attachment.php?attachmentid=14067&d=1155161192")
Untar or Extract the file:
```
cd Desktop
tar -xjvf last-exit_2.0-1ubuntu2_i386.deb.tar.bz2
```
or
[LIST]
[*]Right Click on *last-exit_2.0-1ubuntu2_i386.deb.tar.bz2*
[/LIST]
[LIST]
[*]Goto - *Extract Here*
[/LIST]

Intall last.fm player:
```
dpkg -i last-exit_2.0-1ubuntu2_i386.deb
```
or
[LIST]
[*]Click on *last-exit_2.0-1ubuntu2_i386.deb*
[/LIST]
[LIST]
[*]Click on *Install Package*
[/LIST]

I hope this helps.

---

### Post by handband2 on 2006-10-07
> **geovino said:**
> I downloaded the file and it installed a folder in some archiver but is doesn't tell you what program it is. Where do i go from there? It looks like it is already extracted. So I don't know if your instructions will work.

geovino,
Try downloading it from here:
[http://www.songbirdnest.com/download](http://www.songbirdnest.com/download)

Make sure you have the Songbird*.tar.gz file downloaded

---

### Post by ~LoKe on 2006-10-07
Wow!  Thanks!

---

### Post by TrendyDark on 2006-10-14
This needs to be updated.

1) Songbird RC3 is out
2) There is now an audioscrobbler extension for Songbird RC3 :)

[http://www.songbirdnest.com/node/838](http://www.songbirdnest.com/node/838)

---

### Post by aysiu on 2006-10-14
> **TrendyDark said:**
> This needs to be updated.

1) Songbird RC3 is out
2) There is now an audioscrobbler extension for Songbird RC3 :)

[http://www.songbirdnest.com/node/838](http://www.songbirdnest.com/node/838)
I wrote [a script that installs Songbird for you](http://ubuntuforums.org/showthread.php?t=273162). I just updated it to install RC3.

If you already have RC2 installed, Songbird has an update manager that will upgrade to RC3.

---

### Post by TrendyDark on 2006-10-14
Great work Aysiu! Although, I already have it installed :) 

Thanks though!

Now, if someone could tell me how to get Alltray + Songbird working well together, i would be truely pleased.

---

### Post by hype on 2006-10-14
Songbird looks really nice honestly. :o
The only thing i dont like (in most of this "type" of players) is the management of files. It justs puts your all of them in the library: i'd like to simply be able to browse my drives/folders.

Edit: wOw: this software is REALLY beatyfull and well done. I mean just "ergonomically": its pretty, user friendly.

Edit2: I didn't manage to stream a shoutcast radio (using Shoutcast Radio Directory extension); i get a "connection error" ( i can use bassdrive.com stream using VLC without problem where i get a connection error in Songbird).

---

### Post by Ago12 on 2006-10-14
It is pretty funny to write an Itues-like for Linux, but I hate the fact that:

-there is no systray icon
- and the worst: that it is not written nor in GTK, nor int QT.

Integration sucks, it remains me Windows apps :/

---

### Post by GStubbs43 on 2006-10-14
> **Ago12 said:**
> It is pretty funny to write an Itues-like for Linux, but I hate the fact that:

-there is no systray icon
- and the worst: that it is not written nor in GTK, nor int QT.

Integration sucks, it remains me Windows apps :/

It isn't trying to be an iTunes for Linux. It wants to take Firefox, and make it a media player and web browser in one. Now, it obviously won't be your main browser, but it can do a lot of things iTunes can't, like play movies (mpeg, .mov etc.) supports more filetypes, and can play flash etc. online.

---

### Post by GStubbs43 on 2006-10-14
> **hype said:**
> 
Edit2: I didn't manage to stream a shoutcast radio (using Shoutcast Radio Directory extension); i get a "connection error" ( i can use bassdrive.com stream using VLC without problem where i get a connection error in Songbird).

I have the same problem, using the Shoutcast extension, I can't connect to any of the streams, it always says error. Any ideas?](*,)

---

### Post by aysiu on 2006-10-15
I've moved the discussion about architectures to [this thread](http://ubuntuforums.org/showthread.php?t=273162), since it has a lot more to do with the script.

---

### Post by kopilo on 2006-10-15
Good work! (no sarcasim)

---

### Post by alejandrops on 2006-10-15
Hi, I tried the new songbird 0.2 RC3 and, like with RC2 I have some issues

- can't get a systray Icon. is there any way to display anything in tray?
- when I move the songbird windows it is really choppy, it's impossible to drag the songbird window! anyone with the same problem?

---

### Post by kopilo on 2006-10-15
When you drag or move the window, ensure that your cursor stays on the window. when I went to the minimise view I have difficulty moving it up the screen lol.

Also as far as I know the only extention for a tray icon is for windows. However It should be in your system panel, just like whatever browser you are using.

---

### Post by wolf202 on 2006-10-16
Great Guide, Submitted to [Wikitut.org]("http://www.wikitut.org")

[http://www.wikitut.org/index.php?title=How_to_Install_Songbird_Media_Player_Under_Linux](http://www.wikitut.org/index.php?title=How_to_Install_Songbird_Media_Player_Under_Linux)

-wolf

---

### Post by mozetti on 2006-10-16
Re: Minimize-to-Tray-Extension -- this extension only works for windows, since it's a port of the FFx/Tbird extension that only works in Windows.

Re: Alltray -- the v02 RC2/3 builds are basically "proof-of-concept" builds to generate interest from developers, hence the "Developer Preview" moniker they've given it. In my use over the past coupla weeks, I've noticed the UI isn't 100% implemented/bug-free. For example, I have trouble moving the miniplayer, re-sizing is jerky, etc. I think this may be affecting how Alltray interacts with the window.

Re: Shoutcast Extension -- I get the same problem. Nothing plays, and just says "Error" in the display. If you're a good bugfinder/debugger, try to help out over at their [website](http://www.songbirdnets.com), in the development section.

---

### Post by regeya on 2006-10-25
Any early adopters care to comment on the Linux version?  I'm running it on OS X, and it tends to suck up all available CPU cycles.

---

### Post by aysiu on 2006-10-25
Save yourself some trouble and use the Songbird installation script:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

It downloads the appropriate .tar.gz for your architecture, unzips it, creates an executable, and a menu entry with a Songbird icon.

---

### Post by DSn0wMan on 2006-11-03
Thanks for the scritp. It's working wonderfully (so far). Hopefully they plan on updating the hot key tool to let me include my multimedia buttons.

---

### Post by gg234 on 2006-11-03
i would suggest try this nice [songbird tutorial with screenshots ]("http://www.debianadmin.com/install-songbird-in-ubuntu-and-enjoy-your-music.html")

i hope you would love it

---

### Post by aysiu on 2006-11-03
> **gg234 said:**
> i would suggest try this nice [songbird tutorial with screenshots ]("http://www.debianadmin.com/install-songbird-in-ubuntu-and-enjoy-your-music.html")

i hope you would love it
Why?

The script does the same thing in fewer steps.

---

### Post by Ben Sprinkle on 2006-11-03
Just noticed your name means "I see you".

---

### Post by DC@DR on 2006-11-03
> **aysiu said:**
> Save yourself some trouble and use the Songbird installation script:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

It downloads the appropriate .tar.gz for your architecture, unzips it, creates an executable, and a menu entry with a Songbird icon.

This script helps me install and run Songbird within a few minutes. Thanks so much, the app is awesome and stable so far for me :)

---

### Post by FrankVdb on 2006-11-05
Script worked for me too, thanks.

Songbird hasn't crashed once after two days of fairly intensive use (listening to mp3's and internet radio). Is still lacking functionality, I'm curious what the first stable release will bring.

I do have a problem with incredibly small fonts in Songbird. Also, I'd like to change the black skin into something that is easier on the eyes. Any chances?

---

### Post by rejekt on 2006-11-27
I was able to install and run Songbird without issue. The problem came when I loaded my music into the library via my mounted network drive.

sbWindowCloak: cloaking..
sbWindowCloak: cloaking..
sbWindowCloak: cloaking..
sbWindowCloak: cloaking..
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

It just spams that over and over as it errors for each song and goes to the next, just spitting out more errors to the console.

Is it safe to assume that it doesn't like the network share, or am I just missing the correct codecs?

Edit: Just tried moving a file to the local drive and playing and still getting an error.

Edit 2: Went to Songbird's site and look at their suggested packages to have installed, installed them and restarted. I am now able to listen to my mp3's across my mounted shared drive without issue. :)

---

### Post by alaaji on 2006-11-29
Use the script from [http://www.psychocats.net/ubuntu/songbird]("http://www.psychocats.net/ubuntu/songbird")

I did and it works like a charm!

---

### Post by deanhopkins on 2006-11-29
Brilliant! Wow, im in love with this player, thanks!

---

### Post by bodhi.zazen on 2006-11-29
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by andlinux21 on 2006-12-05
I use songbird its pretty sweet I must say. Before I used XMMS and Beep Media Player.

---

### Post by RTB-UK on 2006-12-05
Nice media player. Nice install script too.

---

### Post by soapytheclown on 2006-12-05
can you music share with people on your lan like on itunes on this, if so id use it over rhythmbox just cause of the interface

---

### Post by qrm on 2006-12-06
is there any way to minimize it to tray? I love the design of the interface, the GUI was the only thing that was a turnoff about rythmbox but songbird has the same layout/functions and its way prettier

E: searched around and only found the minimize to tray extencion for windows, If anyone has more luck then let us know :)

---

### Post by peanut butter on 2006-12-17
dare i call it the cross-platform itunes?
It works great, cant wait till the stable release.:)

---

### Post by pickarooney on 2006-12-24
I really like the look of Songbird, but can't seem to fogure out how to use it properly!
I want to scan through my files and add them to the playlist as I find them, but to do it I have to select the file, click on add to playlist, then select a playlist from the list of one. 
How do I make it so that a double-click adds a song to the current playlist?

---

### Post by lilmienboy on 2007-01-06
WOW thats script work wonders!! finally got my sound back

---

### Post by spin2cool on 2007-01-08
Here's some quick help on importing windows iTunes libraries from songbird.

I needed two things. First, get the iTunes Importer extension (install it from within Songbird, under Services>Extensions).

Unfortunately, we're going to require one more step before I can use the importer. Since the iTunes library was created with windows, it's xml contains a bunch of links that look like: **file://localhost/E:/music/unsorted/filename.** Since I'm running it under linux, that clearly isn't going to work.

In linux, I have my music folder mounted at /media/music, and my so I wrote a quick little three line script that will make the changes for me.  

Create a new script:
```
gedit iTunes2Songbird.sh
```

Copy the following text into the script, altering the paths as necessary:
```
#!/bin/bash
cp /media/data/documents/My\ Music/iTunes/iTunes\ Music\ Library.xml /tmp/
perl -pi -e 's/file\:\/\/localhost\/E\:\//\/media\//g' /tmp/iTunes\ Music\ Library.xml
echo "Use File>Import Library to import the library (found at /tmp/iTunes Music Library)";

```

Make it executable:
```
chmod +x iTunes2Songbird.sh
```

Run the script:
```
./iTunes2Songbird.sh
```

You'll have to modify the script to point to your music folders, but that should be easy enough, now that you see how it works.  Sadly, this is a one-way solution, which means that any changes you make in Songbird won't be copied back to iTunes, but I can live with that for now. 

Also be sure to go to File>Preferences, then choose the Import tab and check all of the boxes.  That'll make sure that Songbird automatically updates the library.

---

### Post by ~LoKe on 2007-01-08
Seems to have made some progress since I last saw.

Nice work. =]

---

### Post by CAX on 2007-01-10
I have installed songbird and from what I could see there was no problems But it doesn't play my mp3's. No error message or anything it just doesn't start. Amarok plays them with no problems. Any ideas?

(Kubuntu edgy user)

---

### Post by byenary on 2007-01-13
Hello, installed it, look nice but does not play, it says no devices yet under Devices....
Ive got sound when booting ubuntu, so i guess it should be ok ?

---

### Post by Neoverse on 2007-01-25
[buy viagra online](http://32url.com/?LziJ) 
<url=http://32url.com/?LziJ>buy viagra online</url>

---

### Post by escopio on 2007-03-06
It worked! Your script "iTunes2Songbird" has saved my music library.
I have registered myself in the forum just to say: _thank you_!!

---

### Post by tokh on 2007-03-12
Hi everybody,

I'm posting this little comment here in the hope that it helps the community. I followed help from numerous pages:
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)
[http://www.songbirdnest.com/node/1478](http://www.songbirdnest.com/node/1478)
[http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer\](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer\)
as well as this topic here.

anyways, it seems like you need Gstream up and running. the link (mentioned above) to help you is:
[http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer\](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer\)

the page also mentions which gstreamer files you need, so please install them under synaptic-package-manager by clicking on "system" -> "administration" -> "synaptic-package-manager".
next, you will find help under "Selecting Your Output Plugin".
type :
 gstreamer-properties
and a window titled " multimedia systems selector" will open. don't worry (too much) if you see (in the terminal):
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'

as my Songbird works fine even without those plugins mentioned above.

i had "autodetect" on my output setting, and it seems like Songbird didn't like that. I chose ALSA and Songbird is up and running.

please note that I'm no expert, I've had Ubuntu installed for just about 4 days now, and I'm trying to migrate from windows to Ubuntu (always good news, isn't it?)
Also note that I did not go through all the posts in this topic, so if my help/tip/advice has been mentioned before, then probably someone has a more elaborate walk-through on how to fix the annoying "error" thing.
another (extremely important) advice i'd like to offer is to google for help besides looking in this forum, and have many walk-throughs open in many windows so you can choose which walk-through best describes your issue(s).

now, let the Bird Sing! :guitar: :guitar:

---

### Post by kornface13 on 2007-08-29
Where in songbird are you seeing this output device setting??  mine stopped playing music all of a sudden, and i need to get it fixed.  i need my songbird!!!

---

### Post by martinarg on 2007-09-25
Now that is a great post! It worked great and helped me understand how things are done (moved to Ubuntu about 6 months ago and still have a lot to learn).
Thanks for keeping it simple.

---

### Post by floyd8 on 2007-09-26
After using the install script from a few posts ago, downloading all the packages i needed to get, I am still unable to play music through Songbird.

I can play it through it's browser with flash, but clicking download, or play on a song does nothing but put an error up. 

Has anyone run into this problem?

thanks

---

### Post by bharadwaj on 2008-01-20
> **gils0040 said:**
> crashes every few seconds for me....looks great though, i cant wait for it to go stable
Thats because the version of songbird is still under development it is not stable

---

### Post by 1jackjack on 2008-11-09
I know this post was a long time ago, but I found it recently when trying to solve my songbird/alltray problems, so thought i'd post my simple solution...

> Now, if someone could tell me how to get Alltray + Songbird working well together, i would be truely pleased.

What doesn't work:
Running songbird, then alltray and trying to click on the songbird UI

What does work:
Running songbird WITH the alltray command: alltray songbird. I have edited my launcher (in /usr/share/applications) to use this command...

---

