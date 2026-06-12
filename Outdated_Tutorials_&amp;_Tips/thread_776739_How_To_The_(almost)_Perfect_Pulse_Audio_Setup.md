---
title: "How To: The (almost) Perfect Pulse Audio Setup"
date: 2008-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by zman0900 on 2008-04-30
After much tinkering, I have finally found a setup with Pulse Audio on Hardy that I am happy with.  Since a lot of people are having trouble with it, here's what I did:  

[SIZE=6]**Updates:**[/SIZE]
[LIST=1]
[*]Added link to method for 5.1 sound
[*]Patched SDL pulse driver.  See changes in Step 3: libsdl1.2debian-all is no longer needed.
I've submitted a bug to try to get this patch incorporated in the Ubuntu version: [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/225467](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/225467)
[*]Created repository for new pulse drive (supports i386, amd64, and lpia)
More changes to Step 3 now.
[/LIST]

1) **Install additional packages**
```
sudo apt-get install libao-pulse libasound2-plugins
```2) **Configure settings**
    --edit your /etc/asound.conf file like so:
      ```
pcm.pulse {
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

```    --edit your /etc/libao.conf like so:
      ```
default_driver=pulse
```    Create any files that don't exist.

    --Go to System>Preferences>Sound
    --Set the top four boxed to PulseAudio Sound Server
    --Set the Default mixer to the name of your sound card

3) **Install additional Pulse packages**
```
sudo apt-get install libflashsupport padevchooser pulseaudio-module-hal pulseaudio-module-x11
```Allow it to install the additional dependencies.

**--Updated here:--**
To ensure you have the default libSDL install, first run this:
```
sudo apt-get install libsdl1.2debian libsdl1.2debian-alsa
```
Now add the following lines to /etc/apt/sources.list (this will add my repository, it only the packages you need):
```
## zman0900's PPA
deb http://ppa.launchpad.net/zman0900/ubuntu hardy main
deb-src http://ppa.launchpad.net/zman0900/ubuntu hardy main
```
Now run the following:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libsdl1.2debian-pulseaudio
```
**Note:** If libsdl1.2debian-pulseaudio will not install for you, do the following two things instead:
```
sudo apt-get install libsdl1.2debian-all
```
and add this to ~/.profile :
```
# Make SDL audio work properly with Pulse
#export SDL_AUDIODRIVER=pulse
```

Both libsdl1.2debian-pulseaudio and libsdl1.2debian-all contain that patched Pulse driver, all just requires you to explicitly use Pulse with the SDL_AUDIODRIVER environment variable.  
**--End Update--**

5) **Set up device chooser**
Go to Applications>Sound & Video>PulseAudio Device Chooser
It will show up as a plug in notification area.
Left click, click Preferences, check Start applet on session login.  

6) **RESTART THE COMPUTER!**
Everything should be set up now.  You should now be able to play audio through both ALSA, esd, and Pulse applications at the same time, and everything will show up in the Device Chooser as a separate, configurable stream.  

[SIZE="6"]**Additional Info:**[/SIZE]
See the PulseAudio website for info about many other applications:
[http://pulseaudio.org/wiki/PerfectSetup#ThirdPartyApplications](http://pulseaudio.org/wiki/PerfectSetup#ThirdPartyApplications)

**About OSS applications:**
If you want to use an OSS application at the same time as any other sounds playing through Pulse, us the command:
```
padsp <some-oss-program>
```This should work for any OSS application.  That will redirect the sound through Pulse.  Without padsp, the OSS application is the only thing that can play sound while its running.  

**Possible Method for 5.1 Sound:**
See here: [http://ubuntuforums.org/showpost.php?p=4835638&postcount=4](http://ubuntuforums.org/showpost.php?p=4835638&postcount=4)

[SIZE=6]**Current Issues: **[/SIZE]
[LIST=1]
[*]Wine does not work properly through alsa, esd, or oss.
[*]The pulse driver for SDL has a very slight audio lag, but it is much less than with the esd driver.
[*]Some other programs may not work that well with alsa through Pulse.
See bug: [http://www.pulseaudio.org/ticket/285](http://www.pulseaudio.org/ticket/285)
[/LIST]
Post something if you know of more.

---

### Post by rabid9797 on 2008-04-30
worked perfectly :) i initially came looking to see if i could fix flash playback, but i ended just following the entire guide and it worked without any flaws/bugs! thanks

---

### Post by irshadcharm on 2008-05-01
will 5.1 surround sound work if i follow the exact steps? This is my sound card....Please help...

```
cat /proc/asound/card0/codec#* | grep Codec
```

Output:

```
Codec: SigmaTel STAC9221 A1
```

---

### Post by zman0900 on 2008-05-01
I believe some additional steps will be required, these steps give you the default 2 channel setup.  If you search the forums some more, I think I may have seen something about getting 5.1 sound to work with Pulse, so you might try that after this.  I myself don't have the hardware to test it.

---

### Post by impert on 2008-05-01
Thanks, but it didn't work for me.

---

### Post by Zorael on 2008-05-01
Do note that Skype won't work until they change how it interacts with ALSA. There is a workaround which dumbs down pulse, disabling stuff like automatic device detection and volume settings individual to apps. If, like me, you only use Skype for the chat anyway, you can grab the OSS version for the time being, and alter your shortcuts to launch it with padsp. The sound stutters, so your voice chat experience may be mediocre, but stuttering "new message" notifications don't bother me much.

I downloaded it (Skype OSS), extracted it into /opt/skype.oss, then made a wrapper script and saved it as **/usr/local/bin/skype.oss**. Off the top of my head:
```
#!/bin/bash

padsp /opt/skype.oss/skype &
```
```
$ sudo chmod +x /usr/local/bin/skype.oss
```

[http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)

---

### Post by Jerdsy on 2008-05-01
Has anyone tried this with Xubuntu?

---

### Post by durand on 2008-05-01
Cool, seems to work with sdl games (no sound but I can see the stream in pavucontrol). I guess it will work when I restart. Thanks :)

---

### Post by jorge.py on 2008-05-01
I get 5.1 working with this:

[http://ubuntuforums.org/showpost.php?p=4835638&postcount=4]("http://ubuntuforums.org/showpost.php?p=4835638&postcount=4")

---

### Post by durand on 2008-05-01
Thanks for the 5.1 trick!

---

### Post by zman0900 on 2008-05-02
I've posted a new .deb file above with a patched version of the pulse driver for SDL.  If any one feels like trying it out, follow the directions above and post something here about how it works for you.  I'm currently using it on my computer and it works good.

---

### Post by durand on 2008-05-02
What does the sdl driver do?

---

### Post by zman0900 on 2008-05-02
> **durand said:**
> What does the sdl driver do?

From the SDL website: "Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer. It is used by MPEG playback software, emulators, and many popular games"

If you run:
```
apt-cache rdepends libsdl1.2debian
```
you can see all of the programs you have that use SDL.  This list is very long for me, but the major things that this affect audio-wise are games.

---

### Post by peacewithall on 2008-05-02
I want to try this guide, problem is I'm have 64 bits 8.04, and the patched deb won't install, I was wondering would installing by your other method (installing libsdl1.2debian-all), work as an alternative?.

I've installed Hardy 3 times because of this sound mess (using other guides), and another question would be, are the changes made in this guide reversable?.

---

### Post by zman0900 on 2008-05-02
> **peacewithall said:**
> I want to try this guide, problem is I'm have 64 bits 8.04, and the patched deb won't install, I was wondering would installing by your other method (installing libsdl1.2debian-all), work as an alternative?.

I've installed Hardy 3 times because of this sound mess (using other guides), and another question would be, are the changes made in this guide reversable?.

As we speak, I am working on getting the package up in a PPA on launchpad which will make both a x86 and amd64 version available if all goes well.

---

### Post by zman0900 on 2008-05-02
I have updated with a new repository and support for other architectures. See the first post.

---

### Post by peacewithall on 2008-05-03
THANK YOU THANK YOU !!!!

It worked, I now have all my speakers working with the 5.1 guide too, and sound is as clear as a bell. I can confirm I have Ubuntu 8.04 64 bit.

This guide works I don't believe it I need to lay down, phew !!.

Did I say thank you?, :)

---

### Post by cor2y on 2008-05-03
Thank you for the How To, its great to see how to extend pulse audio to what it should have been at default install.
Now apps are not getting silenced or capturing the sound daemon exclusively for themself.

---

### Post by peacewithall on 2008-05-03
Also I have skype sounds back using the 'padsp skype' trick, I have yet to test a call though.

Also for those having no sound problems with WINE I found the following post worked perfectly for me,

[http://ubuntuforums.org/showthread.php?t=766872](http://ubuntuforums.org/showthread.php?t=766872)

Its the first post by mriedel, basically set WINE to use only OSS, then add 'padsp ' to the beginning of the wine game link. You can set profiles for every game in WINE too.

---

### Post by Killerah on 2008-05-03
Perfect! Thanks zman! You rock, I can have amarok and firefox going at the same time! Thanks so much, it was really annoying having to close amarok and restart firefox to hear the audio in a flash video.

---

### Post by durand on 2008-05-04
> **zman0900 said:**
> From the SDL website: "Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer. It is used by MPEG playback software, emulators, and many popular games"

If you run:
```
apt-cache rdepends libsdl1.2debian
```
you can see all of the programs you have that use SDL.  This list is very long for me, but the major things that this affect audio-wise are games.

Sorry, didn't make myself clear. What does the patch you applied do? Cos I tried it but sdl games still don't work. Thanks.

---

### Post by SkratX on 2008-05-04
I can hear sound on banshee, firefox and vlc at the same time.
My only problem with pulseaudio is that when i'm hearing music and minimize/maximize any window the sound stutters. I still haven't found a solution for the problem

Anyone else with the same problem?

---

### Post by zman0900 on 2008-05-04
> **durand said:**
> Sorry, didn't make myself clear. What does the patch you applied do? Cos I tried it but sdl games still don't work. Thanks.

I believe the patch changes something with the buffering in the PulseAudio driver for games.  If its not working for you, try running the game from a terminal like so:
```
SDL_AUDIODRIVER=pulse <game>
```
If that work, you will need to add SDL_AUDIODRIVER=pulse to your environment permanently, which can be done by adding the following to ~/.profile:
```
export SDL_AUDIODRIVER=pulse
```


> **SkratX said:**
> My only problem with pulseaudio is that when i'm hearing music and minimize/maximize any window the sound stutters. I still haven't found a solution for the problem

Try editing /etc/pulse/daemon.conf.  Make sure it has the following lines:
```
; high-priority = yes
; nice-level = -11

