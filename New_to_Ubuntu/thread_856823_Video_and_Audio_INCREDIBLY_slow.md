---
title: "Video and Audio INCREDIBLY slow"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by TallTreeRunningMoose on 2008-07-11
Hi everyone,

Whenever I try to play any video files (.avi, .mpg, etc even youtube) on my machine, the output is incredibly laggy.  The video is maybe 2 frames a second, and the audio is barely coherent, regardless of which video player I use (I have tried Totem, VLC and mplayer).  Audio seems to be fine by itself.  I´ve been digging around for a while and have yet to find anything that helps- any advice would be much appreciated.

Specs:
Dell Dimension 2350 (I know its old, but I got it for free, and you can´t argue with that)
Processor		: Intel(R) Celeron(R) CPU 1.70GHz
Memory		: 1034MB
OpenGL Renderer		: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
Audio Adapter		: ICH4 - Intel 82801DB-ICH4

Thank you!

---

### Post by Anynamewilldo on 2008-07-12
Have the same problem here, I did an update last night after watching a movie at my desk.. this morning when I tried to play back the same file it moves very slowly (maybe 1-2fps) I have no audio, except flash in Firefox, which plays fine.  

Very frustrating.

---

### Post by sdennie on 2008-07-12
See if going to System->Preferences->Sound and changing everything to ALSA helps.  You may have to set mplayer/VLC to use ALSA as well.

---

### Post by Anynamewilldo on 2008-07-12
> **vor said:**
> See if going to System->Preferences->Sound and changing everything to ALSA helps.  You may have to set mplayer/VLC to use ALSA as well.

Well, I was poking about a bit trying to figure out what was wrong and realized that if I close Firefox my video playback in mplayer is fine.  If i have a Youtube video paused in the background then it is choppy/no audio.

---

### Post by TallTreeRunningMoose on 2008-07-12
> **vor said:**
> See if going to System->Preferences->Sound and changing everything to ALSA helps.  You may have to set mplayer/VLC to use ALSA as well.

I had done that in System->Preferences->Sound, but not in VLC.  Doing it in VLC made the audio sound great, but now the video is even worse.  Now I get ~half a second of coherent video every 5-15 second, and the video is frozen for the other 14.5 seconds.  It gets better or worse depending on what Video output I tell VLC to use (ex. X11, OpenGL, XVideo), but none is visible.

So, great advice vor- we&#341;e 50% there, but I´m still having video issues.  

Just a side note, I have seen that Compiz is causing issues for a lot of other people, and so I got compizconfig from the Synaptic Package Manager and turned off all the effects - didn´t help me, but it might help you Anynamewilldo.

---

### Post by TallTreeRunningMoose on 2008-07-13
I just remembered that I recently flashed my BIOS to rev A02, and I can´t remember having any problems with it before that (though I don´t think I tried playing too many videos before that).  This may be a red herring, but could flashing my BIOS caused a problem?

---

### Post by TallTreeRunningMoose on 2008-07-13
So, I have been messing around some more, and it seemed like switching the sound output device did more than just fixed the audio.  I now CAN play video, and it looks OK, but that is only if video output is the ONLY thing the computer is working on.  For example, if Firefox is open while it is trying to play a video (say when I´m trying to watch a youtube video) its laggy again.

It seems like this maybe related to CPU usage.  I have noticed that when I´m watching video in VLC, the CPU usage is up near 80-90%, and the same is true when I am browsing the web with Firefox (not necessarily watching video) or running the update manager or something like that.  Does this seem like a reasonable idea?  Is there any way I can make better use of my CPU so it doesn´t have to work so hard on small tasks?  I mean, I have a 1.7 GHz processor, and though it isn´t blindingly fast, it should be able to handle watching youtube videos no problem.  Should I perhaps start another post on this topic?

---

### Post by Urgazhi on 2008-07-23
Not to revive an old topic, but I had the same issue and used the proposed solution to switching to ALSA sound drivers, and now it works beautifully, thank you very much!

---

### Post by fidamehran on 2008-07-24
> **Anynamewilldo said:**
> Well, I was poking about a bit trying to figure out what was wrong and realized that if I close Firefox my video playback in mplayer is fine.  If i have a Youtube video paused in the background then it is choppy/no audio.

