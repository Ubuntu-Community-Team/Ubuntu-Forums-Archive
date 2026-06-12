---
title: "HOWTO Set sound if you have 2 soundcards"
date: 2005-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by MonoLT on 2005-04-15
_**[FONT=Tahoma][SIZE=3][COLOR=DarkSlateBlue]Foreword[/COLOR][/SIZE][/FONT]**_

If you have 2 soundcards and don't hear anything then this HOWTO should help you.

Actually it's fully based on dusu's Thread about sound in Hoary and Linux and comments I've found there: [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) I've just modified it a bit and included some optimizations.

_**[FONT=Tahoma][SIZE=3][COLOR=DarkSlateBlue]Configuration[/COLOR][/SIZE][/FONT]**_

**1.** We need to kill ESD. So open terminal and type:
```

sudo killall esd

``` 

**2.** Now we need to tell ESD not to run when one does not need it. Open esd.conf file:
```

sudo gedit /etc/esound/esd.conf

``` 

and insert this (for some people "dafault" parameter is not suitable so they should use "mixer" instead):
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default // use "mixer" instead of "default" if you don't have sound
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

``` 

**3.** We need to "allow" use of many sounds at the same time. So we need to install libesd-alsa0:
```

sudo apt-get install libesd-alsa0

``` 

**4.** Now create asound file:
```

sudo gedit /etc/asound.conf

``` 

and edit it like this:
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

``` 

What I did here is changed period_size and buffer_size for better performance. Rate is also changed to hear high quality sounds. And pcm is also changed here from "hw:0,0" (first soundcard) to "hw:1,0" (second soundcard (my default one)). This helped me and I hope it'll help you too.

**4.** Last step: allowing sound in Flash files:
```

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

``` 

**5.** Restart ALSA:
```

sudo /etc/init.d/alsa restart

```

and logout from your session. When you login next time you should be able to hear Gnome Welcome Sound :razz: 

_**[FONT=Tahoma][SIZE=3][COLOR=DarkSlateBlue]In the end[/COLOR][/SIZE][/FONT]**_

I want to thank all the people around this forum, especially dusu, ploum and wrochal whole ubuntu support team and of course developers of the best linux distro I've ever used.

---

### Post by ekzema on 2005-04-24
Hi there.

I'm happy as a happy man can be!:)

I perused many posts about this whole double sound card confusion on the last Ubuntu release, and the only post that solved my problems was this one!

Love Ubuntu, but the sound was important for me. Again, thank you very much for taking the time to collect all this useful information in an organized way.^^,

---

### Post by Brian McConnell on 2005-04-30
Hmmm... I'm not sure if I'm any better off since I applied these changes. This howto looked like it'd be perfect for me since I've also a preferable second soundcard and would like multiple sounds capability.

I have selected Alsa from System>Preferences>Multimedia Systems Selector, still I cannot play music files if I've enabled sound server startup from System>Preferences>Sound. 
I should also note that since it was necessary for me to use "mixer" instead of "default" in this code:

```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default // use "mixer" instead of "default" if you don't have sound
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

it was also necessary for me to use "mixer" instead of "default" in the line shown below as "pcm.!default {"

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}


```


I'd like to be able to have those system sounds while playing music files and such. I was hoping this howto would get me there, but it looks like I've still got some adjustments to make. What else can I do to get Rhythmbox and system sounds to coexist?

Thanks for your efforts MonoLT, they are much appreciated.

---

### Post by Brian McConnell on 2005-04-30
Well, it appears that selecting esd from the system>preference>multimedia systems selector did the trick for having Rhythmbox run while sound server is enabled at startup. I can play video files on Totem at the same time as well, but no sound. Probably something to do with the sound server at startup, as that seems to be the biggest chink in the chain (Fockers reference, there).

---

### Post by cowlip on 2005-06-25
Hi, this howto fixed my exact problem.  Usually, I just disable esd server startup undre "souns" applet, but this works regardless.

I wonder why it exists anyways?  So many motherboards come with onboard that people just install a soundblaster live into.

---

### Post by Copter on 2005-07-07
Hi everyone. Im total noob in linux world. Installed Kubuntu 2 days ago and with the help of You guys Im able to do everything I want to do :razz:. Setting 2 soundcards was essential to my hobby. Thanks a lot MonoLT and the rest of ppl here. This howto rocks  \\:D/ 

copter :]

---

### Post by weejamer on 2005-08-07
Can i ask 1 question... 