```
That's what mine has and it works ok, but if you don't have more than one processor, maybe a higher priority would be necessary, so you might play with the nice level a bit.  Lower numbers are higher priority (i.e. try something like -13 or -15 if -11 isn't enough).  I would probably avoid -20 though.

---

### Post by TerminusEst on 2008-05-04
Great! Now I've gone from no surround sound to no sound at all :(

---

### Post by SkratX on 2008-05-04
I have that on the daemon.conf file, but i still get the stutter

---

### Post by zman0900 on 2008-05-04
> **SkratX said:**
> I have that on the daemon.conf file, but i still get the stutter

I'm not sure what else to tell you about that.  What are your computer's specs?

---

### Post by SkratX on 2008-05-04
1.6GHz Centrino laptop, 1.2Gb RAM, Intel ICH6 is the sound device.
Starting to think that this was not the best choice for ubuntu...this was, i think, the poorest release yet =(

looks like there are many people with the same problem
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190754)

---

### Post by zman0900 on 2008-05-05
> **SkratX said:**
> 1.6GHz Centrino laptop, 1.2Gb RAM, Intel ICH6 is the sound device.
Starting to think that this was not the best choice for ubuntu...this was, i think, the poorest release yet =(

looks like there are many people with the same problem
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190754)

It wouldn't surprise me if it is a bug in Pulse, it is a nice audio system, but it is far from being ready for main stream use.  Putting it in a LTS distribution like this was probably not a great idea, but at least it will get some of the bugs out in the open.  Though I really think there should be an easy option to remove it for those who don't feel/can't work around the bugs.  :?

---

### Post by FastZ on 2008-05-05
> **TerminusEst said:**
> Great! Now I've gone from no surround sound to no sound at all :(

Same here, except I had sound before I followed this how-to.  I had hoped to get sound in flash playback in Firefox but now I lost all sound.  

How do you reverse everything that was done in this how-to?

---

### Post by durand on 2008-05-05
> **zman0900 said:**
> It wouldn't surprise me if it is a bug in Pulse, it is a nice audio system, but it is far from being ready for main stream use.  Putting it in a LTS distribution like this was probably not a great idea, but at least it will get some of the bugs out in the open.  Though I really think there should be an easy option to remove it for those who don't feel/can't work around the bugs.  :?

Here's how you can remove pulseaudio:

From the ubuntu wiki:
> PulseAudio Removal

If you decide you no longer like PulseAudio and would like to disable it: Remove the added lines to /etc/asound.conf If /etc/asound.conf did not exist when you installed PulseAudio, you may remove /etc/asound.conf entirely. 

After this, you may remove all of the installed PulseAudio packages. 

To disable pulseaudio in hardy you need to select alsa for for all options in /system/preferences/sound


I myself am not sure if surround sound is working or not. I only need it for games but I'm not sure how to test it. It feels like surround sound but...

---

### Post by soundf on 2008-05-06
sorry for the dumb question, but how do I get premission to change files in /etc?

---

### Post by zman0900 on 2008-05-06
> **soundf said:**
> sorry for the dumb question, but how do I get premission to change files in /etc?

```
sudo <editor> <file>

for example:
sudo gedit /etc/asound.conf
```

---

### Post by soundf on 2008-05-06
ok it worked!
im not sure this is related, but when I want to remove stuff and move things i get this massege: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I did run it but it says:
dpkg: requested operation requires superuser privilege

what should i do?

---

### Post by zman0900 on 2008-05-06
> **soundf said:**
> ok it worked!
im not sure this is related, but when I want to remove stuff and move things i get this massege: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I did run it but it says:
dpkg: requested operation requires superuser privilege

what should i do?

Whenever you are installing or removing packages, or generally doing thing that require modification of system files, you usually need to prefix the command with sudo.  Sudo gives the process you are running temporary root (superuser) privileges.

---

### Post by newbuntuxx on 2008-05-06
Hey,

I have been using linux for the past two days (hence the name newb!). I am an ex-xp user. Given the latter, I had a few .rm files that i wanted to listen to. After installing mplayer and the codecs, i was able to run the files and listen to them, however, every time i run a .rm file, i would get the following error:

```
[pulse] failed to connect to server: connection refused
```

After following your guide, that error message disappeared. And running .rm files is smoother than ever.

Naturally, I was blindly following your instructions, of course I didn't understand a single thing (apart from the apt-get). Nonetheless, everything worked, and i am looking forward to learning linux.

thanks again. sorry for the long post.

Ps. I am running Ubuntu 8.04 32 bit.

---

### Post by Mushed on 2008-05-07
<sorry, can't figure out how to delete my post>

---

### Post by Mushed on 2008-05-07
> **zman0900 said:**
> ```
sudo <editor> <file>

for example:
sudo gedit /etc/asound.conf
```

I'm also a newb. There is no 'asound.conf' file in my /etc folder. Now the guide says that I should create such missing file. The above won't work being as I don't already have the file; how do I change the permissions in my /etc folder so I can do this?

EDIT: The code worked, that's what i get for assuming. Thanks.

---

### Post by kpkeerthi on 2008-05-07
This thread needs to be stickied. Mods?

---

### Post by Genius314 on 2008-05-07
Great, I can run Firefox and Amarok playing together... but nothing else seems to work.
Audacity plays, but no sound comes out. LMMS does the same thing (SDL works, but it sounds choppy).
Anything special needed for these two programs, or did I just do something wrong?

EDIT: Running LMMS before others seems to work. Audacity still doesn't play anything (no errors, it just doesn't have any output...)

---

### Post by pickboy87 on 2008-05-07
Sorry for a dumb question, but here goes:

What's the difference between Pulse Audio vs. OSS or Alsa? I'm currently using OSS, so what's the benifit of switching? (I'm using 2.1 Klipsch Speakers and using M-Audio Revolution 5.1)

---

### Post by gotjpeg on 2008-05-07
So for the surround sound trick under the sample sound channels. Do I out in 5 or 6 if it's 5.1 surround sound?

---

### Post by Stunts on 2008-05-09
Hi!
Great HowTo.
Now I can use multiple apps with sound!
It got me 90% things working.
All that doesn't work now is Neverwinter Nights, which uses SDL.
I'm not sure how to make it work now, but once I get an answer I'll post it here.

Thanks again for this!

---

### Post by zman0900 on 2008-05-09
> **gotjpeg said:**
> So for the surround sound trick under the sample sound channels. Do I out in 5 or 6 if it's 5.1 surround sound?

I believe you would want to go with 6.

---

### Post by Stunts on 2008-05-10
OK, I've got everything working now. Even Neverwinter Nights which uses SDL and ALSA.
I got this answer on NWN linux forums, so credit goes to "Skildron".
You ahve to edit your ~/.asoundrc file and paste the following in there:
```

pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dsp0 {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer {
	type dmix
	ipc_key 1024
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 1024
		buffer_size 8192
		rate 48000
	}
	bindings {
		0 0
		1 1
	}
}

ctl.dmixer {
	type hw
	card 0
}

