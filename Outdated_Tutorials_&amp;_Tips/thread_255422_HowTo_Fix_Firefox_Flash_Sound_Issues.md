---
title: "HowTo: Fix Firefox Flash Sound Issues"
date: 2006-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Old Pink on 2006-09-11
*Sometimes flash just doesn't produce sound, or you can find flash will "give up" playing sound after a given period. Use this fix to stop that. *

Easy as pie. :)

Open terminal, and enter: 
```
sudo aptitude install alsa-oss
```Wait for the install to complete, before typing: 
```
gksudo gedit /etc/firefox/firefoxrc
```A file will open, and in the file you will see: 
> FIREFOX_DSP=&#8221;none&#8221;Change this to:
> FIREFOX_DSP=&#8221;aoss&#8221;Hope this helps you all. :)

***Update: **I have been notified that this also works on Firefox clones/forks such as "Flock" :) *

---

### Post by Old Pink on 2006-09-13
If this helps you, please leave a comment. :)

---

### Post by frequenicity on 2006-09-13
This is indeed the fix. Sound will still be slightly out of sync (most notable in streaming video after the initial 20 seconds or so...off by about 1/2 a second) but that, as far as I know, is out of our hands.

---

### Post by brianC on 2006-09-13
I can here again Ican hear agian.....  just can't spell!!!!!

---

### Post by 3rr0r on 2006-09-19
anyone know how to apply this fix to opera?

---

### Post by telperion on 2006-09-19
> **3rr0r said:**
> anyone know how to apply this fix to opera?

aoss opera

---

### Post by mrgnash on 2006-09-19
Didn't make any difference.

---

### Post by KDayz on 2006-09-19
woot, i think it works now. Thanks alot been looking for this fix. Why doesnt firefox just fix this glitch?

---

### Post by dalee on 2006-09-19
Hi,

Thanks for this HOWTO! I had lost the sound in FireFox. It now works again!

dalee

---

### Post by evilghost on 2006-09-19
Thanks for the fix but I'm not sure that this isn't just a band-aid.  Prior to the updates on Sept 19 I didn't have out of sync issues nor was flash an issue.  I installed the updates and flash no longer produced sound.  I used the fix documented above and tried both "aoss" and "alsa" and both produce the same out of sync issues with "alsa" being less of out of sync.

---

### Post by andiii on 2006-09-20
great, that did it for me!

I just had to to change the Swiftfox Launcher command into "aoss swiftfox"

---

### Post by dmizer on 2006-09-20
doesn't seem to make a difference for me at all.  it use to be WAY out of sync, but now it's in sync.  i have no idea what i did to get the sound in sync, but this was not the fix.  maybe has something to do with having installed totem-xine or maybe w32codecs?

with aoss, i can play one flash video.  after which firefox locks.
without aoss, i can play two flash videos.  after which firefox locks.

---

### Post by phormion on 2006-09-22
This fix doesn't work for me. 

I'm running Dapper, with esd, which seems to be the default. Whether esd is running or killed, if I put FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc and then start firefox, and then try to open a video on youtube, it only plays for the first second or so, then freezes. This happens *always* - it's very easy to reproduce on my Ubuntu install. 

Of course I have aoss installed (from alsa-oss), I've also tried running firefox as 'aoss firefox' or using a script that calls 'aoss /usr/lib/firefox/firefox ...'. No success yet. 

Somebody was saying this is caused by the cache setting being to small, so I've set browser.cache.disk.capacity to 100MB in Firefox, but it still doesn't help. 

Any other ideas?

edit: I have Flash 7.0r63 (not the latest I see) and Firefox 1.5.0.7. I've downloaded the latest updates today.

---

### Post by KDayz on 2006-09-23
Ok i used the above fx above but now i noticed that my Firefox freezes alot especially when it tries to load a page that has flash on it. I'm not sure why this is happening. anyone experience this also?

---

### Post by lH)4~mK0e on 2006-09-23
you don't need alsa-oss you can edit the "none" value to "alsa" not "aoss"

---

### Post by phormion on 2006-09-24
> **miwarlock002 said:**
> you can edit the "none" value to "alsa" not "aoss"

No you can't. As far as I read the script, the FIREFOX_DSP variable should hold the name of a binary that can wrap around /dev/dsp access (like esddsp, artsdsp or aoss). There's no binary name 'alsa' on my Ubuntu installation, and I don't recall ever encountering such a program. 

Also, the firefox script checks to see if FIREFOX_DSP holds a program name (the 'if type $FIREFOX_DSP' line). 

edit: Using FIREFOX_DSP *still* doesn't work for me after upgrading to flahplugin 7.0r68 and amarok 2:1.4.3-0ubuntu6~dapper1. Videos are still freezing after one second. 

edit2: It seems that you have to use amarok for a while in order for the flash plugin not to be able to play sound; if you start firefox, fire up a web page on youtube and then close it (keep firefox open), then play a few seconds of an mp3 in amarok, and then open another youtube video, everything works ok. However, if you let amarok play for a while and then retry using youtube or bolt in firefox, oops, no sound. You have to restart firefox.

---

### Post by maddbaron on 2006-09-24
Well I entered it I hope it works later.


> **telperion said:**
> aoss opera

How do I do that?

---

### Post by lH)4~mK0e on 2006-09-24
ok, my mistake.  I had none.  My sound did not work.  I switched to alsa.  It worked.  I was just sharing my experience.  Sorry if it didn't work for you.  aoss didn't work too good for me.  Seemed to make my flash pages hang.  Hope it works for others.

But then again, I have seriously altered my sound installation.  I have installed libsdl1.2debian-all and libopenal0a.

---

### Post by phormion on 2006-09-24
miwarlock002, could you tell me what you get if you type the following in a shell, please? 

$ which alsa

$ dpkg -S `which alsa`

Also, did you alter your firefox startup script? What output do you get if you run firefox from a terminal with 'firefox -V'?

---

### Post by TigerCR1200 on 2006-09-24
It worked for me, however it was just a quick test. It did work while I was playing an MP3 in Rhythmbox as well. I will try later today to make sure it is still working as that seems to be somewhat of a problem as well.

---

### Post by myo on 2006-09-24
> **maddbaron said:**
> 
How do I do that?

just open opera with "aoss opera" it seems to work.

---

### Post by lH)4~mK0e on 2006-09-24
> **phormion said:**
> miwarlock002, could you tell me what you get if you type the following in a shell, please? 

$ which alsa

$ dpkg -S `which alsa`

Also, did you alter your firefox startup script? What output do you get if you run firefox from a terminal with 'firefox -V'?

I have tried both of these commands and produced no results.  I did remember, however that I ran:

```
gstreamer-properties
```

and specified Advanced Linux Sound Architechture.  I did edit the /etc/firefox/firefoxrc file to reflect "alsa."  None will attempt to use esddsp or esd itself so I think that's why it worked.  I could put in "auto" and it would probably still work.  I just know that as None it didn't have audio on youtube.  It could have just been a random occurance as well.  Also, I did not install the ubuntu repository install of flash simply because it would produce an error state on install.  Sorry for the lax information initially.  I had to retrace all of my steps from setup.

---

### Post by Rob2687 on 2006-09-24
It doesn't freeze when I use esddsp

---

### Post by phormion on 2006-09-24
miwarlock002, thanks for replying. However, I'm thinking that it might be something else that fixed the problem irrespective of the change you made to firefoxrc. If 'alsa' is not a valid binary on your machine (as proven by you saying which alsa doesn't print anything) and you haven't changed your firefox startup script (/usr/lib/firefox/firefox), chances are you are running the browser without any DSP wrapper, just like the FIREFOX_DSP value would be set to 'none'. 

How 'bout the output of 'firefox -V'? It should print what DSP wrapper it uses.

---

### Post by lH)4~mK0e on 2006-09-24
> **phormion said:**
> miwarlock002, thanks for replying. However, I'm thinking that it might be something else that fixed the problem irrespective of the change you made to firefoxrc. If 'alsa' is not a valid binary on your machine (as proven by you saying which alsa doesn't print anything) and you haven't changed your firefox startup (/usr/lib/firefox/firefox), chances are you are running the browser without any DSP wrapper, just like the FIREFOX_DSP value would be set to 'none'. 

How 'bout the output of 'firefox -V'? It should print what DSP wrapper it uses.

Here is the output:

```
FIREFOX_DSP=alsa
APPLICATION_ID=firefox
CMDLINE_DISPLAY=
DISPLAY=:0.0
OPTIONS=
DEBUG=0
DEBUGGER=
Running: /usr/lib/firefox/firefox-bin -a firefox
```

---

### Post by Rob2687 on 2006-09-24
It defaults to another one (probably auto/esd) if the one in firefoxrc is invalid.

Just enter some random thing in there and it will still work.
FIREFOX_DSP=blalhballh

---

### Post by phormion on 2006-09-24
OK, so it's how I suspected, firefox gets run as if FIREFOX_DSP would be set to 'none' - the important part is what comes after "Running: ". 

If I put FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc, I get: 

> 
...
Running: aoss /usr/lib/firefox/firefox-bin -a firefox


As you can see, firefox is being run through aoss. However, if I use either "none" or "alsa", the result is the same: 

> 
...
Running: /usr/lib/firefox/firefox-bin -a firefox


As far as I can see, no DSP wrapper is used in either of the last 2 cases - there shouldn't be any difference between using "alsa" or "none" in firefoxrc (you could try replacing alsa with anything else that is not a binary name and see what happens). Since FIREFOX_DSP is not exported by the script, it's not visible in the firefox binary's environment, so it can't make any difference after the script has called the firefox binary. 

So if you don't have problems with sounds in Flash and interaction with other applications using sound, I don't think it's because of the firefoxrc setting. Unfortunately I don't know that much about gstreamer to figure out if it makes a difference. 

On a positive note, somebody from Adobe showed a demo of Flash 9 on Ubuntu at some conference recently: [http://blogs.adobe.com/penguin.swf/2006/09/flashforward_linux_demo.html](http://blogs.adobe.com/penguin.swf/2006/09/flashforward_linux_demo.html). I thought it's worth mentioning, since I thought that complaining to Adobe was one way to ensure that the flash plugin gets fixed, and this is at least proof that something is being done in their camp.

---

### Post by lH)4~mK0e on 2006-09-24
Yeah I am finding that out.  I put in "auto" and now when I run firefox -V I get this:

```
FIREFOX_DSP=
APPLICATION_ID=firefox
CMDLINE_DISPLAY=
DISPLAY=:0.0
OPTIONS=
DEBUG=0
DEBUGGER=
Running: /usr/lib/firefox/firefox-bin -a firefox
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]

```

... but it still works.  gstreamer perhaps? esd is not running as verfied in the System Monitor process tab list..

---

### Post by phormion on 2006-09-24
miwarlock002, I've no idea. 

However, I've tried something I wanted to do for some time (and Rob2687 was suggesting it, too) - use FIREFOX_DSP="esddsp". The video and sound are delayed (but so are they if you don't use any DSP wrapper), but at least the audio plays without interruptions. 

