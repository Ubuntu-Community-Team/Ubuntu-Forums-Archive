---
title: "Latest audacious media player"
date: 2006-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Hairy_Palms on 2006-06-23
Beep Media Player has discontinued development and audacious replaced it (bmpx sucks for now) they provide a repo but it doesnt work on breezy or dapper due to version problems, so this howto shows how to install audacious with the docklet plugin on dapper drake.

1. First get all its dependancies (most of these will be installed on a default ubuntu system)
```
sudo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libflac7 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgnutls12 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libsidplay1 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g
```

2, now install the fixed version of audacious, i dont know how long my webspace will hold up if this is popular but well see 
```
wget http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb
sudo dpkg -i audacious-1.1.2_1.1.2-1_i386.deb
```

now your done! 

**_Install the Tray Plugin_**

If you want the system tray plugin then follow the next part
either grab the .deb or compile from source, if you want to grab the .deb follow step 1 if you want to compile follow stesp 2
1 ```
wget http://four.fsphost.com/hairypalms19/audacious-docklet-0.1.1_0.1.1-1_i386.deb
sudo dpkg -i audacious-1.1.0_1.1.0-1_i386.deb
```

2, install some additional libraries
```
sudo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libbinio1c2 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libflac7 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgnutls12 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libresid-builder0c2a libsamplerate0 libsidplay1 libsidplay2 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g libglade2-dev libxxf86vm-dev libxml-parser-perl
```

3, second grap the audacious development packages
```
wget http://vdlinux.sourceforge.jp/dists/experimental/audacious/binary-i386/audacious-dev_1.1.0-0vd1_i386.deb
sudo dpkg -i audacious-dev_1.1.0-0vd1_i386.deb
```

4, grab the plugin and compile it
```
wget http://nedudu.hu/downloads/audacious-docklet-0.1.1.tar.bz2
tar -jxf audacious-docklet-0.1.1.tar.bz2
cd audacious-docklet-0.1.1/
./configure
make
make install
```



**_Set Global Hotkeys_**

* Run gconf-editor

* Go to "Apps->Metacity->Keybinding Commands"

Here we have a list of twelve slots for commands. We want one of them
(command_1, say) to Play/pause in audacious and another to skip to the next song (command_2)

you can see a list of audacious commands by typing audacious --help in a terminal


Double click the first and edit the key. In "Key Value", enter "audacious -t". 
Double click the second and edit the key. In "Key Value", enter "audacious -f".
Press OK.

Note that there is a bit of explanatory text at the bottom of the gconf-editor
screen.

We have our command, but now we must also tell Metacity what key to press to run it.
Go to "Global keybindings" (in the list to the left). As you see, there
are a lot of stuff to bind keys to. 
Scroll down until you find the line
"run_command_1"

* Select the line and double-click or select "Edit key". Change the key value
to "<Control>p". Press "Ok".

Scroll down until you find the line
"run_command_2"

* Select the line and double-click or select "Edit key". Change the key value
to "<Control>n". Press "Ok".

now ctrl-p and ctrl n should play/pause and skip to the next song no matter what program your looking at :)