```

Some people had to change the rate setting in the file from 48000 to 96000 to produce usable output, so you might want to keep that in mind and tinker a bit with it.

After making this change, just log out and back in and voila!
100% working sound!

Hope this helps someone!

---

### Post by Jim_in_Germany on 2008-05-10
Great Howto.
I was having problems playing videos in Firefox and VLC media player at the same time (whichever app was launched first &#314;ocked the sound).
This totally sorted me out.
Thank you.

---

### Post by Vibys on 2008-05-12
Thank you for this, i also had the problem of amarok locking the sound. All working well after this.

---

### Post by dysonsphere23 on 2008-05-12
You fixed it!!!!!
Thank you so much.
Now I can have my hockey play-by-play on vlc and Frank Black on rhythm box at the same time.

Again thanks for the great how-to.

---

### Post by bobloblian on 2008-05-13
Good work, thanks :)

---

### Post by Puptentacle on 2008-05-13
FANTASTIC! Since Pulse came on the scene in Hardy I've been having a massive "clipping" type sound but for some reason this seems to have fixed it. I won't spend any time wondering WHY, but it did. Thanks!!! :guitar:

---

### Post by Silpheed2K on 2008-05-13
I dont see a /etc/asound.conf file

---

### Post by MeURi on 2008-05-14
@ Silpheed2K:

Create it ;)

```

$ sudo vim /etc/asound.conf

