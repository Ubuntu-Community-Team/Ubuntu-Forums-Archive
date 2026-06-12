---
title: "Howto: Happy ALSA, OSS, ESD, with Duplex - Sound Settings"
date: 2005-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by intangible on 2005-06-27
I know it's been done before, but I don't think anybody has compiled all the settings into a single happy set of instructions.

This setup should work with most sound systems, it is from my Nforce2 setup at home, it makes everything work quite nicely together, OSS, ESD, ALSA and make your Mic work while sound is playing (great for UT2004!!).

These instructions assume you know how to edit config files on your system and add/remove packages on your own.

[list=1]
[*] Goto **System->Preferences->Sound** and disable "Enable Sound Server Startup"

[*] Install **libesd-alsa0** which will remove libesd0, but that's ok.

[*] Make **/etc/esound/esd.conf** look like this:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

[*] Make **/etc/asound.conf** look like this:
```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
```If you look, the first setting will let you select a different sound card as your primary if you have multiple sound cards.

[*] Make **/etc/libao.conf** look like this:
```
default_driver=alsa
```

[*] Reboot to make sure all the systems startup correctly.
[/list]
OSS stuff will still tie up the sound card, but they don't run all the time.  Just configure most things to use ALSA and you'll be good.

Side-Effect: The Ubuntu startup sounds will go away, but i think the trade-off is worth it.

**Note**: If stuff plays a little static through ESD, in **/etc/esound/esd.conf** try changing
*spawn_options=-terminate -nobeeps -as 2 -d default*
to
*spawn_options=-terminate -nobeeps -as 2 -d duplex*

---

### Post by i3dmaster on 2005-06-27
[QUOTE=intangible]
[*] Install **libesd0-alsa** which will remove libesd0, but that's ok.
[/QUOTE]
I did not find this pkg but I got a libesd-alsa0. So I installed that one. Wonder if this is just a typo...

---

### Post by intangible on 2005-06-27
It was a typo, fixed.

---

### Post by i3dmaster on 2005-06-27
[QUOTE=intangible]It was a typo, fixed.[/QUOTE]

I tried it, but looks like it gave me a disaster. My screen resolution keeps on 640x480 after reboot and I cannot get it back to what it was before... its totally broken. I've noticed that when I install the libesd-alsa0 pkg, it told me that a bunch of pkgs need libesd0 but it still went ahead removed libesd0 and installed libesd-alsa0.... Even I replaced back the libesd0, the screen never came back... xorg.conf seems not changed, but gnome-display-properties can only see 640x408@60Hz... I need help

---

### Post by RastaMahata on 2005-06-27
what should I select in system > preferences > multimedia ??

Input: alsa ?
Output: OSS ?

---

### Post by intangible on 2005-06-27
Alsa for both

---

### Post by intangible on 2005-06-27
libesd-alsa0 should've taken over all the dependencies that wanted libesd0

It sounds like somehow something else got uninstalled, it's worked flawlessly on the three Ubuntu computers I've tried, I'm sorry you had problems.  I just went through the install procedure again on another installation to make sure I didn't feed you bad info.

If you removed the old libesd0 first without letting apt-get or synaptic handle removing that automatically when you told it to install libesd-alsa0, that might have caused a problem.
Try seeing if **ubuntu-desktop** is still installed, if not, add it back.

---

### Post by i3dmaster on 2005-06-27
[QUOTE=intangible]libesd-alsa0 should've taken over all the dependencies that wanted libesd0

It sounds like somehow something else got uninstalled, it's worked flawlessly on the three Ubuntu computers I've tried, I'm sorry you had problems.  I just went through the install procedure again on another installation to make sure I didn't feed you bad info.

If you removed the old libesd0 first without letting apt-get or synaptic handle removing that automatically when you told it to install libesd-alsa0, that might have caused a problem.
Try seeing if **ubuntu-desktop** is still installed, if not, add it back.[/QUOTE]

I did not manually remove anything, I was just installing the libesd-alsa0 and it said a bunch of things like such such pkg is depending on libesd0... (I remember, gdk, gedit, and some other gnome apps) however, libesd-alsa0 will be installed... and apt did go ahead to remove libesd and install the libesd-alsa0 even that. Since apt did not get any panic on this action, I was thinking everything should be fine but...

---

### Post by intangible on 2005-06-27
That sounds like the normal procedure, are you sure you haven't upgraded anything else recently, maybe a kernel update or video card drivers?

---

### Post by i3dmaster on 2005-06-27
[QUOTE=intangible]That sounds like the normal procedure, are you sure you haven't upgraded anything else recently, maybe a kernel update or video card drivers?[/QUOTE]

Yes, I upgraded kernel to 2.6.10--34.3.

---

### Post by i3dmaster on 2005-06-27
[QUOTE=i3dmaster]Yes, I upgraded kernel to 2.6.10--34.3.[/QUOTE]

Ok, confirmed its the kernel since you just rang me a bell and I switched to another kernel and my screen went back. Sorry I was thinking it might because of the libesd stuff.

---

### Post by intangible on 2005-06-27
Glad you found the problem :)

Even happier I didn't cause you to break anything :D

---

### Post by NeoChaosX on 2005-06-27
Oh, since you have OSS through ALSA enabled, add this to the instructions to get sound in Firefox:

Edit **/etc/mozilla-firefox/mozilla-firefoxrc** change FIREFOX_DSP to "AOSS"

I've also noticed that if you're using RealPlayer, there's crackling in sounds unless you set buffer_size to 8192.

---

### Post by i3dmaster on 2005-06-28
[QUOTE=NeoChaosX]Oh, since you have OSS through ALSA enabled, add this to the instructions to get sound in Firefox:

Edit **/etc/mozilla-firefox/mozilla-firefoxrc** change FIREFOX_DSP to "AOSS"

I've also noticed that if you're using RealPlayer, there's crackling in sounds unless you set buffer_size to 8192.[/QUOTE]

Good tips, thanks!

---

### Post by intangible on 2005-06-28
Thanks for the addition.  Depending on your system, you may do better with a larger buffer size.  4096 seemed to work pretty well for me, but I've heard some people needing to go higher (one person even said 32768 for them!!!)

---

### Post by rutty on 2005-06-28
This was helpful, but I'm still having a few problems. I've spent ages trying to configure my Hoary installation to work with Cedega (WoW) and teamspeak at the same time and have tried all sorts of tricks to get it working (using the "echo" workaround etc) and I just made everything worse.

Eventually returning to this thread meant that I got my sound back in WoW! However, it skips a bit now when it never did before (perhaps because I've set it to use DMIX via a thread in Transgaming perhaps?) and I can't get any sound at all in teamspeak. If I start teamspeak then I still get no sound in WoW.

I have on-board sound (I know!) via my nForce 2 K7N2 Delta mobo. Would it just be much easier to buy a cheapo soundblaster soundcard? Is hardware mixing easier to configure?

Despite looking through no end of threads on here and elsewhere I just can't seem to find a one-stop solution for on-board sound in Hoary. I'll keep looking though ;)

PS, bit of a noob at this Linux lark

---

### Post by intangible on 2005-06-28
Unfortunately with the onboard sound support for Nforce2 never being fully supported by nvidia under Linux, you may encounter problems like that.  Try not using dmix under cedega and see if that helps.

---

### Post by rutty on 2005-06-28
[QUOTE=intangible]Unfortunately with the onboard sound support for Nforce2 never being fully supported by nvidia under Linux, you may encounter problems like that.  Try not using dmix under cedega and see if that helps.[/QUOTE]

Thanks, I'll give it a go.

I do have a habit of breaking more than I fix, but it's fun trying to fix these little issues ;)

---

### Post by NeoChaosX on 2005-06-28
[quote=intangible]OSS stuff will still tie up the sound card, but they don't run all the time. Just configure most things to use ALSA and you'll be good.[/quote]I've got a fix so OSS programs can run alongside other programs.

In **/etc/asounf.conf**,  change **type asym** in the pcm.duplex section to **type plug**

---

### Post by NeoChaosX on 2005-06-28
With this config, sound in Gaim doesn't work if there are other programs using the sound card. I've tried changing it to different options in /etc/libao.conf, but Gaim still won't produce sound unless all other programs are closed.

EDIT: Now sound in Gaim doesn't work, period.

---

### Post by RastaMahata on 2005-06-28
[QUOTE=intangible]Alsa for both[/QUOTE]
 well, if I select alsa for input, I cant use sound recorder...
If I select OSS, I can record sounds easily :)

---

### Post by Gnobody on 2005-06-30
How do I revert this? My sound sounds scratchier now with this "tweak" no matter what I do and UT2004 worked fine before this with VoIP support.  I have a SBLive! 5.1 btw

---

### Post by intangible on 2005-07-01
Remove **/etc/asound.conf**  There is none installed with Ubuntu.

Doesn't a SBLive do hardware mixing anyway?  This is mainly for people with ac97 sound that doesn't do hardware mixing.

---

### Post by zerohalo on 2005-07-02
[QUOTE=NeoChaosX]With this config, sound in Gaim doesn't work if there are other programs using the sound card. I've tried changing it to different options in /etc/libao.conf, but Gaim still won't produce sound unless all other programs are closed.

EDIT: Now sound in Gaim doesn't work, period.[/QUOTE]

In my experience, Gaim only works with ESD not ALSA. The only way I've been able to get Gaim to play sounds at the same time as I'm playing multimedia is to use ESD across the board rather than ALSA. I currently have Rhythmbox, Totem, BMP, VMware (sounds in WinXP running as a VM), Ubuntu system sounds, and Gaim all working together. The only problem is mPlayer, which I prefer to watch videos with than Totem. To use mPlayer I have to kill the esd daemon. I don't know why mPlayer doesn't work with ESD, but maybe someone knows?

