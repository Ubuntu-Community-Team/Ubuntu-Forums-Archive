---
title: "HOWTO: Solve sound missing or out-of-sync in Flash Player"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by remusus on 2006-06-02
OK, I found this solution while I was trying to get my sound card to use dmix to mix sounds, since alsa thought it was able to do hardware mixing but it never could.

First, edit/create ~/.asoundrc to include the following (nano ~/.asoundrc)
```
pcm.!default {
        type plug
        slave.pcm "dmix"
}
```
NOTE: This will cause alsa to use software mixing on cards with hardware mixing support... I don't know if this step is necessary to fix sync on cards with hardware mixing support.

Install alsa-oss (sudo apt-get install alsa-oss).  Then, run your browser prefixed with aoss (ie "aoss firefox") and your flash sync and/or lack-of-sound will be fixed.

For Firefox, you can have it automatically run it with aoss by editing /etc/environment (sudo nano /etc/environment) and adding
```
FIREFOX_DSP=aoss
``` to the end of the file.  Other browsers probably have similar methods, but I am not personally familiar with them.

---

### Post by bigzak on 2006-06-02
I'm going to give this a shot later on; it's a problem that's been bugging me for ages! There's nothing worse that watching Strong Bad and the paper not being in sync ;-)

---

### Post by remusus on 2006-06-02
Well I was very much surprised when doing this this made the sync in Flash Player perfect, since the main goal was just getting the sound in Flash Player to work at the same time as a music player... but if it works I won't complain ;)

---

### Post by raggamuffin on 2006-06-02
thanks for this, remusus...

this problem had been bugging me for a while; this quick fix works perfectly for me...

---

### Post by grsing on 2006-06-02
You didn't happen to find out what package aoss is in, did you?  I've got alsa-utils installed, but aoss comes across as not found.

---

### Post by space42 on 2006-06-02
[QUOTE=grsing]You didn't happen to find out what package aoss is in, did you?  I've got alsa-utils installed, but aoss comes across as not found.[/QUOTE]

The package is alsa-oss.

This solution does not fix the sync issue for me.  It seems to be the worst with video like youtoube.  It goes out of sync right away.

My solution is running windows firefox or IE in wine with flash 8.

---

### Post by remusus on 2006-06-02
@space42, what sound card, sound kernel module and browser are you using?  I'd like to know which cards this works and doesn't work for...

---

### Post by Pionner on 2006-06-02
Tried on 3 fresh Dapper install with onboard soundcards (two Intel and a Sis963). 

It works like a charm. Thanks.

---

### Post by Dr. Feelgood on 2006-06-20
It works when I run firefox from terminal using "aoss firefox" but I can't get it to work automatically.  I edited the same file as directed.  Is there another file I'm missing?  I tried it with and without quotation marks with the same results.

---

### Post by bionnaki on 2006-06-20
worked perfectly for me.
thanks.

---

### Post by zue on 2006-06-20
K, when I do (sudo apt-get install alsa-oss) I get 
```
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate

```

Am I a dumbass?

---

### Post by woot on 2006-06-20
maybe you dont have universe repositories enabled? (in your /etc/apt/sources.list or by graphical way in synaptics)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa-os&searchon=names&subword=1&version=dapper&release=al](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa-os&searchon=names&subword=1&version=dapper&release=al) says the package should be in universe...

---

### Post by unixping on 2006-06-29
This did in fact fix the problem. But I came back to use the computer a couple hours later and everything was out-of-sync again. I checked all the files and they still had the same code.

---

### Post by sYs^ on 2006-06-29
thank you for this howto, it was a so annoying thing :>

---

### Post by SirKillalot on 2006-06-29
thank you man!

---

### Post by Dr. Feelgood on 2006-06-29
I still can't get it to work automatically.  It works great when I run "aoss firefox" from terminal but no matter what file I edit it just won't do this automatically.  What gives?

---

### Post by monomaniacpat on 2006-06-29
[QUOTE=Dr. Feelgood]I still can't get it to work automatically.  It works great when I run "aoss firefox" from terminal but no matter what file I edit it just won't do this automatically.  What gives?[/QUOTE]

