---
title: "Newest Zsnes in Hoary Howto"
date: 2005-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-05-31
If you are like me, the old version of Zsnes in Hoary's universe makes you sad. Problem is that Sid is only a little better, so you must do more to get the most recent version. Here are the steps.

I got 1.42 working for me with this. Someone test!

Open up your terminal. 

First you must remove the old zsnes:

> sudo apt-get remove zsnes

Then you need to install some things:

> sudo apt-get install libpng3 libstdc++6 

Then: 

> wget [ftp://ftp.uni-bayreuth.de/pub/linux/Mandrakelinux/devel/cooker/i586/media/contrib/zsnes-1.42-1mdk.i586.rpm](ftp://ftp.uni-bayreuth.de/pub/linux/Mandrakelinux/devel/cooker/i586/media/contrib/zsnes-1.42-1mdk.i586.rpm)
 

 

(note: the forum truncates the address so you have to copy the link instead)

Then:

> sudo alien zsnes-1.42-1mdk.i586.rpm  

Finally when thats done:

> sudo dpkg -i zsnes_1.42-1_i386.deb 

If there are no errors, launch with the command:

> zsnes


EDIT
------------------------------------------------------------------------------------------------------------------------------

There is now a better way to get newer Zsnes.

> wget [http://sethkinast.com/ubuntu/hoary/backports/zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb)

> sudo dpkg -i zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb

Thank Seth for making this new package.

---

### Post by bored2k on 2005-05-31
>  sudo apt-get zsnes
```
sudo apt-get zsnes
E: Invalid operation zsnes

```
;)

Thanks for the reminder, now I got the urge to play classics like Zelda: Link to the Past and some other RPG's I never got to finish because I was a huge ignorant fool (FF 3 I'm looking at you).

---

### Post by ltmon on 2005-05-31
I've been snes9x, fronted by snes9express to play my snes games (battle toads rocks!).  Both these are installable from universe.

I don't really know a great deal about the emulator, I just do enough to get a game on screen.  My question really is, what would zsnes and in particular the new version do for me?  What is the difference between one snes emulator and the next?

Cheers,

L.

---

### Post by tiglionabbit on 2005-05-31
I had no problem installing it from CVS.  However, I was helped by the good people in #zsnes on freenode, and I couldn't repeat it for you.  The new version of zsnes is a ton faster in 32 bit color, but has bad crashes all over, but fortunately never in mid play.

Btw, it's `sudo apt-get install zsnes`.  Apt-get needs a command, like install/remove/etc.  `man apt` and the pages referenced in it plz.

Link to the Past is an awesome game!  I own it on SNES and GBA and STILL I had to play it on zsnes just so I could use my bright LCD monitor, playstation controller, and the HQ2X filter that makes it look awesome.

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=tiglionabbit] playstation controller[/QUOTE]

Yep. I just bought a retrocon so I wanted the new zsnes to work. I am happy.

---

### Post by bored2k on 2005-05-31
[QUOTE=poofyhairguy]Yep. I just bought a retrocon so I wanted the new zsnes to work. I am happy.[/QUOTE]
 My brother used to work at RadioShack. He gave me this ps2 adapter.. oh my CPS2/NEOGEO games so rule with that..

---

### Post by poofyhairguy on 2005-05-31
I can safely say that Super Mario Kart works great with this new release. Quite nice I say. This howto+

[IMG]http://www.axess.com/twilight/console/detail/retrocon.jpg[/IMG] 

+

usb adaptor is fun time

---

### Post by TravisNewman on 2005-06-02
Whoa Mario Kart works? Mario Kart has never worked in ANYTHING!!!

---

### Post by benplaut on 2005-06-03
geeks  :roll:

---

### Post by statsministern on 2005-06-03
Synaptic wants to upgrade Zsnes 1.42 to 1.35... how do i get rid of that upgrade?

---

### Post by Evoreth on 2005-06-03
[QUOTE=statsministern]Synaptic wants to upgrade Zsnes 1.42 to 1.35... how do i get rid of that upgrade?[/QUOTE]
I simply locked the package in Synaptic: Package -> Lock Version.
That might not be the best solution, though.

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=Evoreth]I simply locked the package in Synaptic: Package -> Lock Version.
That might not be the best solution, though.[/QUOTE]


good idea.

---

### Post by jdong on 2005-06-03
Guys, DON't force RPM's to install on Ubuntu... that's really not a responsible thing to do.

It's much better if you just compile from source and use **checkinstall** to get it debian-aware.

---

### Post by statsministern on 2005-06-03
[QUOTE=Evoreth]I simply locked the package in Synaptic: Package -> Lock Version.
That might not be the best solution, though.[/QUOTE]

