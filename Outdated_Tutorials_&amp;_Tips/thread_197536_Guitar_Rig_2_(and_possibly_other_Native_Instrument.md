---
title: "Guitar Rig 2 (and possibly other Native Instruments apps)"
date: 2006-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by miscz on 2006-06-15
[COLOR="YellowGreen"]NEW HOW-TO:[/COLOR]
(is it me / my browser or do the Ubuntu Forums color links in a weird way?)

Adam0509 created useful scripts for installation of Guitar Rig. New ones use [PlayOnLinux](http://www.playonlinux.com/en/presentation.html), here are [english](http://www.playonlinux.com/topic-932.html) and [french](http://www.playonlinux.com/forums/see_topic.php?topic=884) ones.
The old version (regular script) is [here](http://adam050986.free.fr/linux/).
I have not tested them, I'm not the author so ask adam0509 if you have trouble :)

alternatively:
(It may not work with new Wine versions! Wine 0.9.51 break things according to Adam0509)
1. Install wine-dev and jack/libjack-dev packages. Build-essential package is needed too, obviously.
2. Download WineASIO sources [here](http://people.jacklab.net/edogawa/files/wineasio/). Neither VST nor ASIO SDK are needed as far as I can tell.
3. Compile WineASIO and add it to Wine:
```
make
sudo cp wineasio.dll.so /usr/lib/wine
regsvr32 wineasio.dll.so
```
4. Start Jack via QJackCtl, configure it to get good quality and low latency (realtime kernel might help so you might want to install it, custom RT kernel is available as a normal package since Ubuntu 7.10)
5. Run Guitar Rig via Wine (the executable, not VST plugin), it still might not run at the first tries so repeat until it starts.

Enjoy!
Thanks for the tip, eightdollarbeer!

A little tip for Audigy SE users as I had some trouble with getting recording to work properly: disable Capture Feedback, set Analog Source to Mic, set Digital Source to i2s in, set Shared Mic/Line in to Mic. Make sure IEC958 is disabled too if you want any sound output at all :)

[COLOR="Red"]FOLLOWING HOW-TO IS OUTDATED[/COLOR]
It might be usefult to somebody so I won't delete it :)
[COLOR="DimGray"]
It's my first time writing a how-to and I'm not a native speaker so if something is hard to understand - ask :) I'm writing this howto after I managed to get GR2 running so there might be certain steps missing, I'll try to check it later or respond to questions.

First of all, we need to install via apt:
-wine, wine-dev, winlib, winelib-dev from Dapper repositories (0.9.9) for registering GR2 and as a dependency
-jackd, libjack0.100.0-0, libjack0.100.0-dev, qjackctl, libasound2-dev - Jack is a low latency audio server we'll connect GR2 to

Configuring audio in Wine
-Run winecfg and select Jack as an output

Compilation of FST (open source thingy for opening Steinberg VST plugins)
-Get FST 1.7.1 from [here](http://joebutton.co.uk/fst/) and extract it somwhere
-Get Steinberg VST SDK 2.3 from [here](http://www.steinberg.de/532+M52087573ab0.html)
-Extract and put vstsdk2.3 directory into fst-1.7.1 directory
-Compile fst with make (no ./configure or make install involved)
-Fst binary is ready to go, run it later with ./fst *path-to-the-vst-plugin*

Getting Guitar Rig 2 on Ubuntu
I installed GR2 while using Windows and moved Guitar Rig 2 directory and VST plugin (it's optional during installation but we need it). Installing GR2 via Wine might be possible but I do not have install CD at the moment.
Run Registration Tool with wine and complete registration process. Typing serial number on Wine 0.9.12 (most recent one in Wine repositories) is broken so use Dapper repository version. Do not attempt to run Guitar Rig 2.exe with Wine, it will break stuff (I don't know how, you can fix it by creating new config).

Fun begins :)
-Start Jack with QJackCtl (Jack Control), closing other audio apps might be required. For getting as low latency as possible consult other howtos, I've got 5ms with just messing with setting and it's good enough for me.
-Go into wherever you've put FST and run ./fst */path/to/Guitar Rig 2.dll*, sometimes it won't work, kill wine process and try again, you should be able to succeed usually in 1-4 tries
-Using Jack Control connect ALSA capture to GR2 input and GR2 output to ALSA playback
-In GR2 preset properties set correct paths to preset banks and component templates (they're in GR2 directory)

Play your guitar and remember - it must be connected! :P I've spent few minutes trying to figure out what did I do wrong when all I had to do is insert a plug into my guitar :-\"

[edit]
It would be nice if anybody said if it works or not :)
BTW, most of the credit must go to radekrazor who made most of the progress in getting GR2 to work, I've just made a compilation of information from old GR2 topic in Dapper dev forum.[/COLOR]

---

### Post by gibson on 2006-06-21
Great howto - ive been waiting for something like this for a while.

What soundcard do you have?

I have a [http://www.maudio.co.uk/products/en_gb/FireWireSolo-main.html](http://www.maudio.co.uk/products/en_gb/FireWireSolo-main.html) aswell as my sblive, but would rather use the maudio for my guitar... one of the few things keeping my in windows!

Just can not get the maudio card to work ](*,) 

all the best 
G

---

### Post by miscz on 2006-06-22
Right now I use built in AC97 (Intel or Realtek, not sure), it sucks but I guess it's good enough for a begginer guitarist like me. I can't help you with M-Audio, I have no experience with such hardware. I will probably get some real sound card soon but nothing as advanced/expensive, most likely PCMCIA SB Audigy.

---

### Post by yeehawjared on 2006-08-25
I'm having problems doing this:
-Extract and put vstsdk2.3 directory into fst-1.7.1 directory
-Compile fst with make (no ./configure or make install involved)

Extracting into folders isn't the problem... make never works because it can't find what it's looking for.  Here's my error:

jared@lappy:~/Desktop/fst-1.7$ make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
cp: target `./vst' is not a directory
make: *** [hackheaders] Error 1

from the README:
2) Unzip the SDK into xfst's root directory.

3) Type 'make'. If everything works correctly this should create an
   executable file called 'xfst'.

I need help organizing my folders so that make works

---

### Post by The Soundophiliac on 2006-08-26
It works alright but Guitar Rig keeps asking me for some direcotries all the time, although I did set the directories in preferences. It also doesn't load any banks.

---

### Post by yeehawjared on 2006-08-26
how did you get fst to compile?  What's your directory structur like when you execute make?

mine looks like this.  There's a zip file in vstsdk that I extract into fst's directory.  Tried moving the directories around a few times, make still can't find the vstsdk it's looking for.

/fst-1.7.1
/fst-1.7.1/vstsdk2.3/source/....

---

### Post by The Soundophiliac on 2006-08-26
I think I did just what you did. Then I changed to /fst-1.7.1 and ran make. The vstsdk folder (whatever the name of that was) I extracted was inside a zipfile inside the file I downloaded.

---

### Post by miscz on 2006-08-26
> **The Soundophiliac said:**
> It works alright but Guitar Rig keeps asking me for some direcotries all the time, although I did set the directories in preferences. It also doesn't load any banks.

Set paths to banks in third settings tab, in presets section. It works mostly right for me but it always sorts the list alphabetically. Make sure that you try to access banks on Linux partition, not the Windows one.

yeehawjared:
Which version of FST are you trying to compile? It seems that you're trying 1.7 and this stuff is very picky about versions (I don't really know why)
> jared@lappy:~/Desktop/fst-1.7$ make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
cp: target `./vst' is not a directory
make: *** [hackheaders] Error 1

---

### Post by The Soundophiliac on 2006-08-27
> **miscz said:**
> Set paths to banks in third settings tab, in presets section. It works mostly right for me but it always sorts the list alphabetically. Make sure that you try to access banks on Linux partition, not the Windows one.

Did just that.
In which directory do you have the .dll? That might be of some importance.

---

### Post by miscz on 2006-08-27
I've made GR2 reside in my local apps directory (/home/miscz/apps/Guitar Rig 2) and GuitarRig2.dll is in /home/miscz/apps/. I don't think it's important where do you put it, just make sure you have correct permissions, maybe they messed up when you copied GR2 from Windows partition.

If it doesn't help you can always use a workaround and import banks every time you run GR2.

---

### Post by powder22 on 2006-08-27
When I goto select Audio in winecfg, winecfg locks up and im unable to select audio. In terminal is says this: 

winecfg
/home/tom/.wine/user.reg is not a valid registry file
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
*** glibc detected *** double free or corruption (out): 0x7c181e00 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
err:seh:raise_exception Unhandled exception code c000013a flags 0 addr 0xffffe410err:seh:raise_exception Unhandled exception code c000013a flags 0 addr 0xffffe410

Not sure what to do to make it work, or if it will at all. If anyone knows how to fix this, please let me know.

---

### Post by yeehawjared on 2006-09-16
I'm still having problems doing this:
-Extract and put vstsdk2.3 directory into fst-1.7.1 directory
-Compile fst with make (no ./configure or make install involved)

I download fst-1.7.1.  I extract it to desktop
I download vstsdk2.3.  I extract it to desktop. In that folder is another zip flie.  I extract that.  I put that last folder into fst-1.7.1

I open a terminal cd /home/jared/Desktop/fst-1.71./
I run make and get an error.

take a look at this screenshot.  You can see the directory structure and error message

Has anyone done compiled this lately?  I feel like i've tried every directory combination possible.  What should I do?  Thanks guys

---

### Post by venublood on 2006-11-19
> **yeehawjared said:**
> I'm still having problems doing this:
-Extract and put vstsdk2.3 directory into fst-1.7.1 directory
-Compile fst with make (no ./configure or make install involved)

I download fst-1.7.1.  I extract it to desktop
I download vstsdk2.3.  I extract it to desktop. In that folder is another zip flie.  I extract that.  I put that last folder into fst-1.7.1

I open a terminal cd /home/jared/Desktop/fst-1.71./
I run make and get an error.

take a look at this screenshot.  You can see the directory structure and error message

Has anyone done compiled this lately?  I feel like i've tried every directory combination possible.  What should I do?  Thanks guys

I have done the same and worked fine for me, sorry man :( .
I'm running Edgy. First, I've tried with fst-1.8 but didn't work due to issues with lash. Then, changed to fst-1.7, downloaded vstsdk2.3, extracted it, extracted again another zip and moved the folder to the fst-1.7 dir, typed make and the executable was made. 
I have some troubles to find the "Guitar Rig 2.dll", so it's on Program Files/Steinberg/VstPlugins/ or /Program Files/VstPlugins.
Sometimes ./fst /dir/Guitar Rig 2.dll doesn't work, but trying again a few times works.
Thanks a lot for this how-to!!
Here's a screenshot under Edgy:
[IMG]http://img157.imageshack.us/img157/2517/guitarig2bc0.png[/IMG]
I only need now to fix midi sound on Guitar Pro to get rid of Windows...
Excuse my english...

---

### Post by shu on 2006-12-27
Guys I've compiled everything and I can launch GuitarRig, make connections in QJackCtl and so on. But I cannot do anything with the GuitarRig window, can't change any dials, nothing.. what could be wrong?

---

### Post by ogaitnas123 on 2007-07-16
More edits: Later I'll try at home: remove the spaces from the path or names for the guitar rig stuff, reading at winehq, seems like [spaces] causes some confusion at wine.

What version of wine are using ? --- edited: ignore, stupid question, you list your wine version at the first post... must read carefully
But after you mention some dapper version... you can run wine --version and tell what version exactly it is, thanks.


I follow all the steps, and various vst's runs fine. Ex.: Amplitube 2, Amplitube Jimi Hendrix, Other free 
vst amp sims, like freeamp2 also runs.

I'm asking because Guitar Rig installed and activated as normal with wine, but the vst doesn't  
opens, fst starts, then it do nothing and do not exit with error.

I'm asking cos' I'll try to recompile my wine at home to match the version that you're using, at this
time I'm using fedora 7 with his standard wine...

---

### Post by ogaitnas123 on 2007-07-16
Just adding that removing the spaces from the names of the directories I managed to run GuitarRig
(1 not gr2) with success :D

---

### Post by eightdollarbeer on 2007-07-24
a must for guitar rig and wine .google wineasio jacklab has the source . grab that get the asio sdk or asio.h from somewhere you will also need wine devel and i thing jack devel . pit the asio.h into the untarred wineasio directory make make install then as the user u use wine with run regsrv32 wineasio.dll . run wine cfg select audio select jack close. install the audio software non vst eg standalone for guitar rig . run jack with quackctl . run the sound app go into audio settings select asio as your driver then you have the rig running no fst no dssi just works even better than b4. this works with just about every audio application i can throw at it. auto connects the lines aswell. 

yes say you love me.

---

### Post by GuilhermeBrant on 2007-10-08
I've already got lash and jack and wine installed,and downloaded the vst sdk and the fst.
 Now what do I do?Where do I extract them to?And how do I compile it?If you could give me the exactly commands I'll have to use,and their meaning I would really appreciate it.
  Thanks!

---

### Post by miscz on 2007-10-23
1. Install wine-dev and jack/libjack-dev packages. Build-essential package is needed too, obviously.
2. Download WineASIO sources [here](http://people.jacklab.net/edogawa/files/wineasio/). Neither VST nor ASIO SDK are needed as far as I can tell.
3. Compile WineASIO and add it to Wine:
```
make
regsvr32 wineasio.dll.so
```
4. Start Jack via QJackCtl, configure it to get good quality and low latency (realtime kernel might help so you might want to install it, custom RT kernel is available as a normal package since Ubuntu 7.10)
5. Run Guitar Rig 2 via Wine (the executable, not VST plugin), it still might not run at the first tries so repeat until it starts.

Enjoy!
Thanks for the tip, eightdollarbeer!

A little tip for Audigy SE users as I had some trouble with getting recording to work properly: disable Capture Feedback, set Analog Source to Mic, set Digital Source to i2s in, set Shared Mic/Line in to Mic. Make sure IEC958 is disabled too if you want any sound output at all :)

---

### Post by adam0509 on 2007-11-15
> **miscz said:**
> 1. Install wine-dev and jack/libjack-dev packages. Build-essential package is needed too, obviously.
2. Download WineASIO sources [here](http://people.jacklab.net/edogawa/files/wineasio/). Neither VST nor ASIO SDK are needed as far as I can tell.
3. Compile WineASIO and add it to Wine:
```
make
regsrv32 wineasio.dll.so
```
4. Start Jack via QJackCtl, configure it to get good quality and low latency (realtime kernel might help so you might want to install it, custom RT kernel is available as a normal package since Ubuntu 7.10)
5. Run Guitar Rig 2 via Wine (the executable, not VST plugin), it still might not run at the first tries so repeat until it starts.

Enjoy!
Thanks for the tip, eightdollarbeer!

A little tip for Audigy SE users as I had some trouble with getting recording to work properly: disable Capture Feedback, set Analog Source to Mic, set Digital Source to i2s in, set Shared Mic/Line in to Mic. Make sure IEC958 is disabled too if you want any sound output at all :)


Tryed with guitar rig 3 demo, but didn't work...

---

### Post by adam0509 on 2007-11-21
Hi,


Tested again with a *hum* [SIZE="1"]TPB t*rr&#8364;nt[/SIZE]...

Works !!!


I've made a small script, here it is :


```

#!/bin/bash



echo -e "This script will install Guitar-Rig (and probably other Native Instrument App easily\n"

echo -e "Let's install Ubuntu package\n"

## If you use Fedora, maybe you should use "yum" or so...

sudo apt-get install wine wine-dev qjackctl libjack-dev

## Creating a specific wineprefix

wineprefixcreate --prefix "/home/$USER/.wine_gr/"

## configuring Wine

echo -e "\n\n\n IMPORTANT : Choose JACK in Audio setting !!!\n\n\n"

env WINEPREFIX="/home/$USER/.wine_gr/" winecfg

cd wineasio-0.5/

make

env WINEPREFIX="/home/$USER/.wine_gr/" regsvr32 wineasio.dll.so

cd ..

## Change "Guitar Rig 3.0.exe" to your *.exe file !!

echo -e "\n\n\n JUST INSTALL GUITAR-RIG 3 AND DON'T TICK ANYTHING AFTER \n\n\n"

env WINEPREFIX="/home/$USER/.wine_gr/" wine "Guitar Rig 3.0.exe"

## It's a generic desktop, feel free to edit it before executing the script

cp GR.desktop /home/$USER/Desktop/

cp GR.desktop /usr/share/applications



echo -e "\n Hit ENTER to quit !"

read enter

exit 0

```


I suggest you to get the full archive, with README, wineasio and Desktop file !

[http://adam050986.free.fr/linux/](http://adam050986.free.fr/linux/)


HAVE FUN GUYS

:guitar:





P.S : there is an error in your post, about "regsrv32" : it's regs**vr**32

P.S2 : I got sound not working perfectly because of my ******* DELL UBUNTU 6400n and integrated sound-card... Please post if it works for you !!!



[B]
EDIT :[/B]

I'm not sure JACK is necessary in fact... it seems to work with alsa too... please test and post ^^

---

### Post by yeehawjared on 2007-11-27
awesome, can't wait to try.  I'll post my results tonight.

---

### Post by spacepluk on 2007-11-28
Thanks for the update :)

I had to copy the compiled .so by hand to make it work:

```
sudo cp wineasio.dll.so /usr/lib/wine
```

and then:

```
regsvr32 wineasio.dll
```


Saludosss

---

### Post by yeehawjared on 2007-12-02
got guitar rig 3 to install and execute... awesome. 

Now I need it to work with my low-latency external sound card - a Tascam US-122.

I got my tascam working, but not through Guitar rig.  I'm going to try messing around with JACK.

See screenshot to see what I'm working with.

---

### Post by adam0509 on 2007-12-06
erm... don't know... did you select the good devices ??? (I see hw:1, this seems correct to me...)


...I think you should test with other Jack Apps (Audacious, hydrogen...), make it work (get on jack related forum), and then try again with Guitar-Rig...



What about guitar rig ? Good sood ? Work without jack ? Crashes or not when changing effect ?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9936](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9936)

---

### Post by adam0509 on 2007-12-23
can't succeed to compile wineasio now... duh...


you'll find pre-compiled file here :

[http://www.kvraudio.com/forum/viewtopic.php?t=182682&postdays=0&postorder=asc&start=0&sid=29c262c9c45eca2f95b13f81b58f1355](http://www.kvraudio.com/forum/viewtopic.php?t=182682&postdays=0&postorder=asc&start=0&sid=29c262c9c45eca2f95b13f81b58f1355)

EDIT : It's impossible to compile with Wine-dev 0.9.51, use 0.9.50 or maybe 0.9.52...



Thus, i've made a PlayOnLinux script, so you'll get usr-friendly install. Check :

[B]French version :
[/B]
 [http://www.playonlinux.com/forums/see_topic.php?topic=884](http://www.playonlinux.com/forums/see_topic.php?topic=884)


[B]English version :
[/B]
[http://www.playonlinux.com/en/topic-932-GuitarRig2amp3.html](http://www.playonlinux.com/en/topic-932-GuitarRig2amp3.html)



Instructions :

0) Copy script to a file
1) Download PlayOnlinux
2) Run it
3) Get in Tools>Execute a non official script
4) Choose the file ou copyed the script into
5) Enjoy !
6)... maybe you'll need to tweak wineversion (get in tools>Change wine version or something like this)

---

### Post by AdiNX on 2008-01-22
i just wanted to thank you for this how-to..
the same method works for Guitar Rig 3 by the way :guitar:

---

### Post by Burillo on 2008-02-13
anyone got M-Audio FireWire Solo working? 'cos if not - i'll have to boot up Windows for that...

---

### Post by sofamensch on 2008-02-20
for compiling newest asio version you need to get gcc-3.4 (this special version) for some reason. the others wont do it.

and also you need asio.h which can be found via google: file:asio.h.

I included the latest Asio (0.7.2) with the asio-fix found on the website compiled.

---

### Post by mdk7 on 2008-03-07
I can't get this to work no matter how hard I try, it's getting very frustrating.

Guitar Rig 3 is installed and opening in Wine, the WINE ASIO driver is selected in guitar rig but nothing I try to connect in JACK has any effect.  (I can hear the normal "clean signal" of the guitar when it's plugged in but Guitar Rig doesn't sense any input.

[[IMG]http://img146.imageshack.us/img146/7793/screenshotconnectionsjagc7.th.png[/IMG]](http://img146.imageshack.us/my.php?image=screenshotconnectionsjagc7.png)

I tried the PlayOnLinux method and when it asks me to select where the .EXE is it defaults to the "C drive" under the .playonlinux folder even though the real .EXE for the installed program is in .wine, so I pointed it to there the first time and no dice.

Can someone please help me figure this out.  I'm frustrated as all hell about this after just wasting hours on it.

---

### Post by sofamensch on 2008-03-19
I must admit i never got it working too.
Maybe the new Ubuntu Sound Engine that replaces Alsa will fix that for us?

For now we have to Dual-Boot :-(

---

### Post by Kronie on 2008-06-14
Hey, guys. I have this cheap Behringer iAxe393 USB guitar.. and it relies on bitchy ASIO driver that's specifically  designed for the guitar. the driver is compatible only with windows(xp, Vista) and Mac OSX.. as far as i know, if i make the remote machine, it will use "virtual" sound devices and all the usb stuff, and wine wont launch the asio setup.. so is there any way i can install my guitar under ubuntu? i dont really want to switch back to windows just because of that..

---

### Post by joes_meat on 2008-08-02
Trying to run it with Wine 1.0 on Ubuntu Hardy.
Anyone had experience with this?

$ wine Guitar\ Rig\ 3.exe 
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:RegisterDeviceNotificationA (hwnd=0x10028, filter=0x32fcc8,flags=0x00000000),
	returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationA (hwnd=0x10028, filter=0x32fcd0,flags=0x00000000),
	returns a fake device notification handle!

---

### Post by Tails9 on 2008-10-16
I have the same messages.

I can't get it working either.
I couldn't get wineasio and wineasio-x (I'm on x64 here) to compile because it couldn't find libjack, although it was installed.

I tried both the precompiled wineasio 0.5 and 0.7 but I can't select ASIO under Guitar Rig (3) at all. Guitar Rig runs fine besides that.

When I select ASIO in GR3, I get al these red xrun messages in JACK, and GR crashes when I try to select it a second time.
I'm not using the RT kernel yet.

So, what is all this "xrun" and why can't I select ASIO in GR? (must have something to do with eachother)

---

### Post by babin on 2008-10-27
I have a ubuntu 8.04 and I could run Guitar rig 3 with wine. but I can't install USB interface driver.

I need It...! sombody help me:(

---

### Post by kurotenshi on 2009-04-15
Hi, i've been tring to install GuitarRig 3 on Jaunty and I can't seem to make it work with any of the guides in here. Install goes well but then it just not starts.

Using wine 1.0.1

---

### Post by aenima1891 on 2009-04-22
i'm using jaunty and i have the same problem

---

### Post by Wa59 on 2009-05-01
I'm using jaunty, Guitar Pro runs well, but there is no sound at all, even tough wineasio is selected in the audio settings.

---

### Post by Tails9 on 2009-05-02
> **Wa59 said:**
> I'm using jaunty, Guitar Pro runs well, but there is no sound at all, even tough wineasio is selected in the audio settings.

You mean Guitar Rig?

---

### Post by wsjunior on 2009-06-13
Just forget it guys, it will never work correctly.

The only option is to use this ugly Rakarrack instead.

[http://rakarrack.sourceforge.net/](http://rakarrack.sourceforge.net/)

---

### Post by gromipakao on 2010-03-05
Hey guys, just wanted to let you know that Guitar Rig 4 works like a charm (way less latency than in windows! ) on my Ubuntu 9.10, just followed the first step in this post, and found wineasio installation documentation when I had trouble converting it to a debian executable...btw, my machine is quite archaic no 64 stuff...:)

---

### Post by marshello5 on 2010-03-06
nice to hear :D
i'm waiting traktor pro in ubuntu...?

---

### Post by Tails9 on 2010-03-06
Thanks for letting us know, I was waiting for news like this :)
I wonder if it works on x64 too...

---

### Post by Everynameistaken on 2010-03-09
I'm actually trying to get Guitar Rig 4 to work with Ubuntu 64-bit as we speak.

I can hear my guitar playing through in Jack, I can select the WineASIO driver in Guitar Rig's setting and the program seems to be running just fine, but I get no input or output activity.

---

### Post by Everynameistaken on 2010-03-09
Uh, correction on that one.  I just got it to work.

So yeah, it does with with 64-bit.  But only after a lot of blood, sweat, and tears.

---

### Post by Tails9 on 2010-03-09
Would you like to give a brief explanation on how you did it? 
I would find it very useful :)

---

### Post by Everynameistaken on 2010-03-09
Unfortunately, I'm a complete newbie at this whole Linux gig so I probably can't say much of any intelligence on it.  There was a lot of trial and error and ignorant flailing around.

It was basically the same process as the 32-bit method.  I needed the 64-bit version of WineASIO, Jack and the control GUI for it, and the latest version of Wine.  

I installed Jack from Synaptic and downloaded a .DEB file that auto-extracted ASIO to the proper directories. Then I used [regsvr32 wineasio.dll.so] to get Jack, Wine, and ASIO all simpatico, I guess (I honestly don't know enough about terminal commands to have any clue what I really did here - thank God for the internet.)

At that point, I just needed to use the Jack "Connections" tab after Guitar Rig was running to link my system input to Guitar Rig's input and then Guitar Rig's output to system output.  It didn't seem to matter what audio driver I was using in Wine or anything.  ALSA worked the same as Jack.

I think that was the whole thing.  I'm sure somebody more knowledgeable than me could write an actual how-to if they'd like.

---

### Post by gromipakao on 2010-05-04
hey guys, remember me? I bragged about my perfect guitar rig setup under karmic koala a few posts back:) well, I switched to lucid and now I'm just not able to install wineasio, when I do it the way I did it before, on karmic, I can see it in guitar rig's setup, I can select it, but the sample rate is 0 and no other choice is available...damn. Just wanted to know if there are similar experiences or maybe a solution, I wanna play my goddamn guitar through a virtual marshall :) thanks in advance

---

### Post by ynos313 on 2010-05-12
GR 4 Pro works well on Ubuntu Studio Lucid for me, but I have some shorts Xruns sometimes. I juste installed wineasio, I run Jack then GR 4, it connects to jack automatically, and I can play :guitar:




(Sorry if my english is bad, I'm french :mrgreen:)

---

### Post by Demeo on 2010-05-13
Licid, Gutar Rig 4, works, BUT i can't change latency. In Jack set 10 ms, but in GR4 i'ts always 68 ms and don't change after changing in Qjackctl

SOLVED with changing ~/.jackdrc

---