Rob2687, I think the change that broke most people was to change the default FIREFOX_DSP value in the firefox script from "esddsp" to "none", at least that's what this comment from the script implies:

> 
...
if [ -z "${FIREFOX_DSP}" ]; then
    #FIREFOX_DSP="auto"
    FIREFOX_DSP="none"
    # esddsp is dreadful, see [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760)
fi


Being a developer myself, I honestly don't agree with the change (explained in the page linked). esddsp might be buggy and have limitations, but it got the job done for people. I think there are way more people affected by this change than the ones that hit the limitations of esddsp. I think warning users about the script's limitations would've been a lot more appropriate.

---

### Post by mhavila on 2006-09-26
I was experiencing the same symptoms. Ubuntu 6.06 with Firefox 1.5.0.7 and Flash Player 7.0.68, alsa-oss package installed and FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc.
Flash videos (like in YouTube or Google Video) play with no sound, and always hang after 1 or 2 seconds playing.

But, the following solution by Daniel Carrera at launchpad.net solved the problem. Now the videos play smoothly and with sound! :-D
[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12)

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

I hope this helps.
Marcio Avila,
Brazil

> **phormion said:**
> 

I'm running Dapper, with esd, which seems to be the default. Whether esd is running or killed, if I put FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc and then start firefox, and then try to open a video on youtube, it only plays for the first second or so, then freezes. This happens *always* - it's very easy to reproduce on my Ubuntu install.

---

### Post by andb on 2006-09-27
The above solution is one Ive been using for a while and it is trully the best.
The only difference in my set up is that I used:

ln -s /tmp/.esd-1000 /tmp/.esd

Flash is just looking for a different esd socket. Try this. Sound syncs up perfectly, no need for aoss...

the 1000 is just the default user id, so the socket there is real.
If this works for you, then lets stop telling people to use aoss!
Happy youtubing!

---

### Post by termite on 2006-09-27
Nothing works for me.  I've tried alsa-oss, and I've tried this new solution.  No sound whatsoever.

Any ideas?

---

### Post by andb on 2006-09-27
termite, does sound work in general? Do you have ESD enabled in System>Preferences>Sound? Is it possible you forgot to remove one of the sound config files from the other solutions?

---

### Post by termite on 2006-09-27
Yes, sound does work in general.  I can play mp3's with amarok and I get startup/shutdown sounds.

No idea re sound config files.  If you could, tell me how to start from a state in which I installed alsa-oss, but my firefoxrc is set to "none", and I used the above trick with your socket 1000 addition, back to a clean state so I can start over.  Then tell me what to do from the beginning.  I seem to have changed too many things.

Macromedia need to get on and fix this stupid bug...

---

### Post by lH)4~mK0e on 2006-09-27
If you are watching a flash movie and want sound, then anything else with sound must be closed.  esd and the like, are still all centered around the antiquated OSS so you are pretty much at their mercy.  I tried to research exactly why mine just worked from the ICH6 AC97 sound card I have being friendly to it, but there were times it worked out of the box and times it didn't (I have done several reinstalls for research purposes).  I modified my gstreamer-properties under a suggestion for mixing to ALSA and it still doesn't help me have multiple audio going unless it's contained in the Ubunutu umbrella.  Flashplayer, is going to use OSS because it's easier to patch than do a full release.  Hopefully in 9 this will be addressed.  Basically with the gstreamer modified, I can open anything that is within ubuntu (i.e.gaim and rhythmbox) and have the two of them able to use sounds at the same time.  However, if I open something that uses my sound then I will not have sound in flash.

---

### Post by yacine on 2006-09-30
Thanks Matt.H your solution worked!

---

### Post by hikaricore on 2006-10-05
woot, you're my hero, even works for swiftfox :)

---

### Post by beercz on 2006-10-11
> **Matt.H said:**
> *Sometimes flash just doesn't produce sound, or you can find flash will "give up" playing sound after a given period. Use this fix to stop that. *

Easy as pie. :)

Open terminal, and enter: 
```
sudo aptitude install alsa-oss
``` 
Wait for the install to complete, before typing: 
```
sudo gedit /etc/firefox/firefoxrc
``` 
A file will open, and in the file you will see: 
 
Change this to:
 
Hope this helps you all. :)
Thanks Matt.H - very helpful :-)

---

### Post by Ximinez on 2006-10-13
No result at all for me. :(  Any other ideas?

Ximinez

---

### Post by Ximinez on 2006-10-13
Wow!  Thanks, that worked great.  I booted up that window and switched mine to ESD.  Now its working great!  No delay, no issues that I can find as of yet.

Thanks!
Ximinez

> **miwarlock002 said:**
> I have tried both of these commands and produced no results.  I did remember, however that I ran:

```
gstreamer-properties
```

and specified Advanced Linux Sound Architechture.  I did edit the /etc/firefox/firefoxrc file to reflect "alsa."  None will attempt to use esddsp or esd itself so I think that's why it worked.  I could put in "auto" and it would probably still work.  I just know that as None it didn't have audio on youtube.  It could have just been a random occurance as well.  Also, I did not install the ubuntu repository install of flash simply because it would produce an error state on install.  Sorry for the lax information initially.  I had to retrace all of my steps from setup.

---

### Post by robcarr2 on 2006-10-13
I use Flock (its the new browser by Mozilla and is based on the FireFox engine) and this worked for me too :)

---

### Post by drewsimon on 2006-10-13
Awesome! Thanks Matt! This fixed my problem. :)

---

### Post by Bobseye on 2006-10-13
This fix worked great, thanks!

---

### Post by familyjules74123 on 2006-10-18
I did this, and it did not work. This is what I got after the first command which is why I think it doesnt work, but I'm new to ubuntu so I'm not really sure what I', supposed to do.

> mike@mike-laptop:~$ sudo aptitude install alsa-oss
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


---

### Post by lamadredelsapo on 2006-10-18
Great fix. Thanks for this one :D

---

### Post by raeb on 2006-10-18
Worked like a charm.  Thanks a lot  :D

---

### Post by PixelCloud on 2006-10-19
downloading the flash player 9 beta fixes these problems also :D

---

### Post by PixelCloud on 2006-10-19
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

---

### Post by wilberfan on 2006-10-19
> **mhavila said:**
> 
But, the following solution by Daniel Carrera at launchpad.net solved the problem. Now the videos play smoothly and with sound! :-D
[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12)

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

This killed my sound completely!!    Anyone know how to 'undo' these commands?

---

### Post by nickpaton on 2006-10-19
> **PixelCloud said:**
> downloading the flash player 9 beta fixes these problems also :D

Install details can be found here:

[http://www.ubuntuforums.org/showthread.php?t=279990]("http://www.ubuntuforums.org/showthread.php?t=279990")

Big thanks to bruenig :p

---

### Post by Bobseye on 2006-10-20
When first tried this was a fix. However now the problem persists and I have to redo fix which works sometimes but not always. Very frustrating. I am a real novice and I really appreciate Old Pink's step by step walk through of the fix. Any ideas on a permanent fix?

---

### Post by wilberfan on 2006-10-20
> **Bobseye said:**
>  Any ideas on a permanent fix?

There are half-a-dozen threads here about the release of a Flash 9 beta...  I don't know how well that will address this issue...  I wuz gonna try it this weekend!  :-?

---

### Post by st1100pilot on 2006-10-21
Worked perfectly! Thanks!!

---

### Post by wilberfan on 2006-10-21
Interesting.

I got Flash 9 installed, but it does NOT fix the sound lag problem...  :(

---

### Post by GStubbs43 on 2006-10-21
> **wilberfan said:**
> Interesting.

I got Flash 9 installed, but it does NOT fix the sound lag problem...  :(

How did you install it? Did you restart your browser?
Did you read [this?]("http://www.ubuntuforums.org/showthread.php?t=280252")

---

### Post by wilberfan on 2006-10-21
> **GStubbs43 said:**
> How did you install it? Did you restart your browser?
Did you read [this?]("http://www.ubuntuforums.org/showthread.php?t=280252")

I installed it based on these instructions:  [http://ubuntuforums.org/showthread.php?t=279990]("http://ubuntuforums.org/showthread.php?t=279990")
and DID restart the browser...

...but here's what's weird.   Check out this youtube video of The Who:  [http://www.youtube.com/watch?v=rrQZZSCFSpw]("http://www.youtube.com/watch?v=rrQZZSCFSpw")

It's HORRIBLY out of sync--but many of the others [(here]("http://www.youtube.com/watch?v=WI_k4eocK4Y&mode=related&search=") or [here]("http://www.youtube.com/watch?v=0KxOTr4jnNc&mode=related&search=")) are FINE!  :-k    Did I pick the ONE odd video--or is something else going on?!  :confused:

---

### Post by GStubbs43 on 2006-10-21
Yeah, that one video is totally out of sync. So if the other ones work, then I think you installed it fine. What does about:plugins say (If you are using Firefox)

---

### Post by wilberfan on 2006-10-21
> RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.25

Yeah...what are the odds that I'd pick a youtoob that was that far out of sync to test my Flash 9 installation?!   

D'oh!  #-o

---

### Post by Ambimom on 2006-10-21
Opera uses firefox plugins.

Just make sure that in your Tools Advanced Content Plugins the path for plugins includes mozilla firefox;

And...if your plugin list has a bunch: mozilla, firefox, netscape, and opera

Remove all but opera and firefox....delete the others.

---

### Post by The Geoff on 2006-10-21
I've had constant problems with FF/Flash audio, the above fix worked but then gave up, but I've recently installed the Flash 9 beta and all is good with the world again :)

---

### Post by Lux Perpetua on 2006-10-22
This seems to have fixed my problems. I just tested it on one YouTube video and one Google Video video, neither of which had sound for me in the past.

---

### Post by Old Pink on 2006-10-24
> **Lux Perpetua said:**
> This seems to have fixed my problems. I just tested it on one YouTube video and one Google Video video, neither of which had sound for me in the past.

That's good to hear. :)

---

### Post by jwdvd on 2006-10-24
you da man :-D

---

### Post by Sirron on 2006-10-29
ok, I figured that since the sound worked before, I don't need to download anything. So I skipped the first step, and it works fine. Was that a bad idea :???: ?

---

### Post by SebMKd on 2006-10-30
> **Lux Perpetua said:**
> This seems to have fixed my problems. I just tested it on one YouTube video and one Google Video video, neither of which had sound for me in the past.

Upgraded Dapper with Firefox 2, ran this script and still don't have sound with these websites! ](*,)

---

### Post by techweenie on 2006-11-02
I am running AMD64 Dapper with Firefox32 and Flash 9 beta and I get no sound whatsoever with flash.  Flash 7 worked perfectly, but when I upgraded to 9 it stopped.  I went through all the fixes I could find but nothing has helped so far. Any suggestions?

---

### Post by Alpha_Maverick on 2006-11-27
yay!!! I have audio!!!
TY!
TY!
TY!
TY!
TY!
:) 8)

---

### Post by kubuntux on 2006-12-08
> **SebMKd said:**
> Upgraded Dapper with Firefox 2, ran this script and still don't have sound with these websites! ](*,)

After the upgrade to Firefox 2.0 I experienced the same problem.
The following worked for me:
open firefoxrc file
```
sudo nano /etc/firefox/firefoxrc
```
change ```
FIREFOX_DSP="aoss"
``` to ```
FIREFOX_DSP="none"
``` and save the changes.

Now just restart Firefox 2 and verify if it worked for you too. ;)

**ByeZ!**

---

### Post by Nim on 2006-12-11
Hey,

my computers sound is working for everything, eg dvds and even listening to radio on bbc4 website. But when I try to watch programmes on dailymotion (they're using a macro falsh player 7) it's suddenly stopped playing sound (it was working up until 3 or 4 days ago). I'm not sure what has changed (I think I may have installed some updates). 

I sure these and wanted to try the fix, however am VERY new to Linux and am not sure what the "terminal" you need to open is (to enter the code into). 

Please help me :-)

---

### Post by Nim on 2006-12-11
I just found the firefoxrc file and it says this:
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

does anyone know what this means?

---

### Post by beercz on 2006-12-11
> **Nim said:**
> Hey,

my computers sound is working for everything, eg dvds and even listening to radio on bbc4 website. But when I try to watch programmes on dailymotion (they're using a macro falsh player 7) it's suddenly stopped playing sound (it was working up until 3 or 4 days ago). I'm not sure what has changed (I think I may have installed some updates). 

I sure these and wanted to try the fix, however am VERY new to Linux and am not sure what the "terminal" you need to open is (to enter the code into). 

Please help me :-)
To get to the terminal (where you will enter commands via the 'command prompt') do this:
Click on the Applications menu;
Click Accessories;
Click Terminal.

A window will appear containing the command prompt, with a flashing cursor.  Type the commands here.

When you have finished, type 'exit' and press the ENTER key.  That will close the terminal window.

Good luck!

---

### Post by Nim on 2006-12-11
Thank you so so much :-) :-) it worked!