I had and still have that problem. Video normally runs okay, but whenever I have Firefox running on the background, (didn't check with other apps running on the background) I have this issue. Video and audio becomes slow.

Could it be that Ubuntu has some problems multi-tasking?

---

### Post by sdennie on 2008-07-24
> **fidamehran said:**
> I had and still have that problem. Video normally runs okay, but whenever I have Firefox running on the background, (didn't check with other apps running on the background) I have this issue. Video and audio becomes slow.


Do you have any pages using Flash in Firefox when this occurs?  That could very well cause a problem like this.

> 
Could it be that Ubuntu has some problems multi-tasking?

Generally not. In my experience these sorts of problems are generally caused by poorly behaved closed source software (i.e. Flash) or poorly implemented closed source drivers (i.e. nvidia).  This is not always the case but, it's not unreasonable to look at these sorts of things before deciding if the bug lies with Ubuntu.

---

### Post by TallTreeRunningMoose on 2008-07-24
> **vor said:**
> Do you have any pages using Flash in Firefox when this occurs?  That could very well cause a problem like this.


It happens regardless of what tabs I have open- Flash or no Flash.  Even if no tabs are open, I still have the problem.  Its also not just a Firefox problem- I can have almost any 2 programs open, and as long as they are both trying to do something, they are both incredibly slow.

> **vor said:**
> 
Generally not. In my experience these sorts of problems are generally caused by poorly behaved closed source software (i.e. Flash) or poorly implemented closed source drivers (i.e. nvidia).  This is not always the case but, it's not unreasonable to look at these sorts of things before deciding if the bug lies with Ubuntu.

I don't think its poorly closed source software- I can create this problem immediately after starting up.  It could be a driver issue- I didn't consciously install any drivers, since I didn't see anything anywhere that said I needed to.  When I tried to reinstall my video driver, it said it was already installed (I think), but I have not tried to mess with any other drivers.  Also, I have windows as well on this machine, and it seems to have similar problem.  It doesn't seem to be nearly as bad as the problems when I'm running ubuntu, but it is there.

---

### Post by benjaminjames on 2008-07-26
ok so i am gettting this problem now aswell when i try to watch a avi video in fullscreen it is very laggy and unwatchable i tried closing everything else but it still happens, im using an amd 2000 sempron with a geforce4 mx440 and  1 gig of ram any ideas?? btw i have the restricted drivers installed

---

### Post by stmiller on 2008-07-26
You can try using a low-latency kernel which is what people use who work with lots of audio and video in Linux. All audio and video work much smoother with a low-latency kernel. I wish Ubuntu, a desktop oriented distro, would use a low-latency kernel by default.
```

sudo apt-get install linux-rt

```

If the video you are watching is HD content, then there is not much you can do. (Other than watch using a faster dual-cpu computer.) :)

In Windows, the Nvidia driver actually helps in video playback. But this feature does not exist in the Linux driver and Nvidia is highly criticized for that. So all video playback is put directly onto your CPU.

---

### Post by benjaminjames on 2008-07-26
ok cool i will definately try this but will switching the kernel change anything else??

---

### Post by gjoellee on 2008-07-26
**Part 1.**
Flash 10BETA runs much better in Linux then flash 9. Download the tar.gz file from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
now extract it and put it to your home folder.

**Part 2.**
Now lets remove flash 9. by (THE FOLLOWING IS BASED ON THAT WHAT IS DEFAULT) go to your home folder and press  CTRL + H and find ".mozilla" enter that folder. Now go to "plugins" in that folder you should find "libflashplayer.so" if you have flash installed...delete libflashplayer.so.

**Part 3.**
Go to terminal and type > cd install_flash_player_10_linux
 and after that type > ./flashplayer-installer to as it says you to do to it is installed. Restart firefox if it was running when you install flash...

---

### Post by benjaminjames on 2008-07-27
does flash have anything to do with avi playback?

---

### Post by TallTreeRunningMoose on 2008-07-30
> **stmiller said:**
> You can try using a low-latency kernel which is what people use who work with lots of audio and video in Linux. All audio and video work much smoother with a low-latency kernel. I wish Ubuntu, a desktop oriented distro, would use a low-latency kernel by default.
```

sudo apt-get install linux-rt

```

If the video you are watching is HD content, then there is not much you can do. (Other than watch using a faster dual-cpu computer.) :)

In Windows, the Nvidia driver actually helps in video playback. But this feature does not exist in the Linux driver and Nvidia is highly criticized for that. So all video playback is put directly onto your CPU.

I gave this a try, but no luck.  It may have helped a bit, but I couldn't tell.

I also found this other thread talking about how Hardy turns dynamic CPU scaling on automatically [here]("http://ardour.org/node/1759").  I eventually ended up removing powernowd, and that seemed to help a bit more, but I'm still having all the same problems.  

I have yet to try to install the different version of flash recommended in the other post, but I'm pretty sure that is not the source of my problem, as I don't think vlc uses flash to play avi's, and it has issues doing that when firefox (or almost any other program) is or isn't open.

---

### Post by daevyd on 2008-08-03
I can't believe the poor DVD playback quality issues we're having.  There has GOT to be a way around this!!  If only we could find a common thread as to why this is happening.  I'm having the same quality issues whether I have other windows open or not.  Web flash works but Totem & VLC leave a lot to be desired.  DVD viewing is impossible.

---