---

### Post by varunus on 2005-07-02
[QUOTE=zerohalo]In my experience, Gaim only works with ESD not ALSA. The only way I've been able to get Gaim to play sounds at the same time as I'm playing multimedia is to use ESD across the board rather than ALSA. I currently have Rhythmbox, Totem, BMP, VMware (sounds in WinXP running as a VM), Ubuntu system sounds, and Gaim all working together. The only problem is mPlayer, which I prefer to watch videos with than Totem. To use mPlayer I have to kill the esd daemon. I don't know why mPlayer doesn't work with ESD, but maybe someone knows?[/QUOTE]

Gaim can be configured to work with ALSA; you just need to select "command" as the sound output method, and type "aplay %s".

In my opinion, you should get the libesd-alsa0 package anyway, so esd will use alsa, and then follow this howto to get esd and alsa playing together.  Then, mplayer will work.  Its time linux stopped using OSS completely.  Thankfully, the next version of ALSA (1.09) will have dmix enabled by default, so no configuration will be necessary.


Also, to the OP, if some people find that /etc/asound.conf doesn't work, try making the config file ~/.asoundrc (notice the . in front of the file name).  That works too.  (Hehe, I know since I wrote the original howto for warty on how to do this... ;-) )

---

### Post by NeoChaosX on 2005-07-02
[QUOTE=varunus]Gaim can be configured to work with ALSA; you just need to select "command" as the sound output method, and type "aplay %s".[/QUOTE]

Odd, I tried this and I'm getting silence. Anything I should set?

---

### Post by thoffland on 2005-07-02
I've tried to set this up about 4 times and I still only can get one thing to play at a time... and I have no system sounds. The only driver that works with XMMS is OSS. I've downloaded all the codecs for wma, wav etc, but I still have to stop XMMS and wait a few seconds before playing a video for either Xine or 

I have a sound card built into my mobo Intel 8280... but I'm actually using my USB 5.1 Speakers.

---

### Post by zerohalo on 2005-07-02
[QUOTE=varunus]Gaim can be configured to work with ALSA; you just need to select "command" as the sound output method, and type "aplay %s".

In my opinion, you should get the libesd-alsa0 package anyway, so esd will use alsa, and then follow this howto to get esd and alsa playing together.  Then, mplayer will work.  
[/QUOTE]