How can i switch between my 2 sound cards?

---

### Post by kumpf on 2005-08-18
This is a nice HOW-TO, but I have a quick suggestion...

It seems that Ubuntu is very close to being able to go "prime-time" but lacks a few of the more user friendly options that Joe-Computer-User needs.  Based on the number of people that found this thread helpful, maybe someone who understands the sound architecture stuff really well could write an app for the next release of ubuntu that allows for configuration with ComboBoxes or something else more intuitive.

Audio has been managable for me, but it's been a lot of digging through configuration files to make things work.  (I have VIA on-board audio that I don't use, and a soundblaster card which works great after digging through setup/config files)

Ubuntu is great!  let's fill in the small gaps to broaden its friendlyness to more users!
  :)

---

### Post by mbeach on 2005-09-09
I've also got to give a big thank you for this one.   My Logitech Quick Cam Zoom camera has audio capture and apparently being set as the first sound device.  It has long fallen behind the desk and I sort of forgot about it.  After several flawless installs on some spare GX150's at work I tried Ubuntu on my home machine - only problem was the sound - not bad at all.

---

### Post by grimdeath on 2005-09-10
WOW thank you soo much, before this i was having to go into my bios and disable my onboard sound so ubuntu would default and run my soundcard instead...thats all fine and dandy except for the fact that i dual boot between it and windows xp pro, so i can finally use my soundcard on both easily

im using onboard + sounblaster live 24

i think my soundcard is faulty though were as i cant get the darn mic to work on it in windows or ubuntu :/ been forced to use soundcard for output and onboard for input(mic)....hope i can get this figured out soon!

---

### Post by cowlip on 2005-09-10
I just want to tell you guys that Breezy fixes this problem :D  You can select your soundcard in the sound preferences applet, and then raise volume in the volume mixer.  I hope it helps

---

### Post by baataa on 2005-09-14
I first tried the other guide to properly installing the soundcard n stuff and it worked, somewhat. I finally heard the startup sound and got sound in flash movies. (although with a slight delay) Then I saw it said to go here if you have two soundcards and I just found out my motherboard has onboard sound too. Anyway I applied the instructions here but now the sound is all choppy in flash. :(
xmms seems fine though. Any idea what the cause could be ? Do I need an even larger buffer ? Smaller ?

---

### Post by baataa on 2005-09-15
I think I fixed it. I checked my motherboard manual and noticed it had onboard sound and the chipname matched the one in alsamixer. It was using my onboard instead of my pci card.. I disabled the onboard in BIOS and when I rebooted sound was gone. after that I edited the esd.config and changed the hw: to 0 instead of 1, after alsa reboot I had sound again. Glory be!

---

### Post by cowlip on 2005-09-20
[QUOTE=baataa]I think I fixed it. I checked my motherboard manual and noticed it had onboard sound and the chipname matched the one in alsamixer. It was using my onboard instead of my pci card.. I disabled the onboard in BIOS and when I rebooted sound was gone. after that I edited the esd.config and changed the hw: to 0 instead of 1, after alsa reboot I had sound again. Glory be![/QUOTE]
 You can disable that sound module in /etc/hotplug/blacklist too :)  Just do "lsmod | grep snd" and look for a name that is similar to your onboard snd

---

### Post by nickless on 2005-10-04
Hrm I have no real problem here, because I hear sound :) but I don't understand the whole sound & linux thing, not completely at least.
I have now bought a soundblaster live with this nice emu-whatever chipset, that is said to be so great for Linux :D When I booted the soundcard was detected and adjusting the volume in kmix was no problem. But my onboard card is still the preferred card or something. In my taskbar the kmix applet still only shows the volume of the onboard card.
Then now my card should be able to play many sound at the same time, which it does, but shouldn't I change now the configuration so that the sound deamon doesn't wait for those 2 seconds? I believe maybe this will fix the flash sound delay also...

---

### Post by joneall on 2005-10-24
I have a Dell 4600, which comes with an Intel sound adapter on the motherboard (I think).  I also have an Audigy (2) sound card.

Yesterday, I tried Ubuntu 5.10 Live and managed to switch the sound card to the Audigy (from somewhere in the Gnome menus) and the sound worked fine. :)   (By default, it chose the Intel.)