Uggh, me too. :(

---

### Post by sbassett on 2006-07-11
Try changing it in:
```

/etc/firefox/firefoxrc

```
as well.

---

### Post by Dr. Feelgood on 2006-07-12
Yup, I did that too, both with quotes and without quotes.  For future reference, are you guys getting it to work with or without quotes?

---

### Post by theonlyvlad on 2006-07-13
Has anyone tried this in opera? I don't know how google video and youtube work, but YouTube sounds always fall apart, and GVid pretty much stays together.

---

### Post by nrune on 2006-07-13
Hey folks, I have this installed right but the audio synch is just off and badly It does not matter weither it is youtube or gvid. When I run it from the command line aoss firefox, same problem with the vid synch. Any ideas?

---

### Post by octathlon on 2006-07-13
New Dapper install with On-board Intel sound card. This doesn't work for me even if I run aoss-firefox from in a terminal.  I get no sound at all.

UPDATE:  I edited /etc/firefox/firefoxrc, changing "none" to "aoss" and this solved it.  I now have sound.  Thanks a lot!!!!!!:D

---

### Post by ericesque on 2006-07-14
you can easily get it to work without typing the aoss firefox command in the terminal every time:

right click on your firefox icon, select properties

in the configuration menu, simply change the command to 'aoss firefox'

you'll have to repeat this for any firefox icon you use, but it's pretty darn simple and quick to do.  no complaining ;)

---

### Post by Daiver on 2006-07-17
Well, there's no way I'm ever going to get flash audio to sync with the video.  I've tried practically everything, yet nothing works. =(

---

### Post by carrig4n on 2006-07-19
I too have the packages installed, run aoss firefox, and get no results with a Sigmatel audio card :(

---

### Post by ace2005 on 2006-07-20
I made the changes and now the apps which did play sound before using alsa no longer play sound :(

Do i need to install dmix? I looked in the repo but i can't find it

---

### Post by bruenig on 2006-07-22
thanks

---

### Post by Seamus on 2006-07-24
Hmmm this didn't work for me :(

I have a livechat application for work that has an embedded wav in Flash and I can't get it to work in FF. It works in Opera 9 with flash support, (makes a ringing noise when someone logs into the live chat) but no joy even with the fix.

> $ more .asoundrc
pcm.!default {
        type plug
        slave.pcm "dmix"
}

I don;'t want to keep using Opera becauase I suspect it has a memory leak, so would be keen to stick with FF any ideas?

---

### Post by Xera on 2006-07-28
thanks it worked :), so annoying being on google video and not getting sound :p, thanks again

//Xera

---

### Post by amoore on 2006-07-30
> **remusus said:**
> OK, I found this solution while I was trying to get my sound card to use dmix to mix sounds, since alsa thought it was able to do hardware mixing but it never could.

First, edit/create ~/.asoundrc to include the following (nano ~/.asoundrc)
```
pcm.!default {
        type plug
        slave.pcm "dmix"
}
```
NOTE: This will cause alsa to use software mixing on cards with hardware mixing support... I don't know if this step is necessary to fix sync on cards with hardware mixing support.

Install alsa-oss (sudo apt-get install alsa-oss).  Then, run your browser prefixed with aoss (ie "aoss firefox") and your flash sync and/or lack-of-sound will be fixed.

For Firefox, you can have it automatically run it with aoss by editing /etc/environment (sudo nano /etc/environment) and adding
```
FIREFOX_DSP=aoss
``` to the end of the file.  Other browsers probably have similar methods, but I am not personally familiar with them.

The above solutions works for me but, it breaks the new skype betea 1.3.0.30_API makeing skype unuseable!!!!](*,) ](*,)

---

### Post by shanepardue on 2006-08-10
this tactic doesn't help me either on a realtek ac'97.

looks like it's not working for many people.

---

### Post by plb on 2006-08-11
audigy here and doesn't work =\ been battling this problem for years lol. well not really battling...it doesn't bother me that much...just an annoyance really.

---

### Post by jdusablon on 2006-08-13
Didn't work for me either, even by running aoss firefox from terminal.

Hope this didn't break anything else.

---

### Post by wildutah on 2006-08-13
Wonderful.  This solution works perfectly for me.  Spent too long fighting with Flash (ugh, why YouTube why?).

Now things work reasonably well.:D

---

### Post by rpalyvoda on 2006-08-14
It worked fine for me, but made Skype unusable, so I had to undo everything...

---

### Post by cactaur on 2006-08-14
It worked for a little while, then the sound stopped again, for me.

---

### Post by jennhi on 2006-08-15
All fixes were fine until I moved from onboard audio to an Edirol SD-90 Studio Canvas, and now the flash sound moves out of sync (worse as the minutes start piling up). Is there anything else I can do to fix this?

Thanks!
Jennifer

---

### Post by adds2one on 2006-08-15
This made no difference for me. Seems to be an ongoing problem for so many people, I hope we can find a solution that works for everyone.

---

### Post by Mr.Matozo on 2006-08-22
> **Dr. Feelgood said:**
> It works when I run firefox from terminal using "aoss firefox" but I can't get it to work automatically.  I edited the same file as directed.  Is there another file I'm missing?  I tried it with and without quotation marks with the same results.

Changing the Firefox icon command propertie to 'aoss firefox' did the trick for now :)

---

### Post by TrustyChords on 2006-08-26
just adding the > FIREFOX_DSP="aoss" to my environment file did the trick, not to mention it better syncc the sound to the video. This was/is a major annoyance. Thanks for the great post!!