Thank you, varunus. I ran the how-to and now everything works, including Gaim, and MPlayer. (I actually already had the libesd-alsa0 package installed already, but no asound.conf, which is probably why I could never get ALSA working properly before. 

However, I found that the command "aplay %s" did NOT work. Rather, I selected Gaim to work with ESD. But since ESD is now using ALSA, it worked. I'm a happy camper!

---

### Post by NeoChaosX on 2005-07-03
Flipside to keeping ESD - it knocks Flash sound out of sync if it's running. If you're a big fan of Flash-based stuff (Homestar Runner, for example), keep this in mind.

---

### Post by zerohalo on 2005-07-03
[QUOTE=NeoChaosX]Flipside to keeping ESD - it knocks Flash sound out of sync if it's running. If you're a big fan of Flash-based stuff (Homestar Runner, for example), keep this in mind.[/QUOTE]

This is the sort of thing that is a downside of Linux: The lack of established standards for fundamental functions, like sound mixing, that affect a host of client applications. It's one thing to have 10 different Word processing programs which cater to a variety of tastes and personal opinions, because not that much depends on those word processers. It's another thing to have a variety of core functions upon which applications depend, because you have a mess of some applications depending on one and some on another. I know this probably runs contrary to certain open-source thinking, but at some point, someone, or a group of someones, needs to make an arbitrary decision that "this is the standard for core function x in Linux and anyone writing programs that use core function x need to do it this way" or else go start your own OS. Okay, sorry, this got to be off topic and I don't intend to start a discussion on the matter as I know these things are complex. It would just be nice to solve some of them :-).

---

### Post by filemanager on 2005-07-03
I did this and now my Linux OS won't boot 8(

---

### Post by varunus on 2005-07-03
Won't boot?  That's strange...what error messages do you get?  Can you post them here?

If you want to undo the changes, you can boot up in recovery mode from GRUB and enter the following:

rm /etc/asound.conf
rm /etc/alsa/asound.conf
rm /home/yourusername/.asoundrc
apt-get install libesd0

That should return your computer to its original state.  However, I doubt that this howto stopped you from booting...Can you post your errors before you try an uninstall?

---

### Post by filemanager on 2005-07-03
[QUOTE=varunus]Won't boot?  That's strange...what error messages do you get?  Can you post them here?

If you want to undo the changes, you can boot up in recovery mode from GRUB and enter the following:

rm /etc/asound.conf
rm /etc/alsa/asound.conf
rm /home/yourusername/.asoundrc
apt-get install libesd0

That should return your computer to its original state.  However, I doubt that this howto stopped you from booting...Can you post your errors before you try an uninstall?[/QUOTE]


Well, I did everything the thread said to, and then I rebooted, but when it got to the "Starting hotplug subsystem" part it froze. So I booted into WinXP and looked around the forums, and someone said to hit Ctrl+C which would skip the step. So I tried that and it did indeed skip the step, but when Linux loaded my mouse froze, and apparently so did the entire computer. So I rebooted again, but this time it booted into Linux fine without freezing, so I went through the steps above again, but backwards (to undo them). I couldn't figure out how to remove files which were "read only" but that rm command did the trick!

---

### Post by Lapeth on 2005-07-03
Well, for me the described procedure worked great at first shot. Thank you very much for posting this; it saved me a very large headache. I've previously tried to get ALSA working on Redhat 9 to no avail, but on Ubuntu with your guide - piece of cake. :)  :)  :)

---

### Post by Ulokye on 2005-07-04
Just a short reply to my friend here that had problems with sound under cedega.


find this in your .point2play/configuration_profiles/cedega4.3.x
(if you don't run point2play replace it with .cedega)

```
 [WinMM]
"Drivers" = "wineoss.drv"
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

```

change it to.

```

 [WinMM]
"Drivers" = "winealsa.drv"
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

```

---

### Post by filemanager on 2005-07-05
What's the difference between ESD and Alsa?

Also, should the onboard ac'97 sound be enabled, or disabled?

---

### Post by intangible on 2005-07-05
You should only disable the AC97 onboard sound if you have an add-in sound card.

OSS is the old sound system on Linux, some things still use it, so you may still see it referenced in places.
ALSA is the new sound system on Linux, basically the drivers and the way programs interact with the sound card.  It has backward compatibility peices for OSS.
ESD, polypaudio, JACK, and ARTS are sound servers, some programs tell sound servers to play sound for them instead of playing directly to the sound card.  The biggest advantage of this is being able to play sounds on remote desktops and sound mixing without having to do it in the sound card or the sound card drivers.  The problem with them is they usually introduce lag into the sound, so it sucks when playing movies through one of these (however everyone says JACK is much better than the others at this, it's designed for audio sync).  KDE uses ARTS by default, Gnome uses ESD or polypaudio (which is a replacement for ESD).

---

### Post by filemanager on 2005-07-05
[QUOTE=intangible]You should only disable the AC97 onboard sound if you have an add-in sound card.

OSS is the old sound system on Linux, some things still use it, so you may still see it referenced in places.
ALSA is the new sound system on Linux, basically the drivers and the way programs interact with the sound card.  It has backward compatibility peices for OSS.
ESD, polypaudio, JACK, and ARTS are sound servers, some programs tell sound servers to play sound for them instead of playing directly to the sound card.  The biggest advantage of this is being able to play sounds on remote desktops and sound mixing without having to do it in the sound card or the sound card drivers.  The problem with them is they usually introduce lag into the sound, so it sucks when playing movies through one of these (however everyone says JACK is much better than the others at this, it's designed for audio sync).  KDE uses ARTS by default, Gnome uses ESD or polypaudio (which is a replacement for ESD).[/QUOTE]
 Thanks for clearing that up for me. I kept hearing these references everywhere but never understood them.

I have a Sound Blaster Live! 24-bit sound card (so that's 'add-in' right?)

So disable AC97, then do the steps posted, reboot, and glorious sound shall be emitted from my speakers?

I will try this again! The first time I had the AC97 enabled

---

### Post by filemanager on 2005-07-05
Also, some people have said I need to install the emu10k1 driver. Do I still need to do that if I do the steps posted?

---

### Post by varunus on 2005-07-05
I don't think you should need the driver.  After turning off the AC97, ALSA should find your sound blaster, and you shouldn't need this howto.  (But I would recommend installing libesd-alsa0 anyway.)

---

### Post by rmco2003 on 2005-07-06
I've followed all steps word for word on this guide, and my card is not detected for some reason. I'm using a Sound Blaster Live! 24-bit sound card, and I've tried setting my sound card to 1 on the settings file but that doesn't do anything and I've also tried setting ALSA to the default media settings thing but that didn't help. My sound card just isn't detected and there's no reason I can see that is stopping it working. I've disabled onboard sound and everything.

Help would be really appreciated.. ](*,)

---

### Post by filemanager on 2005-07-06
[QUOTE=rmco2003]I've followed all steps word for word on this guide, and my card is not detected for some reason. I'm using a Sound Blaster Live! 24-bit sound card, and I've tried setting my sound card to 1 on the settings file but that doesn't do anything and I've also tried setting ALSA to the default media settings thing but that didn't help. My sound card just isn't detected and there's no reason I can see that is stopping it working. I've disabled onboard sound and everything.

Help would be really appreciated.. ](*,)[/QUOTE]
 I have the exact same card, and exact same problem =\

---

### Post by Heliode on 2005-07-07
Have you tried the [ALSA sound card matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix) ?

Try 'sudo modprobe emu10k1'. That is the module that should work with your sound card. 

After that, you may have to change something... right-click on the little speaker-thing in the top right corner of the screen, open volumecontrol, goto file -> change device. If everything went well it should be listed there.

I had a problem like this with my Soundblaster Audigy 2. My problem was that the emu10k2 module, which supports the card, isn't included in hoary, so I ended up compiling it myself. 

You're in luck though. When you get your cards working, you'll be saved a lot of trouble since they support hardware-mixing, which means you can hear sound from different applications all the time!

Hope this helps

---

### Post by rmco2003 on 2005-07-07
one thing I'm wondering about is does linux support mixing stereo sound into surround sound like my eax console does on windows? I'm guessing I would have to use a media player that supported mixing to 5.1 speakers

[B]EDIT: I've just tried what you suggested but it still comes out with
[quote=Linux]**[COLOR=Red]No volume control elements and/or devices found.**[/COLOR][/quote]
Guess the problem still remains unsolved.[/B]

---

### Post by filemanager on 2005-07-07
[QUOTE=rmco2003]one thing I'm wondering about is does linux support mixing stereo sound into surround sound like my eax console does on windows? I'm guessing I would have to use a media player that supported mixing to 5.1 speakers

[B]EDIT: I've just tried what you suggested but it still comes out with

Guess the problem still remains unsolved.[/B][/QUOTE]
 I got the same error :(

What does modprobe do?

---

### Post by linuxrobot on 2005-07-07
Hello,
My sound is not working _at all_.  No sound in games, startup, or anything!
(I have not, as of yet, tried to listen to a music cd, so *maybe* that will work...I don't know. :-? )
 I have a  Intel Corporation JN440BX AA729057-406 mobo.  My sound is integrated in to my mobo.  When I do the Belarc Advisor ( [http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html) ) , under multimedia it says:
Crystal WDM Audio Codec (2x)
Crystal WDM Audio Control Registers

Will **intangible**'s method work?

I'm getting the same error as **rmco2003** and **filemanager**;
"*No volume control elements and/or devices found.*"   ](*,) 

Thanks!

**LinuxRobot**  8)

---

### Post by filemanager on 2005-07-07
> **linuxrobot]Hello,
My sound is not working _at all_.  No sound in games, startup, or anything!
(I have not, as of yet, tried to listen to a music cd, so *maybe* that will work...I don't know. :-? )
 I have a  Intel Corporation JN440BX AA729057-406 mobo.  My sound is integrated in to my mobo.  When I do the Belarc Advisor ( [http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html) ) , under multimedia it says:
Crystal WDM Audio Codec (2x)
Crystal WDM Audio Control Registers

Will **intangible**'s method work?

I'm getting the same error as **rmco2003** and **filemanager** said:**
> (*,) 

Thanks!

**LinuxRobot**  8)
 We should form a club! lol

---

### Post by intangible on 2005-07-07
Unfortunately this howto just makes sound work "better", you have to have working sound first :/

---

### Post by intangible on 2005-07-08
Found that this setup breaks **aplay** and possibly other things, to fix, replace this in **/etc/asound.conf**:```
pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}
``` with this ```
pcm.!default {
    type plug
    slave.pcm "duplex"
}
```

---

### Post by albanianlord on 2005-07-08
I'm having a pretty weird ass problem:
I have the realtek high definition audio card (uggh) and I know the ac97 code works, because on slax my soundcard works perfectly, but in ubuntu, I get nothing. Alsa 1.09 

please help me out....

---

### Post by NeoChaosX on 2005-07-09
Intangible: Thanks for the fix, it also fixed the problems I was having with libao.conf and Gaim not working.

---

### Post by intangible on 2005-07-09
My esd also has lots of static unless I change **/etc/esound/esd.conf** to this:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1 -d duplex
spawn_wait_ms=50
# default options are used in non-spawned mode
default_options=-d duplex
```

Also, for SDL applications, add these lines to **/etc/environment** and restart:
```
SDL_AUDIODRIVER="alsa"
AUDIODEV=default
```

To make apps like VMWare and other OSS apps work properly, do this:
**sudo apt-get install alsa-oss**

and before launching the program, do this in the terminal you're gonna start the proggy from: **LD_PRELOAD=/usr/lib/libaoss.so**  To make that work system wide for all remaining OSS apps, you can add it to **/etc/environment** and reboot, BUT be forewarned, this could cause problems for some people, I only suggest it if you ARE WILLING TO ACCEPT BREAKAGE!  That said, I do it here and no problems so far with any apps, even UT2004 seems to work properly.

---

### Post by mistermax on 2005-07-09
[QUOTE=intangible]I know it's been done before, but I don't think anybody has compiled all the settings into a single happy set of instructions.

This setup should work with most sound systems, it is from my Nforce2 setup at home, it makes everything work quite nicely together, OSS, ESD, ALSA and make your Mic work while sound is playing (great for UT2004!!).

These instructions assume you know how to edit config files on your system and add/remove packages on your own.

[list=1]
[*] Goto **System->Preferences->Sound** and disable "Enable Sound Server Startup"

[*] Install **libesd-alsa0** which will remove libesd0, but that's ok.

[*] Make **/etc/esound/esd.conf** look like this:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

[*] Make **/etc/asound.conf** look like this:
```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
```If you look, the first setting will let you select a different sound card as your primary if you have multiple sound cards.

[*] Make **/etc/libao.conf** look like this:
```
default_driver=alsa
```

[*] Reboot to make sure all the systems startup correctly.
[/list]
OSS stuff will still tie up the sound card, but they don't run all the time.  Just configure most things to use ALSA and you'll be good.

Side-Effect: The Ubuntu startup sounds will go away, but i think the trade-off is worth it.

**Note**: If stuff plays a little static through ESD, in **/etc/esound/esd.conf** try changing
*spawn_options=-terminate -nobeeps -as 2 -d default*
to
*spawn_options=-terminate -nobeeps -as 2 -d duplex*[/QUOTE]


I've carried out these instructions on my machine, but don't get any sound out of my music player- I do get sound from Frozen Bubble but that is the only thing that gives me sound.

I've got a C-Media 5:1 surround card that I bought for £5 and I was wondering if the above configuration was generic or specific to your card? I'm not really all that great with hardware config. so any help/thoughts would be appreciated!


*Edit- I just tried Frozen Bubble and I no longer sound in it!*

---

### Post by Xgkkp on 2005-07-13
Okay here is a strange one, it took me about 10 minutes to work out what was wrong after doing this but.. My music is now playing fast. It's a tiny difference in pitch, but I used a seperate stopwatch and when the music player (mpd) said 3:00 the stopwatch said about 2:45. Any clues what's going wrong?

I did this to get everything over to ALSA and all set up correctly, so that I can hopefully get JACK working and all the music programs.

---

### Post by RastaMahata on 2005-07-13
try [thread=30076]this other asound.conf[/thread] if the one on this thread doesnt work. I've found out gaim sounds dont play with the config posted in here, but they do work with the one in the other thread...

---

### Post by Teo on 2005-07-14
Works great :)
But there's one strange thing.

Each time I do "**sudo gedit** /smth/smth..." I got this in terminal:
```
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
```
Bit strange, huh? :)

---

### Post by konrads on 2005-07-22
I have two soundcards in my PC a built in intel (works fine), SB Audigy 2 (doesn't) and a Booktree video tuner.

The SB is detected by modprobe and shows it's 40 something channels (all the soundrouters and so on). But I get no sound out of it. xmms plays via alsa to it, but alas on my speakers  - nothing. I tried the configuration supplied in this thread, but it didn't work. I am quite confused. How could i debug this more? Maybe a channel is muted?

---

### Post by konrads on 2005-07-22
Okay, i fixed it. Here is a quote from [http://forums.fedoraforum.org/showthread.php?t=59064&page=1](http://forums.fedoraforum.org/showthread.php?t=59064&page=1)

I had this problem too,
here is how I fixed it:
open gnome mixer, Edit->Preferences
Select Audigy Analog/Digital Output Jack, IEC958 Optical Raw and Tone
now check that Tone and IEC958 is desibled, and enable Audigy Analog/Digital Output Jack
I did it in gnome, didn't find those options in alsa mixer from shell

---

### Post by Teo on 2005-07-22
[QUOTE=intangible]I know it's been done before, but I don't think anybody has compiled all the settings into a single happy set of instructions.

This setup should work with most sound systems, it is from my Nforce2 setup at home, it makes everything work quite nicely together, OSS, ESD, ALSA and make your Mic work while sound is playing (great for UT2004!!).[...]
[/QUOTE]
OK, there's a thing:
I did just like in description, but something is wrong:
When playing sound using Rhythmbox after some period of time esd process hangs and takes 100% CPU time - I have to go to console, and kill esd process then everything back to normal.
System -> Preferences -> Sound -> Enalbe sound server startup is checked and I prefer not to disable it (without it I can't get sound from Gaim).

---

### Post by Teo on 2005-07-22
[QUOTE=Teo]OK, there's a thing:
I did just like in description, but something is wrong:
When playing sound using Rhythmbox after some period of time esd process hangs and takes 100% CPU time - I have to go to console, and kill esd process then everything back to normal.
System -> Preferences -> Sound -> Enalbe sound server startup is checked and I prefer not to disable it (without it I can't get sound from Gaim).[/QUOTE]
I've installed nForce audio driver from [www.nvidia.com](www.nvidia.com) and Rhythmbox works fine now - BTW nVidia OSS dirver gives better sound (more clear and soft for high frequencies) than OpenSource ALSA and ESD.

---

### Post by dasRauschen on 2005-07-23
hi everyone, i've been browsing the forum for a few days now and hope this is the right place to ask for help - be warned that i am new to linux, too ... 

i have problems getting my soundblaster 'extigy' to work as it should. ubuntu recognized both the onboard unit and the extigy, and all the software i tried works fine with the internal sound chip. i followed **intangible**'s howto to the letter and the comments/corrections made in this thread, but it didn't fix my prob ... ok, as i said, the extigy *is* recognized, as the output of 'cat /dev/sndstat' suggests:

```
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux dasRauschen 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Creative Technology Ltd. Sound Blaster Extigy at usb-0000:00:1d.7-1.4, full spe
Intel ICH5 with ALC202 at 0xc0000c00, irq 17

Audio devices:
0: USB Audio (DUPLEX)
1: Intel ICH5 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: Sound Blaster Extigy

Timers:
7: system timer

Mixers:
0: USB Mixer
1: Realtek ALC202 rev 0

```

when i send a *.wav file to /dev/dsp ('cat file.wav > /dev/dsp'), the speakers connected to the extigy give a short crackling noise and then *my system FREEZES* and does not recover (at least not within 10mins). same thing happens, when i ask xmms to use the extigy.

does anyone have an idea on how to fix this? any help is much appreciated. what information do you need? thanks in advance

---

### Post by dasRauschen on 2005-08-02
GREAT! Problem at least 90% fixed!  \\:D/ 

The Extigy is recognized but obviously cannot be accessed when it is connected via a usb-hub, got the hint from  the German [UbuntuUsers.de](http://www.ubuntu-de.org/viewtopic.php?t=7778&highlight=)  (for those of you who can read German). Simple solution ... but, hey, what a way to learn something about Linux&Sound.

Btw: Is anyone able to suggest mehtods to get the center and rear speakers working, too? so far 'only' stereo. oh, but what a stereo!   ;-)

---

### Post by blakamin on 2005-08-05
what happens if you've got no **/etc/asound.conf**?

---

### Post by dasRauschen on 2005-08-05
well, you can always create one.  ;-)

---

### Post by chruesu on 2005-08-11
Hi folks!

Thanks a lot for this great howto! Unfortunately, I still don't manage to get my sound properly configurated. Maybe, someone can give me some more specific advise? Thanks!

**The probs:**
[list]
[*]By playing music with amaroK, Email-notification-sound works, too.
However, then neither realplay nor audacity are able to play (record) sound.
[*]Another application, is X-lite (voip-softphone): I can only use it if no other application uses sound. This is very annoying 'cause I will not be aware of incomming calls if I'm playin' music.
Maybe X-lite is using OSS? Because it calls my speakers "Intel ICH (DUPLEX) [OSS]".
Is there a way to force X-Lite to use Alsa or can you recommend a different softphone?
[*]A good thing is, that I can record realplay-streams with audacity if I have only the these two apps. running.
[/list] 


**Hardware:**
AC97 Codec ALC203, SoundBlasterTM compatible
stereo speakers (on a laptop)

**Confs:**
$ lsmod |grep snd
```
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  2 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
```


esd.conf
```
# http://ubuntuforums.org/showthread.php?t=44753
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

asound.conf
```
# http://ubuntuforums.org/showthread.php?t=44753
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}


```

---

### Post by NeoChaosX on 2005-08-11
You got the /etc/asound.conf wrong. Try the advice from [this](http://www.ubuntuforums.org/showpost.php?p=246252&postcount=47) post and see if that helps.

---

### Post by chruesu on 2005-08-11
Thanks NeoChaosX for the fast reply!

No, it does not help... i have the impression, it's rather even worse?

However, I have to admit the following:
at the same time I also tried to solve the realplay-alsa-thing according to [this](http://ubuntuforums.org/showpost.php?p=80282&postcount=21) 

So, realplayer is now playing at the same time like amarok, however the realplay-sound is kind of wiggly and recording with audacity does not work anymore.

The X-lite prob isn't solved either

So, shall I re-change the realplay-bin and/or asound.conf?

---

### Post by NeoChaosX on 2005-08-11
Oh, RealPlayer's playback is scratchy? Change buffer_size in asound.conf to 8192. That seems to be the minimum to get clear sound in Real.

As far as Xlite goes, I have similar problems with TuxKart. It seems prgorams that use only OSS still require all other sound-using programs to be off. It's annoying, but somewhat necessary.

---

### Post by chruesu on 2005-08-11
[QUOTE=NeoChaosX]Oh, RealPlayer's playback is scratchy? Change buffer_size in asound.conf to 8192. That seems to be the minimum to get clear sound in Real.[/QUOTE]
Thanks NeoChaosX and sorry for askin' questions with solutions posted one page above.
I tried several values and Realplay-sound is indeed better.
However, still the email-notifications sound's scratchy with this adjusted asound.conf :-? 

[QUOTE=NeoChaosX]..It seems prgorams that use only OSS still require all other sound-using programs to be off. It's annoying, but somewhat necessary.[/QUOTE]
I do not understand why this should be somewhat necessary?
IMHO only annoying... 
Anyway, thanks for the advice. Of course I would be very grateful if somebody is aware of a workaround that helps to solve my X-Lite-prob. Thanks!

---

### Post by flip on 2005-08-15
Just wanted to post to say how much help this thread has been, and to add my 2 cents. A combo of all the configs and alternative packages (namely libesd-alsa0) has my ubuntu successfully mixing alsa audio, playing audio in mozilla (finally flash with audio!) and even mixing OSS?

Yup turns out everyone posting above is right, mixing OSS audio is pretty much impossible AFAIK. I was searching everywhere looking for info about getting OSS to stop blocking. I didn't find anything that worked.

Finally cursing my CRAPPY onboard sound chip, I dissabled it in my BIOS and dusted off my 4 year old Creative 5.1 Live PCI card (they don't even make these any more). Plugged it in and it worked: all the alsa goodness from this thread, and suddenly mixing in the OSS sound too. Turns out that even though both of these sound devices were AC97, not all AC97 devices are created equal. Creative does mixing on the card where Dell ships crappy onboard 5.1 devices that have all the same plugs, but not the functionality. Dig out your old audio cards folks, they haven't got much better in the past 4 years.

So now I'm playing World of Warcraft (without having to kill esd!) and listening to music at the same time. 

Many thanks all, I've never been happier with my desktop setup.

- flip

---

### Post by intangible on 2005-08-18
Thanks for the kudos, I'm glad I could help somewhat :D

---

### Post by absinthe on 2005-08-28
I'm using dmix, and with beep/xmms every once and awhile my music starts crackling/reverbing badly. All I have to do to fix it is pause and unpause. Why?

---

### Post by Magadass on 2005-08-30
I used this in combination with downloading the NForce driver from nvidia and selecting to only install the sound driver, my OSS works as expected from Nvidia's old old old driver but nothing else works, and the end of wav files is cut off like the last 1/2 second isnt there....its really annoying...I cant believe sound is sooo broken, they really need to fix this!

---

### Post by Statik on 2005-09-11
Trying to get sound working in Doom3. I've followed the stuff here and got sound in all my applications so far. My asound.conf is:
> # Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
 

Part of the output when I run Doom3-demo is:

> ------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.8
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
buffer size select failed: Invalid argument
close pcm
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------
-------------------------------------- 

So, I'm trying to figure out how to fix that.

Also, since ESD is not starting now, how do I get system sounds back, like menu clicks, etc.?

Edit: Got the system sounds back by enabling sound server at startup. Doesn't seem to have hurt anything else. Now, all I need is sounds in Doom3. Any ideas?

Edit: LSMod gives me this section that deals with snd:
> snd_intel8x0           29984  1 
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0 
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm 

Does this help?

Edit: Installed alsa-oss, as it wasn't installed. Got sound in Doom3 now . . . garbled, but sound. Now to clean it up a bit. Sounds like it might be buffers or something. My command for doom3 is now:

> doom3-demo +set s_alsa_pcm plughw:0 


Got things tweaked in Xine so that mp3s aren't all crackly. Can't seem to fix Doom3 tho. The doom3 output in the terminal shows tons of this sort of thing:

> idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024 

Which, makes me think the buffers are overflowing, but I can't seem to make it go away. Any ideas?

Statik

---

### Post by intangible on 2005-09-16
Additional setup info from an Audigy 2 user to make the front SPDIF port work on your computer:

1. all you gotta do is go to ICE958 Optical Raw just turn it off and viola! sound from spdif
2. that is for the audigy 2 zs platinum front panel 
3. then just tweak the volume to your liking

---

### Post by TiMBuS on 2005-09-21
To everyone using a SB LIVE! 24-bit:
The problem is ALSA *cannot* recognise your card. Sorry to say it, but this is one of creatives worst inventions ever. It might work great on windows, but wow. Its so bad on ubuntu. To quickly test your card out, modprobe snd-ca0106
if this works, lucky you. edit /etc/modules and on a new line put snd-ca0106

If this doesn't work, you need to go through the painstaking process of getting alsa-source, extracting it, running "configure --with-cards=ca0106" then "make" followed by "make install"

THEN modprobe ca0106 - if that doesn't work see if you have other modules hijacking the card.
If all works, edit /etc/modules and add snd-ca0106

Sometimes you have to redo this after system updates. I'm considering just removing the card.

Don't forget to compile you need to have gcc and the needed libraries.. Ububtu has it all in one package called 'build-essentials' i think.

---

### Post by camp on 2005-10-06
Hi all!

I don't know what to say!?... I think I love you all!!! :D 

It worked like a charm! hopefully, my sound on Gaim will die all the time and so on! Very pleased!
I can even play some music on XMMS, a video clip in mplayer and still hear sounds from Gaim!

I'm a happy camper! This just shows how good this K/Ubuntu community is!

Have a nice day to you all!
/JC

---

### Post by one_ro on 2005-10-06
Hi,
I went through the procedure, ecerything went OK but after restarting I got an error message from aRts (please see attached png).
Could you please advice on this? (Kubuntu 5.04, KDE 3.4).
After upgrading to KDE 3.4 (a while ago), I have no "System/Preferences" menu but another "Preferences" menu apart from 'System". And there I didn't find "Sound" but a "Sound and Multimedia" submenu, which subsequently takes me to "Sound System".
The point is that I don't know where to disable the "Enable Sound Server Startup"...
Another problem would be that I now have this constant background sound (don't really know if it's because this Howto or because of a previous alsaconf, though).
Oh, and if we're still in the sound land, how can one test if having mic input? I set the input in the Kimix mixer, but I still cannot record anything.
Thanks very much for any hint!

---

### Post by camp on 2005-10-07
Hi all,

I'm happy with my setup, but... (I hate that word!)... I can't have sound in Firebird and XMMS, or any other program at the same time!?

I have as suggested, edited /etc/mozilla-firefox/mozilla-firefoxrc, changing FIREFOX_DSP to "AOSS"... still no sound at the same time. I need to stop every other sound, and then restart Firebird to actually make it play the sounds.

Any ideas!?
/JC

---

### Post by alesdoc on 2005-10-07
i've breezy colony 4.

I've tried to follow the howto, but i discovered that the packge libesd-alsa0 was still on my laptop, so i checked the three conf files.

The first one /etc/esound/esd.conf was the same as in the howto

The second one doesn't exist on my pc

The third one is on my pc and i changen the driver switching from esd to alsa.

I rebooted the pc, but nothing was changed. All the system sound are ok, but the mp3 files aren't played very well. Tha sound is scratchy sound especially the "bass" sound is scratchy.

Any ideas?

---

### Post by z-vet on 2005-10-13
[QUOTE=one_ro]Hi,
I went through the procedure, ecerything went OK but after restarting I got an error message from aRts (please see attached png).
Could you please advice on this? (Kubuntu 5.04, KDE 3.4).
After upgrading to KDE 3.4 (a while ago), I have no "System/Preferences" menu but another "Preferences" menu apart from 'System". And there I didn't find "Sound" but a "Sound and Multimedia" submenu, which subsequently takes me to "Sound System".
The point is that I don't know where to disable the "Enable Sound Server Startup"...
Another problem would be that I now have this constant background sound (don't really know if it's because this Howto or because of a previous alsaconf, though).
Oh, and if we're still in the sound land, how can one test if having mic input? I set the input in the Kimix mixer, but I still cannot record anything.
Thanks very much for any hint![/QUOTE]

I double this. Sounds seems to work fine but ie got the same error on KDE startup:
```
Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = 4096, can_write = 6144, errno = 11 (Resource temporarily unavailable)
This might be a sound hardware/driver specific problem (see aRts FAQ)
```
Sound system is disabled, so i can't understand what's wrong here...

---

### Post by antidrugue on 2005-10-14
Wow! Thanks "intangible"

For myself, I use Debian Sarge and based my dmix setup on (which is perfect for KDE):
[http://alsa.opensrc.org/index.php?page=Dmix+Kde+-+arts%2C+ESD+and+SDL+quick+and+dirty+HOWTO](http://alsa.opensrc.org/index.php?page=Dmix+Kde+-+arts%2C+ESD+and+SDL+quick+and+dirty+HOWTO) 

But those lines (from you) did the trick for Gnome:

-"Install libesd-alsa0 which will remove libesd0, but that's ok."
-" Make /etc/libao.conf look like this:
Code: default_driver=alsa "

Thanks, you people from Ubuntu are just what the doctor ordered for my system!

---

### Post by antonymous on 2005-10-16
I'd like like to echo **alesdoc**'s comments that /etc/asound.conf does not exist on my computer either - should I just go ahead and create one?

I've just upgraded from hoary to breezy, as well...

---

### Post by TiMBuS on 2005-10-19
Yep, just make a new /etc/asound.conf

However I always make the file $HOME/.asoundrc which is the same thing. ($HOME is your /home/username/ dir)

---

### Post by Josef K. on 2005-10-21
[QUOTE=z-vet]I double this. Sounds seems to work fine but ie got the same error on KDE startup:
```
Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = 4096, can_write = 6144, errno = 11 (Resource temporarily unavailable)
This might be a sound hardware/driver specific problem (see aRts FAQ)
```
Sound system is disabled, so i can't understand what's wrong here...[/QUOTE]

same problem here ](*,)
what should I do?

---

### Post by Statik on 2005-10-24
OK, back to digging through the doom3 stuff and my .asoundrc file. I got rid of my etc/ashound.conf all together, renamed it to a back file, and I'm starting from nothing.

When doom3-demo initializes, part of it says:
```

------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.9
opened Alsa PCM device plughw:0 for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes

```

Then, just when the first menu comes up, we get:
```

--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 25088
1008 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
224 MB Video Memory
Async thread started
snd_pcm_writei short write: 4095 out of 4096
snd_pcm_writei short write: 4095 out of 4096
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped

```

with the nice repeating error until the game is closed.

now, it looks like I'm having trouble writing all my data to the soundcard. It doesn't really look like a buffer problem, but a data problem. Are the chunks getting lost or something? Does anyone have a bit more indepth knowledge of what the system is telling me?

Is there a sound testing progam that I could use that might spit back errors I can use?

My current .asoundrc file consists of only:
```

pcm.card0 {
    type hw
    card 0
}
ctl.card0 {
    type hw
    card 0
}
pcm.dsp0 {
    type hw
    card 0
}
ctl.mixer0 {
    type hw
    card 0
}

```

I'm trying to work my way down through the docs at [ALsa.Opensource.Org]("http://alsa.opensrc.org/.asoundrc") and see if I can divine what the settings should be.

Statik

---

### Post by rockmanac on 2005-10-25
Thanks!!!  I've been having issues since I got Ubuntu installed on my machine... I even asked the Linux expert at work.... No one could figure out the problem... I guess the lesson I learned here is I should have come to the forums first!

-A

---

### Post by corepusher on 2005-11-02
Hi Intangible!!!
Thanks for the help!!! I was trying to solve sound problems from weeks ago and finally the problem was solved. There's only one detail and is that the output volume is very low. Even if I put the PCM volume level to the max and the Master vol the sound is still very low. Im testing this with XMMS reproducing mp3's and the driver config is set in ALSA. My soundcard is a C-Media PCI CMI8338-SWIEC. Do you know what can I possibly do to fix my output vol??

---

### Post by iNerdSure on 2005-11-02
Dear sound experts on the forum, 

I have been struggling since the release of Breezy to get sound working on my laptop Acer 4061. I'm a Linux newbie convert from M$Wxp. Tried various solutions offered on Ubuntu and other forums, but without success. 

ins@inerdsure:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
ins@inerdsure:~$

I've also tried running ALSA and unmuted all the controls. But no success.

Any experts out there that can show me the light, or rather sound me out? Many thanks in advance.

---

### Post by Madaa on 2005-11-08
Ok, got soundblaster 24 work thx to TiMBuS and howto,
but only front speakers give sound, is this in software
 (xmms) or something else ?

Thx for help

Madaa

---

### Post by neohunt on 2005-11-09
Hi,

I'm new to linux and to this forum. Thanks for this HOWTO, it helped me a lot and now I'm playing sounds perfectly

---

### Post by gray-squirrel on 2005-11-09
[QUOTE=TiMBuS]To everyone using a SB LIVE! 24-bit:
The problem is ALSA *cannot* recognise your card. Sorry to say it, but this is one of creatives worst inventions ever. It might work great on windows, but wow. Its so bad on ubuntu. To quickly test your card out, modprobe snd-ca0106
if this works, lucky you. edit /etc/modules and on a new line put snd-ca0106

If this doesn't work, you need to go through the painstaking process of getting alsa-source, extracting it, running "configure --with-cards=ca0106" then "make" followed by "make install"

THEN modprobe ca0106 - if that doesn't work see if you have other modules hijacking the card.
If all works, edit /etc/modules and add snd-ca0106

Sometimes you have to redo this after system updates. I'm considering just removing the card.
[/QUOTE]

I've actually gotten my SoundBlaster Live! 24 bit to work on the first try under ALSA 1.0.8 with the i386 kernel, and it still worked even after I installed the AMD K7 kernel.  I temporarily lost my sound after removing the i386 kernel, but I was able to get it back so I could still get sound using the K7 kernel.  However, I have never been able to get sound under 1.0.9, and the computer was complaining about unresolved symbols.

I noticed they have 1.0.10RC2 up last week, so I will have time to play around with that version later this week.

Generally, you have to (possibly recompile and) reinstall the ALSA driver when a new kernel image is installed.  From my experience, I've lost sound after even a patched kernel image is installed (I guess this is what you meant by system updates).  (The same has held true for my Unichrome 3D drivers, but that's another story.)

I suspect that part of this is may be a kernel issue, as I noticed modules for other sound cards were on my computer, even before I downloaded the ALSA source.  That may be why the sound card is not being recognized so easily.

Also, I recently noticed there was a way to [uninstall]("http://www.alsa-project.org/~valentyn/Alsa-sound-mini-HOWTO-7.html") the existing ALSA drivers (see section 7.11); this probably should be done before upgrading or reinstalling to prevent confusion.  I will remove mine before installing the latest version this time; I have never done this before.

---

### Post by wammy on 2005-11-09
:(

i did exactly as said here and now the only thing left in the sound panel is the microphone setting?? so no sound at all.
prefs-> sound only shows: default soundcard: camera


i have an nforce2 mobo and run breezy + gnome

```
lsmod |grep snd
snd_ca0106             27172  0
snd_ac97_codec         72188  1 snd_ca0106
snd_usb_audio          68160  3
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  4 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  2 snd_ca0106,snd_pcm
snd_usb_lib            13824  1 snd_usb_audio
snd_rawmidi            22816  1 snd_usb_lib
snd_seq_device          8204  1 snd_rawmidi
snd_hwdep               8608  1 snd_usb_audio
snd                    48644  14 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore               9184  2 snd
usbcore               104188  7 snd_usb_audio,snd_usb_lib,quickcam,usbhid,ehci_hcd,ohci_hcd
```

---

### Post by handy on 2005-12-17
intangible, you've got that magic something...  :KS 

You've solved my sound prob's & UT2K4, sounds great, & runs as smoothly, if not more so, than it did when run without sound!

Thanks for your time & effort.

handy

---

### Post by sept00 on 2005-12-23
Hi all, after struggling extensively with my sound settings, I have one more hint for people experiencing sound difficulties: 

If you have a webcam connectes, check to see if your /etc/asound.conf isn't trying to send sound to your webcam: Open a terminal window and run "sudo gedit /etc/asound.conf" or "kdesu kate /etc/asound.conf" if you're using KDE. Check to see what card you are using. It should look something like this right at the top of the file:

```
...
pcm.card0 {
   type hw
   card 0
}
...
```

Next, open a terminal window and run "sudo cat /proc/asound/cards" and see what pops up as card "0". If it's your webcam, check which number your sound card has. My ouput looked like this:

```
0 [U0x46d0x8b0    ]: USB-Audio - USB Device 0x46d:0x8b0
                     USB Device 0x46d:0x8b0 at usb-0000:00:10.3-2.1, full speed
1 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with ALC650F at 0xe000, irq 22
```

I changed the setting in the /etc/asound.conf accordingly and am living happily with sound ever since:

```
...
pcm.card0 {
   type hw
   card 1
}
...
```

You could also just blacklist your USB-sound device, but I haven't tried that:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

I hope this helps. I'm pretty new to Linux so please correct me if I've gotten anything wrong.

---

### Post by rickyjones on 2005-12-30
I've read through this entire thread, and as of today I still cannot get sound from two programs at the same time.

richard@edmund:~$ lsmod |grep snd
snd_atiixp             18912  3 
snd_ac97_codec         72188  1 snd_atiixp
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_atiixp,snd_pcm
richard@edmund:~$ 

I followed the howto at the beginning of this thread to the letter. That resulted in sound from one application at a time, just as I had before, and it sounded a little more "tinny." I've since tried to undo what was done, and I think I have restored my sound to where it was before. But now I'm still utterly confused as to what my problem could be. :(

Any help would be greatly appreciated. For reference, this issue is on a Toshiba Satellite M45-S169. The sound card (see lsmod probe above) is an onboard Realtek/ATI card?

Thanks!

-Richard

**EDIT**

I don't know what happened, but it's somehow working now? I dunno. Sound confuses me.

Thanks!

-Richard

---

### Post by drfalkor on 2006-01-01
is this working in kubuntu ?

---

### Post by nicky75 on 2006-01-07
Thank you!!!! It's work fine in Ubuntu 5.10 too, why don't it port in trips and trick for Ubuntu Breezy???

---

### Post by ilbahr on 2006-01-09
hi,

I just want to add that virtual sound mixing works out of the box under breezy for my sound card:  Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

All that is required is to change to alsa if you want to system>prefrences>multimedia system

change it to alsa. now virtual sound mixing work perfectly.

For any application that require oss just stick aoss command infront of it

aoss <application name>. This work perfect with realplay for example.
aoss realplay

For realplayer you can do that automatically by editing the realplay script shell find the line (this is near the end of the script)
$REALPLAYBIN "$@"

and replace it with

aoss $REALPLAYBIN "$@"

Now any application that require play (from sox package) replace play with aplay and it will work fine.

Now everything work fine you can play realplayer while opening totem and having gnubiff alert you of new emails no problems at all.

Those are my 2 cents of advise.

---

### Post by chaumurky on 2006-01-14
[quote=RastaMahata]well, if I select alsa for input, I cant use sound recorder...
If I select OSS, I can record sounds easily :)[/quote]

That's what I needed to do as well. Still, if I so much as touch the mic level control it cuts out and i need to restart the alsa-utils server. I'll have to look further into this. (I have a cs-4235 chip).

---

### Post by chaumurky on 2006-01-14
OK, I've discovered that switching on and off the 'mic playback boost' get's it going again (no need for the sound server restart now). This is surely a bug?

---

### Post by chaumurky on 2006-01-14
Right. So now I have scripts for gtkguitune and audacity with the following line before launching the program...

```
amixer sset 'Mic Playback Boost' on && amixer sset 'Mic Playback Boost' off

```

I'm finding Linux has as many corks as there are holes!!

:rolleyes:

---

### Post by TechSonic on 2006-01-23
I did all that stuff there and I still don't have full deplex sound.  I set everything I could think of to alsa if not already and teamspeak and aa still cause one another to have no sound.

Why does my friend who just got Kubuntu have no problems at all with SB live and I do? He can use teamspeak and hear sound in AA but I can't?  We both got the same hardware, video and sound.  We both have ATI Radeon RX9250 video cards that work fine, but we also have Sound Blaster Live and his works and mine does not.  Is it because I have 24bit and he has live 5.1?  Do I need to put in my old sb live 5.1 to make it work? Also what will I do with my 24 bit after that? It'd be like wasting money.  I read for hours over the stuff on the .asoundrc stuff and all of that jazz and yet, every thing I did had no effect on fixing my sound problem.

If I don't get this fixed, I'm going to jump out the window yelling like a mad man until the cops pick me up and toss me in the loony bin.

Sorry I had to rant to someone, I'm over the limit of fustration with this.           This one problem, this problem only, is the reason why I still can't fully convert to linux from Windows.  I have everything else the way I want it but this, I'm so close and yet the last detail just stones me to death.  I've spent way to much time working on this.  It's been 3 weeks getting everything hunkydory.

---

### Post by intangible on 2006-01-24
Try making **/etc/asound.conf** looking like this if you're running 5.10:
```

pcm.!default { 
	type plug 
	slave.pcm "duplex" 
}

pcm.dsp0 {
	type plug
	slave.pcm "duplex"
}

pcm.dsp1 {
	type plug
	slave.pcm "duplex"
}

pcm.dsp-1 {
	type plug
	slave.pcm "duplex"
}


ctl.mixer0 {
        type hw
        card 0
}

pcm.duplex {
	type asym
	playback.pcm "dmix"
	capture.pcm "dsnoop"
}


```
This tutorial was made for the previous version of Ubuntu, things improve every version :)

---

### Post by Statik on 2006-01-25
HI All,

Just an update. My sound issues with Ubuntu and Doom3-demo went away with a new motherboard. Hardware issue I guess. The only problem now is . . . My volume controls are muted and at 0% on boot. I have to open the volume control and unmute both MASTER and PCM as well as move them away from 0%. I have my save session settings box checked yet this reoccurs with every reboot. 

How can I change this?

Statik

---

### Post by axlf on 2006-01-28
Hej.

I can't get multiple sounds to work. Appreciating your work i tried the howto and various .asound configurations, even the last one posted for breezy.

After a while i found out that my second soundcard, if set to primary, is having no trouble playing two sounds at once.

I thought it might be a driver issue, but the driver from nvidia is just for OSS.

You could say, however, why bother if the second one works?
Well, i am not quite satisfied with the primary's latency using voip.

Any ideas?

Configuration:

NForce 1 with onboard AC97
+ SigmaTel PCI

```

axl@localhost:~$ uname -r
Kernel 2.6.12-10-k7

axl@localhost:~$ lspci
0000:00:05.0 Multimedia audio controller: nVidia Corporation: Unknown device 01b0 (rev c2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:01:02.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)

axlf@localhost:~$ cat /proc/asound/cards
0 [nForce         ]: NFORCE - NVidia nForce
                     NVidia nForce with AD1885 at 0xe2080000, irq 11
1 [au8820         ]: au8820 - au8820
                     au8820 at 0xe1000000 irq 5
2 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10

axlf@localhost:~$ lsmod | grep snd
snd_mpu401              6408  0
snd_au8820             37056  0
gameport               14920  3 analog,snd_au8820
snd_mpu401_uart         7360  2 snd_mpu401,snd_au8820
snd_rawmidi            25056  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
snd_intel8x0           33344  2
snd_ac97_codec         84028  2 snd_au8820,snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  4 snd_au8820,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  15 snd_mpu401,snd_au8820,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm

```

---

### Post by peRosine on 2006-01-30
Thanks mate. This one worked for me with my Soundblaster Live 24 bit. (no hardware mixing).

Thanks!

---

### Post by louis_nichols on 2006-02-02
Well... I must say... I haven't had sound problems so far. I let the system configure itself and I hear everything. Unlike other distro's I've tried. So, this makes me happy. Still, I can't seem to get surround sound. In windoze I configure Line-In and Mic as outputs and use them. But in Linux I haven't found a way to do that. Myself, I'm not all that interested in duplex, but I would love to have another set of outputs. I also use an nForce2 chipset. Any ideas?

Edit: my interest is not as much in havin surround sound as it is in having 2 apps output stereo sound on different channels.

---

### Post by wncben on 2006-02-13
Hey, I just wanna say thanks!  I went through and entered the comands and now I have sound in my applications (though no log in or system sounds).  Now if only these souns keep working :D    

  Thanks
~Ol' Ben

---

### Post by wncben on 2006-02-13
I found that by going back to sound preferences and re enabling the 'enable sound server' button i get system sounds back.

~Ol'Ben

---

### Post by chantal on 2006-02-13
Here's a reply for Statik. To store your Alsamixer mixer settings, first unmute the ones you want with "M" on kb, mount the levels pretty high, then after escaping from the Alsamixer, run this line in terminal

sudo alsactl store

---

### Post by Scanner on 2006-02-17
Don't mean to be a bother but where should this go in the /etc/asound.conf or is this a complete replacement from earlier versions of this file from this thread?


[QUOTE=intangible]Try making **/etc/asound.conf** looking like this if you're running 5.10:
```

pcm.!default { 
	type plug 
	slave.pcm "duplex" 
}

pcm.dsp0 {
	type plug
	slave.pcm "duplex"
}

pcm.dsp1 {
	type plug
	slave.pcm "duplex"
}

pcm.dsp-1 {
	type plug
	slave.pcm "duplex"
}


ctl.mixer0 {
        type hw
        card 0
}

pcm.duplex {
	type asym
	playback.pcm "dmix"
	capture.pcm "dsnoop"
}


```
This tutorial was made for the previous version of Ubuntu, things improve every version :)[/QUOTE]

---

### Post by intangible on 2006-02-19
As a complete replacement.  5.10 already has Dmix enabled by default so you don't have to have the extra junk in there for that.

---

### Post by NicePics13 on 2006-02-24
***Intangible***'s original fix is what I'm using right now with my nForce2 barebone.
This fixes the crackling sound in **ZSNES** & **Wine**, sound recording in **Audacity** works and I can open multiple files in **mplayer**.
I increased the *buffer_size* to *8192* and fixed the **Gaim** issue not with the aplay command (as I couldn't get that to work), but with *play %s*
Heck, even *mplayer %s* worked!
Thanks!

---

### Post by bronwe on 2006-02-24
Hi I am using breezy and this seems to work for me too.

:D 

-Bronwe

---

### Post by bronwe on 2006-02-24
Hi.

I am using breezy and the howto in the first post worked, just by downloading 

libesd-alsa0

This is good.  Just get Synaptic to re-install libesd-alsa0.

---

### Post by speedsix on 2006-02-27
Hi, the asound listed in the first post is good but it could do with being modified to be able to specify card/devices for both input & output.

For example my output is "hw:0,2" (spdif) and my mic is pcm "hw:0,1".

I have done this;
```

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          **pcm "hw:0,2"**
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"
     slave {
          **pcm "hw:0,1"**
     }

     bindings {
          0 0
          1 1
     }
}

```

Doesn't seem to be the most elegant way what with the default soundcard listed at the top but it works

---

### Post by chaumurky on 2006-03-10
Is this tweak still applicable for Dapper?

---

### Post by metalox on 2006-03-14
Oh dear it doesn't work for me. Thanks for the Howto, it sounds easy and good, but it broke my sound system! Using Breezy. Soundcard: ESS ES1938 (Solo-1). It was working OK but I had some issues recording with Audacity. Recording worked but every few minutes it was recording loud "noise" which I did not hear during recording but i could see it happening. I hoped following Intangible's Howto might help. But now I just get noise on the Line-In!

I followed the original posting:
1) Goto System->Preferences->Sound and disable "Enable Sound Server Startup". OK.
2) Install libesd-alsa0. It was already installed. OK.
3) Edit /etc/esound/esd.conf OK.
4) Edit /etc/asound.conf This file did not exist so I created it. OK?
5) Edit /etc/libao.conf OK.
6) Reboot. OK