Well that works for now... I usually compiles but not in this case  :-?

---

### Post by mrt on 2005-06-03
I have no sound - any ideas?
```
mike@linus:~$ zsnes

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

Sound init failed!
freq: 32000, channels: 2, samples: 1024
ZSNES could not find any joysticks.
mike@linus:~$
```

---

### Post by Stabicron on 2005-06-05
Why can't anyone follow the handy guide in zsnes own forums and just compile it, zsnes anyways is a breeze to do. All you need is the build essential packacke and nasm. I will post the link to the easy to do insturctions.

[http://board.zsnes.com/phpBB2/viewtopic.php?t=2322](http://board.zsnes.com/phpBB2/viewtopic.php?t=2322)

Just follow the as root part and only do this small substitution
instead of:
make install
do
sudo make install

Also in the tar step they say take a close look at the tar ya get and match the filename of course *copy and paste doesn't always work* :P

When done it should be located in /usr/local/bin/ 

What I do after is use the menu editor for gnome from the unoffical ubuntu guide and make a entry for zsnes and point it to that. From then on I can run it from the menus anytime I wish. The menu editor in kde works as well.

That is the only change you will need to make for Ubuntu, runs really well too.

---

### Post by poofyhairguy on 2005-06-06
[QUOTE=Stabicron]Why can't anyone follow the handy guide in zsnes own forums and just compile it, [/QUOTE]

You can. I prefer to use Alien. You can do it either way though.

---

### Post by pdk001 on 2005-06-06
thanks for the tip. i will try it right away

---

### Post by NTolerance on 2005-06-06
[QUOTE=Stabicron]Why can't anyone follow the handy guide in zsnes own forums and just compile it, zsnes anyways is a breeze to do. All you need is the build essential packacke and nasm. I will post the link to the easy to do insturctions.

[http://board.zsnes.com/phpBB2/viewtopic.php?t=2322](http://board.zsnes.com/phpBB2/viewtopic.php?t=2322)

Just follow the as root part and only do this small substitution
instead of:
make install
do
sudo make install

Also in the tar step they say take a close look at the tar ya get and match the filename of course *copy and paste doesn't always work* :P

When done it should be located in /usr/local/bin/ 

What I do after is use the menu editor for gnome from the unoffical ubuntu guide and make a entry for zsnes and point it to that. From then on I can run it from the menus anytime I wish. The menu editor in kde works as well.

That is the only change you will need to make for Ubuntu, runs really well too.[/QUOTE]


I agree, compiling ZSNES from source on Ubuntu is easy.

---

### Post by Leif on 2005-06-06
[QUOTE=mrt]I have no sound - any ideas?
[/QUOTE]

Do you still get this ? I get this when another device is using the audio channel already. Shutdown xmms/totem etc., wait a minute or two and try again.

---

### Post by Stabicron on 2005-06-06
[QUOTE=mrt]I have no sound - any ideas?
```
mike@linus:~$ zsnes

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

Sound init failed!
freq: 32000, channels: 2, samples: 1024
ZSNES could not find any joysticks.
mike@linus:~$
```[/QUOTE]

If this is still a problem for you I have a few questions. First how did you install it? did you compile or do what was posted at the beginning. Second, what kind of sound device do you have? Is it a soundblaster or maybe onboard audio via motherboard. Third were you doing anything else that plays sound at the time? Like xmms or maybe xine or anything else that outputs sound. Some sound devices don't like it when more than one thing accesses it *usually on older devices, but yeah they still exist*.

If you installed it via the method posted at the beginning of this thread I would try getting the source and following the instructions to compile it and see if that works. Worth a shot in anycase I would think.

---

### Post by poofyhairguy on 2005-06-06
[QUOTE=Leif]Do you still get this ? I get this when another device is using the audio channel already. Shutdown xmms/totem etc., wait a minute or two and try again.[/QUOTE]

there is a way around that. Search for sound in the forum...

---

### Post by mrt on 2005-06-06
Its a soundblaster card, but uses an Ensonique driver(?).  There is also onboard audio (intel mobo) but no distro I've tried recently seems to be able to use it, so I've disabled it in BIOS and bought the aforementioned soundblaster.

No other sound app was running at the time.  I installed it according to the original post, but I'll try compiling current sources tonight.  

I thought it might be SDL related, but I was able to get the SDL version of [http://www.nexuiz.com/](http://www.nexuiz.com/) to run with sound after doing this [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

I'll post back later with what I find, thanks for the replies.

---

### Post by mrt on 2005-06-06
./configure yields
```
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required
``` 

but i'm sure sdl is installed.  "sdl-config" however is missing

---

### Post by jdong on 2005-06-07
there is a -dev package (maybe libsdl-dev?). Do a Synaptic search for sdl, and install all the -dev packages.

---

### Post by joele on 2005-06-10
This problem was easy to fix (once I found how) LOL I tried all sorts of suggestions with no results...

The solution that worked was installing 'libsdl1.2debian-all' replacing 'libsdl1.2debian-oss' which was installed by default... problem solved all apps that were missing sound now work 100%..

---

### Post by poofyhairguy on 2005-06-15
edit

---

### Post by TristanMike on 2005-06-28
I'm sorry, I'm confused now, which is the best way?  To do as the poofyhairguy said at the beginning?  Or to compile from the website?
TristanMike

---

### Post by &#12465;&#12452;&#12488; on 2005-06-28
[QUOTE=panickedthumb]Whoa Mario Kart works? Mario Kart has never worked in ANYTHING!!![/QUOTE]
It's been working in both ZSNES and SNES9x for some years now.

---

### Post by bored2k on 2005-06-28
> **&#12465 said:**
> It's been working in both ZSNES and SNES9x for some years now.
 Street Fighter Alpha has never worked though.. Not like I have needed it since the past year or so after I gave CPS2 another shot >:-D

---

### Post by &#12465;&#12452;&#12488; on 2005-06-28
[QUOTE=bored2k]Street Fighter Alpha has never worked though.. Not like I have needed it since the past year or so after I gave CPS2 another shot >:-D[/QUOTE]
Oh, I remember running Street Fighter Alpha in SNES9x! Err, it was xSNES9x, to be exact (the Xbox port). You needed to download some special graphic packs and such to make it work. I remember they implented SDD-1 decompression "on-the-fly" some time ago. All Snes9x versions over 1.42 should support Street Fighter Alpha and Star Ocean. I can't remember if the ZSNES team also implented this.

---

### Post by bored2k on 2005-06-28
> **&#12465 said:**
> Oh, I remember running Street Fighter Alpha in SNES9x! Err, it was xSNES9x, to be exact (the Xbox port). You needed to download some special graphic packs and such to make it work. I remember they implented SDD-1 decompression "on-the-fly" some time ago. All Snes9x versions over 1.42 should support Street Fighter Alpha and Star Ocean. I can't remember if the ZSNES team also implented this.
 All that fuzz to play a horrendous port ? I'm glad we have CPS2/MAME :D

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=TristanMike]I'm sorry, I'm confused now, which is the best way?  To do as the poofyhairguy said at the beginning?  Or to compile from the website?
TristanMike[/QUOTE]


It probably goes like this:

1. Use the backport- disadvantage is that it isn't the newest version of Zsnes.

2. Compile it yourself using the "make deb" command instead of "make" (after you install the program fakeroot)- disadvantage is that is compiling from source....a thing I dislike to do a lot.

3. Force the RPM using the old instructions- its the newest version of Zsnes but apt-get thinks the older version is newer (and will upgrade it if you do not lock it in synaptic). Also some think that forcing RPMs is asking for trouble. I like doing it for fun.....so I like this way best.

Do what fits you.

---

### Post by TristanMike on 2005-06-30
Merci Beaucoup (thank you)!  :) 
Tristan Mike

---

### Post by &#12465;&#12452;&#12488; on 2005-07-03
[QUOTE=bored2k]All that fuzz to play a horrendous port ? I'm glad we have CPS2/MAME :D[/QUOTE]
It was probably more to get Star Ocean working than Street Fighter, because Star Ocean is claimed to be one of SNES's best RPG's after all.

---

### Post by RagnArok on 2005-07-10
I don't get sound in my games!? this is pscyho! I've never got sound from zsnes in Ubuntu? it worked perfectly for me in Slackware?
plz do anyone know what may be the problem? xmms workes perfectly and i've done the soundfixes from the Ubuntu guide ??

---

### Post by BoyOfDestiny on 2005-07-21
Don't worry, blame esd. "sudo killall esd". then run zsnes... if you want to disable esd you can do so from gnome menu... just search for other posts on this... A LOT of people are having sound problems in hoary... please let it be gone in breezy.

---

### Post by Corp on 2005-07-31
I've tried to install zsnes 3 different ways now, and every time I get the same error. Whenever i try to run zsnes it says this: 

Could not set 512x448 video mode: No available video device

I have searched on google, this forum, and the zsnes forums and none of the suggestions have helped me. I have tried editing all of the zsnes config files i could find, but it still tries to run it in 512x448 for some reason. does anybody know why this happens, or how I can fix it? Thanks in advance.

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=Corp]I've tried to install zsnes 3 different ways now, and every time I get the same error. Whenever i try to run zsnes it says this: 