I really am so grateful. Thanks so much for the help!

xxx

---

### Post by beercz on 2006-12-11
> **Nim said:**
> Thank you so so much :-) :-) it worked!

I really am so grateful. Thanks so much for the help!

xxx
You're welcome.

Glad it's all working for you now.

---

### Post by Aviatrixie on 2006-12-12
Just a quick note to let you know my Ubuntu box was shelved for a couple months while I upgraded my son's box and when I put my box back in service the updates hosed my Flash sound. A forum search led me to this thread and I did the actions in the first post:

HowTo: Fix Firefox Flash Sound Issues
Sometimes flash just doesn't produce sound, or you can find flash will "give up" playing sound after a given period. Use this fix to stop that.

Easy as pie.

Open terminal, and enter:
Code:

sudo aptitude install alsa-oss

Wait for the install to complete, before typing:
Code:

sudo gedit /etc/firefox/firefoxrc

A file will open, and in the file you will see:
Quote:
FIREFOX_DSP=”none”
Change this to:
Quote:
FIREFOX_DSP=”aoss”
Hope this helps you all. 

That fixed the problem... good job!

Still using Dapper 386. 

Just thought I'd let you know. :)


Trixie

---

### Post by sirlancelot on 2006-12-12
My sound was fixed after upgrading to the latest Flash 9 Beta (78 i think).

It IS beta though so it might still cause problems for some people. I haven't had any though.

---

### Post by Statik on 2006-12-12
No matter what I try I cannot seem to get sound from flash in firefox 2. I've even uninstalled flash and reinstalled it using the instructions in this thread. Everything reports as being installed correctly, but nothing. Any ideas on where to look?

Statik

---

### Post by ge5239 on 2006-12-12
oh gosh.. it's working, thank you ;D

---

### Post by chombee on 2006-12-13
Nim wrote:
> I just found the firefoxrc file and it says this:
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760).

does anyone know what this means?

Just from reading what you posted, I think it means that if you set the FIREFOX_DSP option to "auto" or "esd", for example if you change the line to:

```
FIREFOX_DSP="auto"
```

then you might have problems with Firefox becoming unstable, due to a bug in firefox. And you can find info about the bug on this (rather technical) web page: [https://launchpad.net/malone/bugs/29760](https://launchpad.net/malone/bugs/29760)

It looks like it should be perfectly safe to set the FIREFOX_DSP option to "aoss" as the instructions in this thread recommend, so you don't need to worry about the bug.

Although you probably won't understand the bug report (I didn't) at least you can see that all known bugs in Ubuntu are publicly reported on that website, and discussion about the bugs and possible fixes to them are public too. Anyone can participate in reporting bugs, providing information about bugs, commenting on bugs and their possible solutions, or (if you have the time and skill) submitting fixes for bugs. This is quite different to (say) bugs in Windows!

P.S. from the bug report it sort of looks like the bug might have been fixed, so the comment you found in the firefox rc file might just be out of date anyway.

---

### Post by penguinland on 2006-12-17
This worked great. Thanks!

---

### Post by GameMaster on 2006-12-19
can u ppl tell me wher is terminal ? i cant find it. plz help me some1. i got the same problem

---

### Post by Statik on 2006-12-19
errr . . . If you have the default Ubuntu install, just click the little 'Applications' word in the top right, in that menu, hover over Accessories and in the new menu you should see terminal.

Hope that helps.

Statik

---

### Post by Statik on 2006-12-19
As a followup for my problem, I had the sudden 'duh' moment where I decided to run firefox from terminal to see if any errors occured. After visiting youtube.com I have tons of this sort of thing:
```

ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card

```

I'm gonna see if I can grab whatever happens at the initial visit as well.

Statik

---

### Post by Statik on 2006-12-19
Hmmm. Only seems to happen the first time I visit a flash site after booting. After that nothing happens.

Statik

---

### Post by mordox on 2006-12-19
it works !!

---

### Post by baLes on 2006-12-19
Hmm, I followed all the steps but I still can't get my sound to work but it still plays the video.

---

### Post by zippy028 on 2006-12-20
I tried many fixes for flash and sound and none seemed to work. I finally fixed the problem by going to the prog. menu /system/preferences/sound. I had the option to select a default sound card. My choices were (1) USB device.  (2) Nvidia Nforce2  (3) MPU-401-ART. The default was set to USB device. I selected the #2 option and had to repeat this about three times before my choice stuck. After this I have working sound with flash in Firefox. I am using Dapper with Firefox 1.5.0.8 using a 2.6.12-27-K7 kernel. I have also installed the alsa-oss pkg. and use the aoss option in /etc/firefox/firefoxrc file.

HTH,
John

---

### Post by Statik on 2006-12-20
I only have one choice here . . . the NVidia CK804   That's it.

Statik

---

### Post by craig700 on 2006-12-22
I'll second Statik, suffering all the same problems. I've seen the same console messages from firefox, and gedit even reports the same failures from terminal:

"- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo."