```

assuming your favorite editor is vim; change it to nano, gedit, whatever you prefer

@ everyone:

I still have issues with VLC... it can only output in stereo or reversed stereo mode, no 5.1 or whatever

Anyone else?

---

### Post by zman0900 on 2008-05-14
> **MeURi said:**
> I still have issues with VLC... it can only output in stereo or reversed stereo mode, no 5.1 or whatever

Anyone else?


Have you tried installing the vlc-plugin-pulse package?

Also make sure its turned on:
> Description: Pulseaudio audio output plugin for VLC
 This plugin adds support for the Pulseaudio to the VLC
 media player. To activate it, use the `--aout pulse' flag or select the
 `pulse' audio output plugin from the preferences menu.


---

### Post by MeURi on 2008-05-14
Hi zman0900

vlc-plugin-pulse is installed, and VLC is set to use PulseAudio as output, and still no luck

Audio options I can choose are: stereo, reversed stereo, right, left

On a side note, Totem works apparently flawlessly (some days ago it got stuck playing dvds, and saying that audio channels were 0... dunno what was wrong, since i didn't touch anything)

---

### Post by MeURi on 2008-05-14
Ok, I reply to myself...

Some DVDs play fine with VLC (and by defaults it says that output is Dolby Surround, not stereo or whatever else); these do not play under Totem (the awesome 0 audio channels issue, plus playback stuck at 0:00)

Other DVDs play fine in Totem, 5.1 channels, etc; these do not play fine under VLC (stereo, rev stereo, right and left options as output)

I don't know what's wrong, since VLC under Windows plays everything I put into the dvd-recorder... (and yeah, it plays correctly the same DVDs I have problems with under Ubuntu)

:confused:

---

### Post by BOK on 2008-05-18
Worked for me. Thanks! :)
Though I added the /etc/asound.conf stuff into $HOME/.asoundrc and had to add "default-sample-channels=6" to /etc/pulse/daemon.conf to get 2-channel sound through my 5.1 SIS7012-chip (with only 2 speakers connected).

---

### Post by rainwalker on 2008-05-18
Could you add instructions for reversing these changes? I like to know how to change things back before I go tinkering (learned that the hard way)

---

### Post by Bakon Jarser on 2008-05-18
> **zman0900 said:**
> 
[*]Wine does not work properly through alsa, esd, or oss.

Change wine to OSS and use a pulse audio wrapper.

padsp wine "executable program"

---

### Post by zman0900 on 2008-05-18
> **Bakon Jarser said:**
> Change wine to OSS and use a pulse audio wrapper.

padsp wine "executable program"

I've tried that, but it seems very unstable.  The only thing i've been able to get to work is Ultimate Doom for windows, and it only has sound about 1 out of 10 times I try it.  And I did use padsp.

---

### Post by Bakon Jarser on 2008-05-18
> **zman0900 said:**
> I've tried that, but it seems very unstable.  The only thing i've been able to get to work is Ultimate Doom for windows, and it only has sound about 1 out of 10 times I try it.  And I did use padsp.

Hmmmmm....The only windows program I use is pokerstars and it works every time for me.  I guess doom has a little more complex audio setup:confused:

---

### Post by wolfen69 on 2008-05-19
thanks to the OP. works great. i was having to shutdown firefox before i could play music. and vice-versa before i could watch flash with sound. i will refer people to this link. thanks again.

---

### Post by Dritzen on 2008-05-19
This worked like a charm.

Thank you for making this guide.

---

### Post by rainwalker on 2008-05-20
The only problems I have with this setup are:

1) No sound plays at the log-in screen like it used to

2) Audi in VLC hiccups slightly

---

### Post by zman0900 on 2008-05-20
> **rainwalker said:**
> The only problems I have with this setup are:

1) No sound plays at the log-in screen like it used to

2) Audi in VLC hiccups slightly

I've also noticed that with the login screen.  My sound plays when logging in, but not the ready sound when gdm loads.  I believe this is due to the way ubuntu has the pulseaudio executable running.  It runs within the login session, rather than as a system daemon.  I think I read somewhere that running it as a system daemon is a security risk.

As for VLC, I don't use it, so I can't be of much help there. (I run mplayer compiled from source, it plays anything and everything I can throw at it :))

---

### Post by Lalapalooza on 2008-05-20
When I installed: sudo apt-get install libao-pulse libasound2-plugins, I got this error--

dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libao-pulse (0.9.3-1) ...
Setting up libasound2-plugins (1.0.15-1ubuntu3) ...
Errors were encountered while processing:
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do I need to do?

Thanks!

---

### Post by zman0900 on 2008-05-20
> **Lalapalooza said:**
> When I installed: sudo apt-get install libao-pulse libasound2-plugins, I got this error--

dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libao-pulse (0.9.3-1) ...
Setting up libasound2-plugins (1.0.15-1ubuntu3) ...
Errors were encountered while processing:
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do I need to do?

Thanks!


Sounds like possibly a problem with dpkg...  This might be something worth starting a new thread for.  You would probably get more help that way.

---

### Post by FrozenSilence on 2008-05-21
PulseAudio Device Chooser will not run after doing all these steps.  Cursors turns to busy, when hovering over the dock, but eventually returns to normal, without opening the program.

---

### Post by web250 on 2008-05-21
I fixed flash/pulseaudio problems with the updated (1.0.16) libasound2-plugins and libasound2. Also installed the updated libflashsupport and flashplugin-nonfree (10)

---

### Post by dangerjunkie2002 on 2008-05-23
Hi,

Thanks for the guide. I got it working in Gnome on my Dell Precision M6300 notebook. It also cured a ticking sound I had on the audio in SecondLife with ALSA.

This may be a really dumb question but how do I make this work in KDE please? Pulse isn't shown as a choice in the "sound" section in "hardware" in "System settings"

Thanks,
Paul.

---

### Post by quill3033 on 2008-05-24
OK I'm posting this because something odd happened. I have installed Hardy 8.04 on a partition in my c drive and have dapper 6.06 on another partition in that drive. Then I installed Hardy on a usb hard drive and subsequently have not been able to boot if that drive is not switched on - this is not what my question is about I know I can fix this eventually and am waiting to finish busy study period to do it. But here is the thing - I used some of what was in the tutorial above (the libasound installation) and nothing else and then thought I'd give up and just use skype on the dapper partition until I have time to do what the tutorial instructs. I don't remember which hardy partition I did this to(the internal or the usb drive), so... but the thing is that now skype works fine -ie. I can ring out and receive p/c with no sound probs on BOTH partitions! Only thing is that I have to turn off any music program I'm using at the time to be able to answer p/calls. What I found puzzling was why the fix appears to have worked on Skype on both drives or... maybe skype fixed itself quite aside from my attempt at fixing it...

I also installed ubuntu beside xp on my father's computer it will give him the audio playback problem message when he is making an outgoing call but not when he is receiving a call. Why would that be? It's not great for my trying to convince him to migrate over to Linux :-) although he does love Firefox and Thunderbird and easy cd burning and not slowing down his system with anti-virus anti-spy software.
Does Ekiga have the same problem with pulseaudio?

---

### Post by chiefci on 2008-05-26
Hello,
I get a lot of problems since I update my Ubunto 7.10 to Hardy with Sound.
I'm looking for a simple installation of pulseaudio, but here I found it.
Works perfect, but one thing anymore. I have two Soundcards on my box, one SB 16 no problem and a special one creative labs, proteus X with E-MU chip.Hardy don't know this card and I'm not able to use this card.
Is there anybody who know this Soundcard and has a Idee what can I do.
Thanks

Chief

---

### Post by Bionic_Beefpile on 2008-06-03
Well I can definitely use multiple applications with sound output after following this guide, but now whenever I try to play something in Firefox using Flash, the browser crashes.  Does anyone else have this problem or perhaps a fix for it?

I should say that the browser crashes whether or not I'm running any other audio programs.

::EDIT:: This was fixed by upgrading the flash player to the latest version (9.0 r124).  Thanks for the guide!

---

### Post by zman0900 on 2008-06-03
> **Bionic_Beefpile said:**
> Well I can definitely use multiple applications with sound output after following this guide, but now whenever I try to play something in Firefox using Flash, the browser crashes.  Does anyone else have this problem or perhaps a fix for it?

I should say that the browser crashes whether or not I'm running any other audio programs.

::EDIT:: This was fixed by upgrading the flash player to the latest version (9.0 r124).  Thanks for the guide!

I have also experienced this problem occasionally, and I believe it is a fairly well-known problem with firefox 3 and flash.  I am running 9.0.124.0ubuntu2.  I've read that its probably a problem with flash, but it still seems to exist for people who installed the version 10 beta.  I've also read that it might be because of libflashsupport, but I think I experienced the problem before installing it, so I'm really not sure that causes it for me.

---

### Post by Bionic_Beefpile on 2008-06-03
Ahh I see.  I thought it was fixed, but actually I'm still getting random crashes.  Wouldn't surprise me in the least if flash/firefox were still a bit buggy.  Regardless, the steps described in the OP really made my audio setup much much nicer. =D>

---

### Post by markbuntu on 2008-06-03
If you have updated to firefox 3.0 and use any flash you need to get rid of libflashsupport. firefox and flash will crash a lot less often. They will still crash, but far less often than with libflashsupport.

For me it happens now intermittently only on certain sites like hulu where long videos may or may not cause kernel panic. Before firefox3.0 it was virtually impossible to use a site like this.

People are reporting here in the forums that flash 10beta crashes as well so it is probably not a big help yet.

---

### Post by wingnux on 2008-06-03
THANK YOU VERY MUCH!!!

Now I get flash, exaile and sdlmame, all with sound at the same time! =)

---

### Post by beebelo on 2008-06-03
I have an official Ubuntu package named libao2.  What's the difference between libao-pulse and libao2?  Should I have both installed?

---

### Post by rainwalker on 2008-06-03
> **beebelo said:**
> I have an official Ubuntu package named libao2.  What's the difference between libao-pulse and libao2?  Should I have both installed?

I'm not sure what the package is for, but I'm guessing the "libao-pulse" one is specifically if you're using pulseaudio (probably special in some way).

---

### Post by beebelo on 2008-06-03
Ok, thanks Rainwalker.  Well I've got everything in the Howto done, so here goes ...

Well this is looking Very Good!  At this moment I'm playing music and YouTube at the same time (and hearing both)!

---

### Post by wingnux on 2008-06-04
SDLMAME sounds pretty bad now, there are lots of cracks and stuff. Any way to fix it? Thanks in advance!

---

### Post by BerT0 on 2008-06-07
is this also applicable to Ubuntu 7.1?

---

### Post by jukingeo on 2008-06-09
Hello,

I am having problems with sound on certain applications in Ubuntu.  What I have is a Sound Blaster X-Fi that is currently configured to run with OSS.  For the most part certain applications such as Totem Movie Player (which also plays my sound files), Cinelerra, Audacity, and Mupen64+ work with the card.  But other emulators such as Gens, Stella, and GFCE NES do not work with sound.  Also native Linux games such as Neverball do not work either.  I also have another video editor, Open Movie Editor, and that too doesn't work with sound.

I did make my own post about this and someone linked me here.

I tried following the procedure below, but got stopped really fast. <scroll down>

> **zman0900 said:**
> After much tinkering, I have finally found a setup with Pulse Audio on Hardy that I am happy with.  Since a lot of people are having trouble with it, here's what I did:  

[SIZE=6]**Updates:**[/SIZE]
[LIST=1]
[*]Added link to method for 5.1 sound
[*]Patched SDL pulse driver.  See changes in Step 3: libsdl1.2debian-all is no longer needed.
I've submitted a bug to try to get this patch incorporated in the Ubuntu version: [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/225467](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/225467)
[*]Created repository for new pulse drive (supports i386, amd64, and lpia)
More changes to Step 3 now.
[/LIST]

1) **Install additional packages**
```
sudo apt-get install libao-pulse libasound2-plugins
```2) **Configure settings**
    --edit your /etc/asound.conf file like so:
      [code]pcm.pulse {
 

This is where I got stopped.  In my etc folder there isn't a "asound.conf" file to edit.

So what do I do now?

Any input would be much appreciated as I would like sound for my apps.

Thanx,

Geo

---

### Post by zman0900 on 2008-06-09
> **jukingeo said:**
> This is where I got stopped.  In my etc folder there isn't a "asound.conf" file to edit.

So what do I do now?

Just run: 
```
sudo gedit /etc/asound.conf
```
and the file will be created.  No need to worry, the default is to not have one.  If you don't have gedit, try a different editor such as nano.

---

### Post by jukingeo on 2008-06-10
> **zman0900 said:**
> Just run: 
```
sudo gedit /etc/asound.conf
```
and the file will be created.  No need to worry, the default is to not have one.  If you don't have gedit, try a different editor such as nano.

Hello,

As of my last post, despite the fact I got stopped because I didn't ahve the asound.conf file, I did notice that I now have sound on my NES emulator, but still no sound for GENS (Sega Genesis) or Stella (Atari 2600).

But, I need to know what to do to get these emulators also working, or specifically what is happening so I can understand what is going on and why I didn't have sound on the emulators in the first place.

Thanx,
Geo

---

### Post by zman0900 on 2008-06-10
> **jukingeo said:**
> Hello,

As of my last post, despite the fact I got stopped because I didn't ahve the asound.conf file, I did notice that I now have sound on my NES emulator, but still no sound for GENS (Sega Genesis) or Stella (Atari 2600).

But, I need to know what to do to get these emulators also working, or specifically what is happening so I can understand what is going on and why I didn't have sound on the emulators in the first place.

Thanx,
Geo

I'm not familiar with either of those programs, but if they use OSS for sound, will need to run them as:
```
padsp gens
padsp stella
```
in order for pulse to handle their audio.  If not, if they use alsa, they may just be using the wrong sink, and by editing that asound.conf you should be able to fix that since the edit causes the default sink to be pulse.  If you can't get it working, you might try the sites for those programs as well to see if they have any info.

---

### Post by jukingeo on 2008-06-10
> **zman0900 said:**
> I'm not familiar with either of those programs, but if they use OSS for sound, will need to run them as:
```
padsp gens
padsp stella
```
in order for pulse to handle their audio.  If not, if they use alsa, they may just be using the wrong sink, and by editing that asound.conf you should be able to fix that since the edit causes the default sink to be pulse.  If you can't get it working, you might try the sites for those programs as well to see if they have any info.

Ahhhh, I get it now.  That is why the asound.conf file is important.  Because as of last night when I put pulse on my system, the NES emulator began to play sound right away.

Well, at least I know I am on the right track.

Thanx,

Geo

---

### Post by Vivaldi Gloria on 2008-06-10
zman0900,

your guide fixed all my problems. thanks.

---

### Post by cohs on 2008-06-10
i could not get the pulse audio chooser to show up in my sounds & video menu.   any help?

---

### Post by jukingeo on 2008-06-10
> **zman0900 said:**
> I'm not familiar with either of those programs, but if they use OSS for sound, will need to run them as:
```
padsp gens
padsp stella
```
in order for pulse to handle their audio.  If not, if they use alsa, they may just be using the wrong sink, and by editing that asound.conf you should be able to fix that since the edit causes the default sink to be pulse.  If you can't get it working, you might try the sites for those programs as well to see if they have any info.


One more thing on information you posted in the code box.  Where is that supposed to be entered?  Is that to be entered in the terminal?

---

### Post by jukingeo on 2008-06-10
> **zman0900 said:**
> 
Now add the following lines to /etc/apt/sources.list (this will add my repository, it only the packages you need):
```
## zman0900's PPA
deb http://ppa.launchpad.net/zman0900/ubuntu hardy main
deb-src http://ppa.launchpad.net/zman0900/ubuntu hardy main
```
Now run the following:


Ok, I was able to follow your directions up to this point.  However, when I open up the sources.list file, I do not get a place to add the code you posted.  Instead I get a screen that has tabs and selections on it.  Across the top the tabs are: UBUNTU SOFTWARE; THIRD-PARTY SOFTWARE; UPDATES; AUTHENTICATION; STATISTICS.

The page then has a bunch of list boxes that are titled "Downloadable from the Internet".

Do you know what this is?

At any rate going back to the /etc/apt folder I did see another filed that was called sources.list.save and THIS file does have a listing where I can post your code.  However, when I do so, Ubuntu will not let me save it saying I don't have permission.

Any suggestions on how to proceed next?

Edit:

I rebooted my system and checked everything out to see if I got lucky again as I did with NES.

Nope, but one thing I noticed is that now internet streams, such as YouTube are no longer working.   I set everything back in Sound Preferences, and no change.

One thing is for sure...I am going to need my YouTube to work again.

Thanx,

Geo

---

### Post by Vivaldi Gloria on 2008-06-10
> **jukingeo said:**
> Ok, I was able to follow your directions up to this point.  However, when I open up the sources.list file, I do not get a place to add the code you posted.  Instead I get a screen that has tabs and selections on it.  Across the top the tabs are: UBUNTU SOFTWARE; THIRD-PARTY SOFTWARE; UPDATES; AUTHENTICATION; STATISTICS.

Press Alt + F2 and type

```
gksudo gedit /etc/apt/sources.list
```

now add the lines and save.

---

### Post by Vivaldi Gloria on 2008-06-10
> **jukingeo said:**
> Where is that supposed to be entered?  Is that to be entered in the terminal?

Either in the terminal or press Alt+F2 and type them.

You can also edit the menu items in the applications menu and add padsp before the commands.

Or you can make desktop launchers with those commands.

Or you can make panel launchers with those commands.

...

---

### Post by jukingeo on 2008-06-10
> **zman0900 said:**
> 
and add this to ~/.profile :
```
# Make SDL audio work properly with Pulse
#export SDL_AUDIODRIVER=pulse
```



Ok, I am getting there!  Now the question is this:  Where do I find ~/.profile?

And where do these go?

padsp gens
padsp stella

---

### Post by Vivaldi Gloria on 2008-06-10
> **jukingeo said:**
> Where do I find ~/.profile?


In the linux world "~" is a shorthand for

```
/home/what_ever_your_user_name_is
```

So ~/.profile becomes


```
/home/whateveryourusernameis/.profile
```

So open your home folder in nautilus, press Ctrl+H to see hidden files and find .profile there.

---

### Post by jukingeo on 2008-06-11
UPDATE:

Ok, I managed to finally get through the entire procedure and as of now this is what I have in terms of sound:

Native Linux:


Neverball:  Works great!

EgoBoo (NetHack variant): Works Great!

Open Movie Editor: Same, no change, choppy video, no sound.

Internet and YouTube:  Worked great before, but now has choppy video and sound.  Almost like slow motion.  I definitely need this fixed.

Emulators:


GFCE (NES emulator):  Works Great!

Stella (Atari 2600 emulator): Works but plays noticeably faster then on the original Atari, however there are settings within Stella that can adjust for that.

Gens (Sega Genesis emulator):  At first it wasn't working, but I found out I had to UNCHECK the "audio enable" for it to work.  So now I have sound, but it is extremely choppy.  Naturally I would like to fix this.

ZSNES (Super Nintendo):  Still no sound (sound is enabled in program).

I also have DosBox, but I have not tested that as of yet.

Cinelerra still works.  Audacity STOPPED working (again I need this fixed).

So overall MORE things are working now than before, but things that worked before have stopped working now.

Hopefully I can get every thing to work.


Thanx for the help thusfar.

Geo

---

### Post by ludovicc on 2008-06-11
Hello,

I've followed your guide because my sound became all choppy (kind of mobile phone quality) a few days ago (it might be related to some recent updates from Ubuntu repositories). Before that all was working well, including Flash in Firefox. After forcing the use of Pulse everywhere, it improved a little bit, but the sound is still not as clear as before. Do you have any idea for how to solve this issue? 

My card: NVidia
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888

Ubuntu 8.04 64 bits.

Thanks,
Ludovic

---

### Post by jukingeo on 2008-06-11
> **ludovicc said:**
> Hello,

I've followed your guide because my sound became all choppy (kind of mobile phone quality) a few days ago (it might be related to some recent updates from Ubuntu repositories). Before that all was working well, including Flash in Firefox. After forcing the use of Pulse everywhere, it improved a little bit, but the sound is still not as clear as before. Do you have any idea for how to solve this issue? 

My card: NVidia
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888

Ubuntu 8.04 64 bits.

Thanks,
Ludovic

Actually with me my Firefox was working PERFECTLY...but now that I put on Pulse, I can't watch videos on the internet anymore.  So I am hoping that someone can help me fix that.

The good news is that just about everything has sound now.  Both GENS and Dosbox have a choppy sound, but with Dosbox it isn't as bad as with GENS.

With Stella, I had to play with the speed to get it right.  NES is playing fine and now all native Linux games are playing fine.

So I am ALMOST there.

Anyway, if you come by a fix for your problem, please share here as I would like to be able to fix my situation as well.

Thanx,

Geo

---

### Post by psyke83 on 2008-06-11
As far as I can see, this guide will break Flash for many users on Hardy, as libflashsupport is required for Flash v9 to work with PulseAudio, and it isn't installed by default. Unfortunately, even if you do install this package, it will cause Firefox to crash regularly on pages with Flash content.

The good news is that there are backported fixes coming to Hardy soon, but I have created a guide that addresses these problems for those that cannot wait. Please see Part A & B of my guide here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Also, people experiencing skipping with PulseAudio may find a solution from Part C.

---

### Post by rainwalker on 2008-06-11
> **psyke83 said:**
> As far as I can see, this guide will break Flash for many users on Hardy, as libflashsupport is required for Flash v9 to work with PulseAudio, and it isn't installed by default. Unfortunately, even if you do install this package, it will cause Firefox to crash regularly on pages with Flash content.

The good news is that there are backported fixes coming to Hardy soon, but I have created a guide that addresses these problems for those that cannot wait. Please see Part A & B of my guide here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Also, people experiencing skipping with PulseAudio may find a solution from Part C.

When I try to do that, I get this:
> Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 150198 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on libflashsupport (>> 1.9-0ubuntu1) | libasound2-plugins (>= 1.0.16); however:
  Version of libflashsupport on system is 1.9-0ubuntu1.
  Version of libasound2-plugins on system is 1.0.15-1ubuntu3.
dpkg: error processing flashplugin-nonfree (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree


Apparently, libflashsupport IS required. Also, I DO have libasound2-plugins installed...
Help?

---

### Post by psyke83 on 2008-06-12
> **rainwalker said:**
> When I try to do that, I get this:


Apparently, libflashsupport IS required. Also, I DO have libasound2-plugins installed...
Help?

You didn't follow my guide properly. It needs libflashsupport OR libasound2-plugins >= 1.0.16, but you only have 1.0.15 on your system. You didn't follow Part A.

Please reply in my thread for queries relating to that guide.

---

### Post by zman0900 on 2008-06-12
I tried out your guide, and it seems to help with the firefox crashes.  I now have the new libasound2-plugins and flash 10 beta, and I have gotten rid of libflashplugin.  I already had the updated kernel due to a recent update.  So far everything seems to work good.

---

### Post by rainwalker on 2008-06-12
> **psyke83 said:**
> You didn't follow my guide properly. It needs libflashsupport OR libasound2-plugins >= 1.0.16, but you only have 1.0.15 on your system. You didn't follow Part A.

Please reply in my thread for queries relating to that guide.

Ack, sorry, I got mixed up between guides and thought I had already done Part A :-?

---

### Post by blackvd on 2008-06-12
I followed the guide here and in completely jacked my audio. So I reversed it and went back to alsa which works 80% of the time. Problem I have now though is:

1. When I log into gdm it fails the first time and works the 2nd.

2. My audio buttons on my laptop no longer control my media players. And yes I reset them in keyboard shortcuts. Though the media button still opens vlc.

Any help would be greatly appreciated! 

Thanks!

---

### Post by blackvd on 2008-06-12
Got it working by changing mixer device.

excellent!

---

### Post by rainwalker on 2008-06-12
> **blackvd said:**
> I followed the guide here and in completely jacked my audio. So I reversed it and went back to alsa which works 80% of the time. Problem I have now though is:

1. When I log into gdm it fails the first time and works the 2nd.

2. My audio buttons on my laptop no longer control my media players. And yes I reset them in keyboard shortcuts. Though the media button still opens vlc.

Any help would be greatly appreciated! 

Thanks!

I have the login issue too! I don't know what do to

For the media buttons I use KeyTouch

---

### Post by blackvd on 2008-06-13
Well I got the volume ones to work but the previous,next,play/pause,and stop buttons still don't work.

What is KeyTouch and what kind of laptop do you have?

---

### Post by rainwalker on 2008-06-13
> **blackvd said:**
> Well I got the volume ones to work but the previous,next,play/pause,and stop buttons still don't work.

What is KeyTouch and what kind of laptop do you have?

It's a really cool app some guy wrote to tell Linux how to use the multimedia buttons on his comp.
I have a Dell Inspiron 8600, but KeyTouch has tons of different keyboard models to choose from. It didn't have my exact one but I chose another Dell and it works fine.

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

---

### Post by blackvd on 2008-06-13
> **rainwalker said:**
> It's a really cool app some guy wrote to tell Linux how to use the multimedia buttons on his comp.
I have a Dell Inspiron 8600, but KeyTouch has tons of different keyboard models to choose from. It didn't have my exact one but I chose another Dell and it works fine.

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

Doesn't seem to work for me. I'd like to get it back to how i had it which was working. Any clues from the original poster what I messed up?

---

### Post by jukingeo on 2008-06-13
> **psyke83 said:**
> As far as I can see, this guide will break Flash for many users on Hardy, as libflashsupport is required for Flash v9 to work with PulseAudio, and it isn't installed by default. Unfortunately, even if you do install this package, it will cause Firefox to crash regularly on pages with Flash content.

The good news is that there are backported fixes coming to Hardy soon, but I have created a guide that addresses these problems for those that cannot wait. Please see Part A & B of my guide here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Also, people experiencing skipping with PulseAudio may find a solution from Part C.

Hello, I followed your guide here, and while my videos are playing great again, I have no sound.  That is no sound across the board.

I have noticed that sound seems to be a massive problem with Ubuntu, even more so than video.  Many of the video problems I had were solved with maybe 1 to 3 fixes.  My printer was a piece of cake and I had no trouble at all with configuring USB devices.

Sound right now is a major issue.  I must have tried over a dozen fixes and nothing is working right.

Just for the record this is what I have and what I want to do:

My system

Dell Dimension 4600 with 2.8ghz proc, 1.5gig ram, nVidia 5200 series video card with 256meg ram (I think...that is the ram, but I know it is a 5200 series card).  Sound Card is a Sound Blaster X-Fi (currently configured to use OSS as ALSA will NOT work with this card).

This is what I want to do:

1) Basic functions such as internet surfing and emails, document creation.  No problem there as most of these functions work natively with Ubuntu

2) Gaming machine:  My larger "heavy" games I am going to still rely on Windows XP, but I would like to use Ubuntu for older games and play native Linux games with.  I am also into emulations.

This is what I WANT to do:

a) Emulators:

Sega Genesis
Atari 2600
NES
SNES
N64
DosBox

b) Native Linux games (basically anything that comes along that I like)


c) Some Windows emulations...so Wine has to work with sound too.


The next part of the sound package is audio and video editing.

These are the programs I need to work with sound:

Audacity
RoseGarden
Ardour
Cinelerra (this always did work with sound)
Open Movie Editor


I also want my internet to fully work with sound and video play back (which is a given).


As a final note, I been thinking about upgrading Ubuntu to Ubuntu Studio.

Should I do that first since as of now my sound is royally messed up and perhaps I should install that before doing any further tweeking?

Thanx, I would appreciate any help as this is becoming very frustrating.

Geo

---

### Post by blackvd on 2008-06-13
Anyone find a fix for gdm restarting or getting the media keys working again?


Edit: I redid the directions and audio works good now. But I'm still having the gdm and media keys problem.

---

### Post by jukingeo on 2008-06-13
Hello all,

I have since updated Ubuntu to Ubuntu Studio.  I must say, really nice looking interface and many many cool apps.

One of the reasons I upgraded to Ubuntu Studio today was in the hope of correcting my sound problems.  Sadly OSS and sound still isn't working.

However, at this point I pretty much have everything loaded on to Ubuntu that I want to work with.  So I am hoping that I can get my sound fixed.

---

### Post by niceguy123 on 2008-06-15
I followed the instructions in the first post. For some reason sudo gedit would would work half way though. I restarted my computer and the youtube sound worked. I completed the process anyway, but am not sure what I gained.

---

### Post by v4169sgr on 2008-06-15
Please see [http://ubuntuforums.org/showthread.php?t=828338](http://ubuntuforums.org/showthread.php?t=828338)

Followed this guide carefully, making sure to make backups at every stage of all config files edited, and having bookmarked the guide itself.

All flash, sound applications etc work as before, no change, which is a relief, at least nothing broken [apart from the gdm drums].

On loading my sample SDL application, frozen-bubble, without SDL_AUDIODRIVER set on the same line, I have same behaviour as before i.e. massive CPU utilisation, uncloseable application, no sound.

With

```
SDL_AUDIODRIVER=pulse frozen-bubble
```

I have, normal CPU utilisation [i.e. much less than before], an application I can close out of easily, but ... still no sound.

```
This is the output:

        [[ Frozen-Bubble-2.1.0 ]]

  http://www.frozen-bubble.org/

  Copyright (c) 2000-2006 The Frozen-Bubble Team.
 
    Artwork: Alexis Younes
             Amaury Amblard-Ladurantie
    Soundtrack: Matthias Le Bidan
    Design & Programming: Guillaume Cottenceau
    Level Editor: Kim and David Joham

  Originally sponsored by Mandriva <http://www.mandriva.com/>

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License version 2, as
  published by the Free Software Foundation.