Today, I tried it again and can't do it.  Either I can't find the right menu or else the Audigy card was not detected by the boot.  :( 

Help, please.  Thanks in advance.  John

---

### Post by joneall on 2005-10-25
I think I solved my problem.  Ubuntu 5.10 finds both sound cards, Ubuntu 5.04 does not.

Thanks anyway.  :???:

---

### Post by gumbico on 2005-11-03
Niiice, no thinking required.  I just followed the steps and sound is everywhere now (Flash audio finally works).  Thanks!

---

### Post by delsdog on 2005-11-05
I have just added an Audigy 4 to my setup, and disabled the onboard soundcard in BIOS, but no matter what combination of files I edit I can't seem to get any sound out of Breezy. I don't really want to do a complete re-install. Is there an easy way to get to the initial sound setup scripts like there is with xserver? Or alternatively does anyone know of a surefire way to get my sound working again? (It previously worked fine on the old onboard card, and I know the new SB4 works as the beast that is Windows uses it ok)

---

### Post by _Zardoz_ on 2005-11-06
Everything works but flash sound, it is redirected on the integrated soundcard instead of my audigy!!!!

---

### Post by 23meg on 2005-11-18
I have an external USB audio device in addition to my laptop's internal sound chip and in Breezy I have to select it in Preferences / Sound every time I plug it in for the preferred audio engine to select it as default. The "New audio playback device detected" message pops up every time I plug it in. Is there a way of setting things so that it becomes the preferred device whenever it's plugged in?

---

### Post by marsanpin on 2006-04-02
Well, after trying so many distros I must say I'm impressed.
Very good this post; helpful and straight to the point.
I can now run all my audio stuff thanks to this forum and dedicated members.
I had to register to thank you and hope to get some time to involve myself with more configs and scripts and...

Mario

---

### Post by jadugarr on 2006-04-02
Does anyone know how to switch between soundcards in kde?  I like to use both for different applications.

---

### Post by bastler on 2006-06-21
Thanks for this HowTo, it worked well for me.

Just one Problem: I use one onboard-soundchip and one USB-Device (always connected) for sound and have them set up to do specific things (onboard for music and multichannel via digital out, usb-sound for ICQ-ping, system beeps etc.).

Unfortunately the two soundcards' "hw:X,X"-Addresses change on every reboot, depending on the order they happen do be recognized by the system, which is extremely annoying.

Is there any way to fix this, so both soundcards always boot with the same hw:X,X-Addresses, regardless of what happens around them?


using ubuntu dapper final on i386

---

### Post by ssavelan on 2007-02-14
This is a pretty old thread.  I wonder how Ubuntu Studio is doing; I want to contribute.

I am on my back-up partition that I was going to use for experimental audio; but, i crashed the audio on my main ubuntu drive... yadayada, ironically sound still works over here.  This one only runs the Echo Layla24.  The other one was running both the layla and the onboard via-82xx driver.  I'm not sure what killed it.  I was running the beta ALSA and was very happy with it (XXX-rc2, Feb '07).  I was getting adventurous and trying to use wine to run some winduhs (cr)apps and the sound for Flash gave up for some reason.  Then I was trying to remove and re-build the ALSA_balls and still no Flash, sound okay with everything else.  I boot today and ubuntu knows nothing of my onboard soundcard, still no sound in flash, error message, something about no alsa_pcm default (will upload soon).  I am on the verge of starting again with a mint install.

I hope that I can use this How-to to get the other partition's sound working without returning to ground zero.  I have so many great things that I've set-up on that install, it would take a few days to get back.  ALSA, JACK, Citrix Client, JAVA that runs everything hanging by a thread, two sound cards, all media content, SAGE, R.  Okay, so it will probably only take 6-8 hours.  

Who is the sound master for ubuntu?  I want to help.

---

### Post by Tominator on 2007-07-08
> **cowlip said:**
> I just want to tell you guys that Breezy fixes this problem :D  You can select your soundcard in the sound preferences applet, and then raise volume in the volume mixer.  I hope it helps


Here it is two years later and using Fiesty Fawn. Fiesty offers the same option but it is of no help if your second sound card driver has to be manually loaded. I love the whole idea of Ubuntu but I really struggle trying to do things like this. If you need a vehicle fixed, or If you are interested in all of the thousands of meters of fiber optic cables that are assembled by the very complex machinery that I operate on the job, I'm your guy. On the basis of my years long use of Ubuntu, I pronounce it not ready for prime time, unless the average user gets it pre-installed on a Dell.

---

### Post by manimaul on 2007-12-19
There is a much easier way:

#sudo asoundconf list
#sudo asoundconf set-default-card <name of card>

---