Sound playback works but recording is not working properly! 

7) system > preferences > multimedia

Output: ALSA (pipeline: alsasink). OK
Input: ALSA (pipeline: alsasrc). ERROR!
"Error: Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"

Does this have something to do with it? Any advice much appreciated.

---

### Post by metalox on 2006-03-15
> Sound playback works but recording is not working properly! 

7) system > preferences > multimedia

Output: ALSA (pipeline: alsasink). OK
Input: ALSA (pipeline: alsasrc). ERROR!
"Error: Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"


In reply to my own post above: I take it back! Sound is working well this morning :)  However the Error remains. Is this serious/fixable?:-k

---

### Post by FloSynergy on 2006-03-20
hi all,

thanks for all the info on this thread.

i have just recently purchased an audigy 2 zs pcmcia sound card to replace my on-board sound, which got fried a while back. workig without music sux! :mad: i run kubuntu, and some of the instructions on this post seem to be laid out for ubuntu gnome... :( 

when i plug in the pcmcia, everything just freezes. if i unplug it, the system crashes and reboots.
if i plug it in and then start up, the system finishes about 30% of its boot-up process, then freezes.:-k 

since i'm a total beginner at linux (only 1 year experience working with xandros, and 3 months with kubuntu), i'd really appreciate it if someone could give me advice here.

thanks,

flo

---

### Post by varcsscotty on 2006-03-30
Thank you so much for this easy and working tutorial.  I fixed my sound problems in less than 5 minutes...how amazing is that!:D

---

### Post by Intangir on 2006-04-03
weird, the guy who started this thread uses the name intangible.. thats the name i use if someone has already taken Intangir

---

### Post by intangible on 2006-04-05
[QUOTE=Intangir]weird, the guy who started this thread uses the name intangible.. thats the name i use if someone has already taken Intangir[/QUOTE]

Aha! So you're the one who always gets my name at the good sites these days!

:)  I use intangi at places where intangible is already taken.