Could not set 512x448 video mode: No available video device

I have searched on google, this forum, and the zsnes forums and none of the suggestions have helped me. I have tried editing all of the zsnes config files i could find, but it still tries to run it in 512x448 for some reason. does anybody know why this happens, or how I can fix it? Thanks in advance.[/QUOTE]

What video card do you have?

---

### Post by Corp on 2005-07-31
Sorry, TI4200, I think it has the right drivers and everything, because under device manager it is listed as a TI4200, however I'm a linux noob so I wouldn't be suprised if I was wrong.

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=Corp]Sorry, TI4200, I think it has the right drivers and everything, because under device manager it is listed as a TI4200, however I'm a linux noob so I wouldn't be suprised if I was wrong.[/QUOTE]


Good. An Nvidia card. That will make it easier.


You have the official drivers?

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Does it crash and just give you an error?

---

### Post by Corp on 2005-07-31
Just installed the drivers, rebooted, and tried to run zsnes again, but it still gives the errors. Would it be easier to do this over aim?

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=Corp]Just installed the drivers, rebooted, and tried to run zsnes again, but it still gives the errors. Would it be easier to do this over aim?[/QUOTE]

I can't hit aim right now. Try something: go in synaptic and install this:

snes9express

Tell me what works with it....and we will see whats messed up and whats not.

