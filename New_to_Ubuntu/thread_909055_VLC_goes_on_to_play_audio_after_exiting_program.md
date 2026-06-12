---
title: "VLC goes on to play audio after exiting program"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Halbarad on 2008-09-03
Hi, very weird bug here. I watch a DVD with VLC (0.8.6e Janus wxWidgets interface), installed in Ubuntu Hardy 8.04.
The first time I watch a DVD, everything runs smooth. I exit (via File/Exit), and both video and audio stop -- as expected. (**But**, if I look in System Monitor, VLC is still there, "sleeping".)
If I start VLC again, with the same or anther DVD, then I exit before the DVD ends, the video stops, but the audio goes on. New sessions add new audio tracks and new sleeping VLC processes in System Monitor (one new VLC for each new session). While I am writing, I listen to the sound of two A Bug's Life and one Cinderella (I have three VLC processes going on... sleeping, but talking).
This happens only with DVDs -- whether on the hard disk or in the cd drive -- not with AVI files.

I can of course terminate the VLC processes by ending them in System Monitor, but this does not properly feel neat.

I wonder if anyone else had similar problems, or if you can suggest some investigations.

---

### Post by mc4man on 2008-09-03
> if you can suggest some investigations.

What happens when you click the square stop button before exiting?

---

### Post by Halbarad on 2008-09-03
> What happens when you click the square stop button before exiting? 

A good question, since I never stopped the DVD that way! The audio stops, but VLC sleeping processes pile up, one at a time (I have three now, occupying respectively 18, 18 and 16 M of memory). From time to time, they use a little percent of the CPU. I tried to activate them (Continue Process) and nothing happened -- they went on sleeping.

Thanks to your suggestion, it does not look like an *audio* problem. I wonder, would it be better to open another thread, called "VLC stays in memory after exiting" or something?

---

### Post by jemate18 on 2008-09-03
> **Halbarad said:**
> A good question, since I never stopped the DVD that way! The audio stops, but VLC sleeping processes pile up, one at a time (I have three now, occupying respectively 18, 18 and 16 M of memory). From time to time, they use a little percent of the CPU. I tried to activate them (Continue Process) and nothing happened -- they went on sleeping.

Thanks to your suggestion, it does not look like an *audio* problem. I wonder, would it be better to open another thread, called "VLC stays in memory after exiting" or something?

Open terminal... type
```
 killall vlc

```

This will close VLC

---

### Post by Halbarad on 2008-09-03
> Open terminal... type

 killall vlc

This will close VLC


Thx... I can both kill and end the VLC processes from System Monitor, but I prefer your approach via Terminal.

However, this does not solve the main problem: VLC needs to be manually shot down after watching a DVD -- unless one wants to have one or more silent processes staying there, eating up memory and resources etc.

The question is: **is this a bug of VLC or weird behaviour of my system?** Has anyone checked this in one's system? I mean, every time you watch a DVD and exit, does VLC terminate or is an instance of it still there, sleeping in memory?

---

### Post by philinux on 2008-09-03
A suggestion.

Close vlc and kill all instances. Then I would delete the .vlc folder from your home directory. 

Run vlc to re-create it's default settings.

---

### Post by Halbarad on 2008-09-03
> Close vlc and kill all instances. Then I would delete the .vlc folder from your home directory.

Run vlc to re-create it's default settings. 

Philinux, thank you for the suggestion, but it looks as if it was not a matter of settings -- I actually did not configure vlc at all. A detailed report follows.

```
[Report.]
[vlc closed]
~$ killall vlc
#killed all vlc instances
~$ ls -al .vlc
	total 60
	drwxr-xr-x  3 a a  4096 2008-09-02 23:46 .
	drwxr-xr-x 46 a a  4096 2008-09-03 19:02 ..
	drwxr-xr-x  2 a a  4096 2008-09-02 23:46 cache
	-rw-r--r--  1 a a 47450 2008-09-03 09:52 vlcrc
# contents of hidden dir /home/a/.vlc 
~$ mv .vlc .vlc.orig
# rename .vlc as .vlc.orig
[VLC. Play an AVI, not a DVD, file. Exit.]
[VLC correctly ends.]
[Again: VLC correctly ends.]
[Now let's try with a DVD. Exit. VLC is still there. Restart and play another DVD. Exit without having stopped video. VLC is still there and audio goes on. Two instances of VLC are running.]

```

The fact that this happens only with DVDs should be important, but I know too little to be able to interpret it. Ac3 audio and MPEG2 video codecs -- if the trouble is with these, I should have trouble with every player or process that uses the same codecs as vlc. On the other hand, if the trouble somehow depends on the complexity of the DVD structure, this suggests a bug of vlc, which I am inclined to exclude because to my knowledge no one ever complained about it.

Let's assume VLC is alright and my system is to be blamed. What could be wrong, and with what?

My first thought was: VLC tries to close a shell audio process that does not respond. But this cannot be the case, because the audio shuts down if I stop the movie before exiting vlc.

However, my guess is: vlc tries to stop all the shell processes that it activated in the system, but at least one of them does not respond correctly, and so vlc cannot terminate. Is this reasonable at all?
All ideas for further investigation are very welcome!
(I both fear and hope that, before this trouble with vlc is over, I shall know much more on the architecture of this operating system than I do now...#-o)

---

### Post by philinux on 2008-09-03
Well..

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/54630](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/54630)

Try changing the sound in System>prefs>

Try pulse audio, alsa or autodetect.

---

### Post by philinux on 2008-09-03
I tried to duplicate this on my system. And I've not got the problem. Same version of VLC.

On my system I've set it so on insert dvd nothing happens only disc mounts on desktop.

I manually start VLC and then choose open disc.

---