---

### Post by japs_it88 on 2006-05-03
I followed your procedure and that helped my greatly in making my mic work, but on the other hand the sound quality has just sank very low.
have you got any suggestion?

thanks in advance

---

### Post by intangible on 2006-05-03
I apoligize, but this howto is fairly outdated, it was written for Hoary, so it's almost two releases old... if you read through all the replies in the thread, there's a few updates to the details for Breezy.   I plan on writing new howtos for Dapper in June and hopefully those will solve any problems you may have.

---

### Post by Mon on 2006-05-06
It seems like you're using Dapper already, as probably many of us do. Can't you start a bit sooner than June? ;)

---

### Post by Arjunanda on 2006-05-21
[QUOTE=intangible]OSS is the old sound system on Linux, some things still use it, so you may still see it referenced in places.
ALSA is the new sound system on Linux, basically the drivers and the way programs interact with the sound card.  It has backward compatibility peices for OSS.
ESD, polypaudio, JACK, and ARTS are sound servers, some programs tell sound servers to play sound for them instead of playing directly to the sound card.  The biggest advantage of this is being able to play sounds on remote desktops and sound mixing without having to do it in the sound card or the sound card drivers.  The problem with them is they usually introduce lag into the sound, so it sucks when playing movies through one of these (however everyone says JACK is much better than the others at this, it's designed for audio sync).  KDE uses ARTS by default, Gnome uses ESD or polypaudio (which is a replacement for ESD).[/QUOTE]

Could you add this into the howto? It would be crucial to get this explanation in the first place, to get an idea what is what and why the config is needed. For me the linux sound system has been a real mess even though I have been working with the system for years. I only knew ALSA is the new, ARTS sucks and ESD is from enlightenment project. The above clarified it very well. Thanks intangible

---

### Post by Arjunanda on 2006-05-21
[QUOTE=intangible]Found that this setup breaks **aplay** and possibly other things, to fix, replace this in **/etc/asound.conf**:```
pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}
``` with this ```
pcm.!default {
    type plug
    slave.pcm "duplex"
}
```[/QUOTE]

Please add also this into the guide. It is not easy to read through all the 13 pages.
Thanks for great guide, intangible!

---

### Post by hanzj on 2006-05-21
[QUOTE=intangible].   I plan on writing new howtos for Dapper in June and hopefully those will solve any problems you may have.[/QUOTE]

I'm looking forward to you Dapper howto. Could you pm or email me when you have created it?

Thanks.

---

### Post by Arjunanda on 2006-05-25
Thanks for the howto. I am running Breezy - and this made things working well. All .mpg:s, mp3's work well. Mplayer, audacity, amarok, xmms. But skype has some problems: Somtimes it says "problem with sound device". Skype seems to block the audio completely for itself and not allow other apps to use it at the same time.

" Skype does not natively support ALSA, so you will need to install ALSA OSS emulation layer in order to use ALSA devices in Skype. You should have snd-pcm-oss and snd-mixer-oss modules in your kernel, either loaded separately or compiled in as part of the kernel."
[http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

What would be the way to make it work?
Also the mic volume is very low, even though in the GNOME mixer it is set maximum for both, the ALSA mixer and the OSS mixer. How to fix this?

After doing this thing, some .wmv movies started playing in fast speed. How should I correct that?

---

### Post by zorgrian on 2006-05-25
**Uuahrm ah hem!**
I really really really want to get skype going on my machine (standard ubuntu installation i.e. not 64 bit )
After about an hour and a half of scooting around the net looking for solutions to

1) how to get ALSA working with skype
2) how to get skype working at all