---

### Post by dqualls on 2006-08-26
> **remusus said:**
> OK, I found this solution while I was trying to get my sound card to use dmix to mix sounds, since alsa thought it was able to do hardware mixing but it never could.

First, edit/create ~/.asoundrc to include the following (nano ~/.asoundrc)
```
pcm.!default {
        type plug
        slave.pcm "dmix"
}
```
NOTE: This will cause alsa to use software mixing on cards with hardware mixing support... I don't know if this step is necessary to fix sync on cards with hardware mixing support.

Install alsa-oss (sudo apt-get install alsa-oss).  Then, run your browser prefixed with aoss (ie "aoss firefox") and your flash sync and/or lack-of-sound will be fixed.

For Firefox, you can have it automatically run it with aoss by editing /etc/environment (sudo nano /etc/environment) and adding
```
FIREFOX_DSP=aoss
``` to the end of the file.  Other browsers probably have similar methods, but I am not personally familiar with them.
Hello, I'm new to ubunto. 

I downloaded and installed all firefox plugins. I have picture but NO audio on youtube. 

As you said to do, I downloaded and installed alsa-oss (I think). 

Would you please explain to me how to do this fix step-by-step in detail? 

Thank you!

---

### Post by Intangir on 2006-08-30
well ive tried everything on this thread

(i had tried it all before but tried it again anyway..)

NOTHING works.
i havent managed to find 1 video anywhere that has every played in sync thru flash

any video i play directly with mplayer, locally, works fine!
but playing with the flash player just plain sucks.. out of sync

someone needs to post some LINKS cause i think alot of flash video players just suck, or maybe the file its playing from is out of sync

so if you managed to get it work, and you know it works! post the link so we can use a standard test

---

### Post by shanepardue on 2006-08-30
> any video i play directly with mplayer, locally, works fine!
but playing with the flash player just plain sucks.. out of sync

i have the same exact problem as you

---

### Post by Intangir on 2006-08-30
hrm you know what.. i think its not getting any further out of sync

its like a half second out of sync but its staying only a half second out of sync..

instead of getting worse and worse and worse like before..

that could be because of the dmix stuff.. but i didnt work at all without it

---

### Post by kecci on 2006-08-30
Thanks! This is awesome!
Have been looking for a fix to this issue for months! :)

---

### Post by Kalinda on 2006-08-31
Thanks! It works better.. but...

I still can't play music and have Flash at the same time. I went to YouTube and watched a video, which played in sync, with my music paused. Then I hit play in Amarok and told it to go to Homestarrunner.com so I could see if I could do both at the time. At that point Firefox felt the need to crash.

What seems to work best for me is changing the Firefox_DSP to "auto", which lets me have music and flash sound at the same time, removes annoying crackling, but doesn't fix the sync problem.. so I have to pick one or the other.

---

### Post by Paskharen on 2006-09-01
This worked but not with the .asoundrc in the post. I had to go [here]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#dmix_Configuration_for_OSS_Emulation") to find one for my card. I think this is because it has a hardware mixer but I could be wrong :D May be worth a try if the first .asoundrc doesn't work for you...

@remusus: Thanks for a great post anyway, got dmix working now and everything, sweet ;)

---

### Post by shanepardue on 2006-09-01
> **Paskharen said:**
> This worked but not with the .asoundrc in the post. I had to go [here]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#dmix_Configuration_for_OSS_Emulation") to find one for my card. I think this is because it has a hardware mixer but I could be wrong :D May be worth a try if the first .asoundrc doesn't work for you...

@remusus: Thanks for a great post anyway, got dmix working now and everything, sweet ;)
still doesn't sync for me. i used the config for my via xx82 soundcard and it still doesn't sync. i'm running alsa version 1.0.10 which is the latest from the ubuntu repositories. have you compiled alsa's latest driver? i'm afraid of doing that because every time i try to update a driver from source, i break it.

---

### Post by Dr. Feelgood on 2006-09-01
Well I have finally at long last found the solution to my problem.  I had originally upgraded from Breezy to Dapper instead of a doing a fresh Dapper install.  After having a few really weird problems plague me over the past few months I decided to try a fresh install.  What a difference!!  This fix now works perfectly for me!  If you guys are having some unexplained stuff go wrong don't rule out some conflicts with the upgrade if that was the route you chose.

---

### Post by dmizer on 2006-09-17
not only did this not work for me, but it breaks firefox when trying to play flash.

Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)

also, i'm running icewm.

---

### Post by ampop on 2006-09-19
remusus, thank you very much.
I was looking about this issue a long time ago.

---

### Post by chameleon_789 on 2006-09-28
Tried this with both 'aoss firefox' and the environment variable, no luck...

Sound Card : Audigy 4 Pro

---

### Post by UltraMathMan on 2006-09-29
Worked like a charm!