[SDL Init] [Graphics............] 
Warning: can't initialize sound (reason: No available audio device).
[Levels] Ready.

```

I have a C-Media CMI8768, and the the default mixer track is set to the device itself.

Thanks very much indeed for the guidance so far, which shows that I am on the right track. How do I get SDL sound from here?

---

### Post by v4169sgr on 2008-06-16
Solved!

I somehow missed this step

```
sudo apt-get install libsdl1.2debian-pulseaudio
```

because I used the update manager straight away after updating the sources list [after backing it up first! ;-)].

Using synaptic to correct that solved my SDL gaming sound issues.

Magic!:popcorn::KS

---

### Post by abhiroopb on 2008-06-17
A few problems:

1. I actually did not have ANY issues with sound, I did not know about the Pulse Audio issue and I did not see why any of this was necessary, the reason I did this is because I posted elsewhere that I was having problems with skype sound. So could someone explain why this would be potentially useful?

2. Skype is still not working (i.e. ringing) when other sound is playing. This is most crucial at this point, the only problem, issue, I am having.

Please help!

---

### Post by abhiroopb on 2008-06-17
Just to add I reverted all of the changes and it is just as before so again I would like to ask what is the point of this fix?

---

### Post by zman0900 on 2008-06-17
> **abhiroopb said:**
> what is the point of this fix?

When Hardy was originally released, there were some problems playing SDL games with the new pulse audio system, and this was a fix for that.  I believe this problem has also been solved by the updated kernels that have been released, but I don't know for sure.  This guide also enables the full pulse audio system, hardy only uses about 1/4 of it.  It enables the device chooser where you can set volume for individual apps and soundcards, move apps from one soundcard to another, or even play things through multiple soundcards.  Also, alsa is configured properly for pulse so that it redirects through pulse.

As for Skype, it is one of those problem apps with Pulse.  I believe skype uses OSS which means you should be able to run it through padsp to get sound from it and pulse at the same time, but Skype's sound system is written very strangely so it does not work properly with Pulse at this time.  I think there may also be an ALSA version of skype availabe, but I heard that it had problems with unsteady, crackling sound.  Perhaps this is fixed by the new kernel, or maybe the new libasound2-plugins (see link to other guide a page or 2 back).  If that doesn't work, you only choice may be one of those guides for completely removing pulse from hardy and returning to pure ALSA.  Good luck.

---

### Post by abhiroopb on 2008-06-17
Thanks a lot for the explanation. As it stands I installed Hardy: watched movies in mplayer/smplayer, used amarok for music, played Enemy territory quake wars, played numerous other games, and basically done virtually everything in ubuntu. Everything worked GREAT, perfect in fact. The only problem was that skype would not work while another device was using the sound. Basically lets say I was watching a movie, and someone called, I would see skype was ringing but I would not be able to hear anything. This is fine I guess, but the MAIN issue was that when I answered the call I still could not hear anything. This means I basically have to reject the call, pause the other app thats using sound and call that person back.

Whwere are the guides for removing pulse?

Thanks

---

### Post by zman0900 on 2008-06-17
> **abhiroopb said:**
> Whwere are the guides for removing pulse?

I don't have a link, but I think I've come across one or two in the forums.  Search some, or try google, its in the tubes somewhere.

---

### Post by eng12345 on 2008-06-19
only ****** it up even worse. how do i undo this?

---

### Post by wingnux on 2008-06-21
Anyone also having crappy sound on sdlmame?

---

### Post by blackvd on 2008-06-23
I'm still curious as to why my media keys quit working no matter what i try to do to fix them? Seems odd that anything i did would have affected them.

---

### Post by JoshLukas on 2008-06-23
I don't know where to post this exactly, since there are some other threads to pulse audio, SPDIF etc. But, this seems to be the most active thread concerning with pulseaudio.
Unfortunately, following the howto posted in this thread didn't work for me. I got no Audio at all. Since, I can't even activate spdif with alsa, I decided to let pulseaudio do the stuff. With the A52 codec now everything is going out via spdif (coax) as Dolby Digital. The description what I've done is posted on [my site]("http://aryuna.de/spdif_mit_ubuntu_hardy_und_audiophile_2496"). However, there is still a problem which is a bit annoying. The sound is somehow pitched down, so everything sounds weird and slow. And from time to time the sound is shuttering heavily. Mostly while synaptic is working, if unzipping large files, or copying a larger amount of files. Sometimes sound stops working and only a reboot helps to get sound again. Is there a solution to get sound working properly with ALSA, or Pulseaudio via SPDIF? Can somebody give me some help or advice?
My hardware is described on my site as well.

Thx,

Josh

---

### Post by JoshLukas on 2008-07-02
dingdong

---

### Post by PCasau on 2008-07-02
Hi! I'm just new to ubuntu and I also have some sound problems. I'd like very much to go through this How-To but I just can't find asound.conf. What does that mean?

---

### Post by supta on 2008-07-02
It works for me. i got no sound problem with rhythmbox and flash anymore.

BTW, i don't install libsdl1.2debian-pulseaudio from your repo. i install it from ubuntu repo and didn't get any problem after finishing this installation.

---

### Post by quall on 2008-07-03
I LOVE YOU, I love you , ILOVEYOU ILOVEYOU 
I - L- O - V -E - Y - O - U

Jesus, I am so freaking happy. I have spent days upon days trying to fix my audio issues. 

This fixed the embedded audio buttons on my Vostro 1500. They now alter the audio of the selected device, which is my USB surround system.

Not only that, but the PulseAudio applet flat out rocks. Frozen-bubble, which I could NEVER get audio working properly on the USB device, can now be forced to a specific audio device through that app. Rhythmbox was using my laptop speakers too, even with the USB sound completely defaulted everywhere. After this fix, it goes to the USB device. I cannot express my gratitude, I can finally listen to my music and watch movies in decent sound.....

PCasau, I had no asound.conf either. I simply created it (he says to do this at the end of the post).

---

### Post by rockstar on 2008-07-04
So I followed this How to.  Then I read all 13 paged to make sure I wasn't being redundant. When I went to System>Preferences>Sound and hit test.  Then I get the failed to connect dialogue.  I double checked all the steps. So when it still didn't work I tried the Ubuntuwiki 
[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")

I then:
> Now, go into Applications -> Sound and Video -> click on PulseAudio Preferences.

    *

      Checkmark all three options under Network Access. This will allow other computers on your LAN with PulseAudio to access this computer's sound devices.
    *

      Checkmark Enable Multicast/RTP Receiver. This allows receiving multicast streams from other systems on your LAN.
    *

      Checkmark Enable Multicast/RTP Sender. This allows sending multicast streams (One source sends packets, all others may receive them simultaneously)

Leave the other options alone for now, unless you want to loop outgoing streams through the local speakers.

Next go into System -> Preferences -> Sound and make sure that Enable Software Sound Mixing is checked. Also, under the Sounds Tab, I set devices to Autodetect. 

Now when I hit "test" the entire system crashes and shuts down! I don't know what I did.

---

### Post by quall on 2008-07-04
If you hit test on the specific audio device instead of PulseAudio, in System -> Preferences -> Sound, does any sound play? If not then it might be a problem with the device installation and not PA.

---

### Post by pokipoki08 on 2008-07-07
The guide work perfect but under Sound Preferences, you must check "Enable Software Sound Mixing (ESD)", otherwise the connection will be refused. I also get buzzing on the left channel but it was solved after following Parts A, C and D of the guide below

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by jmate24 on 2008-07-09
Thanx!!!!!!!!!!!!:lolflag:

---

### Post by Roasted on 2008-07-10
Is there a big advantage to pulse audio over alsa?

I have scratchy audio at high volume using vlc, amarok, and sometimes youtube. Other programs, such as audacious, or even vlc (but only when I play movies) play perfectly in perfect clarity at high volume.

I'm wondering if switching to pulse would be a wise move and may help with this issue?

---

### Post by quall on 2008-07-12
Well, I think it is better. I like the fact that multiple applications can play sound through the same sound device at the same time. I can adjust the volume on the application level (where no controls exist), and I can specify which device each application should use.

I did not have any of the issues you speak of though, but it can't hurt to try it, I mean, you select it as the default device in the sound settings. If you don't like PA, then you can just select alsa again. Just make sure that you get the PulseAudio applet if you install pulse.

---

### Post by markbuntu on 2008-07-13
Well, pulse does not play nice with oss or jack but then again, jack has its own issues.

---

### Post by furyy on 2008-07-14
It's bit weird that padevchooser doesn't come installed by default by now :confused:
Atleast in intrepid pa is using pc speaker as default sink :confused: and you could set new default sink / move streams with padevchooser.

---

### Post by blaise69 on 2008-07-14
I'm having trouble recording from my main Line-in when using Pulse Audio.

Following this guide has enabled me to have sound through multiple applications without any problems, so I'm happy with that.

However the only capture devices seem to be my mic from the front of my machine, I also have a mic and Line-in on the back of my machine, I intend to use the Line-in to record my guitar from.

How can I get this identified and working?

Cheers,

Blaise.

---

### Post by MillDaKill on 2008-07-15
Thanks for the guide,  I just made the changes today and I will report back with my status.  Hopefully this fixes my crashing "pulseaudio -d" problem which happens about every 15 mins..

---

### Post by AmbroseBierce on 2008-07-22
Hey,
I tried thsi method out and it only partly works. Sound works but my internal mic ins`t working anymore. But some how it also works when i use the skype-static-oss version. If i try to record via the ubuntu recording tool it says(free translated from German^^) "Problem with Dataflow" and also "no subclass defined" or something like that. Does anybody else have this problem? How to solve it?