### Post by Halbarad on 2008-09-03
> Well..
[https://bugs.launchpad.net/ubuntu/+s...vlc/+bug/54630](https://bugs.launchpad.net/ubuntu/+s...vlc/+bug/54630)

> I tried to duplicate this on my system. And I've not got the problem. Same version of VLC.

Thank you so much for trying to replicate the bug and for the reference to the Launchpad thread. I can't believe I did not find it when I tried many combinations of "vlc audio process does not stop" etc.

One could conclude that the bug is a difficult one, because it does not affect all the machines or systems. But the good news is that the bug is going to be fixed in vlc version 0.9.0 -- this seems to me beyond dispute, after reading the Launchpad thread. -- And until the new release comes, I can kill the surviving instances of vlc with my bare hands.
However, before giving up, let's give another stab to it (hehe, looks like the serial killers forum).
> On my system I've set it so on insert dvd nothing happens only disc mounts on desktop.
I manually start VLC and then choose open disc. 
Try changing the sound in System>prefs>
Try pulse audio, alsa or autodetect. 

Your settings are exactly like mine; the current sound settings for music and movies are autodetect.
I'm going to try the others.
> [report]
[set System/Prefs/Sound/Music and Movies to ALSA. Close]
[vlc started. Played DVD. Exit. Vlc still in memory, audio on.]
$ killall vlc
[set System/Prefs/Sound/Music and Movies to OSS. Close]
[no change. vlc still in memory etc.]
$ killall vlc
[set System/Prefs/Sound/Music and Movies to PulseAudio. Close]
[same behaviour as above]

Another funny thing is that, if I exit while the main menu of the DVD is displayed, the music goes on looping -- this intimates that the problem is not so much in the audio modules as in the vlc process that "asks them" to play the music again, over and over.

I have also checked what happens if I merely open a VOB file in vlc -- from one of the DVDs already used for the tests above: vlc correctly terminates and vanishes from the System Monitor. This seems to me a decisive test: the bug must have to do with the menu structure. And the really puzzling question is, why the vlc way of handling the menu structure can cause a bug in some systems but not in others.

---

### Post by C. Wizard on 2008-09-03
I have the same problem with all video files, not just DVDs.  Doesn't matter how I exit VLC, I end up having to go into the process table to kill it.

---

### Post by Marshal0505 on 2008-09-03
This is why i close the file before closing VLC, else it's kill pid/vlc.
I remember getting the same behaviour with VLC on Windows, so always assumed this a VLC bug.

---

### Post by philinux on 2008-09-03
How come it does not happen for me? Thankfully.

---

### Post by mc4man on 2008-09-03
The continuing sound when exiting without stopping playback seems (at least here) to occur on some titles, others the sound stops. ( though I have gotten into the habit of halting playback before exiting.

The process not being killed on exit only seems to occur (here) when using  file -> open directory - from the vlc gui.
If you take the opposite path - r.click on a directory -> open with vlc, then exiting kills vlc. ( as does any of the various other ways.

---

### Post by Mister.Vash on 2008-09-03
This may be a known bug with vlc that is supposed to fixed in the next release.  Are you using the 'Open Directory' command in vlc?  That is the one that I am aware of and you have to manually kill the process after using the 'Open Directory' command

---

### Post by Halbarad on 2008-09-04
It looks as if the same bug had different forms in different machines and systems. Even in the Launchpad forum mentioned by Philinux (the lucky one...) the bug shows up in several variations.

To me, the relevant news is that the bug is in vlc and not in my system. All I can do is to wait for the 0.9 release of this very good player.
> If you take the opposite path - r.click on a directory -> open with vlc, then exiting kills vlc.
The same happens to me: if I r.click etc. the process ends, **but** another bug comes up: I can't navigate the menu (either with my mouse or with keypad) of a DVD opened that way (whereas I can navigate the menu of the same DVD if I open the folder from the vlc GUI).
> The process not being killed on exit only seems to occur (here) when using file -> open directory - from the vlc gui.
I am sure that, on my pc, the bug occurred also with DVD discs: I wrote detailed reports about the testing I did. But when I try to replicate the bug now, I am unable to do so. And C. Wizard says he has the bug with all video files. Well, if it's weird, it's weird. I can recall hundreds of debugging sessions in which the behaviour of a program looked as entirely erratic -- but of course it was not. It's up to the Videolan team to fix it now.

---

### Post by mc4man on 2008-09-16
The latest 0.9.2 release seems to resolve the audio running on and the process not being killed when exiting from a 'open directory'

There's also 2 new settings - 'allow only one running instance' and 'one instance when started from file'
(not necessary to fix above

---

### Post by Halbarad on 2008-09-17
This is very good news! I'll try it as soon as I can. Thank you!

---

### Post by mc4man on 2008-09-17
There are a couple of minor 'issues' with the new ver. and or the package people seem to be using.
[http://ubuntuforums.org/showthread.php?t=921519](http://ubuntuforums.org/showthread.php?t=921519)
when you start up a disk you'll see vlc working it's way thru to the menu displayed on screen. (not a big deal)

If you use file -> open directory on a VIDEO_TS folder on your hdd there will be no disk navigation, though 
if you right click on a VIDEO_TS -> open with vlc it works fine.

The mouse cursor acts funny sometimes.

Overall it works fine (to the extent I tried it

---

### Post by Netrunner on 2009-03-05
Hi, i'm using VLC media player 0.8.6h Janus
that's what happens:
Add folders of music to playlist.
Then close vlc.
It continues to play the whole playlist.
top output
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+ COMMAND            
26518 me  20   0  583m  50m  18m S    4  1.3   0:35.72 vlc                
and that it's strange..
and i have to close it with killall vlc

---