...I arrived at this posting, at followed the instructions to the letter.

It has at least allowed me to select the sound-card... but I can't use alsa input at all and...
Skype reports 'problem with sound card' after using it (unsuccessfully) once.

DO you have any solutions?

---

### Post by Arjunanda on 2006-05-25
Yes, now it is working but isnt really realible. Sometimes it complains about problem with sound device. I am able to call and receive calls, but my mic level is very low. In my mixer the mic level is maximum.

So to your problem 1, I think you should follow this howto. Then it is pretty much enough to have alsa-oss module insalled. Maybe you should try running skype with command:
aoss skype

Hope that this helps.

---

### Post by lostdata on 2006-06-07
well i remember i had the same prob in breezy now i loaded dapper and no sound.. lookin forward to that howto...

---

### Post by kipman725 on 2006-06-08
Thank you thank you thank you :D 

non of the other guides worked for me with my nforce 2 onboard audio, this one worked well and now finaly I can run alsa without stuttering.

---

### Post by gsanse on 2006-06-12
Did you try skype_dsp_hijacker?

---

### Post by gsanse on 2006-06-12
[QUOTE=zorgrian]**Uuahrm ah hem!**
I really really really want to get skype going on my machine (standard ubuntu installation i.e. not 64 bit )
After about an hour and a half of scooting around the net looking for solutions to