Thank you! :)

---

### Post by wilberfan on 2006-10-19
I use _Swiftfox_, but have seen no mention of this version of Firefox in this thread...

Are there variations to this fix that I should use for Swiftfox??

---

### Post by rafaelcapanema on 2006-11-29
Yay, it works! Although I prefer to use gedit instead of nano.

---

### Post by hasimir44 on 2007-05-31
this works with swiftfox too.. 

```
aoss /opt/swiftfox/swiftfox
```

thanks!

---

### Post by dethell on 2007-12-19
I'm using 7.10 but with the Flash Debug player needed by Flex Builder Alpha for Linux from Adobe. Had the audio sync problems.

I had already edited the /etc/firefox/firefoxrc file to us aoss which allowed sound to work at all, but the .asoundrc fix was needed to correct the sync problem.

Thanks!

David

---

### Post by CubeXombi on 2008-02-24
I just wanted to give my 2 cents.

I've tried, I really have to get my audio working for the longest time, 
First it would work GREAT but, only on google video and daily motion, not much else.. on youtube and a few othe places I would get sync issues with:
FIREFOX_DSP="none"
I tried installing alsa-oss and going with:
FIREFOX_DSP="aoss", 
but in the end, my sound was iffy, sometimes it would *glitch* for a few ms and then resume off sync, sometimes no sound at all.

Decided to switch to PulseAudio to see.. 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
Followed this ---^ 

Stole the following of it to show what worked for me.

(in short)
> 
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter libflashsupport

Then:
> 
gksu gedit /etc/firefox/firefoxrc
edit:: 
> FIREFOX_DSP="esd"

Next create the asound.conf:
> gksu gedit /etc/asound.conf

and paste in the following:

> pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

Go to System -> Administration -> and click on Users and Groups.
Click on Manage Groups, and scroll all the way to the bottom of the list where you will find:

    * pulse
    * pulse-access
    * pulse-rt

[COLOR="Red"]Make sure[/COLOR] to highlight each, one at a time, and click Properties. Just put a check next to each user that you want to be able to have access to sound, cause.. well.. otherwise you won't.

---

### Post by menace34 on 2008-04-11
Running Hardy Heron Beta, and all of a sudden my sound in flash player goes away in Firefox 2.  I did the following to fix it.  Thanks for the help!!

> **CubeXombi said:**
> I just wanted to give my 2 cents.

I've tried, I really have to get my audio working for the longest time, 
First it would work GREAT but, only on google video and daily motion, not much else.. on youtube and a few othe places I would get sync issues with:
FIREFOX_DSP="none"
I tried installing alsa-oss and going with:
FIREFOX_DSP="aoss", 
but in the end, my sound was iffy, sometimes it would *glitch* for a few ms and then resume off sync, sometimes no sound at all.

Decided to switch to PulseAudio to see.. 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
Followed this ---^ 

Stole the following of it to show what worked for me.

(in short)


Then:

edit:: 


Next create the asound.conf:


and paste in the following:



Go to System -> Administration -> and click on Users and Groups.
Click on Manage Groups, and scroll all the way to the bottom of the list where you will find:

    * pulse
    * pulse-access
    * pulse-rt

[COLOR="Red"]Make sure[/COLOR] to highlight each, one at a time, and click Properties. Just put a check next to each user that you want to be able to have access to sound, cause.. well.. otherwise you won't.

---

### Post by emkay_de on 2008-06-12
hi i m useing kubuntu 7.10 and opera 9.50 and the solution to edit my 
/home/.asoundrc file as on:
[http://bbs.archlinux.org/viewtopic.php?pid=346626](http://bbs.archlinux.org/viewtopic.php?pid=346626)
solved my no sound flash problem. i also reinstalled via repositries "kdemultimedia" packages.

important is also to check if the .asoundrc points to the right soundcard
eg. (pcm "hw:2,0") or (pcm "hw:1,0") you can check it by typing
"cat /proc/asound/cards" in your console and get the correct nummer from there to write in your 
.asoundrc file.

cu

---

### Post by clconway on 2008-08-06
Using PulseAudio, I found I also needed to edit /etc/firefox/firefoxrc with
> FIREFOX_DSP="padsp"

---

### Post by Pokkulompus on 2008-08-09
Okay, someone tell this dumb ******* WHERE to write these? I installed Ubuntu today, so I am not very good at these things.

---

### Post by bullrun on 2009-01-10
Was surprised to see my audio so far out of sync on 8.04 with Flash 10, fairly brand new install, quad-core dell, vmware 6.5.1, ensonic alsa...  Tried FF and Swiftfox.. both an issue.

Have tried the fixes on page1, and it 'seems' better but not right still.  Guess maybe I'll try pulse audio and give that a go.

Update: Made the switch to pulseaudio, and everything is sync'd up nicely :)

---