---

### Post by Striken on 2008-07-27
Followed the guide, and lost all sound I had.
 
Thanks anyway.

---

### Post by emshains on 2008-07-27
I dont have the .conf files in /etc/

---

### Post by d4v1dv00 on 2008-07-27
Sweet, now my sound is back with please. TQ

---

### Post by POW R TOC H on 2008-07-31
This worked like a charm... Thank you!

---

### Post by kofshower on 2008-08-01
How I can do this step if I use KUbuntu?
---------------------------------------------------------------------------
--Set the Default mixer to the name of your sound card

---

### Post by ZootNerper on 2008-08-09
Thanks. It seems to have improved things.

-- Zoot

---

### Post by omshanti on 2008-08-18
Success! Thank you; this has been frustrating me for a while.

---

### Post by ivodalves on 2008-08-21
Hi,

My laptop is working ok with pulse now, except one thing.

It may look stupid but I only have sound in my hearphones. I don't have sound in the laptop speakers.

Can anyone help?

Best regards,

Ivo

---

### Post by art.in.memphis on 2008-08-21
I followed this to the letter but still no sound.  I had to change settings from DEFAULT to my preferred sound card in the PulseAudio Applett to get this to work. My card is a CA0106 Soundblaster.  I have that card set as the default card in the *.conf files but I still had to make the manual selection in PulseAudio Applet