You're done! 
now go grab a nice skin from [http://www.winamp.com/skins/](http://www.winamp.com/skins/) to celebrate!

---

### Post by Poka64 on 2006-07-12
I would like to have the dev packs for audacious :/
audacious-dev_1.0.0+1.1dr2-0vd2_i386.deb

---

### Post by BuffaloX on 2006-07-12
It's really cool with this guide/howto.

Will this enable "ape" playback from monkey audio?
Because then I'll definetely go for it. I miss my "ape":sad:
Oh btw must be 3.99 I think.

---

### Post by Hairy_Palms on 2006-07-12
@poka64 ive updated the links to point to the latest dev packs,
@buffaloX i have no idea, sorry id never even heard of .ape files before,
i found and old hoary howto by searching the forums,
[http://www.ubuntuforums.org/showthread.php?t=52785](http://www.ubuntuforums.org/showthread.php?t=52785)
but i dont know if it still works in dapper as ffar as i can find the plugin hasnt been updated for audacious.

---

### Post by Poka64 on 2006-07-13
Broke my docklet plugin :/

Failed to load plugin (/usr/lib/audacious/General/libdocklet.so): libaudacious.so: cannot open shared object file: No such file or directory

What should I do, all the other plugins work

---

### Post by XioNoX on 2006-07-13
[http://www.mikesplanet.net/?p=36](http://www.mikesplanet.net/?p=36)

dev:
[http://mikesplanet.net/dapper/audacious-dev_1.0.0+1.1dr2-1vd2~dapper1_i386.deb](http://mikesplanet.net/dapper/audacious-dev_1.0.0+1.1dr2-1vd2~dapper1_i386.deb)

---

### Post by Poka64 on 2006-07-13
XioNoX: thx for the "right" devpackage, now the docklet plugin works again :)

---

### Post by saracen on 2006-07-15
Version 1.1 was released on July 10th.  Does anyone have a .deb for this for dapper?

---

### Post by zenwhen on 2006-07-16
Thanks a lot for this howto.

---

### Post by Hairy_Palms on 2006-07-16
im going to try compiling version 1.1 later tonite. ill update if all goes well :)

---

### Post by hype on 2006-07-16
Good, the equaliser is working :D

I noticed a little bug when pressing on the tray icon to restore audacious, it displays the player, Eq and playlist at the same position, not the position when i minimized audacious.( i tested on Xgl)

 Other bug, related to Xgl too, when i click and hold audacious, the player goes "behin" other opened windows, not in front.

---

### Post by Hairy_Palms on 2006-07-18
i dont use XGL, works fine for me on normal Xorg though, im having a bit of trouble gettin the audioscrobbler to compile with te latest 1.1 audacious but i should be able to update later today. maybe that will fix the problem.

---

### Post by Hairy_Palms on 2006-07-18
Main Package Updated link here
[http://three.fsphost.com/mikemorley/audacious-1.1.0_1.1.0-1_i386.deb](http://three.fsphost.com/mikemorley/audacious-1.1.0_1.1.0-1_i386.deb)
the old docklet plugin still works for me 
please post if it doesnt for you

---

### Post by Jonnhy on 2006-07-19
The old docklet plugin not works for me :( 

My packages: audacious-1.1.0_1.1.0-1_i386.deb, audacious-docklet-0.1.1_0.1.1-1_i386.deb

---

### Post by Hairy_Palms on 2006-07-19
hmmm try fully uninstalling and reinstalling the docklet, then make sure youve got all 3 files in /usr/lib/audacious

/usr/lib/audacious/General/libdocklet.a
/usr/lib/audacious/General/libdocklet.la
/usr/lib/audacious/General/libdocklet.so

the docklet plugin source link on the website takes you to a hungarian page and i cant find where the source is anymore so i cant recompile.

---

### Post by dolby on 2006-07-29
for some reason even tho i just unistalled the [previous](http://www.ubuntuforums.org/showthread.php?t=195867&highlight=audacious) version i cant seem to be able to play flac files now. also noticed that your .deb is much small 1.5mb in compare with mikes which is 2.2mb

---

### Post by DJiNN on 2006-08-19
> **XioNoX said:**
> [http://www.mikesplanet.net/?p=36](http://www.mikesplanet.net/?p=36)

dev:
[http://mikesplanet.net/dapper/audacious-dev_1.0.0+1.1dr2-1vd2~dapper1_i386.deb]("http://mikesplanet.net/dapper/audacious-dev_1.0.0+1.1dr2-1vd2%7Edapper1_i386.deb")

Thanks for the links & the help.... i'm listening to "Audacious" now.... wicked.... !! :) Now i'm off to get me some skins. 

DJiNN

---

### Post by redgilda on 2006-08-27
> **Hairy_Palms said:**
> hmmm try fully uninstalling and reinstalling the docklet, then make sure youve got all 3 files in /usr/lib/audacious

/usr/lib/audacious/General/libdocklet.a
/usr/lib/audacious/General/libdocklet.la
/usr/lib/audacious/General/libdocklet.so

hey there :) I've got a problem with the docklet plugin.. it doesn't show up in the Plugins section in the preferences... Ive got all the 3 files mentioned above in the correct place...

any ideas?

---

### Post by redgilda on 2006-08-27
ok i uninstalled everything and installed again from Mike's packages:
[http://www.mikesplanet.net/?p=36](http://www.mikesplanet.net/?p=36)

But yeah, the docklet didn't meet my expectations :p I was hoping that the player will disappear from the taskbar - keeping the main window on desktop and the icon in tray... alas the damn taskbar thingy stays :/

---

### Post by squirrelpimp on 2006-08-29
as the .debs in this repo(deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious) don't work, i recompiled them for dapper, so if anyone is interested in audacious-1.1.2 i can upload the deb.

cheers, lars

edit: here it is: [http://www.stud.uni-karlsruhe.de/~ulbhe/deb/audacious_1.1.2-0vd2_i386.deb](http://www.stud.uni-karlsruhe.de/~ulbhe/deb/audacious_1.1.2-0vd2_i386.deb)

---

### Post by Hairy_Palms on 2006-08-29
the player does dissappear from the taskbar, to make it dissappear you just click on the docklet icon rather than using minimise

---

### Post by wbc1228 on 2006-08-29
> **squirrelpimp said:**
> as the .debs in this repo(deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious) don't work, i recompiled them for dapper, so if anyone is interested in audacious-1.1.2 i can upload the deb.

cheers, lars

edit: here it is: [http://www.stud.uni-karlsruhe.de/~ulbhe/deb/audacious_1.1.2-0vd2_i386.deb](http://www.stud.uni-karlsruhe.de/~ulbhe/deb/audacious_1.1.2-0vd2_i386.deb)

the link works, but the file doesn't.
When I tried to installed it, I get the error "Could not open audacious_1.1.2-0vd2_i386.deb.  This package might be corrupted or you are not allowed to open the file".
I checked the permissions and that wasn't the problem, so I'm guessing it is corrupted?!?
or did I do something wrong?
anyone else having this issue?

also, does anyone have version 1.0 of audacious?
the version I'm using right now (1.0.0+1.1dr2-1vd2 from Mike's Planet website, not sure about the funky revision number, but that is what synaptic is telling me) isn't displaying unicode id3 tags correctly.

---

### Post by Hairy_Palms on 2006-08-30
ive got a package of the latest version 1.1.2 ill upload it for you all
[http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb](http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb)

---

### Post by wbc1228 on 2006-08-30
> **Hairy_Palms said:**
> ive got a package of the latest version 1.1.2 ill upload it for you all
[http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb](http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb)
the docklet plugin is still available at 
[http://three.fsphost.com/mikemorley/audacious-docklet-0.1.1_0.1.1-1_i386.deb](http://three.fsphost.com/mikemorley/audacious-docklet-0.1.1_0.1.1-1_i386.deb)


thanks Hairy_Palms!
it is working great!

---

### Post by bur[n]er on 2006-08-31
Can someone repost the docklet .deb?  Version 1.1.2 is working great from the lastest post.

---

### Post by Hairy_Palms on 2006-08-31
kk here it is
[http://four.fsphost.com/hairypalms19/audacious-docklet-0.1.1_0.1.1-1_i386.deb](http://four.fsphost.com/hairypalms19/audacious-docklet-0.1.1_0.1.1-1_i386.deb)
ive updated the first post with the latest versions too

---

### Post by squirrelpimp on 2006-08-31
@all: somehow the .deb seemed to got broken on the way to the server. The copy i have here still works. However i'm glad that there's a working version now and apologize for the trouble.

cheers, lars

---

### Post by Hairy_Palms on 2006-09-01
what was broken the docklet or the player?
what exactly was broken about it?
both work fine here.

---

### Post by squirrelpimp on 2006-09-01
i uploaded a deb of audacious which somehow got damaged on the way to the server (md5 mismatch). I now uploaded it again and it should be working, although it doesn't seem to be needed anymore:)

[http://www.stud.uni-karlsruhe.de/~ulbhe/deb/audacious_1.1.2-0vd2_i386.deb](http://www.stud.uni-karlsruhe.de/~ulbhe/deb/audacious_1.1.2-0vd2_i386.deb)

cheers, lars

---

### Post by jamesford on 2006-09-03
any chance of an amd64 build ?

---

### Post by Hairy_Palms on 2006-09-03
i dont have an amd64 computer so i cant. but the source should compile cleanly if you install the things from the first post i think.

---

### Post by jamesford on 2006-09-03
ive tried but not had any luck :(
checking for libglade-2.0 >= 2.3.1... configure: error: Cannot find libglade

altho libglade2-0 2.5.1 Is installed

---

### Post by Hairy_Palms on 2006-09-03
install libglade2-dev from synaptic, if it says you havent got it then u need the development packages.

---

### Post by jamesford on 2006-09-03
thanks, did the trick :D

edit:actually iyt keeps crashing after a shgort while:
Received SIGSEGV

This could be a bug in Audacious. If you don't know why this happened, file a bug at [http://bugs.nenolod.net/](http://bugs.nenolod.net/)

Aborted

---

### Post by Hairy_Palms on 2006-09-03
if u run audacious from a terminal does it give any more messages about the crash?

---

### Post by jamesford on 2006-09-04
no, that output was from terminal

---

### Post by Hairy_Palms on 2006-09-04
ah ok then, then congrats i think youve found a bug :)

---

### Post by krul on 2006-09-04
The link to the package doesn't work anymore....did you (rem)moved the package?

---

### Post by Hairy_Palms on 2006-09-04
? still works for me 
[http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb](http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb)

---

### Post by krul on 2006-09-04
In console with wget I get a 404.php, but within a browser it works. Strange, but no problem anymore.

---

### Post by tkiesel on 2006-09-04
Thanks to everyone for this thread. Audacious has been a joy to use. BMP has odd minimize-restore issues and both BMP and XMMS would lock up after trying to play dead streams. Gotta love finding 30+ instances of xmms in the System Monitor, some of them more than two weeks old.

One thing I've been knocking my head against is trying to get the xmms-crossfade plugin to work in Audacious.

On [this thread at the Audacious forums]("http://boards.nenolod.net/index.php?showtopic=109") there's much fanfare about the latest version of XMMS Crossfade having support for Audacious. So I went to the [XMMS Crossfade site]("http://www.eisenlohr.org/xmms-crossfade/news.html") and have been messing around with getting the blasted thing to compile for Audacious.

Using the INSTALL file and the [README for the 0.3.11 release]("http://www.eisenlohr.org/xmms-crossfade/readme-0.3.11") on the site, I've tried a few things.

```
./configure --enable-player=audacious
```

doesn't seem to do a whole lot of good. The make command will give a host of errors. When running ./configure, the script reports that player configuration will be donw with pkg-config. I think the problem is due to 'pkg-cofig audacious' not giving the make script the information it wants. pkg-config doesn't seem to even realize that audacious is installed on my system.

If I don't instruct ./configure to specifically compile for audacious, however.... ```
./configure --libdir /usr/lib/audacious/Output
```

The problem becomes the fact that Audacious won't recognize and offer the option of selecting crossfade as an output plugin.

More developments might occur [here]("http://boards.nenolod.net/index.php?showtopic=109").

I'd love to see Audacious make it into Edgy! I'm in love with the stability and simplicity of the program compared to all alternatives I've tried.

Much love,
-T

---

### Post by tkiesel on 2006-09-04
UPDATE:

After getting the audacious-dev package mentioned in [this post by Hairy_Palms]("http://www.ubuntuforums.org/showpost.php?p=938640&postcount=1") I was able to compile the XMMS Crossfade plugin with relative ease.

Thanks to Stany from the [Audacious Boards]("http://boards.nenolod.net/index.php?") for all the help.

These are the steps I used:

(First, you probably want to make sure you've installed build-essential and checkinstall as well as audacious-dev as mentioned above.)

```
Applications --> Accessories --> Terminal
wget http://www.eisenlohr.org/xmms-crossfade/xmms-crossfade-0.3.11.tar.gz
tar -xzvf xmms-crossfade-0.3.11.tar.gz
cd xmms-crossfade-0.3.11
./configure --enable-player=audacious
make
sudo checkinstall
```

I decided to go the checkinstall route after compiling so I can keep an eye on the package with Synaptic/apt.  In checkinstall I renamed the package audacious-crossfade before beginning the install to make sure I don't forget it.

One little snag with the checkinstall that might catch someone: It failed out the first time because it was trying to write docs to the same directory that Dapper's xmms-crossfade package uses. To clear that issue, I ununstalled xmms-crossfade, since I've got no plans to continue using XMMS.

---

### Post by Hairy_Palms on 2006-09-04
nice, i didnt know that the crossfade plugin had audacious support nowadays :)

---

### Post by tkiesel on 2006-09-09
Realistically speaking: Is there a chance at all that Audacious will make it into Edgy?

If it doesn't, can we pull together as fans of the software and maintain it for the backports repo or something? I think (emphasis on think) I could learn to fully repackage xmms-crossfade as audacious-crossfade.

---

### Post by Hairy_Palms on 2006-09-09
i dunno, i think theyve stopped taking requests for edgy now, i dont know how to make package though, the audacious ones here are done with checkinstall.

---

### Post by Fyrzen_ on 2006-09-17
I used to use this during Dapper beta, but right now I'm having doubts.
Does audacious have plug-ins to play musepack(.mpc) and FLAC files? If not, is it compatible with bmp plug-ins?

---

### Post by Myrtti on 2006-09-20
Am I missing out something or isn't there really an audioscrobbler plugin in audacious?

---

### Post by saracen on 2006-09-21
Would someone throw up a deb for the latest release?  [Audacious 1.2.0-rc1 and Audacious-Plugins 1.2.0 released.]("http://audacious.nenolod.net/Main_Page")

---

### Post by saracen on 2006-09-21
I tried to do it myself using checkinstall but none of the audio output plugins show up in the application.  It doesn't play any files...

---

### Post by Myrtti on 2006-09-23
I bumped into a site with all, plugins, docklet and the player using google to search for Audacious Ubuntu. The Last.fm-plugin seems to work too :-D

---

### Post by saracen on 2006-09-24
Do you want to share the link?

---

### Post by Carcass on 2006-09-30
scuse me but this line seems not work 

> deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious

how I can install it??? I must install single .deb to have this program???

What are the .deb need???

Thanks :neutral:

---

### Post by Hairy_Palms on 2006-10-02
sorry i havent been keeping this updated, i recently moved house and dont have internet yet, when i do, ill make a package of the latest version asap

till then it looks like the old links still work

[http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb](http://four.fsphost.com/hairypalms19/audacious-1.1.2_1.1.2-1_i386.deb)
[http://four.fsphost.com/hairypalms19/audacious-docklet-0.1.1_0.1.1-1_i386.deb](http://four.fsphost.com/hairypalms19/audacious-docklet-0.1.1_0.1.1-1_i386.deb)

---

### Post by Mindphaser on 2006-10-09
Hello everybody ^^
If anyone is interested, i made packages of Audacious 1.2.0-rc1 and a current xchat-xsys plugin for the IRC ppl, you can get them here:

[http://darkchamber.homeip.net/debs/](http://darkchamber.homeip.net/debs/)

I built them under Edgy, dont know if they work with dapper. Also i didn't included all plugins (just those i need and those which doesn't need extra deps), if you're missing something just tell me.

greets
Mindo

---

### Post by 3dxtrip on 2006-10-09
Thanks

I will try with your deb's files

---

### Post by bur[n]er on 2006-10-09
The debs two posts up work and play all kinds of formats, but no docklet :(

Anyone have the systray icon (aka docklet) deb?

---

### Post by Mindphaser on 2006-10-10
> **'bur[n]er said:**
> The debs two posts up work and play all kinds of formats, but no docklet :(

Anyone have the systray icon (aka docklet) deb?

Thanx for your feedback !
You can download the docklet plugin now from my server ;)

---

### Post by Dale Cooper on 2006-10-10
@ Mindphaser :
here is a big THANK YOU! =D>

---

### Post by 3dxtrip on 2006-10-15
New version of Plugins Released
1.2.1

I compiled a Deb file:
[http://d.turboupload.com/d/1086010/audacious-plugins_1.2.1-1_i386.deb.html](http://d.turboupload.com/d/1086010/audacious-plugins_1.2.1-1_i386.deb.html)

Size:
782.5 Kib (801278 bytes)

---

### Post by Mindphaser on 2006-10-15
@3dxtrip: nice work, if you would include the last.fm plugin I would use it :)

@all: Also Audacious 1.2.0-rc3 is out, with stuff like freeform-skinning and the usual bugfixes. Package is so fresh its HOT ](*,) 

You can get it here (again) : [http://darkchamber.homeip.net/debs/](http://darkchamber.homeip.net/debs/)

---

### Post by phanki on 2006-10-17
A big thank for this, mindphaser!
Finally i have audacious back on my system. The sound is gorgeous :)
Btw, someone know a song-announcer-script for xchat that works with this version of audacious?
thx & greetz

---

### Post by Mindphaser on 2006-10-18
@phanki: check out the xchat-xsys package on my server, use the command /NP inside xchat to let the people know what youre listen to.
I know there is also a xchat-xsys package on universe, but that package isnt built with support for audacious (otherwise audacious would be a depend of xchat-xsys and that wouldnt be wise for a universe package).

---

### Post by 3dxtrip on 2006-10-18
Thanks for the installer

I'm beginner in Ubuntu, i don't know how compile the plugins with LAST.FM feature

sorry ^^!

---

### Post by Perfect Storm on 2006-10-18
Can you add the output of the ./configure of the plugins?

---

### Post by Mindphaser on 2006-10-18
@3dxtrip: You need to have libcurl-dev installed to build last.fm plugin (enabled by default if libcurl-dev is present). I am not very sure about this , but a look into configure.ac helps for those kind of stuff.

greets
MP

---

### Post by hikaricore on 2006-10-19
Mindphaser, since you're using edgy I can't use your newly build packages.  I'm sure they work fine, but not on dapper :)

Even using force-all option on dpkg and cleaning up the package info manually for my system audacious still dies a horrible command line death.  hehe

I'll just stick with the old builds until I get unlazy and compile myself.

---

### Post by EisenPM on 2006-10-23
This might be off topic, but since I prefer audacious over xmms and bmp, I'll ask anyway...

When opening several mp3s at once in nautilus, they are not all added to the playlist. same with xmms and bmp.

interestingly, amarok does the correct behavior. any ideas on that?

and thanks for the great packages!

---

### Post by Hairy_Palms on 2006-10-30
sorry for the horribly long wait, ive compiled te latest audacious and plugins on dapper, here they are.
im afraid i havent got edgy yet, im without internet at home for the moment, and setting up edgy without internet aint really an option :(

anyway here are the _DAPPER_ Packages

[http://four.fsphost.com/hairy/audacious-1.2.1_1.2.1-1_i386.deb](http://four.fsphost.com/hairy/audacious-1.2.1_1.2.1-1_i386.deb)
[http://four.fsphost.com/hairy/audacious-plugins-1.2.2_1.2.2-1_i386.deb](http://four.fsphost.com/hairy/audacious-plugins-1.2.2_1.2.2-1_i386.deb)

---

### Post by Rob2687 on 2006-10-30
Here's my Edgy packages build from SVN  Oct 30, 2006. Provided as is. I take no responsibility if these bring about the apocalypse. ;)

Audacious
[http://www.badongo.com/file/1630599](http://www.badongo.com/file/1630599)

Plugins
[http://www.badongo.com/file/1630600](http://www.badongo.com/file/1630600)

---

### Post by Mindphaser on 2006-10-30
And packages of the latest official versions of audacious and its plugins are on my server ([http://darkchamber.homeip.net/debs](http://darkchamber.homeip.net/debs))

:)

---

### Post by Merit on 2006-11-05
Thanks a lot Mindphaser for the debs ! I was looking after it on the net and found this topic. I will no more use BmpX since it doesn't use winamp skin for now. Audacious seems perfect for my needs.

---

### Post by ocdude on 2006-11-05
I have no idea what's going on here, but I just compiled the latest on Edgy, and some of my mp3s sound like they are possessed (IE, they play slower than they should).  What's going on here?  I have toolame, the gstreamer-lame package, and yet these mp3s don't play well. XMMS plays them with no problem. What gives? ](*,)

---

### Post by Hairy_Palms on 2006-11-05
you need the mpg123 package and the lame package itself installed, other than that make sure the mpeg plugin is there in audacious preferances

---

### Post by BigDXLT on 2006-11-06
Could someone please mirror Hairy's Dapper .debs?  My dialup connection seems to not like holding a connection to his server.  wget tells me 
"20 redirections exceeded"
and Firefox only downloads a small part of the file and tries to pass it off to me as being complete!

However I was able to download Mindphazers edgy builds (only tried through firefox), though they don't work for me.  (And in case you can't tell, I'm quite new to the whole Ubuntu experience so there may be other forces at work conspiring against me at the moment!)

Thanks!

---

### Post by Vich on 2006-11-08
Has anyone got this working with ALSA, I need it for my digital speakers. In bmp I had an ALSA output plugin, but it didn't work with Audacious (caused it to crash.)

Edit: fixed by downloading and installing Mindphaser's packages (particularly the plugins package). Thanks a lot Mindphaser!

---

### Post by shm on 2006-11-08
deb packages audacious 1.2.1 for dupper (without pulse output plugin)

audacious_1.2.1-0vd1_i386.deb
audacious-common_1.2.1-0vd1_all.deb
audacious-locales_1.2.1-0vd1_all.deb
audacious-plugins_1.2.2-0vd1_i386.deb
audacious-plugins-extra_1.2.2-0vd1_i386.deb
audacious-plugins-extra-console_1.2.2-0vd1_i386.deb
libaudacious4_1.2.1-0vd1_i386.deb
libaudacious-dev_1.2.1-0vd1_i386.deb


[ftp://80.86.249.14/audacious/1.2.1-dapper]("ftp://80.86.249.14/audacious/1.2.1-dapper")
build from sources using this repos
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious-plugins

installation:
download all files in to some dir
and then run sudo dpkg -i *.deb

P.S. crossfade plugin works only through oss :(

---

### Post by darknightuk on 2006-11-10
how do i enable mp3 playback i've installed Mindphaser's packages, no mpg/3 plugin is listed in plugins but i belive i have all correct plugins installed?

---

### Post by Hairy_Palms on 2006-11-15
BigDXLT, im not sure why but my mirror doesnt work with wget, but if you download from a browser it will. :)

---

### Post by BigDXLT on 2006-11-16
Yeah, even that doesn't work for me.  Even tried through Internet Exploder on my windows machine and nuthin'.  The download will start, seem to be going, then end prematurely, leaving me with a corrupted file only a couple bytes in size.  (A few other downloads have done this on me in the past too... but usually one of my machines will get the file I'm looking for!)  Pretty sure it has to do with my dreadful dialup connection.  

I've also tried shm's version, which downloads fine it seems.  When I go to install the packages, I find that the libasound2 package in the repositories isn't quite up-to-date enough for his copy of audacious.  
```
audacious-plugins depends on libasound2 (>> 1.0.11); however:
  Version of libasound2 on system is 1.0.10-2ubuntu4.
```  <-- Synaptic tells me mine is right up to date, though apparently there is something newer out there!  Advice as to my best route of action?

BTW, in the event that I do find that updated libabsound2, could I ask what those plugin-extra and such bring to the table?  I'm basically looking to simulate my old winamp (2.81) experience, which other than a couple of skins was pretty near default, maybe a bit of tweaking in the equalizer, but nothing more really!

---

### Post by Dale Cooper on 2006-11-17
@ Mindphaser : I'm still using your excellent debs. I got a request though... :) Correct me if I'm wrong but it seems that your packages are not compiled with support for ESD. Can you please do so? I've just discovered the joys of ESD + TCP and I'd like to use Audacious with it.
Thank you for the help you could bring me/us ;)

---

### Post by Hairy_Palms on 2006-11-17
there are some mirrors put up by fly 5 for my packages if anyone has trouble with the original,
here are links for the player
[http://fly5.pp.fi/ubuntu/audacious-1.2.1_1.2.1-1_i386.deb](http://fly5.pp.fi/ubuntu/audacious-1.2.1_1.2.1-1_i386.deb)
[http://koti.mbnet.fi/fly5/audacious/audacious_1.2.1-1_i386.deb](http://koti.mbnet.fi/fly5/audacious/audacious_1.2.1-1_i386.deb)
[http://www.saunalahti.fi/fly5/audacious/audacious_1.2.1-1_i386.deb](http://www.saunalahti.fi/fly5/audacious/audacious_1.2.1-1_i386.deb)

and the plugin packages

[http://www.saunalahti.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb](http://www.saunalahti.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb)
[http://fly5.pp.fi/ubuntu/audacious-plugins_1.2.2-1_i386.deb](http://fly5.pp.fi/ubuntu/audacious-plugins_1.2.2-1_i386.deb)
[http://koti.mbnet.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb](http://koti.mbnet.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb)

BIG thank you to fly5 for hosting them,

---

### Post by pooslinger on 2006-11-18
> **ocdude said:**
> I have no idea what's going on here, but I just compiled the latest on Edgy, and some of my mp3s sound like they are possessed (IE, they play slower than they should).  What's going on here?  I have toolame, the gstreamer-lame package, and yet these mp3s don't play well. XMMS plays them with no problem. What gives? ](*,)

I'm having the same problem with certain mp3s.  Everything else plays perfectly.

1.Audacious takes the song from 44.1KHz -> 32KHz or 12KHz and slows it down or 48KHz and speeds it up.
2.Song begins with audible skip/squelch sound.
3.Seek/playback bar stops at ~10 seconds while it keeps playing and time elapses from display.

I have tried debs from this thread and compiled it myself with the same results.

---

### Post by nenolod on 2006-11-20
> **pooslinger said:**
> I'm having the same problem with certain mp3s.  Everything else plays perfectly.

1.Audacious takes the song from 44.1KHz -> 32KHz or 12KHz and slows it down or 48KHz and speeds it up.
2.Song begins with audible skip/squelch sound.
3.Seek/playback bar stops at ~10 seconds while it keeps playing and time elapses from display.

I have tried debs from this thread and compiled it myself with the same results.

Your MP3s are encoded with the wrong emphasis bit set. You can use LAME or mp3check to fix this, most likely. mpg123 ignores the emphasis bit (which is wrong, and causes files that they won't handle properly, too).

Anyway, if you fix the emphasis bit, or reencode, things will properly work.  I am going to assume these files came off of Gnutella. :-P

Also, this forum has a white background on white text if you are using an inverse GTK theme in Mozilla. This is not very usable.

--nenolod

---

### Post by ravemjr on 2006-11-20
> **BigDXLT said:**
> I've also tried shm's version, which downloads fine it seems.  When I go to install the packages, I find that the libasound2 package in the repositories isn't quite up-to-date enough for his copy of audacious.  
```
audacious-plugins depends on libasound2 (>> 1.0.11); however:
  Version of libasound2 on system is 1.0.10-2ubuntu4.
```  <-- Synaptic tells me mine is right up to date, though apparently there is something newer out there!  Advice as to my best route of action?

BTW, in the event that I do find that updated libabsound2, could I ask what those plugin-extra and such bring to the table?  I'm basically looking to simulate my old winamp (2.81) experience, which other than a couple of skins was pretty near default, maybe a bit of tweaking in the equalizer, but nothing more really!

I have the exact same problem...I thought it would've been due to using enlightenment, but after I switched back to Gnome, everything was still the same: older version installed.

I tried looking up for the packages on the ubuntu package directory, but for dapper the version is older...shall I try the versions for edgy or others?

---

### Post by pooslinger on 2006-11-21
> **nenolod said:**
> Your MP3s are encoded with the wrong emphasis bit set. You can use LAME or mp3check to fix this, most likely. mpg123 ignores the emphasis bit (which is wrong, and causes files that they won't handle properly, too).

Anyway, if you fix the emphasis bit, or reencode, things will properly work.  I am going to assume these files came off of Gnutella. :-P

Also, this forum has a white background on white text if you are using an inverse GTK theme in Mozilla. This is not very usable.

--nenolod

mp3check fixed them.  There was junk before the first frame.

Actually I backed up all my CD's to DVD.  I used the same program and version of LAME.  One CD I backed up is fine while others have this junk-header problem.

I don't know what you mean by GTK themes in Mozilla...

---

### Post by 3dxtrip on 2006-11-23
> Audacious-Plugins 1.2.4 has been released to fix a bug in the wavpack plugin when not using Wavpack SVN.

Update: There was a problem with the Wavpack fix in 1.2.4, so we have released 1.2.5 with a fixed fix.

I compiled the source code, for Edgy i386 arquitecture
[http://d.turboupload.com/d/1243337/audacious-plugins_1.2.5-1_i386.deb.html](http://d.turboupload.com/d/1243337/audacious-plugins_1.2.5-1_i386.deb.html)

---

### Post by nenolod on 2006-11-23
By the way, Adam Cecile has packaged Audacious in Debian, which means that Audacious 1.2 will enter Etch. This means that sometime in the next month or so, Audacious will probably wind up in mainstream ubuntu. 

This will make things easier for you and us (as upstream). Celebrate. ;)

--nenolod

---

### Post by Camino on 2006-11-24
Hi,
found a nice link with a working version for Dapper:

[http://diuf.unifr.ch/pai/people/broccoa/linux.php](http://diuf.unifr.ch/pai/people/broccoa/linux.php)

Installed them correctly without any issues...

This is version 1.2.1 with all related plugins to get this one working perfectly

Regards

---

### Post by ravemjr on 2006-11-24
Lol...right after I upgrade to Edgy.
Anyway, my audacious still doesnt read mp3's after I installed the plugins, and the mpg123 plugin doesnt appear on the plugin list...

EDIT: I can't seem to get Hairy Palms' debs to work...
> **Hairy_Palms said:**
> there are some mirrors put up by fly 5 for my packages if anyone has trouble with the original,
here are links for the player
[http://fly5.pp.fi/ubuntu/audacious-1.2.1_1.2.1-1_i386.deb](http://fly5.pp.fi/ubuntu/audacious-1.2.1_1.2.1-1_i386.deb)
[http://koti.mbnet.fi/fly5/audacious/audacious_1.2.1-1_i386.deb](http://koti.mbnet.fi/fly5/audacious/audacious_1.2.1-1_i386.deb)
[http://www.saunalahti.fi/fly5/audacious/audacious_1.2.1-1_i386.deb](http://www.saunalahti.fi/fly5/audacious/audacious_1.2.1-1_i386.deb)

and the plugin packages

[http://www.saunalahti.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb](http://www.saunalahti.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb)
[http://fly5.pp.fi/ubuntu/audacious-plugins_1.2.2-1_i386.deb](http://fly5.pp.fi/ubuntu/audacious-plugins_1.2.2-1_i386.deb)
[http://koti.mbnet.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb](http://koti.mbnet.fi/fly5/audacious/audacious-plugins_1.2.2-1_i386.deb)

BIG thank you to fly5 for hosting them,

I've decided to reinstall the player AND the plugins...but now audacious doesnt show any plugins on its list...

---

### Post by BigDXLT on 2006-11-27
Excellent!  Both Camino's link and Hairy Palm's mirror downloaded perfectly and working great!  And no hoops to jump through either!  :D  Much thanks guys!

---

### Post by wilberfan on 2006-11-27
Why would I have (apparently) all the plugins EXCEPT the one(s) that handle .ogg and .flac files??   Is there an easy way to remedy this?

---

### Post by wilberfan on 2006-11-27
> **wilberfan said:**
> Why would I have (apparently) all the plugins EXCEPT the one(s) that handle .ogg and .flac files??   Is there an easy way to remedy this?

I think those plugins might be missing from 3dxtrip's package??  [http://www.ubuntuforums.org/showpost.php?p=1796886&postcount=86](http://www.ubuntuforums.org/showpost.php?p=1796886&postcount=86)

?

When I installed a DIFFERENT package (1.2.2-1) everything was fine (after I deleted something from the plugin library...)

---

### Post by mustang on 2006-11-27
> **Camino said:**
> Hi,
found a nice link with a working version for Dapper:

[http://diuf.unifr.ch/pai/people/broccoa/linux.php](http://diuf.unifr.ch/pai/people/broccoa/linux.php)

Installed them correctly without any issues...

This is version 1.2.1 with all related plugins to get this one working perfectly

Regards

Thanks a lot! All packages worked great. BMP has been unstable lately (freezes every once in awhile when opening a file).

Going to give audacious a try. Thanks again!

---

### Post by Hairy_Palms on 2006-12-02
if you want audacious to support ogg in my packages, you have to install the vorbis-tools package IIRC, and my packages should now work on edgy too

---

### Post by nenolod on 2006-12-09
I'd just like to say that we ship our own Ubuntu packages now. See [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads).

See ya.

---

### Post by zivagolee on 2006-12-10
> **nenolod said:**
> I'd just like to say that we ship our own Ubuntu packages now. See [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads).

See ya.

Can we get the tray plugin included in the plugins package?

---

### Post by BuffaloX on 2007-01-09
Anyone else have problems with flac in the new alpha 2 release?

---

### Post by 3dxtrip on 2007-02-10
Hi!

I uploaded deb packages for Audacious 1.3-alpha4

You must uninstall previous versions because the new installation is in /usr/local/bin instead of /usr/bin.

Audacious
[http://rapidshare.com/files/15865334/audacious-1.3.0_alpha4-1_i386.deb.html](http://rapidshare.com/files/15865334/audacious-1.3.0_alpha4-1_i386.deb.html)

Audacious Plugins
[http://rapidshare.com/files/15865720/audacious-plugins-1.3.0_alpha4-1_i386.deb.html](http://rapidshare.com/files/15865720/audacious-plugins-1.3.0_alpha4-1_i386.deb.html)

WARNING
> milkycow wrote:
Ogg Vorbis playback crashes Audacious in alpha 4. The player gives a Received SIGSEGV as soon as an ogg file gets loaded. 
This has been fixed in SVN, and will be released in alpha5 in a week or two.


If you want play OGG files, don't install this packages, this bug will fix in a week or two.

Sorry for my english, no se hablarlo (ni escribirlo) bien ^^!

---

### Post by bluebyt on 2007-02-13
> **3dxtrip said:**
> Hi!

I uploaded deb packages for Audacious 1.3-alpha4

You must uninstall previous versions because the new installation is in /usr/local/bin instead of /usr/bin.

Audacious
[http://rapidshare.com/files/15865334/audacious-1.3.0_alpha4-1_i386.deb.html](http://rapidshare.com/files/15865334/audacious-1.3.0_alpha4-1_i386.deb.html)

Audacious Plugins
[http://rapidshare.com/files/15865720/audacious-plugins-1.3.0_alpha4-1_i386.deb.html](http://rapidshare.com/files/15865720/audacious-plugins-1.3.0_alpha4-1_i386.deb.html)

WARNING


If you want play OGG files, don't install this packages, this bug will fix in a week or two.

Sorry for my english, no se hablarlo (ni escribirlo) bien ^^!

Thanks 3dxtrip this is working great! now audacious have a Status Icon plugin!

---

### Post by 3dxtrip on 2007-02-18
Audacious 1.3.0 Alpha 5
[http://rapidshare.com/files/17161182/audacious-1.3.0_alpha5-1_i386.deb.html](http://rapidshare.com/files/17161182/audacious-1.3.0_alpha5-1_i386.deb.html)

Audacious Plugins 1.3.0 Alpha 5
[http://rapidshare.com/files/17161277/audacious-plugins-1.3.0_alpha5-1_i386.deb.html](http://rapidshare.com/files/17161277/audacious-plugins-1.3.0_alpha5-1_i386.deb.html)

---

### Post by 3dxtrip on 2007-03-03
Build with Checkinstall for i386

Audacious 1.3.0
[http://rapidshare.com/files/19298849/audacious_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19298849/audacious_1.3.0-1_i386.deb.html)

Audacious Plugins 1.3.0 (Necesarios para que funcione Audacious)
[http://rapidshare.com/files/19299162/audacious-plugins_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19299162/audacious-plugins_1.3.0-1_i386.deb.html)

Audacious Plugins Ugly 1.3.0
[http://rapidshare.com/files/19299198/audacious-plugins-ugly_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19299198/audacious-plugins-ugly_1.3.0-1_i386.deb.html)

:guitar:

---

### Post by Hairy_Palms on 2007-03-04
youll also need mcs, or audacious will fail to start :)
[http://four.fsphost.com/hairypalms19/mcs_0.4.1-1_i386.deb](http://four.fsphost.com/hairypalms19/mcs_0.4.1-1_i386.deb)

also, has anyone managed to get the docklet plugin working with 1.3.0?

---

### Post by romprod on 2007-03-04
> **3dxtrip said:**
> Build with Checkinstall for i386

Audacious 1.3.0
[http://rapidshare.com/files/19298849/audacious_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19298849/audacious_1.3.0-1_i386.deb.html)

Audacious Plugins 1.3.0 (Necesarios para que funcione Audacious)
[http://rapidshare.com/files/19299162/audacious-plugins_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19299162/audacious-plugins_1.3.0-1_i386.deb.html)

Audacious Plugins Ugly 1.3.0
[http://rapidshare.com/files/19299198/audacious-plugins-ugly_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19299198/audacious-plugins-ugly_1.3.0-1_i386.deb.html)

:guitar:

Your sir are a saviour!

been pulling my hair out with this for quite a while now. Thanks!

---

### Post by romprod on 2007-03-04
Ignore

---

### Post by 3dxtrip on 2007-03-04
> **Hairy_Palms said:**
> youll also need mcs, or audacious will fail to start :)
[http://four.fsphost.com/hairypalms19/mcs_0.4.1-1_i386.deb](http://four.fsphost.com/hairypalms19/mcs_0.4.1-1_i386.deb)

also, has anyone managed to get the docklet plugin working with 1.3.0?

It's right, i was think that mcs is only necesary for build packages, sorry ^^!

Audacious already have a icon tray plugin, and works fine. Docklet is no necesary more.

---

### Post by livesys on 2007-03-05
Installed all 4 .deb and got Audacious 1.3.0 running.
However, I can't play any stream from streamtuner :(
Audacious 1.2.2 have no problem playing these streams.

Am I missing something? A streaming plugin?  I though the mpeg plugin handle that already,

---

### Post by 3dxtrip on 2007-03-05
This is my list plugins

>   Output Plugins
  --------------
  Open Sound System (oss):                yes
  Advanced Linux Sound Arch. (alsa):      yes
  Enlightenment Sound Daemon (esd):       yes
  Jack Audio Connection Kit (jack):       yes
  Analog Realtime Synthesizer (arts):     yes
  BSD/SUN audio output (sun):             no
  PulseAudio sound server (pulse_audio):  yes
 [B] Mac OS X sound support (CoreAudio):     no
  Lame encoder (lame):                    no[/B]
  Null Audio output (null):               yes

  Input Plugins
  -------------
  MPEG 1/2/3 (madplug):                   yes
  MPEG 4 Audio (AAC):                     yes
  Windows Media Audio (wma):              yes
  Module decoder (modplug):               yes
  MIDI modular plugin (amidi-plug):       no
    -> ALSA backend:                      auto
    -> FluidSynth backend:                auto
    -> dummy backend:                     auto
  MIDI to WAVE converter (timidity):      yes
  CD Digital Audio (cdda):                yes
  Microsoft WAV (wav):                    yes
    + sndfile extensions:                 yes
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flac):       yes
  Commodore 64 audio (sid):               yes
  Game music (spc, nsf & gbs):            yes
  PlayStation audio (sexypsf):            yes
  **AdLib synthesizer (adplug):             no**
  Apple Lossless Audio Codec (alac):      yes
**  WavPack 4.31+ (wavpack):                no**
  Musepack support (musepack):            yes
  TrueAudio (tta):                        yes
  Metronom:                               yes

  General
  -------
  Alarm:                                  yes
  Song Change:                            yes
  Status Icon:                            yes
**  Audacious OSD:                          no**
  Control via event device (evdev-plug):  yes
  LIRC:                                   yes
  AudioScrobbler Client:                  yes

  Effect
  ------
  AudioCompressor (AGC):                  yes
  LADSPA effects host (ladspa):           yes
  Voice Removal:                          yes
  Extra Stereo:                           yes
  Echo/Surround:                          yes

  Visualization
  -------------
  Blur Scope:                             yes
  Spectrum Analyzer:                      yes
  Paranormal Visualization Library:       yes
**  ProjectM (GL milkdrop):                 no**

  Transport
  ---------
  stdio transport:                        yes
  curl-based http/https:                  yes
  libmms-based mms:                       yes

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes


I build the package again with libmms support

Audacious Plugins 1.3.0 (with libmms support)
[http://rapidshare.com/files/19626472/audacious-plugins_1.3.0-1_i386.deb.html](http://rapidshare.com/files/19626472/audacious-plugins_1.3.0-1_i386.deb.html)

---

### Post by livesys on 2007-03-06
Hi 3dxtrip,

Thank you for trying, however, I still unable to play Shoutcast mp3 stream from Streamtuner.
mp3 on local disk plays fine.

This is what I get just by running audacious

```

Failed to load plugin (/usr/local/lib/audacious/Output/libjackout.so): libjack-0.100.0.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libwav.so): libsndfile.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libsid.so): libsidplay2.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/General/libscrobbler.so): libcurl-gnutls.so.3: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/General/libcurl.so): libcurl-gnutls.so.3: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Container/libmms.so): libmms.so.0: cannot open shared object file: No such file or directory

```

---

### Post by 3dxtrip on 2007-03-06
Do you uninstalled the previous version?

You must uninstall Audacious 1.2.2 before install 1.3.0

i can play streaming audio from shoutcast.com

---

### Post by 3dxtrip on 2007-03-10
Audacious 1.3.1
[http://rapidshare.com/files/20445720/audacious_1.3.1-1_i386.deb.html](http://rapidshare.com/files/20445720/audacious_1.3.1-1_i386.deb.html)

Audacious Plugins 1.3.1
[http://rapidshare.com/files/20445848/audacious-plugins_1.3.1-1_i386.deb.html](http://rapidshare.com/files/20445848/audacious-plugins_1.3.1-1_i386.deb.html)

---

### Post by hexion on 2007-03-11
Thanks a lot **3dxtrip**!!

Have you think about creating a repository (in tuxfamily.org in example) or sending this packages to audacious devs to upgrade their official repo?

The first option would be great :) and the second... I don't know if they would accept them (my experience with them has been really bad), but just to try...

One issue.. audacious .deb hasn't been built to depend on audacious-plugin .deb. So after installing all, if you make an "aptitude upgrade" it will recommend to delete audacious-plugin package because aptitude thinks that it's not being used:

> Los siguientes paquetes no se usan y se ELIMINARÁN:
  audacious-plugins 
0 paquetes actualizados, 0 nuevos instalados, 1 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 4661kB.
¿Quiere continuar? [Y/n/?] 

Regards

---

### Post by nenolod on 2007-03-11
Hi, we won't accept any packages contributed by users for 1.3 as official.

Using checkinstall to build the packages is a severe violation of debian policy, and as such we won't be able to accept them even as unofficial.

However, there are packages built for edgy based on our debrules for 1.2. They seem to work fine.

-nenolod

---

### Post by 3dxtrip on 2007-03-13
I don't know much about create deb packages... sorry ^^!

Is under your risk if you want to use deb packages that i upload.

> Using checkinstall to build the packages is a severe violation of debian policy, and as such we won't be able to accept them even as unofficial.

You're right, but is a easy method to create.

> CheckInstall is great for quick-and-dirty package generation if all you're worried about is having an easier way to manage applications you're installing from source. However, CheckInstall packages don't pass the sniff test when you are trying to create packages that comply with distro policies.

The right way to create packages is explain here
[http://specialreports.linux.com/article.pl?sid=07/02/21/1546215&from=rss](http://specialreports.linux.com/article.pl?sid=07/02/21/1546215&from=rss)

---

### Post by 3dxtrip on 2007-03-13
> **hexion said:**
> Thanks a lot **3dxtrip**!!

Have you think about creating a repository (in tuxfamily.org in example) or sending this packages to audacious devs to upgrade their official repo?

The first option would be great :) and the second... I don't know if they would accept them (my experience with them has been really bad), but just to try...

One issue.. audacious .deb hasn't been built to depend on audacious-plugin .deb. So after installing all, if you make an "aptitude upgrade" it will recommend to delete audacious-plugin package because aptitude thinks that it's not being used:


Regards

Thanks for these words, but i'm newbie in Linux, maybe later ^^!

> Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.

And, i don't have this issue

---

### Post by marko on 2007-03-15
It appears you have some association with Audacious.  I am really looking forward to 1.3x with amidi-plug built-in.  Will that be released for the various Ubuntu's soon?  Can't wait to try that out with fluidsynth to play my midis..

Thanks much for any insight!

---

### Post by explemonk on 2007-03-27
I just want to say thanks to the OP for the information on setting global hotkeys.  That was the the one feature of Winamp that I was missing badly.  Just needed a little adjustment to get it working using Beryl instead of Metacity and I'm in business!

---

### Post by Hairy_Palms on 2007-04-03
thanks explemonk, also, an audacious media library has been approved as a google summer of code project, audacious could finally become my primary media player.

---

### Post by 3dxtrip on 2007-04-06
> We have released Audacious 1.3.2 to fix some bugs in the 1.3 branch, and to enhance and add some new plugins to the plugin collection. Download it, or discuss it here

[http://boards.nenolod.net/viewtopic.php?p=1570](http://boards.nenolod.net/viewtopic.php?p=1570)


Packages build with Checkinstall

Audacious 1.3.2 i386 DEB
[http://divshare.com/download/346942-151](http://divshare.com/download/346942-151)

Audacious Plugins 1.3.2 i386 DEB
[http://www.divshare.com/download/346965-cca](http://www.divshare.com/download/346965-cca)

> Configuration:

  Install path:                           

  Output Plugins
  --------------
  Open Sound System (oss):                yes
  Advanced Linux Sound Arch. (alsa):      yes
  Enlightenment Sound Daemon (esd):       yes
  Jack Audio Connection Kit (jack):       no
  Analog Realtime Synthesizer (arts):     yes
  BSD/SUN audio output (sun):             no
  PulseAudio sound server (pulse_audio):  no
  Mac OS X sound support (CoreAudio):     no
  Lame encoder (lame):                    yes
  Null Audio output (null):               yes

  Input Plugins
  -------------
  MPEG 1/2/3 (madplug):                   yes
  MPEG 4 Audio (AAC):                     yes
  Windows Media Audio (wma):              yes
  Module decoder (modplug):               yes
  MIDI modular plugin (amidi-plug):       no
    -> ALSA backend:                      auto
    -> FluidSynth backend:                auto
    -> dummy backend:                     auto
  MIDI to WAVE converter (timidity):      yes
  CD Digital Audio (cdda):                yes
  Microsoft WAV (wav):                    yes
    + sndfile extensions:                 no
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flac):       yes
  Commodore 64 audio (sid):               no
  Game music (spc, nsf & gbs):            yes
  PlayStation audio (sexypsf):            yes
  AdLib synthesizer (adplug):             no
  Apple Lossless Audio Codec (alac):      yes
  WavPack 4.31+ (wavpack):                yes
  Musepack support (musepack):            yes
  TrueAudio (tta):                        yes
  Metronom:                               yes

  General
  -------
  Alarm:                                  yes
  Song Change:                            yes
  Status Icon:                            yes
  Audacious OSD:                          no
    -> X Composite support:               no
  Control via event device (evdev-plug):  yes
  LIRC:                                   yes
  AudioScrobbler Client:                  yes

  Effect
  ------
  AudioCompressor (AGC):                  yes
  LADSPA effects host (ladspa):           yes
  Voice Removal:                          yes
  Extra Stereo:                           yes
  Echo/Surround:                          yes
  SndStretch:                             yes

  Visualization
  -------------
  Blur Scope:                             yes
  Spectrum Analyzer:                      yes
  Paranormal Visualization Library:       yes
  ProjectM (GL milkdrop):                 no

  Transport
  ---------
  stdio transport:                        yes
  curl-based http/https:                  yes
  libmms-based mms:                       yes

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes


:guitar:

---

### Post by 3dxtrip on 2007-04-13
> We have released Audacious-Plugins 1.3.3 to fix some defects in the curl VFS backend. In addition, AdPlug's upstream CVS has been merged into our patched version. Download it, or discuss it here.

> Configuration:

Install path: 

Output Plugins
--------------
Open Sound System (oss): yes
Advanced Linux Sound Arch. (alsa): yes
Enlightenment Sound Daemon (esd): yes
Jack Audio Connection Kit (jack): no
Analog Realtime Synthesizer (arts): yes
BSD/SUN audio output (sun): no
PulseAudio sound server (pulse_audio): no
Mac OS X sound support (CoreAudio): no
Lame encoder (lame): yes
Null Audio output (null): yes

Input Plugins
-------------
MPEG 1/2/3 (madplug): yes
MPEG 4 Audio (AAC): yes
Windows Media Audio (wma): yes
Module decoder (modplug): yes
MIDI modular plugin (amidi-plug): no
-> ALSA backend: auto
-> FluidSynth backend: auto
-> dummy backend: auto
MIDI to WAVE converter (timidity): yes
CD Digital Audio (cdda): yes
Microsoft WAV (wav): yes
+ sndfile extensions: no
Tone Generator: yes
Ogg Vorbis (vorbis): yes
Free Lossless Audio Codec (flac): yes
Commodore 64 audio (sid): no
Game music (spc, nsf & gbs): yes
PlayStation audio (sexypsf): yes
AdLib synthesizer (adplug): no
Apple Lossless Audio Codec (alac): yes
WavPack 4.31+ (wavpack): yes
Musepack support (musepack): yes
TrueAudio (tta): yes
Metronom: yes

General
-------
Alarm: yes
Song Change: yes
Status Icon: yes
Audacious OSD: no
-> X Composite support: no
Control via event device (evdev-plug): yes
LIRC: yes
AudioScrobbler Client: yes

Effect
------
AudioCompressor (AGC): yes
LADSPA effects host (ladspa): yes
Voice Removal: yes
Extra Stereo: yes
Echo/Surround: yes
SndStretch: yes

Visualization
-------------
Blur Scope: yes
Spectrum Analyzer: yes
Paranormal Visualization Library: yes
ProjectM (GL milkdrop): no

Transport
---------
stdio transport: yes
curl-based http/https: yes
libmms-based mms: yes

Container
---------
Winamp PLS playlist format (pls): yes
M3U playlist format (m3u): yes
XML Sharable Playlist Format (xspf): yes

DEB Package for i386
[http://www.divshare.com/download/392655-2bb](http://www.divshare.com/download/392655-2bb)

---

### Post by bluebyt on 2007-04-14
I tried to installed the deb "Audacious 1.3.2 i386 DEB" above, but I got this error message?

Unpacking audacious (from audacious_1.3.2-1_i386.deb) ...
dpkg: error processing audacious_1.3.2-1_i386.deb (--install):
 trying to overwrite `/usr/local/bin/audacious', which is also in package audacious-1.3.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 audacious_1.3.2-1_i386.deb

---

### Post by Hairy_Palms on 2007-04-15
it means simply uninstall the old audacious version first :)

---

### Post by 3dxtrip on 2007-04-21
Help!

I've installed Xubuntu on my PC couple weeks ago.

When i try to compile Audacious, i can't configure musepack support, i've installed libmpcdec-dev from Synaptic, but Audacious ./configure do not detect this lib.

How can i force to detect this lib for compile with Musepack support?

Before with Ubuntu i can compile easily, but now i don't understand...^^!

This is my configure's log:

> Install path: 

Output Plugins
--------------
Open Sound System (oss): yes
Advanced Linux Sound Arch. (alsa): yes
Enlightenment Sound Daemon (esd): yes
Jack Audio Connection Kit (jack): no
Analog Realtime Synthesizer (arts): yes
BSD/SUN audio output (sun): no
PulseAudio sound server (pulse_audio): yes
Mac OS X sound support (CoreAudio): no
Lame encoder (lame): yes
Null Audio output (null): yes

Input Plugins
-------------
MPEG 1/2/3 (madplug): yes
MPEG 4 Audio (AAC): yes
Windows Media Audio (wma): yes
Module decoder (modplug): yes
MIDI modular plugin (amidi-plug): no
-> ALSA backend: auto
-> FluidSynth backend: auto
-> dummy backend: auto
MIDI to WAVE converter (timidity): yes
CD Digital Audio (cdda): yes
Microsoft WAV (wav): yes
+ sndfile extensions: yes
Tone Generator: yes
Ogg Vorbis (vorbis): yes
Free Lossless Audio Codec (flac): yes
Commodore 64 audio (sid): yes
Game music (spc, nsf & gbs): yes
PlayStation audio (sexypsf): yes
AdLib synthesizer (adplug): no
Apple Lossless Audio Codec (alac): yes
WavPack 4.31+ (wavpack): yes
Musepack support (musepack): no
TrueAudio (tta): yes
Metronom: yes

General
-------
Alarm: yes
Song Change: yes
Status Icon: yes
Audacious OSD: yes
-> X Composite support: yes
Control via event device (evdev-plug): yes
LIRC: yes
AudioScrobbler Client: yes

Effect
------
AudioCompressor (AGC): yes
LADSPA effects host (ladspa): yes
Voice Removal: yes
Extra Stereo: yes
Echo/Surround: yes
SndStretch: yes

Visualization
-------------
Blur Scope: yes
Spectrum Analyzer: yes
Paranormal Visualization Library: no
ProjectM (GL milkdrop): no

Transport
---------
stdio transport: yes
curl-based http/https: yes
libmms-based mms: yes

Container
---------
Winamp PLS playlist format (pls): yes
M3U playlist format (m3u): yes
XML Sharable Playlist Format (xspf): yes

Bad english, i know ^^!

---

### Post by 3dxtrip on 2007-05-04
Audacious Plugins 1.3.4

>  MPEG 1/2/3 (madplug):                   yes
  MPEG 4 Audio (AAC):                     yes
  Windows Media Audio (wma):              yes
  Module decoder (modplug):               yes
  MIDI modular plugin (amidi-plug):       no
    -> ALSA backend:                      auto
    -> FluidSynth backend:                auto
    -> dummy backend:                     auto
  MIDI to WAVE converter (timidity):      yes
  CD Digital Audio (cdda):                yes
  Microsoft WAV (wav):                    yes
    + sndfile extensions:                 yes
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flac):       yes
  Commodore 64 audio (sid):               yes
  Game music (spc, nsf & gbs):            yes
  PlayStation audio (sexypsf):            yes
  AdLib synthesizer (adplug):             no
  Apple Lossless Audio Codec (alac):      yes
  WavPack 4.31+ (wavpack):                yes
  Musepack support (musepack):            no
  TrueAudio (tta):                        yes
  Metronom:                               yes

  General
  -------
  Alarm:                                  yes
  Song Change:                            yes
  Status Icon:                            yes
  Audacious OSD:                          yes
    -> X Composite support:               yes
  Control via event device (evdev-plug):  yes
  LIRC:                                   yes
  AudioScrobbler Client:                  yes

  Effect
  ------
  AudioCompressor (AGC):                  yes
  LADSPA effects host (ladspa):           yes
  Voice Removal:                          yes
  Extra Stereo:                           yes
  Echo/Surround:                          yes
  SndStretch:                             yes

  Visualization
  -------------
  Blur Scope:                             yes
  Spectrum Analyzer:                      yes
  Paranormal Visualization Library:       no
  ProjectM (GL milkdrop):                 no

  Transport
  ---------
  stdio transport:                        yes
  curl-based http/https:                  yes
  libmms-based mms:                       yes

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes


Help with musepack support please!

I have the developer lib installed, but i can't compile with that

Audacious Plugins 1.3.4 - Whitout MUSEPACK support
[http://www.divshare.com/download/567620-001](http://www.divshare.com/download/567620-001)

---

### Post by Dexterp37 on 2007-05-13
Just wanted to say, that those packages works like a charm. Just one thing: you have to manually install libmcs and libmowgl :)

---

### Post by 3dxtrip on 2007-05-22
I build DEB packages using Checkinstall from SVN Repositories following this how-to
[http://ubuntuforums.org/showthread.php?p=2645212](http://ubuntuforums.org/showthread.php?p=2645212)

For i386

Audacious 1.4.0 Devel from SVN
[http://www.divshare.com/download/703759-ea1](http://www.divshare.com/download/703759-ea1)

Audacious Plugins 1.3.4 Devel from SVN  --->>> More plugins support!!!
[http://www.divshare.com/download/703782-a70](http://www.divshare.com/download/703782-a70)

Audacious Plugins Ugly 1.3.4 Devel from SVN
[http://www.divshare.com/download/703791-fb6](http://www.divshare.com/download/703791-fb6)

libmcs_0.4.1-1_i386.deb
[http://www.divshare.com/download/703956-dbd](http://www.divshare.com/download/703956-dbd)

libmowgli_0.1.3-1_i386.deb
[http://www.divshare.com/download/703930-10d](http://www.divshare.com/download/703930-10d)
You need uninstall previous versions of Audacious.

Let me know about this releases.

---

### Post by cdiem on 2007-05-25
After I install audacious, and try to run it, it gives me the following:
> cdiem@cdiemst:~$ audacious
audacious: error while loading shared libraries: libmcs.so.1: cannot open shared object file: No such file or directory

And I'm sure I have it installed, as well as libmowgli (they appear as installed locally packages in synaptic). What shall I do, to show audacious, that I have these installed?

edited - I solved this by copying the *.so files of libmcs to /usr/lib (I think they were installed in /usr/local/lib by default). Audacious is running, and I like the way it sounds more than Rhythmbox :)

---

### Post by kaede on 2007-05-25
anyone know how to enable crossfading in audacious?

:D

---

### Post by goonies on 2007-05-26
anyone know when the latest stable version of audacious will hit ubuntu repos?

---

### Post by mimihu88 on 2007-05-27
> **3dxtrip said:**
> I build DEB packages using Checkinstall from SVN Repositories following this how-to
[http://ubuntuforums.org/showthread.php?p=2645212](http://ubuntuforums.org/showthread.php?p=2645212)

For i386

Audacious 1.4.0 Devel from SVN
[http://www.divshare.com/download/703759-ea1](http://www.divshare.com/download/703759-ea1)

Audacious Plugins 1.3.4 Devel from SVN  --->>> More plugins support!!!
[http://www.divshare.com/download/703782-a70](http://www.divshare.com/download/703782-a70)

Audacious Plugins Ugly 1.3.4 Devel from SVN
[http://www.divshare.com/download/703791-fb6](http://www.divshare.com/download/703791-fb6)

libmcs_0.4.1-1_i386.deb
[http://www.divshare.com/download/703956-dbd](http://www.divshare.com/download/703956-dbd)

libmowgli_0.1.3-1_i386.deb

[http://www.divshare.com/download/703930-10d](http://www.divshare.com/download/703930-10d)
You need uninstall previous versions of Audacious.

Let me know about this releases.

I installed these ,work great,thks! ubuntu7.04:D

---

### Post by mimihu88 on 2007-06-01
audacious
Failed to load plugin (/usr/local/lib/audacious/Output/libpulse_audio.so): /usr/local/lib/audacious/Output/libpulse_audio.so: undefined symbol: playlist_get_title
Failed to load plugin (/usr/local/lib/audacious/Input/libadplug.so): libbinio.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Visualization/libiris.so): /usr/local/lib/audacious/Visualization/libiris.so: undefined symbol: xmms_remote_playlist_prev
Failed to load plugin (/usr/local/lib/audacious/Visualization/librootvis.so): libImlib2.so.1: cannot open shared object file: No such file or directory

when I start from terminal these error there ?

---

### Post by chartreux on 2007-06-03
After the above installation, for some reason, audacious can play every format EXCEPT the one I need -- **FLAC**. :(:(
Keep getting this error during startup...

[HTML]Failed to load plugin (/usr/local/lib/audacious/Input/libwav.so): libFLAC.so: cannot open shared object file: No such file or directory
[/HTML]

[edit: Problem fixed by updating to Fiesty and reinstalling via Synaptic]

---

### Post by m4443 on 2007-06-04
> **3dxtrip said:**
> I build DEB packages using Checkinstall from SVN Repositories following this how-to
[http://ubuntuforums.org/showthread.php?p=2645212](http://ubuntuforums.org/showthread.php?p=2645212)

For i386

Audacious 1.4.0 Devel from SVN
[http://www.divshare.com/download/703759-ea1](http://www.divshare.com/download/703759-ea1)

Audacious Plugins 1.3.4 Devel from SVN  --->>> More plugins support!!!
[http://www.divshare.com/download/703782-a70](http://www.divshare.com/download/703782-a70)

Audacious Plugins Ugly 1.3.4 Devel from SVN
[http://www.divshare.com/download/703791-fb6](http://www.divshare.com/download/703791-fb6)

libmcs_0.4.1-1_i386.deb
[http://www.divshare.com/download/703956-dbd](http://www.divshare.com/download/703956-dbd)

libmowgli_0.1.3-1_i386.deb
[http://www.divshare.com/download/703930-10d](http://www.divshare.com/download/703930-10d)
You need uninstall previous versions of Audacious.

Let me know about this releases.

Heelp!

```
 audacious
Failed to load plugin (/usr/local/lib/audacious/Output/libpulse_audio.so): /usr/local/lib/audacious/Output/libpulse_audio.so: undefined symbol: playlist_get_title
Failed to load plugin (/usr/local/lib/audacious/Output/libfilewriter.so): libmp3lame.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Output/libjackout.so): libjack-0.100.0.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Output/libarts.so): libartsc.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libwavpack.so): libwavpack.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libadplug.so): libbinio.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libmpc.so): libmpcdec.so.3: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libmadplug.so): libmad.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libsid.so): libsidplay.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Visualization/librootvis.so): libImlib2.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Visualization/libiris.so): /usr/local/lib/audacious/Visualization/libiris.so: undefined symbol: xmms_remote_playlist_prev
Failed to load plugin (/usr/local/lib/audacious/Container/libmms.so): libmms.so.0: cannot open shared object file: No such file or directory

```

---

### Post by 3dxtrip on 2007-06-04
> **m4443 said:**
> Heelp!

```
 audacious
Failed to load plugin (/usr/local/lib/audacious/Output/libpulse_audio.so): /usr/local/lib/audacious/Output/libpulse_audio.so: undefined symbol: playlist_get_title
Failed to load plugin (/usr/local/lib/audacious/Output/libfilewriter.so): libmp3lame.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Output/libjackout.so): libjack-0.100.0.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Output/libarts.so): libartsc.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libwavpack.so): libwavpack.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libadplug.so): libbinio.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libmpc.so): libmpcdec.so.3: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libmadplug.so): libmad.so.0: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Input/libsid.so): libsidplay.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Visualization/librootvis.so): libImlib2.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Visualization/libiris.so): /usr/local/lib/audacious/Visualization/libiris.so: undefined symbol: xmms_remote_playlist_prev
Failed to load plugin (/usr/local/lib/audacious/Container/libmms.so): libmms.so.0: cannot open shared object file: No such file or directory

```

Try uninstall Audacious and install again.

---

### Post by 3dxtrip on 2007-06-04
> **mimihu88 said:**
> audacious
Failed to load plugin (/usr/local/lib/audacious/Output/libpulse_audio.so): /usr/local/lib/audacious/Output/libpulse_audio.so: undefined symbol: playlist_get_title
Failed to load plugin (/usr/local/lib/audacious/Input/libadplug.so): libbinio.so.1: cannot open shared object file: No such file or directory
Failed to load plugin (/usr/local/lib/audacious/Visualization/libiris.so): /usr/local/lib/audacious/Visualization/libiris.so: undefined symbol: xmms_remote_playlist_prev
Failed to load plugin (/usr/local/lib/audacious/Visualization/librootvis.so): libImlib2.so.1: cannot open shared object file: No such file or directory

when I start from terminal these error there ?

Plugins Ugly is not installed

---

### Post by mimihu88 on 2007-06-05
> **3dxtrip said:**
> Plugins Ugly is not installed

but I am sure I did install the "Plugins Ugly"

---

### Post by 3dxtrip on 2007-06-05
> **mimihu88 said:**
> but I am sure I did install the "Plugins Ugly"

Sorry, i get the same error when i load from a terminal.

Do you are use the SVN version?
SVN version have a lot of issues and bugs, but is capable to play music files without problems.

I will build a stable version from Audacious 1.3.2 and Audacious Plugins 1.3.4 with major support.

---

### Post by 3dxtrip on 2007-06-05
Build using Xubuntu Feisty Fawn for i386

Audacious 1.3.2 STABLE
[http://www.divshare.com/download/846068-118](http://www.divshare.com/download/846068-118)
Auacious 1.3.4 STABLE
[http://www.divshare.com/download/846146-6a6](http://www.divshare.com/download/846146-6a6)


OFFICIAL RELEASES!!!
Gutsy Version have a new packages for Audacious
[http://packages.ubuntu.com/gutsy/sound/](http://packages.ubuntu.com/gutsy/sound/)

---

### Post by sojusnik on 2007-06-06
Hi,

Just downloaded the both mentioned .debs for i386,

Couldn't get them to work after installing.
Audacious won't launch at all.

Do they work well for you?

I'm using Feisty Ubuntu with all latest updates.

Thx for help!

---

### Post by 3dxtrip on 2007-06-07
> **sojusnik said:**
> Hi,

Just downloaded the both mentioned .debs for i386,

Couldn't get them to work after installing.
Audacious won't launch at all.

Do they work well for you?

I'm using Feisty Ubuntu with all latest updates.

Thx for help!

Wokrs fine on my PC, try uninstall previous versions or you can download official packages from Ubuntu Packages, versions of Official Packages are:
Audacious 1.3.2
Audacious Plugins 1.3.3

---

### Post by sojusnik on 2007-06-07
Hi,

> Wokrs fine on my PC, try uninstall previous versions or you can download official packages from Ubuntu Packages, versions of Official Packages are:
Audacious 1.3.2
Audacious Plugins 1.3.3

Where especially I can find these versions?

Synaptic only offers 1,2.2-4 version of this program and plugins.

I'm on Feisty.


I hope you have some patience with a Linux newbie,

Thanks in advance!

---

### Post by 3dxtrip on 2007-06-09
> **sojusnik said:**
> Hi,
Where especially I can find these versions?

Synaptic only offers 1,2.2-4 version of this program and plugins.

I'm on Feisty.


I hope you have some patience with a Linux newbie,

Thanks in advance!

No problem ^^

You can download official packages from here:
[http://packages.ubuntu.com/gutsy/sound/](http://packages.ubuntu.com/gutsy/sound/)

Search for Audacious

---

### Post by 3dxtrip on 2007-06-09
> Audacious-Plugins 1.3.5 has been released to fix multiple stability and security issues as well as to bring in proven enhancements from 1.4 development. Please don't report bugs in any previous versions of Audacious-Plugins, they will be ignored.

Audacious Plugins 1.3.5
Build with Checkinstall on Feisty Fawn i386
[http://www.divshare.com/download/893921-405](http://www.divshare.com/download/893921-405)

---

### Post by Corbelius on 2007-07-07
@ **Audacious 1.3.2** (include plugins)
@ **Feisty AMD64**

[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

---

### Post by 3dxtrip on 2007-07-22
Audacious, Audacious-Plugins 1.4.0 DR1 released

> 20 July 2007 | Submitted By William Pitcock (nenolod) 

The first development snapshot of our next generation effort has been released. This contains a lot of new code. (infact, most of it is entirely new code!) We are looking for feedback from the developer and testing communities concerning it.

This is also the first release to be licensed under GPL3. To clarify, only 1.4 will be licensed under GPL3. 1.3 and previous will remain under GPL2. We have included a clause in our license terms that exempts all third-party code from becoming GPL3 when it is loaded into the player, something that was not as feasible to do under GPL2. We hope that this licensing change will be helpful for the developer community.

So anyway, feel free to test, and note that this new codebase should be easier to package as well. To comment, go to our boards.

i386 DEB Packages build with Checkinstall

Audacious 1.4.0-DR1
[http://www.divshare.com/download/1342371-696](http://www.divshare.com/download/1342371-696)

Audacious Plugins 1.4.0-DR1
[http://www.divshare.com/download/1342374-139](http://www.divshare.com/download/1342374-139)

libs dependencies

libmowgli 0.3.0-Devel
[http://www.divshare.com/download/1342394-a79](http://www.divshare.com/download/1342394-a79)

libmcs1
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fm%2Fmcs%2Flibmcs1_0.4.1-2_i386.deb&md5sum=a2b39e1250567dae19ad93a74a731ea6&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fm%2Fmcs%2Flibmcs1_0.4.1-2_i386.deb&md5sum=a2b39e1250567dae19ad93a74a731ea6&arch=i386&type=main)

---

### Post by Kosimo on 2007-07-29
Links are broken :(

Anyone else have precompiled debs of the 1.4.0 + plugins?  thank you

---

### Post by 3dxtrip on 2007-07-29
> **Kosimo said:**
> Links are broken :(

Anyone else have precompiled debs of the 1.4.0 + plugins?  thank you

Links Fixed, sorry for that :-\"

---

### Post by Kosimo on 2007-07-30
> **3dxtrip said:**
> Links Fixed, sorry for that :-\"

Thank you! :-)

Everything is going fine.... But, there is only one thing that is not working since I upgrade it to this 1.4.0.   I used to listen a radio streaming station in mp3... But now is not working anymore. (Any other file in my computer plays perfectly..) only the radio streaming's not working. Any idea?

Thank you again


ps: Pluguins are installed by the way

---

### Post by 3dxtrip on 2007-08-09
> Audacious, Audacious-Plugins 1.4.0 DR2 released
08 August 2007 | Submitted By William Pitcock (nenolod) 

The title says it all. If you're feeling lucky and want to play with some alpha-quality release code, then jump right in and play with the latest developer release. Just be sure to let us know anything out of the 
ordinary about it, in it's own discussion thread.

**wma playback fixed in this release**
Please report bugs to Audacious Team 

Build in Xubuntu Gutsy with Checkinstall (for i386)

Audacious 1.4.0-DR2
[http://www.divshare.com/download/1524744-555](http://www.divshare.com/download/1524744-555)

Audacious Plugins 1.4.0-DR2
[http://www.divshare.com/download/1524767-5f7](http://www.divshare.com/download/1524767-5f7)


Kosimo:
Streaming playback works fine on my PC

Saludos

---

### Post by cdiem on 2007-09-01
Probably it's a little bit late, and I don't know if someone already has mentioned it, but I'd like to share this. 
For setting the global hotkeys of audacious in Ubuntu Feisty Fawn, one has to go through "gconf-editor" -> apps -> compiz ->..., and not apps -> metacity, as posted in the first post of this thread, because if one has "Enabled the desktop effects" of Feisty, the default window manager would be compiz, and not metacity.

---

### Post by Hairy_Palms on 2007-09-02
your totally right :) 
but when i made the first post it was under ubuntu dapper :) compiz didnt exist ^^

---

### Post by cdiem on 2007-09-03
You've made a great post (the first of the thread), from which I have learned a lot. Thank you. 
My post wasn't intended to be critical. It was all about sharing knowledge.

---

### Post by 3dxtrip on 2007-09-09
> Audacious, Audacious-Plugins 1.4.0 DR3 released
09 September 2007 | Submitted By William Pitcock (nenolod) 

The title says it all. If you're feeling lucky and want to play with some alpha-quality release code, then jump right in and play with the latest developer release. Just be sure to let us know anything out of the ordinary about it, in it's own discussion thread.

Some notes: Some of the new code is very slow at the moment. We're working on ways to speed it up, and have made some pretty major advances, but they are not yet complete enough. This will include some final API revision, but we will freeze the API with 1.4.0 Beta 1, in a week or two.

Again, this is very unpolished, and 1.4 Beta 1 will indeed be faster. If you don't like this, we'll see you in 1.4 Beta1 instead.

DEB's Packages created with checkinstall for i386

Audacious 1.4.0-dr3
[http://www.divshare.com/download/1918389-af3](http://www.divshare.com/download/1918389-af3)

Audacious Plugins 1.4.0-dr3
[http://www.divshare.com/download/1918461-70c](http://www.divshare.com/download/1918461-70c)

libmowgli 0.4.0
[http://www.divshare.com/download/1918615-201](http://www.divshare.com/download/1918615-201)

---

### Post by olskar on 2007-09-10
> **3dxtrip said:**
> DEB's Packages created with checkinstall for i386

Audacious 1.4.0-dr3
[http://www.divshare.com/download/1918389-af3](http://www.divshare.com/download/1918389-af3)

Audacious Plugins 1.4.0-dr3
[http://www.divshare.com/download/1918461-70c](http://www.divshare.com/download/1918461-70c)

libmowgli 0.4.0
[http://www.divshare.com/download/1918615-201](http://www.divshare.com/download/1918615-201)


This gives me:
audacious: symbol lookup error: audacious: undefined symbol: g_once_init_enter_impl

---

### Post by 3dxtrip on 2007-09-23
> Audacious, Audacious-Plugins 1.4.0 DR4 released
12 September 2007 | Submitted By William Pitcock (nenolod) 

Audacious 1.4.0 DR4 has been released. We think we have stablized the API, although some minor changes may still happen between now and beta1. We'll be releasing beta1 most likely next week. See you then, or download now for a sneak peak. Just be sure to let us know anything out of the ordinary about it, in it's own discussion thread.

Some notes: Some of the new code is very slow at the moment. We're working on ways to speed it up, and have made some pretty major advances, but they are not yet complete enough and have not been fully realized in DR4.

Again, this is very unpolished, and 1.4 Beta 1 will indeed be faster. If you don't like this, we'll see you in 1.4 Beta1 instead.

DEB Packages

Audacious 1.4.0-DR4
[http://www.divshare.com/download/2080505-163](http://www.divshare.com/download/2080505-163)

Audacious Plugins 1.4.0-DR4
[http://www.divshare.com/download/2080511-ac6](http://www.divshare.com/download/2080511-ac6)

libmowgli 0.4.0
[http://www.divshare.com/download/1918615-201](http://www.divshare.com/download/1918615-201)

Build with checkinstall for i386 machines

---

### Post by Kosimo on 2007-10-04
> **3dxtrip said:**
> DEB Packages

Audacious 1.4.0-DR4
[http://www.divshare.com/download/2080505-163](http://www.divshare.com/download/2080505-163)

Audacious Plugins 1.4.0-DR4
[http://www.divshare.com/download/2080511-ac6](http://www.divshare.com/download/2080511-ac6)

libmowgli 0.4.0
[http://www.divshare.com/download/1918615-201](http://www.divshare.com/download/1918615-201)

Build with checkinstall for i386 machines


Your debs are always welcome ;)

Just a question, does it work for feisty 32 bits?

Thanks!

---

### Post by aparigraha on 2007-10-04
Have to agree. those debs are nice.
I haven't gotten the 1.4.0 to work yet though, so I'm sticking with 1.3.2
Nice work **3dxtrip**

---

### Post by 3dxtrip on 2007-10-05
> **Kosimo said:**
> Your debs are always welcome ;)

Just a question, does it work for feisty 32 bits?

Thanks!

Thanks!

Deb's packages should be work on 32 bits machines, you need libmowgli installed.

---

### Post by 3dxtrip on 2007-10-16
Road to final stable version!

> Audacious, Audacious-Plugins 1.4.0 Beta1 released
15 October 2007 | Submitted By William Pitcock (nenolod) 

Audacious 1.4.0 Beta1 has been released. The API is mostly stablized (we may make a few minor adjustments still), and we have gotten rid of the curl plugin due to bugs. It has been replaced with a libneon-using plugin which is more reliable. Discuss the 1.4 Beta1 release.

Packages buld using checkinstall in Xubuntu Gutsy for i386 machines

Audacious 1.4.0-beta1
[http://www.divshare.com/download/2374947-a9e](http://www.divshare.com/download/2374947-a9e)

Audacious Plugins 1.4.0-beta1
[http://www.divshare.com/download/2374989-d52](http://www.divshare.com/download/2374989-d52)

**Important!!!**
If Audacious don't start open a terminal and type

audacious

If this message appear
> audacious: error while loading shared libraries: libaudclient.so.1.0.0: cannot open shared object file: No such file or directory

Type this:
> sudo su -c 'echo /usr/local/lib >> /etc/ld.so.conf && ldconfig'

Check about this issue on Audacious Boards:
[http://boards.nenolod.net/viewtopic.php?f=5&t=844&start=15&st=0&sk=t&sd=a](http://boards.nenolod.net/viewtopic.php?f=5&t=844&start=15&st=0&sk=t&sd=a)

---

### Post by 3dxtrip on 2007-10-20
> Audacious, Audacious-Plugins 1.4.0 Beta2 released
19 October 2007 | Submitted By William Pitcock (nenolod) 

Audacious 1.4.0 Beta2 has been released. This fixes some bugs that were reported in beta1. Discuss the 1.4 Beta release series.

The audacious website is undergoing a redo. We're working on a new website that will allow for people to submit (and possibly host on a decent mirror) components and skins, as well as add proper commenting and proper documentation infrastructure to the website. (e.g. bye bye MediaWiki really soon now)

Update: There was a bug discovered in the plugins pack. 1.4.0-beta3 has been released to fix it.

Build with checkinstall in Xubuntu Gutsy for i386 machines

Audacious 1.4.0-beta2
[http://www.divshare.com/download/2414871-c57](http://www.divshare.com/download/2414871-c57)

Audacious Plugins 1.4.0-beta3
[http://www.divshare.com/download/2414888-8bd](http://www.divshare.com/download/2414888-8bd)

---

### Post by Kosimo on 2007-10-31
> **3dxtrip said:**
> Build with checkinstall in Xubuntu Gutsy for i386 machines

Audacious 1.4.0-beta2
[http://www.divshare.com/download/2414871-c57](http://www.divshare.com/download/2414871-c57)

Audacious Plugins 1.4.0-beta3
[http://www.divshare.com/download/2414888-8bd](http://www.divshare.com/download/2414888-8bd)

Just waiting debs from Beta 4 ;)

---

### Post by 3dxtrip on 2007-11-02
> Audacious, Audacious-Plugins 1.4.0 RC1 released
1 November 2007 | Submitted By William Pitcock (nenolod) 

Excluding some minor touchups, and translation updates, Audacious 1.4 is now complete, and is now recommended over 1.3. Discuss.

A few bugs reported on Audacious Forums:
[http://boards.nenolod.net/viewtopic.php?f=5&t=858](http://boards.nenolod.net/viewtopic.php?f=5&t=858)

But this release is clean, even more stable and near to final verison!!!
New Skin for Default!!!

[IMG]http://img209.imageshack.us/img209/4512/audaciousnewol7.png[/IMG]

Audacious 1.4.0 RC1
[http://www.divshare.com/download/2610388-85b](http://www.divshare.com/download/2610388-85b)

Audacious-Plugins 1.4.0 RC1
[http://www.divshare.com/download/2610451-5f4](http://www.divshare.com/download/2610451-5f4)

Build for i386 machines with checkinstall on Xubuntu Gutsy

---

### Post by nenolod on 2007-11-03
official backports for gutsy...

add to /etc/apt/sources.list:

```
deb http://backports.dereferenced.org/ gutsy universe
```

check for updates, version 1.4.0~rc1-0dereferenced1 should show up. install, enjoy.

packages for i386, amd64, powerpc (packages for ppc are still building).

---

### Post by Kosimo on 2007-11-03
> **nenolod said:**
> official backports for gutsy...

add to /etc/apt/sources.list:

```
deb http://backports.dereferenced.org/ gutsy universe
```

check for updates, version 1.4.0~rc1-0dereferenced1 should show up. install, enjoy.

packages for i386, amd64, powerpc (packages for ppc are still building).

Wonderfoul! Everything works perfectly.
Recommended to uninstall first the previous version.

Thanks!

---

### Post by pelle.k on 2007-11-04
Nice job, nenolod. I was just about to package it myself ;) but you saved me the trouble.
Oh, i'm so glad they decided to rewrite audacious, but still it looks a bit messy compared to bmp. I prefer it to rhythmbox or any other "music managment suite" though...

btw, am i the only one who thinks the tray icon takes up just a little bit too much space compared to the rest of the notification icons? (yes, i now how to change it, but still, they could have given it a frame of 4 pixels transparency or something...)

---

### Post by mthei on 2007-11-04
Hey thanks. The "unofficial backport" for Feisty only brought me to the last stable version, which still had some bugs that annoyed me. I had just upgraded to Gutsy today, so I'll certainly try this. For whatever reason, Audacious refuses to compile for me (although 1.3.2 worked).

Edit: The new skin really makes the playlist easier to read when it's in slim mode, as opposed to the white font surrounded by the white playlist. Much easier on the eyes, All of the bugs involving the wrong track-time being displayed are now gone in this version as well.

---

### Post by 3dxtrip on 2007-11-04
Many thanks, finally official packages for Audacious!

---

### Post by nenolod on 2007-11-06
official 1.4.0 final packages are now building.

  amd64: audacious built, audacious-plugins building.
  i386: none built yet (other packages in queue)
  powerpc: none built yet (other packages in queue)

---

### Post by sojusnik on 2007-11-09
Hi,

Thx for building the final 1.4 Release of audacious!

Will there be a notification on the official audacious Website:

[http://audacious-media-player.org/index.php?title=Downloads](http://audacious-media-player.org/index.php?title=Downloads)

or should we wait for your next posting?

---

### Post by Kosimo on 2007-11-09
Thank you guys, the repository works perfectly ;)


This is my Audacious 1.4 FINAL with winamp skin


[IMG]http://kosimo.googlepages.com/audacious1.4winampskin.png[/IMG]

---

### Post by sojusnik on 2007-11-09
Hi,

So the version from this source is already the final Version of Audacious or did you install it manually?

Source: deb [http://backports.dereferenced.org/](http://backports.dereferenced.org/) gutsy universe

---

### Post by Kosimo on 2007-11-09
> **sojusnik said:**
> Hi,

So the version from this source is already the final Version of Audacious or did you install it manually?

Source: deb [http://backports.dereferenced.org/](http://backports.dereferenced.org/) gutsy universe

You get the final

---

### Post by sojusnik on 2007-11-09
Thx,

Is it possible to enable crossfading in audacious 1.4?

---

### Post by Kosimo on 2007-11-09
> **sojusnik said:**
> Thx,

Is it possible to enable crossfading in audacious 1.4?

Yes, you need the crossfade plugin.

After adding the repository, make a search in synaptic:  audacious crossfade

---

### Post by sojusnik on 2007-11-09
Hi,

I've Installed:

audacious-crossfade 0.3.12-2build1 

and 

libaudacious5 1.3.2-4

but can't find the crossfade option under preferences and plugins in audacious. Are they compatible?

Thx in advance!

---

### Post by nenolod on 2007-11-12
as far as i am aware, xmms-crossfade (the package audacious-crossfade derives from) does not build an audacious 1.4 package yet.

---

### Post by reaganf2 on 2007-11-14
hi all...
thanks for the backport repository... just installed audacious 1.4 and it works brilliantly... all except for the fact that it doesn't show the eq-audacious-0.21 plugin in the plugin list anymore, even after recompiling...
[http://sacredspiral.co.uk/audacious](http://sacredspiral.co.uk/audacious) mentions a newer version of the plugin called eq-audacious-ng... is it out yet...?? or anybody know how to get 0.21 working in the new version of audacious....?? my music quality seems dead without it...

---

### Post by nenolod on 2007-11-15
sadly, real-life events have been busy as of late, so eq-audacious-ng has been on backburner for a while.

i'll try to get back to it as soon as possible. :)

---

### Post by ariel on 2007-11-25
FYI, the audacious 1.4.2 backport for gutsy as of today has a little problem handling cue sheets. (the default config doesn't work)

If you use .cue's, there is a workaround though, you can find it here:

[http://boards.nenolod.net/viewtopic.php?f=7&t=213&p=2881#p2881](http://boards.nenolod.net/viewtopic.php?f=7&t=213&p=2881#p2881)

Also, if you need monkey's audio support, you will need to ./configure, make, make install the MAC libs and the audacious-mac plugin (starting with MAC-3.99), it took me a while to find them:

- Google for  mac-3.99-u4-b5.tar.gz, build it  (originally this was in sourceforge mac-port project, but it seems it is no longer there)
- Then get the audacious-mac plugin: [http://www.netswarm.net/misc/audacious-mac-0.3.10.tar.gz](http://www.netswarm.net/misc/audacious-mac-0.3.10.tar.gz)

- enjoy your lossless audio with the neatest player around

---

### Post by 3dxtrip on 2007-12-01
News from xmms-crossfade plugin dev

> 11/26/2007 - V0.3.14 released 

Changes: 
Improved software mixer. The volume is now applied just before sending the data to the output plugin, resulting in faster reaction to user input. 
Fixed automatic and end-of-playlist songchange with audacious. 
Fixed playback of internet radio streams.

Check xmms-crossfade with Audacious Support, build with checkinstall for i386 machines.

Audacious Crossfade 0.3.14
[http://www.divshare.com/download/2965638-bb2](http://www.divshare.com/download/2965638-bb2)

Today Audacious updated to 1.4.3 and plugins to 1.42 :guitar:

---

### Post by zivagolee on 2007-12-05
anyone else getting segfaults on 1.4.3 when playing playlists?  Playing mp3s directly work just fine.

Not sure how to get backtraces for it.

---

### Post by Freddy on 2007-12-13
> **zivagolee said:**
> anyone else getting segfaults on 1.4.3 when playing playlists?  Playing mp3s directly work just fine.

Not sure how to get backtraces for it.
Yeah, I have that same problem. Trying to play playlists kills audacious.

This was a shameless bump :).

---

### Post by zivagolee on 2007-12-13
sigh... going on the audacious forums pretty much deems no response/help either.  it's too bad since audacious is the best looking player since xmms IMO..

---

### Post by Freddy on 2007-12-13
> **zivagolee said:**
> sigh... going on the audacious forums pretty much deems no response/help either.  it's too bad since audacious is the best looking player since xmms IMO..
For me the playlist thingie just broke, I have no clue why. The Audacious from this repo is 1.4.3 and the newest build is 1.4.4, so this might have been resolved but I can't get 1.4.4 to compile.

---

### Post by quoderat on 2007-12-14
What errors on compile are you having? I just compiled 1.4.4, and it worked fine.

It has some quirks, like any file I add to the playlist drops two below where I drag it, but it works.

Be glad to help, if I can.

---

### Post by Kosimo on 2007-12-29
Any idea about where to find nice -debs of any repository containing the latest 1.4.5 audacious?

---

### Post by Perfect Storm on 2007-12-29
I have a compiling guide here; [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html) for the latest build.

---

### Post by Kosimo on 2007-12-29
> **Artificial Intelligence said:**
> I have a compiling guide here; [http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2007/11/build-audacious-from-source-710-64bit.html) for the latest build.

Does it works in 32 bits as well?

---

### Post by Perfect Storm on 2007-12-29
Aye

---

### Post by Kosimo on 2007-12-29
> **Artificial Intelligence said:**
> Aye

Cool, gonna follow now.

Thank you :popcorn:

---

### Post by stokedfish on 2008-01-01
**Audacious 1.4.5 and Audacious-Plugins 1.4.4 released**

Any debs for those anywhere?

---

### Post by sojusnik on 2008-01-11
I'm searching too.

---

### Post by zivagolee on 2008-01-11
Check out morgoth's repo.

[http://boards.nenolod.net/viewtopic.php?f=5&t=633](http://boards.nenolod.net/viewtopic.php?f=5&t=633)

Has the latest versions for gutsy.

---

### Post by Wastedyouthfx0 on 2008-05-30
> **pelle.k said:**
> Nice job, nenolod. I was just about to package it myself ;) but you saved me the trouble.
Oh, i'm so glad they decided to rewrite audacious, but still it looks a bit messy compared to bmp. I prefer it to rhythmbox or any other "music managment suite" though...

btw, am i the only one who thinks the tray icon takes up just a little bit too much space compared to the rest of the notification icons? (yes, i now how to change it, but still, they could have given it a frame of 4 pixels transparency or something...)

I don't know how to change the icon.  How can it be done?

---

### Post by pelle.k on 2008-05-30
Waking the dead, are we ;)
You need to find that .png icon that gets loaded as a notification icon and shrink it while keeping the size of the image, and having 2-4 pixels act as a padding (using transparency of course).
It's as simple as that.

```
sudo find /usr -iname audacious
```

---

### Post by ariel on 2008-05-31
just wondering if anyone found .debs for 1.5.1 out there? just too lazy to compile here.

---

### Post by Kosimo on 2008-05-31
> **ariel said:**
> just wondering if anyone found .debs for 1.5.1 out there? just too lazy to compile here.

Same question :)

---

### Post by Hairy_Palms on 2008-08-26
gave it a check, it depends on a later version of libmcs than is in the repos, and i cant find the source of the latest version of libmcs to compile

---

### Post by Perfect Storm on 2008-08-26
> **Hairy_Palms said:**
> gave it a check, it depends on a later version of libmcs than is in the repos, and i cant find the source of the latest version of libmcs to compile

[http://ubuntuforums.org/showthread.php?t=658282](http://ubuntuforums.org/showthread.php?t=658282)
Works also for 32-bit

---

### Post by playtowin on 2008-08-26
OR there is an alternate way with just few clicks.

Install Ultamatix and you'll the latest version including Amarok 2

both for 64 bit and 32 bit. Easy to unistall as well:-\" with just 2 clicks.

---