my setup is:
Edgy 6.10, Firefox 2, Alsa-oss installed, firefoxrc is set to aoss (though i've tried everything else), System/preferences/sound are set to ALSA, Dell D800, Intel 82801DB-ICH4 is my only sound card.

The sound works fine on xine, xmms, everything that need sound for. I'm not sure what Gaim wants or does. Flash 7 worked, roughly.

I've, near exhaustively, tried the suggestions in existing posts, including various firefoxrc settings and various installation sources and techniques. 

This is most disagreeable, and has irritated me.

Craig

---

### Post by DarkStarAeon on 2007-01-14
I tried this, with both: FIREFOX_DSP=”aoss” and FIREFOX_DSP=”alsa”

still no sound from flash.

sigh.

---

### Post by plafuro on 2007-01-18
Maybe i'm a bit late... but... [Flash 9 has finally been released for linux]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4")...

I saw some time ago debs with the beta already... lets see how long it takes to have them for this very last release...

---

### Post by craig700 on 2007-01-18
This new flash, it does nothing. I remain in silence.

---

### Post by paszczak on 2007-01-20
Same problem, new flash 9 (final) and no sound. More, none of the solutions works for me. That is soo sad :/

---

### Post by ge5239 on 2007-01-27
oh no.. 
decided to upgrade to ff 2.0. now i've lost my flash sound. :(

---

### Post by burnt on 2007-01-31
Fix worked for me. Running Firefox 1.5.0.9.

What does alsa-oss do?

---

### Post by burnt on 2007-01-31
Ok, I noticed that though sound works for sites using flash, it also cause Firefox to hang/crash/freeze for some of those sites. When I force quit Firefox and try to restart, I get an error stating that Firefox is still running and to close Firefox first or restart my computer. Not sure what the reason for this is.

---

### Post by joN_jai on 2007-01-31
Try this 


sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

---

### Post by vmalloc on 2007-02-01
Hi, everyone...

I tried the steps above but nothing seemed to help. 

I'm running Ubuntu Edgy with firefox 2.0 which I installed myself from the Mozilla site.
I also have Adobe Flash 9,0,31,0 from the Adobe website installed.

I tried restarting, setting the FIREFOX_DSP to "alsa" or "aoss", tried running firefox with "aoss firefox" - 
nothing helps, sound doesn't working at all.

I also tried the symlink thingie with /tmp/esd.1000 (which I think is an ugly hack which by definition won't survive reboots, but whatever).

Suggestions, anyone????

Thanks in advance...

---

### Post by James_Nostack on 2007-02-02
I am running Firefox 1.5.0.9 and Dapper 6.06 LTS.  I'm using Flash player 7 (I think).  The "aoss" fix worked for several weeks, aside from occasionally having to force-quit Firefox, but with the latest upgrade of Firefox (late January, 2007) it doesn't seem to work any more.

---

### Post by CaveRat on 2007-02-05
I am using FF2 and was using Flash9 and did not have sound no matter what I did. It seems Adobe knew about this problem and fixed the glitch in Linux Flash Player 9 beta 2. I downloaded and installed it and now have sound. [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by vmalloc on 2007-02-07
The page directs to the version I already have (9,0,31,0)...
It is really frustrating that no one knows why this happens - Flash isn't such a far-fetched demand from a desktop OS....

Does anyone know how to roll back to flash 9 beta 2 by force? links are welcome...

---

### Post by Tmi on 2007-02-13
I'm having the no-sound-in-flash-problem too. Seems to be quite common here on the forums.

Does anyone know if it is like this in all distros, or is it something special with Ubuntu? Hope it works better with Feisty if it is so :)

Right now I've pretty much given up on getting sound. If I really need to watch a flash I'll do it in windows on my laptop :(

---

### Post by ssavelan on 2007-02-14
Unfortunately, this did not help.  I was watching Elephant's Dream after trying to work out audio stuff with WINE.  Sound was fine.  Realplayer has sound.  I don't know where my flash sound went though.  errr...:mad: 

First Ubuntu problem in quite some time though.

---

### Post by ssavelan on 2007-02-14
ALSA lib confmisc.c:1283:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3972:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

when I save

...DSP="alsa"

"aoss" didn't work so I thought I would give it a try.

---

### Post by ssavelan on 2007-02-14
The error message posted above actually happens independent of dealing with that file as some experts may recognize.... it happens even when I just run gedit from the terminal.

Well, I have this other partition that runs xubuntu for just such an occassion.  On this one I also have the beta alsa driver...

1.0.14rc2

but, I only have it configured to run the Echo layla24 and ignore the onboard... via-82xx i believe.

The newest driver runs great.  The echomixer is way better than the one for windoze in my biased opinion.. anyway....

I run Edgy-Ubuntu (on my favored partition with all the goodies that had both sound cards running strong for a few weeks) and Edgy-xubuntu on this partition.

It was so sweet, I could run JACK off of the layla and surf/watch movies/play games with the onboard sound, simultaneously, like 10 things at the same time.

I am considering starting a new mint install (my drive is partitioned for just such a cop-out to be convenient) and documenting my every move (especially sudo.... audio stuff, configuration) for the sake of my own trouble-shooting, but also because it might be useful for ubuntu audio in the future.

Who is the Ubuntu audio master and where do I find him/her?  I want to help.

I was trying to get Flash sound back, at first, everything else was working, then JACK would not start, and today, no default device recognized, no onboard soundcard, can't get a sound to come out of that install.

I am going to try:
[URL="http://www.ubuntuforums.org/showthread.php?t=26567"]
http://www.ubuntuforums.org/showthread.php?t=26567[/URL]

and it's siblings, children and relatives to see if I can fix my situation.

Others might find it helpful... the links are old and not recently amended though... if anyone know of more current similar info...

Thanks
:KS

---

### Post by ssavelan on 2007-02-14
I want to subscribe to this link, but don't know how to without posting.

Ubuntu rocks!

Where is the Ubuntu Studio Team?  Some Windows fan laid down the gauntlet to me and said that Ubuntu will never catch-up to MSwin.  We must defend our OS's honor.

---

### Post by odzx on 2007-02-26
i used to get sound with flash before but after compiling alsa 1.0.14rc2 (could not record before doing that) sound in flash stopped working.  when i run fire fox from the terminal and and run a flash animation i get this message repeating it self until i turn flash off: 
> ALSA lib ../../../src/pcm/pcm_direct.c:1509:(snd_pcm_direct_parse_open_conf) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_direct.c:1509:(snd_pcm_direct_parse_open_conf) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189:(_snd_pcm_plug_open) Unknown field hint

can anyone tell me what this message means?

---

### Post by ssavelan on 2007-02-28
As you can see above, I had a similar problem.  I have successfully compiled that driver with one and two sound cards.  In the case above I had to reinstall ubuntu altogether.

If you were using the ALSA directions on their site, you might want to try a few lines of code that I suppose are ubuntu/debian specific.  From:

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")

there are a couple of extra commands, perhaps symbolic links and such that Ubuntu may need that are not listed in the ALSA directions.

(listening to a Google video right now on my laptop)

good luck!

---

### Post by odzx on 2007-02-28
thanx. i'll try that.

---

### Post by ssavelan on 2007-02-28
let me know if it that works for you.

I was mostly thinking of the 

sudo cp ...../firmware/ea something or other/  into the the /your-kernelversion#.#### etc

I think that that may be important in Ubuntu.

---

### Post by vigleik on 2007-02-28
> **Tmi said:**
> I'm having the no-sound-in-flash-problem too. Seems to be quite common here on the forums.

Does anyone know if it is like this in all distros, or is it something special with Ubuntu? Hope it works better with Feisty if it is so :)

Right now I've pretty much given up on getting sound. If I really need to watch a flash I'll do it in windows on my laptop :(

I've been having the same problem. Tried all the fixes, none of them worked. Then I tried the latest build of SimplyMEPIS, and much to my surprise flash 9 was already installed and working. With sound. Flash even played nice with other programs using sound.

So at least in my case it's not like this in all distros. So for now I'll use mepis (though it has its own problems), and I'll check back to see if there's any improvements in ubuntu when the next version comes out in April.

---

### Post by ssavelan on 2007-03-01
that's too bad that you couldn't get flash-sound working with ubuntu.

What kind of hardware do you have?

---

### Post by odzx on 2007-03-01
> **ssavelan said:**
> As you can see above, I had a similar problem.  I have successfully compiled that driver with one and two sound cards.  In the case above I had to reinstall ubuntu altogether.

If you were using the ALSA directions on their site, you might want to try a few lines of code that I suppose are ubuntu/debian specific.  From:

[https://help.ubuntu.com/community/EchoMia]("https://help.ubuntu.com/community/EchoMia")

there are a couple of extra commands, perhaps symbolic links and such that Ubuntu may need that are not listed in the ALSA directions.

(listening to a Google video right now on my laptop)

good luck!
thanks for the reply
well i tried recompiling alsa this way, but it made no difference.
i have a pentium d processor and my sound card according to aplay -l is:
> oded@oded-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

anyway i followed the howto from the link you posted but i could not run the ./configure or the make command as a normal user. only with sudo.

---

### Post by Genesius on 2007-03-02
Here's one for you: Firefox/Swiftfox sound had been working fine, then suddenly stopped. I have system sounds, sound in videos played through VLC/Kaffeine/Mplayer, just nothing in the browser. When I use "sudo aplay -l", I get this:

> [noparse]**** List of PLAYBACK Hardware Devices ****
ALSA lib control.c:816:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:231: control open (0): No such file or directory
ALSA lib control.c:816:(snd_ctl_open_noupdate) Invalid CTL hw:1
aplay: device_list:231: control open (1): No such file or directory
[/noparse]

I've tried reinstalling alsa-oss and alsa-utils with no improvement. Any suggestions?

---

### Post by inthepit on 2007-03-03
this is a possible fix:

```
$  modprobe snd-pcm-oss

```

seemed to do the trick for me

going to restart and see if it still works.  will reply in a moment or edit

**EDIT**
Restarted and still works!!! woot!!!  sound on youtube again!!!

---

### Post by ssavelan on 2007-03-03
> **odzx said:**
> thanks for the reply
well i tried recompiling alsa this way, but it made no difference.
i have a pentium d processor and my sound card according to aplay -l is:

anyway i followed the howto from the link you posted but i could not run the ./configure or the make command as a normal user. only with sudo.

If you can't run ./configure --with-cards=etc,etc

You may have a fairly robust problem.  I know that the VT82xx runs well, though.  You are getting sounds in other programs than flash?  If so, that is strange.  

(%If your install is not too tricked out,- well, i recommend the following anyway) 

I recommend making a mint install.  I have tangled my ALSA configuration past the point of no return several times.  A fresh install and the above posted instructions, done cleanly, from the top, seems to make a nice stable sound system for me.  Another  strategy that I have used with success is having a couple of partitions of ubuntu on my main machine.  if you have the space, it allows you to experiment to the point of system breakage on one install and be able to shuffle your important files back and forth while breaking installs with impunity.  In this way you can eventually figure the perfect sequence of commands to get a dynamite, fully functional (sound) system.

Just a thought, if you have the time for major tinkering.  Having a couple of installs can give you a bit of mind peace.

;)

---

### Post by odzx on 2007-03-03
> If you can't run ./configure --with-cards=etc,etc

You may have a fairly robust problem. I know that the VT82xx runs well, though. You are getting sounds in other programs than flash? If so, that is strange.
yes i do have sound working with all other programs. the VT82xx was recognized when i first installed edgy on this machine, sound was working system wide, including flash. the thing that made me recompile alsa was that i could not get any sound out of my mic. volume control used to look like this:
[http://www.23hq.com/odzx/photo/1672978/view-large?album%5fid=1672974]("http://www.23hq.com/odzx/photo/1672978/view-large?album%5fid=1672974")
now it looks like this:
[http://www.23hq.com/odzx/photo/1718286/view-large]("http://www.23hq.com/odzx/photo/1718286/view-large")
now i can record and use my mic with skype but no more flash sound.
> I recommend making a mint install. I have tangled my ALSA configuration past the point of no return several times. A fresh install and the above posted instructions, done cleanly, from the top, seems to make a nice stable sound system for me. Another strategy that I have used with success is having a couple of partitions of ubuntu on my main machine. if you have the space, it allows you to experiment to the point of system breakage on one install and be able to shuffle your important files back and forth while breaking installs with impunity. In this way you can eventually figure the perfect sequence of commands to get a dynamite, fully functional (sound) system.
i guess that is the way to do it. though i just had to reinstalled a week ago, when i couldn't log on any more , after one to many alsa recompiling. i guess I'd rather do without flash sound for a little longer then going through all of that again. 
using another install on different partition could be a good idea.
thanks a lot for the advice

---

### Post by inthepit on 2007-03-03
could someone else please try the suggestion i made.  just wondering if it is just me it worked for.

---

### Post by Genesius on 2007-03-03
> **inthepit said:**
> could someone else please try the suggestion i made.  just wondering if it is just me it worked for.

Gave it a try, no help.

---

### Post by odzx on 2007-03-04
didn't work for me either.
tried feisty to. didn't work.
for now I'm using "media pirate" firefox extention and VLC player. it seems to do the job well.
good luck

---

### Post by ssavelan on 2007-03-04
> **odzx said:**
> didn't work for me either.
tried feisty to. didn't work.
for now I'm using "media pirate" firefox extention and VLC player. it seems to do the job well.
good luck

Yeah, one of my friends really love VLC for everything.

I use totem-xine with the mozilla-plugins and libxine-extracodecs + realplayer + flash

He likes training VLC to everything, which is apparently possible.  I am not sure that VLC will do all of the embedded flash stuff.  Does anyone know if VLC will do embedded flash?

---

### Post by odzx on 2007-03-04
> **ssavelan said:**
> Yeah, one of my friends really love VLC for everything.

I use totem-xine with the mozilla-plugins and libxine-extracodecs + realplayer + flash

He likes training VLC to everything, which is apparently possible.  I am not sure that VLC will do all of the embedded flash stuff.  Does anyone know if VLC will do embedded flash?

for me VLC was not able to play embedded flash directly. i tried using it with the "media connectivity" plugin for Firefox. VLC did not complain about anything but did not play the file. thats why i use the "media pirate" extension to download the embedded file and then play it with VLC.

---

### Post by zzjing on 2007-03-19
Anyone found anything new yet?  I am using flash9 and firefox2 and none of the fixes works for me.  :-(

---

### Post by Statik on 2007-03-19
I broke down and did a fresh install of Edgy. Sound works great now . . . in fact, I've got every program I've been struggling with installed and working. I even took the opportunity to create a separate home partition this time so I won't have the same difficulty doing reinstalls next time.

Statik

---

### Post by ssavelan on 2007-03-19
> **Statik said:**
> I broke down and did a fresh install of Edgy. Sound works great now . . . in fact, I've got every program I've been struggling with installed and working. I even took the opportunity to create a separate home partition this time so I won't have the same difficulty doing reinstalls next time.

Statik

Yeah, I tell a lot of people to make a couple of ubuntu partitions... especially if sound is not completely satisfactory out of the box.  Allows for experimentation with the idea, "it's okay if I can never boot to this partition again" lol.  It seems that there are a lot of problems with over-riding ubuntu by building newer ALSA's over it and behind it's back.  With scientific experimentation you can find what works and what doesn't.

Sometimes everything works right out of the box and the sound preferences will even let you change the default to your USB device or something equally pleasantly surprising.  Sometimes a HOWTO is so on that you can follow it and get what you want and never think about it again.

I had to wreck at least a dozen installs before I could get my 2 device sound system working exactly how I wanted.

The more you mess up, the more you learn.

P.S. if you are having difficulty with a 64-bit Ubuntu.. try 32-bit

---

### Post by Mujaheiden on 2007-07-13
Hi,

I have a problem with my [USB audio in flash]("http://ubuntuforums.org/showthread.php?t=462907"), and your tip didnt make a difference. But thanks anyway.

---

### Post by spock959955 on 2007-07-21
Refer to this thread:
[http://ubuntuforums.org/showthread.php?t=398577]("http://ubuntuforums.org/showthread.php?t=398577")

The fix listed there seemed to work for me

Good Luck

---

### Post by johnn1949 on 2007-07-29
It fixed sound on CBS innertube for me

---

### Post by direwolf08 on 2007-08-03
Unfortunately, this did not work for me.  I have my computer hooked up to my receiver via digital coax output.  Here is part of the error I get (basically this just repeats):

```
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM spdif
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM plughw:0,0
```

notice the "Unkown PCM pluginhw:0,0". I assume that is referring to card 0, device 0. My digital out is 0,1. Interestingly enough, I don't hear audio when I plug headphones into the speaker jack, either. Is there any way to tell firefox to use card 0, device 1 (my digital output)?  Incedentally, startup sounds and system sounds don't seem to work either.

The output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and my asound.conf file:
```
pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}
```

My system: AMD 64x2 3800+, feisty 7.04 (32bit), integrated nv 6150 gfx, and as seen above, ALC883 7.1 audio.

---

### Post by jshbbe on 2007-08-13
This fixed my Firefox+Flash sound issue.  I would be playing music on Rhapsody.com and everytime I would go to a site with Flash it would get all fuzzy for a few seconds.  Now it doesn't do that anymore, plus I can hear sound from multiple Flash programs being run.  Thanks!

---

### Post by Tomone on 2007-08-18
My sound is finally working again. Since there are so many different problems everyone could have, I probably had to try 15 different solutions before I finally got one that worked for me.
Thank you Spock for posting that link.

---

### Post by Xizorbg on 2007-09-08
Hey Guys-

Using AMD64 w/ M-Audio 7.1 - no dice changing the firefoxrc file.

Any ideas on how I can get it going or other approaches - otherwise Ubuntu Rocks!


Thanks, X

---

### Post by Depilator on 2007-09-09
Try the solution on the bottom of page 3 of this thread. That did the trick for me.

Tried the aoss one first tho so it may be a lucky combination of the two.

---

### Post by Kevinphilp on 2007-09-13
I tried several of the fixes here and finally found something that worked. From another website try

sudo chown -R "usernane":users /home/"username"/.macromedia

Seems when you install macromedia flash it installs the .macromedia file as root and is not accessible to the ordinary users.

---

### Post by rare HERO on 2007-10-22
> **Old Pink said:**
> If this helps you, please leave a comment. :)

This did not work for me.  I still have flash video but no audio after "upgrading" to 7.10

---

### Post by rare HERO on 2007-10-22
> **phormion said:**
> miwarlock002, could you tell me what you get if you type the following in a shell, please? 

$ which alsa

$ dpkg -S `which alsa`

Also, did you alter your firefox startup script? What output do you get if you run firefox from a terminal with 'firefox -V'?

```
Mozilla Firefox 2.0.0.1, Copyright (c) 1998 - 2006 mozilla.org
```

---

### Post by rare HERO on 2007-10-22
I'm still at the flash video working without sound at this point.

Is there a definitive fix out yet?

---

### Post by PineGroveDave on 2007-10-27
> **Old Pink said:**
> If this helps you, please leave a comment. :)


After upgrading to 7.10 I lost sound from Firefox. This recommended fix did the trick. Danke mein Freund! :)

---

### Post by rare HERO on 2007-10-27
> **rare HERO said:**
> Here is what I did to solve my problem.

Updated firefox to 2.0.0.8

```
$ ubuntuzilla.py -a install -p firefox
```

List my soundcard devices
```
$ gksudo asoundconf list
```

Choose the one I want as default
```
$ gksudo asoundconf set-default-card Audigy2
```

Edit firefox so it takes alsa
```
$ gksudo gedit /etc/firefox/firefoxrc
```

Text editor comes up.  Change:
FIREFOX_DSP=&#8221;none&#8221;

To:
FIREFOX_DSP=&#8221;alsa&#8221;

Check sound properties and make sure everything is set to ALSA in the window that comes up:
```
$ gnome-sound-properties
```

:)

---

### Post by aapp on 2007-11-18
hey, i installed all the things n such, but on the last step it wont let me save!!!
First off it just gives me a blank page, then when i put what i need it just says "unexpected error, File doesnt exist"

or if i go through and try to do it without the terminal it says i dont have permission to do it

help?

---

### Post by laranja on 2007-12-29
> **rare HERO said:**
> :)

Finnaly!! I have sound in Flash movies! :)

Thank you so much.

---

### Post by Illuminutus on 2008-01-06
Yeap... that final page on the post short out  both my streaming sound problems and Flashplayer issue. Finaly!!!

---

### Post by ubrox on 2008-03-26
Setting ALSA as default in gstreamer-properties did the trick for me. Nothing else is required.

---

### Post by rOoNy911 on 2008-05-10
Hey guys,

Tbh i am really noob at Ubuntu and commands etc.
I was wondering if anyone could give me a step-by-step instruction on how to fix the sound issue on Firefox?  :popcorn:

---

### Post by psyke83 on 2008-05-11
> **rOoNy911 said:**
> Hey guys,

Tbh i am really noob at Ubuntu and commands etc.
I was wondering if anyone could give me a step-by-step instruction on how to fix the sound issue on Firefox?  :popcorn:

Are you using version 8.04 (Hardy)? If so, look at my guide here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

To fix Flash & PulseAudio (which is the sound server in Hardy), you need to follow parts A & B (the others are optional).

---

### Post by petronell on 2008-06-13
thanks a lot for this reference. fixed my problem fine.

---

### Post by DrMilo on 2008-06-20
After using the command: sudo aptitude install alsa-oss

I have no sound in firefox and it somehow killed my sound in vlc!

How do I reverse it?

---

### Post by parakeets11 on 2008-07-10
Okay, maybe I'm weird, but when I open the file, there is nothing at all.

Its just a blank document.  And  can't make changes to it.

Help is appreciated.

---

### Post by mattgaunt on 2008-07-10
Yeah i get the same problem as parakeet :confused:

---

### Post by JDorfler on 2008-07-10
So far so good.  It even stopped Firefox 3.0 from crashing after playing only on video than trying another one.

---

### Post by parakeets11 on 2008-07-11
Ok...Now that I restarted, my sound doesn't work.  I hear the drums in the beginning but after that there is no sound what so ever.  Is there a way to fix this?

---

### Post by tvrtuscan on 2008-07-28
This took me about 2 solid days to resolve on my PC.  I tried all the other solutions without success.  It turned out to be the PCM was muted in the alsa mixer.  Run alsa-mixer and then press 'M' when you are on the PCM tab.  Also make sure the volume is turned up.  Hope it helps

---

### Post by MrKenmore on 2008-08-12
I am running hardy 64 bit.  This means I have firefox 3.  So I don't have that file to modify (or I can't find it).  I have video but no audio.  I have ALSA working fine with others apps.  Any ideas.