1) how to get ALSA working with skype
2) how to get skype working at all

...I arrived at this posting, at followed the instructions to the letter.

It has at least allowed me to select the sound-card... but I can't use alsa input at all and...
Skype reports 'problem with sound card' after using it (unsuccessfully) once.

DO you have any solutions?[/QUOTE]
Did you try skype_dsp_hijacker?

---

### Post by AngryKidJoe on 2006-06-24
After following the original guide here I get this error, I have to disable my sound in order for the message to halt popping up.
```
Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = 4096, can_write = 6000, errno = 111 (Connection refused)
This might be a sound hardware/driver specific problem (see aRts FAQ)
```
Any insight, perhaps?

---

### Post by melissawm on 2006-07-10
Same thing here as the guy just above... And I also want to use skype.. :(

EDIT:
oh it just went away by using the second version of /etc/asound.conf !! sorry :P

---

### Post by mahavishnu on 2006-07-11
works great in Dapper !!
thanks..

---

### Post by Hg80 on 2006-07-12
Hi works great, but cant mix with Cedega (Guild wars) so atm i can only here teamspeak and no in game sound from Guild wars, but playing a movie and MP3 works fine any help please?

---

### Post by cs378 on 2006-07-15
Okay, I think every thing works fine. I had MPlayer, Rhythmbox and Gaim all play at the same time.

Problems:

Sound is very crappy. ](*,) 
Totem player won't work (with or without others playing) ](*,) 


