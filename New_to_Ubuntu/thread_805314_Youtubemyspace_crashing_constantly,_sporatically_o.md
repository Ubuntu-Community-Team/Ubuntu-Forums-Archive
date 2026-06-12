---
title: "Youtube/myspace crashing constantly, sporatically on firefox"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by OpposingForce on 2008-05-23
Hi I have Ubuntu 8.04 and Firefox 3 beta 5.  I tried searching this and it came up but all the topics were like 2 years old and had no solutions to the problem.  It seems like every other video I watch on youtube crashes firefox with no warning or anything.  I ran firefox through the terminal and was able to easily reproduce the bug.  When it crashed, it just said "segmentation fault" in terminal, thats it, just 2 words.  This also happens on myspace pages with flash elements like the music player built in.  Again, this doesn't happen EVERY single time, just seems to be pretty random, and also quite frequent.  I'd say about 1 out of every 2 or 3 youtube/myspace pages with flash seem to crash the browser.  This has to be some type of flash bug, because the crashes seem to only happen on pages with flash elements.  But I'm not sure if it happens in other browsers too.  Any help would be great thanks

---

### Post by tjwoosta on 2008-05-23
This has been a common problem with many people using firefox with ubuntu

as far as i know there is no real fix for the problem right now

i would recommend trying opera, i had the same problem with firefox crashing but i switched to opera9.50b2 and have had no problems at all

here is a link to download opera9.50b2 (top is 32bit, bottom is 64bit, you will want the .deb)
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/]("ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/")

by the way, the problem is with the mozilla engine and ubuntu (not just firefox3)

it does the same exact thing with firefox2 and all other mozilla based browsers

---

### Post by forrestcupp on 2008-05-23
Actually, the problem is not with the Mozilla engine, but rather it's a problem with Flash and PulseAudio.  The fix is to remove the **libflashsupport** package, and maybe set up to use alsa instead of pulse if you have problems from uninstalling that package.

---

### Post by OpposingForce on 2008-05-23
Thanks for the reply, I actually have Konqueror web browser installed also.  I went on youtube and tried to reproduce the problem and after clicking 2 videos it came up with an error box.  The only difference is that in Konqueror it didnt close the browser, it just refused to play the video (however a refresh got it playing).  In firefox it just completely crashes to the desktop with no error or no warning.  The box in Konqueror said the crash was related to the flash plugin.

> **forrestcupp said:**
> Actually, the problem is not with the Mozilla engine, but rather it's a problem with Flash and PulseAudio.  The fix is to remove the **libflashsupport** package, and maybe set up to use alsa instead of pulse if you have problems from uninstalling that package.


Um, I just checked synaptic.  And it appears that package was never installed in the first place.

---

### Post by tjwoosta on 2008-05-23
> Actually, the problem is not with the Mozilla engine, but rather it's a problem with Flash and PulseAudio. The fix is to remove the libflashsupport package, and maybe set up to use alsa instead of pulse if you have problems from uninstalling that package.
o, my bad...

---

### Post by forrestcupp on 2008-05-24
> **OpposingForce said:**
> 
Um, I just checked synaptic.  And it appears that package was never installed in the first place.

If it wasn't installed, and this is really getting to you, try switching from PulseAudio to ALSA.  If you're using KDE, I don't know the menus, but in Gnome, you go to System->Preferences->Sound, and in the Devices tab, you change all devices to ALSA.

I think they decided with the final release to not install libflashsupport by default.  When I uninstalled that and switched to ALSA, the Firefox Flash crashes disappeared for me.

---

### Post by philinux on 2008-05-24
I'm on 64 bit and libflashsupport is installed and flash dont crash the browser. Rather flash gets replaced with a white rectangle after a while. I have to close the open firefox to get flash back.

It's been bugged so hopefully will gets fixed asap. This could really put newcomers to linux off.

---

### Post by captainsixxx on 2008-05-24
okay? well ya;ll seem to have the same problem that i am having but i am new to all of this and don't understand half of what ya'll were talking about, so being me and all i have to ask how do i fix myself.

---

### Post by OpposingForce on 2008-05-24
> **forrestcupp said:**
> If it wasn't installed, and this is really getting to you, try switching from PulseAudio to ALSA.  If you're using KDE, I don't know the menus, but in Gnome, you go to System->Preferences->Sound, and in the Devices tab, you change all devices to ALSA.

I think they decided with the final release to not install libflashsupport by default.  When I uninstalled that and switched to ALSA, the Firefox Flash crashes disappeared for me.

They're all set to USB audio, and none of the devices work when I click test.  I have OSS4 installed because I have a creative xfi and OSS4 is the only thing that will work with my sound card.  There is no option for OSS4 in the gnome sound menu though.