---

### Post by Corp on 2005-07-31
Installed snes9express, it works. I dont know exactly what you need to know, but i can play games with it.

---

### Post by mjkelly on 2005-07-31
I got zsnes up and running but it lags very badly. Its framerate must be like 10 fps.

Any suggestions?

Im using an ati radeon 9250 but fglrx cant be installed for this card so im using the default driver with mesa3d. Is this the problem? Im sure i dont need any advanced 3d graphics driver to run snes graphics do i?

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=mjkelly]I got zsnes up and running but it lags very badly. Its framerate must be like 10 fps.

Any suggestions?

Im using an ati radeon 9250 but fglrx cant be installed for this card so im using the default driver with mesa3d. Is this the problem? Im sure i dont need any advanced 3d graphics driver to run snes graphics do i?[/QUOTE]

hmm....have you tried the program three posts above?

---

### Post by poofyhairguy on 2005-07-31
[QUOTE=Corp]Installed snes9express, it works. I dont know exactly what you need to know, but i can play games with it.[/QUOTE]

Sound works? Joystick works? Plays well?

---

### Post by Corp on 2005-07-31
Sound works, plays well, but my snes controller using a super smart joy usb adapter does not work after following your other how to.

edit:
It seems the controller doesnt work because it is looking for js0 in /dev instead of in /dev/input

edit 2:
figured out how to change where it looked for the joystick, works fine now :cool:

---

### Post by mjkelly on 2005-07-31
Sound works fine. It says no joysticks detected also.

When i move the mouse around the screen it skips heavily. I think 10fps was an overstatement its more like 2-3 fps. Like if i move the mouse just a slight ammount it skips all the way across the screen. Also the response time is very bad. Like theres a 1-2 second delay from anything i press on the keyboard til its reflected in the game.

EDIT
ok i just turned on the fps and it is between 3-4 fps
EDIT again...
ok i fixed it. i had to turn the resolution up to a higher standard and now its working fine.

---

### Post by Corp on 2005-08-02
Anyone else have any ideas as to why it gives me that error?

---

### Post by TristanMike on 2005-09-30
Out of curiosity, what kind of processor use should I be getting with the Zsnes? Right now, when I start it up and am on the blue screen where I choose my roms, it eats 100% of my processor while on the screen. When a game is loaded, it's hovers anywhere between 75%-85%. Is this a normal usage for the Zsnes? Could some other people please confirm what their Zsnes eats up of the processor. That seems like a lot of juice.
Thank You
TristanMike

---

### Post by DirtDawg on 2005-09-30
[QUOTE=poofyhairguy]
EDIT
------------------------------------------------------------------------------------------------------------------------------
There is now a better way to get newer Zsnes.
Thank Seth for making this new package.[/QUOTE]

Is there a ppc package?

---

### Post by BoyOfDestiny on 2006-05-16
[QUOTE=DirtDawg]Is there a ppc package?[/QUOTE]
Nope.

Anyway, I just want to let everyone know that the zsnes cvs repository is no longer updated. They are now using SVN.

Here is a little script I made to download and build it. 

Make sure you have the dependencies and subversion installed!

#!/bin/sh
svn co [https://svn.bountysource.com/zsnes/trunk/](https://svn.bountysource.com/zsnes/trunk/) zsnes-svn
cd zsnes-svn
cd src
make clean
./autogen.sh
make

---