---

### Post by Tomatosoup on 2008-08-29
It worked for me. Thanks! Though it's very strange I had to this to get things working. Audio worked fine for me. But then it just stopped working (in Firefox).

---

### Post by me121 on 2008-09-06
i just installed libflashsupport and this fixed it.

---

### Post by kakaroth on 2008-09-09
> **me121 said:**
> i just installed libflashsupport and this fixed it.

It just worked for me too.
i have firefox 3.0
I suggest to put this tip in evidence!!!

p.s. I didn't install alsa-oss

---

### Post by Gnorrogh on 2008-10-12
Well, I guess this would help me, but since I don't have a /etc/firefox/firefoxrc I can't do anything? And I can't access root (no idea why), so I can't install libflashsupport as me121 suggested.

EDIT: Nevermind! Got it working! Love you, me121!

---

### Post by bcourter on 2008-10-12
Just got mine working on Hardy 64.  I'd tried just about everything in this thread with no luck, but today I realized that I didn't have PulseAudio set up correctly.  I had wired most of my apps and the sound preference defaults to use ALSA and never got up to speed with Pulse.  

I have multiple sound cards.  Pulse was using the wrong one by default.  padevchooser does not launch for me (still working on this one), but I was able to find the right name for my other card using paman and edit ~/.pulse/default-sink to use that name.  I also followed the instructions at the top of this page:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

(Note that once I followed those instructions, paman no longer shows the names of my soundcards, which I suspect is caused by the load-module lines I inserted to support Pulse.)

Getting Pulse working also solved my sound problem with Miro.  

Hope that helps somebody.

-B

---

### Post by jkings on 2008-12-01
The window that pops up doesn't contain FIREFOX_DSP=”none” its just blank. Any ideas?

---

### Post by Trikaal on 2008-12-11
The fix did work last time, but I have encountered the issue couple of times after it and it doesn't seem to have any effect now.

I am on 6.06 LTS - Dapper Drake

---

### Post by zenneth on 2009-01-07
> **Old Pink said:**
> *Sometimes flash just doesn't produce sound, or you can find flash will "give up" playing sound after a given period. Use this fix to stop that. *

Easy as pie. :)

Open terminal, and enter: 
```
sudo aptitude install alsa-oss
```Wait for the install to complete, before typing: 
```
gksudo gedit /etc/firefox/firefoxrc
```A file will open, and in the file you will see: 
Change this to:
Hope this helps you all. :)

***Update: **I have been notified that this also works on Firefox clones/forks such as "Flock" :) *

i tried but i just got a blank file. i am running 8.04

---

### Post by Pantoof on 2009-01-09
i also got a blank file, on ubuntu 8.10

and where can you install libflashsupport from? I cant find it in synaptic package manager.

---

### Post by Doc Hoss on 2009-01-09
If you get a blank file and you're using Firefox 3, give this a shot.

```

sudo apt-get install libflashsupport

```

Worked great and immediately for me...just restarted Firefox, and it's go time!

---

### Post by Pantoof on 2009-01-10
hey, thanks for your reply. I did that but it says:

Package libflashsupport is not available, but is referred to by another package.

wierd that it cant find it?

---

### Post by Flufflebuns on 2009-01-10
All worked well until the firefoxrc edit. I typed.

gksudo gedit /etc/firefox/firefoxrc

and the file opened, but the file was completely empty.