---

### Post by forrestcupp on 2008-05-26
> **OpposingForce said:**
> They're all set to USB audio, and none of the devices work when I click test.  I have OSS4 installed because I have a creative xfi and OSS4 is the only thing that will work with my sound card.  There is no option for OSS4 in the gnome sound menu though.

There should be an option for OSS.  I can't say for sure, but I would think that if you chose that, and you have version 4 installed, that's what it would use.  

The thing about PulseAudio is that it routes everything to whatever sound system is working.  The point here is to just use the working sound system instead of going through PulseAudio first, which seems to be buggy with Flash.

---

### Post by OpposingForce on 2008-05-26
There's no option for it, there's just ALSA, Pulse Audio, and autodetect.  I know it's installed correctly because it works and I hear sound through Amarok, which I've set to use OSS.  Sound works in native linux games and games run through WINE.

---

### Post by tjwoosta on 2008-05-26
i just tried the fix that was posted earlier (switch to ALSA)

(it did not work for me)

firefox still closes randomly when in the middle of loading pages, and i have flash removed right now

---

### Post by OpposingForce on 2008-05-27
So I guess the fault is just a poorly written flash plugin for linux?  This seems to be a common issue

---

### Post by niwrip on 2008-05-31
FIXED!!!!! (so far anyways)

try this, it worked for me...
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org

---

### Post by marcelo danico on 2008-05-31
I had the same problem, this solution has worked, perfectly:

> I fixed my crash issue thanks to defcon (ubuntu-unleashed), maybe this will help you too ---> [http://www.ubuntu-unleashed.com/2008...phany-web.html](http://www.ubuntu-unleashed.com/2008...phany-web.html)

:)

---

### Post by forrestcupp on 2008-06-04
> **niwrip said:**
> FIXED!!!!! (so far anyways)

try this, it worked for me...
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org

That's basically another way to do what I said earlier.  If you remove libflashsupport, or change its name like you did, it should take care of your problems.

---

### Post by CameO73 on 2008-06-04
[See this thread for the best solution](http://ubuntuforums.org/showthread.php?p=4928900).

---

### Post by stchman on 2008-06-04
> **OpposingForce said:**
> Hi I have Ubuntu 8.04 and Firefox 3 beta 5.  I tried searching this and it came up but all the topics were like 2 years old and had no solutions to the problem.  It seems like every other video I watch on youtube crashes firefox with no warning or anything.  I ran firefox through the terminal and was able to easily reproduce the bug.  When it crashed, it just said "segmentation fault" in terminal, thats it, just 2 words.  This also happens on myspace pages with flash elements like the music player built in.  Again, this doesn't happen EVERY single time, just seems to be pretty random, and also quite frequent.  I'd say about 1 out of every 2 or 3 youtube/myspace pages with flash seem to crash the browser.  This has to be some type of flash bug, because the crashes seem to only happen on pages with flash elements.  But I'm not sure if it happens in other browsers too.  Any help would be great thanks

I use the flashplugin-nonfree package with ALSA and YouTube videos work great.

I have read that the pulse audio is very temperamental.  Switch over to ALSA in your System--->Preferences--->Sound menu.

Flash 9 is still a touch buggy in Linux, but Adobe will not fix it.

---

### Post by domness on 2008-06-07
The problem with me was the same, but it only happens when I've got another music player on such as Rhythembox.

As soon as I've closed any of these (Amarok also), it works perfectly.

---

### Post by OpposingForce on 2008-06-08
> **stchman said:**
> I use the flashplugin-nonfree package with ALSA and YouTube videos work great.

I have read that the pulse audio is very temperamental.  Switch over to ALSA in your System--->Preferences--->Sound menu.

Flash 9 is still a touch buggy in Linux, but Adobe will not fix it.

I use OSS4 and ESD, I have a creative xfi sound card so I don't have a choice.

> **niwrip said:**
> FIXED!!!!! (so far anyways)

try this, it worked for me...
sudo mv /usr/lib/libflashsupport.so /usr/lib/libflashsupport.so.org

Didn't work for me (to stop the crashing)

Closing my music player didn't work either.

edit- Updated to firefox 3-rc1.  I had to link the flashsupport file again and it seemed to be working at first.  I clicked on about 15 vids it didn't crash.  However not too long after that it started making "buzzing" sounds when opening videos again.  And now it's back to it's normal behavior of crashing about 40% of the time.

---

### Post by Taemojitsu on 2008-08-13
Awesome, changing to ALSA seems to have worked for me... I think I originally installed the libflashsupport plugin was because Flash was being buggy with Pulseaudio. Originally I had no crashes, however in the past week or so I have noticed a tremendous amount of crashes, I don't think I changed anything.. and so I found this thread.

---