I hope this helps someone.

---

### Post by oni5115 on 2008-08-21
Not working for me at the moment, but I am also using UbuntuLite / LXDE.  So I can't exactly:

> Create any files that don't exist.

--Go to System>Preferences>Sound
--Set the top four boxed to PulseAudio Sound Server
--Set the Default mixer to the name of your sound card

Will installing the 'sound preferences' application bring a ton and a half of gnome dependencies with it?  what application is it in the repos?

Basically, everything looks like its working - the pulse volume meters are showing sound, padevchooser is working properly, and everything, but I just hear no sound from anything.

---

### Post by CNLiberal on 2008-08-23
I am using an nForce2 motherboard with the SPDIF output.  I can open up the Volume Meter in PUlse and can see sounds playing, but I'm getting nothing over my speakers.  I know the receiver is setup correctly (as it works in Windows).  What do I have to do to get SPDIF working?  I have followed your guide on the first page.  Thanks for the assistance!

Jim

---

### Post by alejaaandro on 2008-08-25
thnx man, int worked great....

---

### Post by markbuntu on 2008-08-25
> **CNLiberal said:**
> I am using an nForce2 motherboard with the SPDIF output.  I can open up the Volume Meter in PUlse and can see sounds playing, but I'm getting nothing over my speakers.  I know the receiver is setup correctly (as it works in Windows).  What do I have to do to get SPDIF working?  I have followed your guide on the first page.  Thanks for the assistance!

Jim

You can get the SPDIF to work in your alsa mixer, whichever one you use. Unfortunately for us, the pulseaudio devs have not figured out yet how to parse devices other than device 0 from ALSA and SPDIF/IEC958 digital devices are usually device 1 or 2 on sound cards so it must be done in ALSA. There is more info about getting digital output to work in some links from here:


[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by CNLiberal on 2008-08-26
If that's the case, and Pulse can't handle SPDIF, then I'm not a happy boy.  Can I edit the asound.conf and tell it to dump all audio out of the SPDIF while still using Pulse?

---

### Post by markbuntu on 2008-08-26
You don't need to edit your asound.conf. All you should have to do is enable the SPDIF output in any alsa mixer and it should work. You may have to set the preferences of your apps to ac3 bypass. There is a digital link from this page that will help you get set up:

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

According to the pulse devs, it is difficult for them to determine which devices are actually independent/usable. They claim it is a ALSA  problem and that ALSA does not export device info so they have no way to tell if a device is usable.

Do not expect any quick solution to this problem.

---

### Post by carl0sgm on 2008-09-07
Hi..

I don't understand this:

[COLOR="Lime"]and add this to ~/.profile :
Code:

# Make SDL audio work properly with Pulse
#export SDL_AUDIODRIVER=pulse[/COLOR]

what does this mean?

I hope somebody can help me!

---

### Post by kevx on 2008-09-19
Thanks for that.:)

---

### Post by markbuntu on 2008-09-19
> **CNLiberal said:**
> If that's the case, and Pulse can't handle SPDIF, then I'm not a happy boy.  Can I edit the asound.conf and tell it to dump all audio out of the SPDIF while still using Pulse?

There is a workaround here to get PulseAudio to recognize your digital output, it may work for you but there are some issues:

[http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

---

### Post by bigjig on 2008-09-19
yo buddy, just installed Ubuntu 3 days ago, been using OpenSUSE so long! 

Ubuntu is so comfortable... thanks for the fix though mate! worked perfectly fine.

cheers.

---

### Post by shane2peru on 2008-09-19
This sooooooo did not work for me.  I'm going back through and reversing the steps to see if I can get my sound back.  At least I had sound before. :)  

Shane

---

### Post by bigjig on 2008-09-20
> **shane2peru said:**
> This sooooooo did not work for me.  I'm going back through and reversing the steps to see if I can get my sound back.  At least I had sound before. :)  

Shane

Sorry to hear that mate. I am hoping u followed it exactly as it says on the steps.

One thing i've noticed.....

> add this to ~/.profile :

Code:
# Make SDL audio work properly with Pulse
#export SDL_AUDIODRIVER=pulse 

I personally think the # in line 2 is a typo so when I updated my .profile I removed the #. You can try that.

I've resolved that but I have now noticed that the sound recorder wont record anything from the microphone input! I never tried to do that before installing the pulse drivers so cant say if its messed the microfone input.

I dont know how to fix that but I am still looking for a fix on that.

---

### Post by shane2peru on 2008-09-20
I did follow the instructions to a tee, the only difference I did was to backup one of the files before editing it. :)  At any rate, turns out my problem was more of a problem with Audacity than with my sound setup.  I compiled Audacity for my machine and am back at work with it.

Shane

---

### Post by dkavraal on 2008-10-12
it did work for me. thank you.

Linux abc-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
(ubuntu 8.04 hardy heron)

---

### Post by directcharitycontribution on 2008-10-22
> **zman0900 said:**
> After much tinkering, I have finally found a setup with Pulse Audio on Hardy that I am happy with.  Since a lot of people are having trouble with it, here's what I did:   ....
Post something if you know of more.

did you say 

and backup they files first?

and can toglle you sounds?

> **durand said:**
> 
Posted by zman0900  "It wouldn't surprise me if it is a bug in Pulse, it is a nice audio system, but it is far from being ready for main stream use. Putting it in a LTS distribution like this was probably not a great idea, but at least it will get some of the bugs out in the open. Though I really think there should be an easy option to remove it for those who don't feel/can't work around the bugs."

Here's how you can remove pulseaudio:

From the ubuntu wiki:
Quote:"PulseAudio Removal

If you decide you no longer like PulseAudio and would like to disable it: Remove the added lines to /etc/asound.conf If /etc/asound.conf did not exist when you installed PulseAudio, you may remove /etc/asound.conf entirely.

After this, you may remove all of the installed PulseAudio packages.

To disable pulseaudio in hardy you need to select alsa for for all options in /system/preferences/sound

I myself am not sure if surround sound is working or not. I only need it for games but I'm not sure how to test it. It feels like surround sound but...


---

### Post by svaens on 2008-11-11
well.. i've also got the problem (i assume everyone has) 
that the startup sound (when the login screen appears) no longer occurs. 

So it is because pulse is not yet running? 

I quite liked that drum sound..... and now i can have no start-up sound? 
Security risk? 

Is this going to be resolved?

---

### Post by Crowder on 2008-12-16
this fix seemed at first to help, but ended up causing many of my applications to crash. here is some of the output from Pidgin, which crashed every time it needed to play a login, logoff, or IM sound -

```
[SIZE="3"]HTTP/1.1 200 OK
Date: Tue, 16 Dec 2008 06:29:35 GMT
Server: Apache/1.3.41.fb1
Content-Length: 105
Expires: Mon, 26 Jul 1997 05:00:00 GMT
Cache-Control: private, no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Connection: close
Content-Type: application/x-javascript; charset=utf-8

(01:29:35) blist: Updating buddy status for <my buddy's screen name went here> (AIM)
E: context.c: [COLOR="Red"]waitpid(): No child processes[/COLOR]
*** PULSEAUDIO: Unable to connect: Internal error
(01:29:35) util: Writing file blist.xml to directory /home/crowder/.purple
(01:29:35) util: Writing file /home/crowder/.purple/blist.xml
Segmentation fault[/SIZE]

```

so far the only real solution i have found for pulseaudio (at least on my machine) is to remove it completely. that seems to be the only way of keeping it from trying to handle everything. Granted, this means only one process can use the audio drivers at a time, but i think i can live with that at least for a while.

i ended up having to go through and undo all the changes this called for.

But thanks anyway! looks like a lot of thought went into this, and it worked for some of us!

---

### Post by Kelen.Chang on 2009-04-25
nice solution and worked for me perfect.

---

### Post by TMcKSmith on 2009-04-27
Thanks OP...worked perfectly!  This has been bugging me for months.

---

### Post by Ian Clark on 2009-04-28
OK First of all, I'm on Intrepid (which has supposedly fixed the Audacity/pulse conflict), AND I can't get sound from different sources at the same time (particularly after using FF).  Is this solution appropriate for me?

Second, I look at this guide, get to this step, and wonder what part of the /etc/asound.conf file this should be added to:
> **zman0900 said:**
> 
    --edit your /etc/asound.conf file like so:
      ```
pcm.pulse {
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

```    --edit your /etc/libao.conf like so:
      ```
default_driver=pulse
```
The file has three or four sections, and I don't think I should just replace the whole file with the above.  Same with the second one.  Where should I put these two pieces of code?  Any help would be appreciated!  Thanks for the guide!

---

### Post by bjourne on 2009-05-04
Didn't work for me either. Went from almost working sound setup (except flash) to no sound at all. Dell XPS laptop.

---

### Post by agentsmith23 on 2009-06-27
I am running Jaunty 9.04 and I can't seem to find /etc/asound.conf. Was it removed?

---

### Post by suebaby41 on 2009-06-27
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse) E: The list of sources could not be read.  The above is what I get when I try to follow any directions to get sound for CD's or media players.  Help!  Cannot hear CD's or Banshee or other installed players.  Never mind.  I found the answers.  Thanks.

---

### Post by Quarterpipesmoker on 2009-07-03
> **zman0900 said:**
> ```
# Make SDL audio work properly with Pulse
#export SDL_AUDIODRIVER=pulse
```

Why is the 2. line also commented out? Shouldn't it be uncommented?

---

### Post by mocha on 2009-07-06
> **Quarterpipesmoker said:**
> Why is the 2. line also commented out? Shouldn't it be uncommented?

Yeah, he made a typo.  FWIW, under Jaunty I've found that I need to use SDL_AUDIODRIVER="esd" instead.  There is some strange bug with some SDL programs and pulseaudio 0.9.14+ that cause intermittent high CPU usage unless you do this.

---

### Post by wayward4now on 2009-07-28
> **durand said:**
> Thanks for the 5.1 trick!

It's ALMOST perfect. Sound playback in warzone2100 is choppy. Everything else seems fine, so far. Thanks for the effort. I'm running Karmic + KDE. Ric

---

### Post by Epaminond on 2009-11-02
I'm running Xubuntu 9.10. The problem was in listening to the music from FF and talking over Skype.
The guide from the first post helped me! Thanks!!!

---

### Post by cathyn on 2010-01-26
This isn't working for me.  When I open Pulse Audio Manager, it looks like the Default Source and Default Sink are both still set to alsa devices, which I imagine should be changed, but to what I am unsure.  Any suggestions?

---

### Post by cathyn on 2010-01-26
Wave off.  Deleting /etc/asound.conf fixed everything, though I don't know why.

---