Sound in Firefox still doesn't work.

---

### Post by Flufflebuns on 2009-01-10
Got this...

flufflebuns@Flufflebuns:~$ sudo apt-get install libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:

---

### Post by greengamer39 on 2009-01-10
I get the same blank file when i try gksudo gedit /etc/firefox/firefoxrc and when i try sudo apt-get install libflashsupport i get the message that says "package libflashsupport is not available..."

---

### Post by Pantoof on 2009-01-10
perhaps that package has been replaced with a newer one that we dont know of..

---

### Post by akaIDIOT on 2009-01-10
> **Doc Hoss said:**
> If you get a blank file and you're using Firefox 3, give this a shot.

```

sudo apt-get install libflashsupport

```

Worked great and immediately for me...just restarted Firefox, and it's go time!

FINALLY :D
After a lot of googling and solutions from 2006 this did the trick, ty very much :D

---

### Post by Pantoof on 2009-01-11
> **Flufflebuns said:**
> Got this...

flufflebuns@Flufflebuns:~$ sudo apt-get install libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:

did it say what packages replace it?

---

### Post by DrMilo on 2009-01-12
I just stumbled on this fix yesterday and it worked where nothing else, everything in this thread so far I believe, did not.

[B]Go to synaptic and install all of the pulseaudio packages and reboot.
[/B]
Yes, it was that simple! My system sounds are back and flash works just fine... after about 8 months of trying everything else! Why all of these packages don't go in by default is a mystery that I will leave to others. Some of them were installed but others not, one or more of them fixed 2 nagging problems.

---

### Post by Pantoof on 2009-01-15
ahh i tried installing some stuff but it didnt help. now im just running windows firefox in wine lol

---

### Post by Zantalos on 2009-01-20
> **Doc Hoss said:**
> If you get a blank file and you're using Firefox 3, give this a shot.

```

sudo apt-get install libflashsupport

```

Worked great and immediately for me...just restarted Firefox, and it's go time!

THANK YOU!!!

I installed latest flash for ubuntu, did what op said, then did this, it's working!

---

### Post by kaston on 2009-01-25
> **Doc Hoss said:**
> If you get a blank file and you're using Firefox 3, give this a shot.

```

sudo apt-get install libflashsupport

```

Worked great and immediately for me...just restarted Firefox, and it's go time!

worked great for me too.  running hardy heron and firefox 3

---

### Post by Spartnova on 2009-01-28
For what it's worth, I solved this problem on my system.  I could get no sound on Firefox 3 w/ 8.10 x64 and Flash 10.  I have an Audigy SE installed.  I disabled my onboard audio in my BIOS and presto - everything works great.  Hope it helps someone else.

---

### Post by zim2dive on 2009-02-02
I had Flash audio working over HDMI with my onboard nvidia 8200... but I had other issues with the 8200 drivers, so I got an Radeon 3450.. installed the latest Catalyst 9.1 (just a few days old).

I have audio working over HDMI now for everything except Flash (and this was working over the nvidia HDMI).

I have already installed alsa 1.0.19.

I have uninstalled and re-installed the Flash 10 plugin.

I have tried all my volume preferences pointing to ALSA, and ATI HDMI, neither works for Flash, but all other audio (songbird, amarok, speaker-test, vlc, etc) works just fine.

I don't fully comprehend the relationship between alsa and pulse, but given my experience on the nvidia side, I found myself much better off trying to use ALSA, so I would prefer an alsa solution (but not sure if that is a logical statement), I did follow the fix-all pulse thread back when wrestling with my nvidia hdmi audio issues, and can say that following that thread killed my hdmi audio there, so again, would prefer not using that thread as my debug.

In BIOS I have disabled my onboard HDMI audio and HD audio.  My Radeon 3450 shows up as card 0, device 3, and I have my .asoundrc configured as such.

Again, ALL other audio (as far as I know) is quite content with my setup, just not the Flash audio.

thanks for any ideas,
Mike

---

### Post by zim2dive on 2009-02-02
> **rare HERO said:**
> :)

So I tried the gstreamer props, the gnome sound props, the asoundconf to my only card (HDMI), the FIREFOX_DSP config, and still Flash is the only thing where I can't get sound. Trying both 3.0.5 Firefox and Opera 9.6.

Every other sound app I try works. I am on Intrepid.  Had working flash sound with onboard nvidia IGP via HDMI, just not via Radeon HDMI.

EDIT:
changing my .asoundrc to > defaults.pcm.device 3   (WORKS) somehow made everything happy. (vs.> pcm.!default {
type hw
card 0
device 3
}      (FAILS)

What a lovely audio system we have ;)

env vars FLASH_AUDIODEBUG and FLASH_FORCE_ALSA were also in the mix.

---

### Post by redkey73 on 2009-02-07
I'm in Firefox 3.0 on Ubuntu 8.10 with motherboard sound, and installing the libflashsupport package solved my problem of no sound in streaming videos.

I found when attempting to install libflashsupport that this package is now obsolete; it has been replaced by flashplugin-nonfree-extrasound, so the updated version of this fix is to type

sudo apt-get install flashplugin-nonfree-extrasound

and then restart Firefox.

---

### Post by davesollows on 2009-02-21
How can this be applied to firefox 3?

I cannot find a firefoxrc file on my system

---

### Post by javaChick on 2009-02-24
I have firefox 2.0.0.17, ubuntu 7.04. Feisty Fawn and latest flash version, and still non does work for me. What should I do?

---

### Post by maximi89 on 2009-02-28
i use firefox with ALSA, and i get the error... i going test with aoss.. 
because i get a library for use flash and alsa :O :)

---

### Post by jar72 on 2009-03-06
> **zim2dive said:**
> So I tried the gstreamer props, the gnome sound props, the asoundconf to my only card (HDMI), the FIREFOX_DSP config, and still Flash is the only thing where I can't get sound. Trying both 3.0.5 Firefox and Opera 9.6.

Every other sound app I try works. I am on Intrepid.  Had working flash sound with onboard nvidia IGP via HDMI, just not via Radeon HDMI.

EDIT:
changing my .asoundrc to  somehow made everything happy. (vs.

What a lovely audio system we have ;)

env vars FLASH_AUDIODEBUG and FLASH_FORCE_ALSA were also in the mix.

OMG! Thank you zim2dive!! I added "defaults.pcm.device 3" to my asound.conf and flash in firefox works. The other code doesn't work like you said.

BTW I have a gigabyte ga-ma78gm

---

### Post by thisweb on 2009-03-14
Wow!   Unbelievable this really works!!  Thank you so so much my friends!


I've been searching for months for this fix and this little line is all thats needed to fix sound in flash on firefox over HDMI. - I have motherboard ATI HDMI.  Here it is again:

#create / edit .asoundrc by typing this from home directory:

sudo gedit .asoundrc

#add this line:

defaults.pcm.device 3

#save

#reboot

voila!!

NB (Disable onboard sound in BIOS first - there is also HDMI under graphics card in bios but this is different from main onboard sound so do not disable this bit, only disable the main onboard sound)

---

### Post by knlgSeekr on 2009-03-25
> **thisweb said:**
> Wow!   Unbelievable this really works!!  Thank you so so much my friends!


I've been searching for months for this fix and this little line is all thats needed to fix sound in flash on firefox over HDMI. - I have motherboard ATI HDMI.  Here it is again:

#create / edit .asoundrc by typing this from home directory:

sudo gedit .asoundrc

#add this line:

defaults.pcm.device 3

#save

#reboot

voila!!



This worked for me too!:) I didn't have to disable anything in the BIOS.

---

### Post by Yeti can't ski on 2009-03-30
Just for the record, I too had the mute Firefox problem (everything else was working properly) and couldn't solve the issue by editing "firefoxrc". 

I couldn't get sound with any videos even when I used Epiphany. 

In my case, I simply suppressed .asoundrc (by doing: mv ~/.asoundrc .asoundrc.old ) and that was it. Problem solved. 

For reference (check post from newton64):

[http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)

---

### Post by daveisfera on 2009-04-07
I'm using Firefox 3 on Mythbuntu 9.04 x64 and I can play videos and such with the Flash 10 player, but I don't hear any sound. I get sound from all of the other applications I run, but Firefox/Flash just doesn't seem to work for some reason.

---

### Post by seleciii44 on 2009-04-14
hi,
i didin't have the firefoxrc file, and i tried to create it myself and added the FIREFOX_DSP=”aoss” line to it. it works now :lol:

---

### Post by fogster74 on 2009-04-18
First off - this works perfectly - I'm very happy! Used the 'firefoxrc' fix and this fixed things immediately. For the record, I'm running the 9.04 64-bit (Release Candidate, I think) and Firefox 3.0.8 (even having Flash running in a 64-bit Ubuntu environment makes me smile!)

I thought I'd quickly outline what I did from a beginners point of view - I remember the frustration I had when I first came over to Ubuntu, people would say "run as sudo" or "run as root" and I'd think "what the??!!"

So, if you're totally new to Ubuntu, here's the step-by-step guide to (attempting) this fix! I've tried to explain each and every step as I go along - I think I would have found this helpful if I'd been an early adopter and, as I think a lack of sound in YouTube is the sort of problem that may put someone off persevering, it's worth a walk through!


**1)** Open a Terminal (a Command line where you can enter commands) - do this by going to Applications -> Accessories and clicking "Terminal".