I just made every change posted. :neutral:

---

### Post by mb108 on 2006-11-09
Tried this out and got things working very nicely, but having microphone problems.

Can hear myself through the speakers, but seems like applications can't capture the input/access device.

Writeup here:
[http://ubuntuforums.org/showthread.php?t=292291]("http://ubuntuforums.org/showthread.php?t=292291")

---

### Post by mb108 on 2006-11-10
> **mb108 said:**
> Tried this out and got things working very nicely, but having microphone problems.

Can hear myself through the speakers, but seems like applications can't capture the input/access device.

Writeup here:
[http://ubuntuforums.org/showthread.php?t=292291]("http://ubuntuforums.org/showthread.php?t=292291")

Fixed.

From a previous post in this thread:
> 
what should I select in system > preferences > multimedia ??

Input: alsa ?
Output: OSS ?


Switched input to OSS, works.

RTFM, eh?:rolleyes:

---

### Post by cccc on 2006-12-09
I've got working under dapper drake:

according to:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

```
gedit ~.asoundrc
```

add the following text:```

pcm.skype {
   type asym
   playback.pcm "skypeout"
   capture.pcm "skypein"
}

pcm.skypein {
   # Convert from 8-bit unsigned mono (default format set by aoss when
   # /dev/dsp is opened) to 16-bit signed stereo (expected by dsnoop)
   #
   # We can't just use a "plug" plugin because although the open will
   # succeed, the buffer sizes will be wrong and we'll hear no sound at
   # all.
   type route
   slave {
      pcm "skypedsnoop"
      format S16_LE
   }
   ttable {
      0 {0 0.5}
      1 {0 0.5}
   }
}

pcm.skypeout {
   # Just pass this on to the system dmix
   type plug
   slave {
      pcm "dmix"
   }
}

pcm.skypedsnoop {
   type dsnoop
   ipc_key 1133
   slave {
      # "Magic" buffer values to get skype audio to work
      # If these are not set, opening /dev/dsp succeeds but no sound
      # will be heard. According to the alsa developers this is due
      # to skype abusing the OSS API.
      pcm "hw:0,0"
      period_size 256
      periods 16
      buffer_size 16384
   }
   bindings {
      0 0
   }
}
```
and changed in the skype settings from ALSA to **OSS**

**now the microphone works great !**

---

### Post by zhaarteth on 2006-12-16
> **NeoChaosX said:**
> Oh, since you have OSS through ALSA enabled, add this to the instructions to get sound in Firefox:

Edit **/etc/mozilla-firefox/mozilla-firefoxrc** change FIREFOX_DSP to "AOSS"

I've also noticed that if you're using RealPlayer, there's crackling in sounds unless you set buffer_size to 8192.

Great tip. But I tried that and I still have no sound in neither Java nor Flash. My Mplayer plugin works great, but I can't get any sound out from any other plugins. ](*,) 

@intangible:

I followed your howto to the T and I finally got Audacity working because of it... well the first time I rebooted. Then, when I started my computer up this morning, I started up Audacity and it gave me the I/O error (host error) as it did before. Then I tried running a few more apps that used (or could use) OSS and came to the conclusion that OSS doesn't work anymore. :confused: 

Everything worked fine the first time I made these changes. So I'm conflusterbated.

I'd love a good suggestion. I mean really.

Thanks a bunch in advance.

PS : I have an Intel 82801AA sound card. Hope that has some relevance.

---

### Post by Statik on 2006-12-16
I'm still struggling with getting sound in Flash9 as well in Firefox2. I'm not getting any errors and flash videos seem to play through all the way without any trouble. All of my other programs have sound. Only Flash doesn't have sound. I've done all of the things in this thread and all of the other threads relating to sound and flash to no avail.

The only other thing I have noticed is that whenever I use sudo gedit  to edit files I get the following information printed in the terminal window:
```

Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.

```

I'm not sure why I would get this when I'm only using gedit.

*sigh*

Any help would be appreciated

Statik

---

### Post by fraterm on 2007-07-06
> **Arjunanda said:**
> Thanks for the howto. I am running Breezy - and this made things working well. All .mpg:s, mp3's work well. Mplayer, audacity, amarok, xmms. But skype has some problems: Somtimes it says "problem with sound device". Skype seems to block the audio completely for itself and not allow other apps to use it at the same time.

" Skype does not natively support ALSA, so you will need to install ALSA OSS emulation layer in order to use ALSA devices in Skype. You should have snd-pcm-oss and snd-mixer-oss modules in your kernel, either loaded separately or compiled in as part of the kernel."
[http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

What would be the way to make it work?
Also the mic volume is very low, even though in the GNOME mixer it is set maximum for both, the ALSA mixer and the OSS mixer. How to fix this?

After doing this thing, some .wmv movies started playing in fast speed. How should I correct that?

With most of the mixer settings choices one could make there is usually a microphone decibel boost toggle, alsa mixer and any mixer that plays well with alsa should have the option to enable normally invisible sound devices to allow you to enable this setting.

---

### Post by s2d4 on 2007-10-28
I've been having this problem for almost a year now. Has anyone figured out a way to get the sound in flash working? The same gedit thing happens to me too. It would be great to finally have multiple sounds so everything can be heard...

---

### Post by Bulletbeast on 2008-08-06
I applied the changes, and now when I try to start xmms2, it gives me this, and no sound:

 INFO: ../src/xmms/main.c:499: Using output plugin: alsa
ALSA lib pcm_dmix.c:841:(snd_pcm_dmix_open) unable to create IPC semaphore
ERROR: ../src/plugins/alsa/alsa.c:218: Couldn't open device: default
ERROR: ../src/xmms/output.c:976: couldn't initialize output plugin
 FAIL: xmms_output_plugin_method_volume_get_available: assertion `plugin' failed

---

### Post by jocko on 2008-08-06
> **Bulletbeast said:**
> I applied the changes, and now when I try to start xmms2, it gives me this, and no sound:

That's probably because you follow instructions from a thread that is very outdated. That will usually only mess things up.
Ubuntu doesn't use esd anymore, and the alsa dmix plugin doesn't play well with pulseaudio (they both try to take full control over alsa, which is very likely why you get the error from xmms2).

Tip: [Check this thread]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+perfect") to set up pulseaudio. I'm pretty sure you'll manage to get better results.

---

### Post by jollyc on 2009-02-05
> **wncben said:**
> I found that by going back to sound preferences and re enabling the 'enable sound server' button i get system sounds back.

~Ol'Ben

That option is the only one I never seem to have in Sys>Pref>Sound.

NFI why but it isn't there. I suspect that might be the one reason why I don't get sound from multiple apps.

Thanks for writing this up however, this sharing of knowledge is what makes the open source community so strong.

If someone can get back to me that would be great.

Thanks,
Chris

---

### Post by Xyonofcalhoun on 2009-04-21
Yeah, me neither on that front. I figured it was just something to do with the difference in Ubuntu versions, I know it says Intrepid on the left, I just upped to Jackal this morning and I'm still trying to sort stuff out. Didn't see that option under either, though.

The problem I had under Intrepid was I could play music (through OSS, I think) but no sound effects played, at all. And, since the upgrade/update manager simply updated Ubuntu (shock!), it kept all the settings from 8.10.

Now, me being me, I went ahead and tried to install a Realtek AC97 driver, which is my chipset AFAIK... which failed to compile saying it needed a "curses library"... which I have, I have them all installed off synaptic. After that, I have no sound full stop, no matter what I do. I've tried the instructions here many times in various guises and am still seemingly no closer.

I hate still being a newbie. :|

Edit: After some (minimal) soulsearching, I found [this page]("http://wiki.archlinux.org/index.php/Fujitsu-Siemens_Amilo_Pro2000#SOUND"), which is relevant to my laptop, I've hotlinked straight to the sound section. I'm guessing the guy's written it for a different distro, but I can't for the life of me work out what to do for the first step, it mentions /etc/rc.conf, which I don't have... any help?

---

### Post by Bulletbeast on 2009-04-21
In order to compile something, you need the *-dev packages for the dependencies. Do you have libcurses-dev?

---