You'll find the terminal contains some information - this is in the form of ```
username@computername:-$
```In my example, my username is 'foggy' and computer name is 'dell', so my terminal prompt looks like this: ```
foggy@dell:-$
```


**2)** In the terminal, after your terminal prompt, type the following (the bit in bold)
```
foggy@dell:-$ **sudo aptitude install alsa-oss**
```
I'll take a brief minute to describe what's going on here. You will currently be 'logged in' with your standard user account - hence your user name appearing in the command prompt. This limits what you can do (a good safety precaution). Some of the things we need to do are in a part of the file system that a standard user is not allowed to access, or are changes to the system, for example. 

Fear not! We can get 'temporary' permission to work as 'superuser' that has these rights by using the '**Sudo**' command. This stands for "Super User DO" - in other words, run whatever comes after it a Superuser. BE CAREFUL though, as a SuperUser you can delete critical system files - so only use it when needed!

**aptitude** is a package manager - a way of downloading applications, patches etc, and **install** tells the system that you're looking to install the file specified (other options allow you to reinstall or remove applications, for example).

We need to install a 'package' relating to sound - without going into too much detail, let's just say we need it for this task. If you want to find out more about alsa-oss, see [**_here**_]("http://help.ubuntu.com/community/alsa-oss")

Once you've typed the above command, you'll be prompted for your user password - the one you use to log on to the system. Enter it and hit enter.

Your Ubuntu install will try to connect to the Ubuntu repositories, a centralised storage location full of files, patches, updates etc (so make sure you're connected to the internet!) and download the appropriate package. You'll probably be prompted to start the install (and this may mean removing some other packages but, don't worry, this is all done automatically by **aptitude**. When prompted, just press '**y**' to start the install.


**3)** Once this has completed (you'll get a message telling you when it's done), enter the following at the terminal prompt (again, the bold bit):
```
foggy@dell:-$ **cd //etc**
```
What's going on here? **cd** changes the directory that you're currently in, '**//**' tells the computer to start at very top of the directory tree, and '**etc**' is the name of the directory you want the computer to switch to.

You'll find the terminal prompt has now changed:```
foggy@dell://etc$ 
```
This confirms that you're now in the **etc** directory.

**4)** Now you need to find your Firefox directory - you need to list the contents of the **/etc/** directory - you do this by using the **LS** command:
```
foggy@dell://etc$ **ls**
```

You should see the terminal window fill will files and directory names - look for one starting 'Firefox'. The instructions above expect your Firefox files to be in a folder called exactly that, 'Firefox' - but this isn't always the case. For me, for example, my Firefox files are in a directory called **Firefox-3.0**.


**5)** Now we've located our Firefox folder, we need to switch into it. Yep - we need the **cd** command again. Here I'm switching to my Firefox-3.0 directory, but you should replace this with whatever you found in your /etc/ directory:
```
foggy@dell://etc$ **cd /firefox-3.0**
```

Ok, so now we should find ourselves in the Firefox directory - my command prompt now looks like:
```
foggt@dell://etc/firefox-3.0$
```
By the way, if you want to check you're in the correct directory, try typing **pwd** after the command prompt and hitting enter- it will confirm the directory you're in. Go on - try it now :)


**6)** Nearly there! We now need to establish if you have the 'firefoxrc' file on your system. If not, you'll need to create it. Start by listing the contents of your Firefox directory (again, using the **ls** command).
```
foggy@dell://etc/firefox-3.0$ **ls**
```


**7)** You'll probably only find a few files and folders listed. Check to see if one of them is called 'firefoxrc'. If so, the next command will open the file but, if not, the next command will create the file:
```
foggy@dell://etc/firefox-3.0$ **sudo nano firefoxrc**
```

**nano** is a text editor - it's what we're going to use to edit our **firefoxrc** file.


**8 )** Assuming you've entered the **sudo nano firefoxrc** command (you may need to enter your password again), you'll now be looking at the **nano** text editor . It's a bit like a very simple word processor - you navigate around using the cursor keys. 

If the main window of the text editor has text, look for a line that looks like
```
FIREFOX_DSP=&#8221;none&#8221;
```
and change this to 
```
FIREFOX_DSP=&#8221;aoss&#8221;
```. 
However, if you're file is empty and there's no lines of text, simply type the last bit ( FIREFOX_DSP=&#8221;aoss&#8221;) at the top of the window.


**9)** Last bit! We now have to save our file. **nano** calls this 'writing out' the file. Simply hold the CTRL button on your keyboard and tap the "O" (letter O, not number 0) key. You'll be prompted for a filename that will be pre-completed with **firefoxrc**, so just click enter. Finally, to exit **nano**, hold down the CTRL button and tap the "X" key on your keyboard.

**10)** THAT'S IT! If you've got Firefox open, I'd suggest you shut it down and relaunch it (just Firefox, there's no need to restart your whole system). Navigate to Youtube and give it a go!

I hope this helps - and, even if this doesn't work, this should hopefully help you try one of the other fixes above.

Good luck!

---

### Post by axedaddy on 2009-04-20
> **Old Pink said:**
> *Sometimes flash just doesn't produce sound, or you can find flash will "give up" playing sound after a given period. Use this fix to stop that. *

Easy as pie. :)

Open terminal, and enter: 
```
sudo aptitude install alsa-oss
```Wait for the install to complete, before typing: 
```
gksudo gedit /etc/firefox/firefoxrc
```A file will open, and in the file you will see: 
Change this to:
Hope this helps you all. :)

***Update: **I have been notified that this also works on Firefox clones/forks such as "Flock" :) *

I am new to Ubuntu. The file opens but I don't see the quote.  Am I doing something wrong.

---

### Post by psyke83 on 2009-04-20
> **axedaddy said:**
> I am new to Ubuntu. The file opens but I don't see the quote.  Am I doing something wrong.

This particular thread is giving very obsolete advice. Attempting to get sound in Firefox using "alsa-oss" is completely silly, because a) Flash 9+ doesn't support OSS, and b) "alsa-oss" itself is obsoleted by "padsp" since the Hardy release, due to PulseAudio being integrated by default. This advice was useful three years ago, when we were all using Flash 7. Today it's only going to mess up your system.

Don't follow the advice in this thread. I just hope a moderator can take a look at this thread and realize it needs to be archived, as too many new users are getting themselves into trouble.

---

### Post by fogster74 on 2009-04-21
> **axedaddy said:**
> I am new to Ubuntu. The file opens but I don't see the quote.  Am I doing something wrong.

AxeDaddy - you've posted this directly below my post which gives a complete guide for beginners!! :-)

Follow the above and you shoubd be ok ;-)

---

### Post by fogster74 on 2009-04-21
> **psyke83 said:**
> This particular thread is giving very obsolete advice. Attempting to get sound in Firefox using "alsa-oss" is completely silly, because a) Flash 9+ doesn't support OSS, and b) "alsa-oss" itself is obsoleted by "padsp" since the Hardy release, due to PulseAudio being integrated by default. This advice was useful three years ago, when we were all using Flash 7. Today it's only going to mess up your system.

Don't follow the advice in this thread. I just hope a moderator can take a look at this thread and realize it needs to be archived, as too many new users are getting themselves into trouble.

Hi Psyke83,

I can't agree 100% with your statement - can you elaborate a little? It's just that I'm running RC of 9.04 (x64) on a clean install. Flash is latest version from the repositories, Firefox is 3.0.8, and I lost sound in Flash. The fix above sorted things perfectly for me (I've documented what I did exactly in my first post here, just a few post earlier).

I certainly don't want to advocate anyone do something that will mess up their system but, equally, this did fix it for me and I'm running a bang up to date system.

Would it be possible for you to provide alternative / updated fix, or a link to the same? I'd be happy to update my instructions accordingly :-)

However - I must stress, the fix I posted did solve the problem for me (as of April 2009) and did not mess up my system in anyway.

---

### Post by psyke83 on 2009-04-23
> **fogster74 said:**
> Hi Psyke83,

I can't agree 100% with your statement - can you elaborate a little? It's just that I'm running RC of 9.04 (x64) on a clean install. Flash is latest version from the repositories, Firefox is 3.0.8, and I lost sound in Flash. The fix above sorted things perfectly for me (I've documented what I did exactly in my first post here, just a few post earlier).

I certainly don't want to advocate anyone do something that will mess up their system but, equally, this did fix it for me and I'm running a bang up to date system.

Would it be possible for you to provide alternative / updated fix, or a link to the same? I'd be happy to update my instructions accordingly :-)

However - I must stress, the fix I posted did solve the problem for me (as of April 2009) and did not mess up my system in anyway.

At the time of this thread's creation, 2006: Flash 7 was the latest version available, which supported ALSA, OSS and ESD output natively. Although ALSA was the default output, it was possible to "force" the audio output method using the method you followed from this thread.

Fast forward to 2009: Flash 10 is the latest release, and only supports one type of audio output: ALSA. However, there is an API available through an external library called "libflashsupport" that allows Flash to be extended with alternative output methods such as ESD, OSS and PulseAudio. However, Flash has a serious bug when using the libflashsupport API, which causes Flash content to cause segmentation faults when navigating between pages in Firefox (and other browsers). This is detailed exhaustively at [bug #192888]("https://bugs.launchpad.net/bugs/192888").

I suspect that you have the "libflashsupport" library installed, as otherwise this configuration change should not work (i.e., Flash 10 does not support OSS output without it).

Nobody should be using the libflashsupport library, as 
[LIST]
[*]it causes instability in Firefox (32bit users will notice constant segmentation faults in Firefox, and 64bit users will notice Flash content "turning grey" at spontaneous intervals), and 
[*]PulseAudio already supports ALSA output properly.
[/LIST]

What you have done to your system is set it up in a needlessly complex way, whilst ignoring the root problem which caused the issue.

Most likely, your PulseAudio setup is not configured correctly on your system. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by daveisfera on 2009-04-23
> **psyke83 said:**
> At the time of this thread's creation, 2006: Flash 7 was the latest version available, which supported ALSA, OSS and ESD output natively. Although ALSA was the default output, it was possible to "force" the audio output method using the method you followed from this thread.

Fast forward to 2009: Flash 10 is the latest release, and only supports one type of audio output: ALSA. However, there is an API available through an external library called "libflashsupport" that allows Flash to be extended with alternative output methods such as ESD, OSS and PulseAudio. However, Flash has a serious bug when using the libflashsupport API, which causes Flash content to cause segmentation faults when navigating between pages in Firefox (and other browsers). This is detailed exhaustively at [bug #192888]("https://bugs.launchpad.net/bugs/192888").

I suspect that you have the "libflashsupport" library installed, as otherwise this configuration change should not work (i.e., Flash 10 does not support OSS output without it).

Nobody should be using the libflashsupport library, as 
[LIST]
[*]it causes instability in Firefox (32bit users will notice constant segmentation faults in Firefox, and 64bit users will notice Flash content "turning grey" at spontaneous intervals), and 
[*]PulseAudio already supports ALSA output properly.
[/LIST]

What you have done to your system is set it up in a needlessly complex way, whilst ignoring the root problem which caused the issue.

Most likely, your PulseAudio setup is not configured correctly on your system. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I am using Mythbuntu 9.04 (which I believe doesn't use PulseAudio) and I believe that I have ALSA setup correctly (sounds works in everything but Flash/Firefox), so do you have any recommendations on what I need to do to get sound working with Flash 10 on x64?

---

### Post by psyke83 on 2009-04-23
> **daveisfera said:**
> I am using Mythbuntu 9.04 (which I believe doesn't use PulseAudio) and I believe that I have ALSA setup correctly (sounds works in everything but Flash/Firefox), so do you have any recommendations on what I need to do to get sound working with Flash 10 on x64?

You really shouldn't see any issues with Flash 10 and plain ALSA, which leads me to believe that perhaps you really do have PulseAudio installed in Mythbuntu...

If that's the case, it's probably a problem with the lib32asound2 plugins not working correctly (which are necessary to allow PulseAudio to play sound in 32bit applications).

I don't own 64bit hardware, so I can't do much testing, sorry. 

Perhaps you could consider testing the 64bit Flash plugin. You'll need to search the forums.

---

### Post by daveisfera on 2009-04-23
> **psyke83 said:**
> You really shouldn't see any issues with Flash 10 and plain ALSA, which leads me to believe that perhaps you really do have PulseAudio installed in Mythbuntu...

How can I check if PulseAudio is installed?

> If that's the case, it's probably a problem with the lib32asound2 plugins not working correctly (which are necessary to allow PulseAudio to play sound in 32bit applications).

How can I verify if this is the issue?

> I don't own 64bit hardware, so I can't do much testing, sorry. 

Perhaps you could consider testing the 64bit Flash plugin. You'll need to search the forums.

I also have standard Jaunty x64 installed on my laptop and sound plays just fine with Flash 10/Firefox 3.0, so I imagine that the issue is something specific to the setup of Mythbuntu, so do you have any recommendations on how I can debug the issue?

I have searched the forums and haven't been able to find anything that deals with this issue on Mythbuntu.

---

### Post by Stalkersway on 2009-04-24
> **psyke83 said:**
> This particular thread is giving very obsolete advice. Attempting to get sound in Firefox using "alsa-oss" is completely silly, because a) Flash 9+ doesn't support OSS, and b) "alsa-oss" itself is obsoleted by "padsp" since the Hardy release, due to PulseAudio being integrated by default. This advice was useful three years ago, when we were all using Flash 7. Today it's only going to mess up your system.

Don't follow the advice in this thread. I just hope a moderator can take a look at this thread and realize it needs to be archived, as too many new users are getting themselves into trouble.

I agree trying to find info is hard enough when the propelm not only is not being fixed but in fact is getting more confusing for me (Not getting at the great posts of handy tips) . But they are getting more out dated

---

### Post by Stalkersway on 2009-04-24
So ive had this probelm for a while not sure on the details before installing Jaunty (Intrepid was installed prior and I was hoping Jaunty would patch the probelm) . I have two sound cards one onboard and the other a audigy2 , the onboard one i have disabled through bios but when i logon Amarok 2 , Banshee , Rhythmbox , Totem and Live will not play any sound also firefoxes sounds dont work either the only one that works is VLC . But as soon as I open PulseAudio Device Chooser click on the icon that it just open and choose the Playbacks Tabs\Systems Sounds\Mono Mute Audio button this message appears "Connection failed: Connection terminated" and for some reason which will be clear to someone other that myself this actually
fixes all my sound probelms . Though it is annoying. Now is there any terminal command that i can use that can make it clearer for  someone in the know ? I have  ALSA , OSS and Pulseaudio is there a conflict there ? Should i have all of those?
Help would be great I have had the same probelm since the first my first unbubtu install of 8.10 and with all of my tinkering I know that with my very limited knowledge im going to screw something up........
 Update now with the very latest update this trick no longer works...for firefox 3 that is though all other players are working fine

---

### Post by Stalkersway on 2009-04-24
Five Minutes after my last post I decided to try and mimic pulseaudio failing by opening System Manager finding Pulsemedia and killing it , low and behold and all audio that i have checked amarok rhythm box vlc player and EVEN Firefox work .....

So can someone explain something that is not too clear to me

---

### Post by caleb_yau on 2009-04-24
I just switched from Xubuntu Gutsy to Ubunty Jaunty and now is when my problems start. I will try some of the various fixes and i'll let you guys know if any of them work.

---

### Post by mitsoulis on 2009-05-03
Hi guys ,

Could you tell me how to configure the sound card output for flash in firefox?

Actually I have two sound cards and it gives output default to onboard card but I would prefer to change it ...

---

### Post by psyke83 on 2009-05-08
> **mitsoulis said:**
> Hi guys ,

Could you tell me how to configure the sound card output for flash in firefox?

Actually I have two sound cards and it gives output default to onboard card but I would prefer to change it ...

If you're using a recent version of **U**buntu (GNOME, not KDE), then ignore this obsolete guide and follow my PulseAudio guide.

N.B. Pay special attention to the part where you select the default sound card in the PulseAudio Volume Control application. All applications (including Firefox/Flash) are affected.

---

### Post by dkavraal on 2009-05-18
Removed pulse, jackd. Restarted alsa, edited firefoxrc to have the line with "aoss".

Now it works with FF3.

---

### Post by Tre_bumpn on 2009-05-18
I tried this. First step went fine, second step pulls up a window....but its empty

Just got sound working for my creative X-fi (got the card free) but only works for MP3 and Ubuntu system sounds. Like the drums at startup.

Firefox and flash remain silent.

Total linux n00b here. Was suprised after all I read about the X-fi cards that I even got mp3 audio to work! :p

---

### Post by Tre_bumpn on 2009-05-21
can anybody give me some ideas what to try? I'm not really sure where to start. Sorry about bumping, but as I look around I'm not finding anything useful I can make sense of. The instructions for this thread were pretty clear and concise, but as I said, the second step left me with just blank window. No firefox =aoss or anything.

---

### Post by esplinter on 2009-05-24
I had this problem in kubuntu jaunty i386 and finally could solve it.

first backup all config files and delete them:

```

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf

```

and then:

```

 $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

```

I found it in this post:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

hope it helps.

---

### Post by downclimb on 2009-06-10
I'm running Kubuntu Jaunty 9.04 and the only fix I needed was to open Kmix and turn up my PCM sound.  Could it really be that easy?

---

### Post by apeeling on 2009-06-14
Hi, so I'm really new to Ubuntu and Linux in general, and I can't seem to fix this problem.  I'm running Ubuntu 9.04 and Firefox 3.0.11. I don't have the firefoxrc file, so I can't go that route (apparently it's outdated anyways). And I followed the pulse audio instructions for Jaunty and that didn't work either. When I open the pulse audio volume control and look at the playback it shows firefox listed, and I can see the volume there going up and down, but I don't hear anything. Anyways, I'd really appreciate any help. Thanks!

--edit--

I fixed it using this post - [http://ubuntuforums.org/archive/index.php/t-1009407.html](http://ubuntuforums.org/archive/index.php/t-1009407.html)
pulseaudio wasn't recognizing the hdmi output.

---

### Post by Caesarjulii on 2009-07-11
Thanks a lot !! Helped me

---

### Post by xtremethegreat1 on 2009-08-12
Didn't work for me. First of all, I didn't find the firefox directory inside /etc. Although I did find firefox-3.0 in there, but it didn't have any firefoxrc file.

However installing flashplugin-installer, flashplugin-nonfree and flashplugin-nonfree-extrasound worked for me.

---

### Post by Kinetic_lord on 2009-08-30
> **ssavelan said:**
>   We must defend our OS's honor.

What honor? There are few companies that care about Ubuntu and makes software for it.

---

### Post by jobromedia on 2009-11-21
There is a problem:

```
gksudo gedit /etc/firefox/firefoxrc
```gives me a blank new document with nothing to alter. Like this:

[[IMG]http://i.imagehost.org/0304/firefoxrc_etc-firefox_gedit.png[/IMG]]("http://i.imagehost.org/view/0304/firefoxrc_etc-firefox_gedit")

So please tell me what to type instead so I get the real firefox file to alter it.

---

### Post by dmizer on 2009-11-22
> **jobromedia said:**
> There is a problem:

```
gksudo gedit /etc/firefox/firefoxrc
```gives me a blank new document with nothing to alter. Like this:

[http://i.imagehost.org/view/0304/firefoxrc_etc-firefox_gedit](http://i.imagehost.org/view/0304/firefoxrc_etc-firefox_gedit)

So please tell me what to type instead so I get the real firefox file to alter it.

There's no file because it doesn't exist.

Since this howto is written to fix sound problems with firefox and alsa, and the current versions of Ubuntu use Pulse audio instead of Alsa, this howto is not relevant to your problem.

---

### Post by cozski on 2010-01-11
> **dmizer said:**
> There's no file because it doesn't exist.

Since this howto is written to fix sound problems with firefox and alsa, and the current versions of Ubuntu use Pulse audio instead of Alsa, this howto is not relevant to your problem.

...unless of course you cannot hear sound in Firefox and you're using the most recent version of ubuntu. I have had to re-configure my sound too get a simple piece of software like Skype to work with sound (forget the webcam - still not happening). So, currently i have no sound in Firefox... do you suppose there might be a problem that might just require a resolution? Maybe I should start a new thread?

---

### Post by TorbenPiechnik on 2010-04-24
> **cozski said:**
> ...unless of course you cannot hear sound in Firefox and you're using the most recent version of ubuntu. I have had to re-configure my sound too get a simple piece of software like Skype to work with sound (forget the webcam - still not happening). So, currently i have no sound in Firefox... do you suppose there might be a problem that might just require a resolution? Maybe I should start a new thread?

I have precisely the same problem>.... did you start a new thread or can anyone help???

Thanks :)

---

### Post by xCeLeRaTo on 2010-04-25
i fixed my flash/firefox no sound issue by editing /etc/modprobe.d/alsa-base.conf i just put a # in front of where it was telling the system to give my usb audio and index of -2 and rebooted. wallah, sound through flash in firefox.

# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
#options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2

---

### Post by Matthew Brenner on 2010-05-10
> **psyke83 said:**
> This particular thread is giving very obsolete advice. Attempting to get sound in Firefox using "alsa-oss" is completely silly, because a) Flash 9+ doesn't support OSS, and b) "alsa-oss" itself is obsoleted by "padsp" since the Hardy release, due to PulseAudio being integrated by default. This advice was useful three years ago, when we were all using Flash 7. Today it's only going to mess up your system.

Don't follow the advice in this thread. I just hope a moderator can take a look at this thread and realize it needs to be archived, as too many new users are getting themselves into trouble.

Thank you for saving me another hour of fruitless terminal commands...

That leaves me and seemingly many others without a solution....

---

### Post by dostyvsky on 2010-06-07
Thanks but didn't help.  What eventually worked for me was to play with some of the different configurations in synaptic.  And this worked for me.  It may have helped that I already did the steps above.

sudo apt-get install flashplugin-nonfree-extrasound

it worked in opera also.  I did have to click on the video to activate the control.:guitar:

---

### Post by dostyvsky on 2010-06-14
Ok my solution did not hold.  Better advice is here [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)     

By better I mean it worked for me.  If it melts your machine down to bare metal ..... I'm really sorry.  ;)

---

### Post by shadrack111 on 2010-11-11
> **Old Pink said:**
> *Sometimes flash just doesn't produce sound, or you can find flash will "give up" playing sound after a given period. Use this fix to stop that. *

Easy as pie. :)

Open terminal, and enter: 
```
sudo aptitude install alsa-oss
```Wait for the install to complete, before typing: 
```
gksudo gedit /etc/firefox/firefoxrc
```A file will open, and in the file you will see: 
Change this to:
Hope this helps you all. :)

***Update: **I have been notified that this also works on Firefox clones/forks such as "Flock" :) *
i tried this but on the first step it said "command not found" im new to ubuntu. please help?

---

### Post by dmizer on 2010-11-11
> **shadrack111 said:**
> i tried this but on the first step it said "command not found" im new to ubuntu. please help?

You should not need to do this any longer. What version of Ubuntu are you using. Also, does sound work in anything else (can you listen to music for example)?

---

### Post by shadrack111 on 2010-11-13
i finally figured it out through other threads. im so new to this. i love ubuntu but something is always going wrong with my computer with it. i want to keep ubuntu though. its just such a hassle. but thanks to all for your help.

---

### Post by Todamont on 2012-05-13
for me, flash wanted to play on computer speakers, not HDMI...
after some playing... settled on this solution:

my ~/.asoundrc file is:

pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

seems to work for me to get flash audio through HDMI :)

---

