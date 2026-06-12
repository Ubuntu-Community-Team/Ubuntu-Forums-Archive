---
title: "HOWTO: (ALSA) Stereo music and 5.1 surround on 5.1 speakers"
date: 2008-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by kustodian on 2008-05-05
There are a lot of HOWTOs which describe how to setup your 5.1 speakers/card, but none of them met my needs, nor they explained what they really did. So here is my little how to.

**[SIZE="3"]For this HOWTO to work:[/SIZE]**
[INDENT]1. your sound card should be working and it has to have analog output,
2. you have to have 5.1 speakers,```

```
3. you have to use ALSA.[/INDENT]

**[SIZE="3"]1. First problem: When listening to stereo music there are 3 situations I encourted:[/SIZE]**
[INDENT]1. only two front speakers work (center, woofer and rear don't work), or
2. two front speakers, center and woofer work, or
3. all six speakers work, but then it's not true stereo because the center speaker works, too.[/INDENT]

[COLOR="Red"][SIZE="3"]**Solution:**[/SIZE][/COLOR]
Create a .asoundrc in your home directory, type this in your console:
in Ubuntu:
```
gedit ~/.asoundrc
```
in Kubuntu:
```
kate ~/.asoundrc
```
and paste this text in it:
```
pcm.!default {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
}
```save it and close it.

[SIZE="3"][COLOR="Red"]**Explanation:**[/COLOR][/SIZE]
Whit this we replaced the default alsa device with our own. This basically copies:
[INDENT]front-left -> rear-left,
front-right -> rear right,
0.5*front-left -> LFE (woofer)
0.5*front-right -> LFE (woofer). The center speaker isn't used, because when you play stereo, you don't need it.[/INDENT]

**If anyone is interested here is a more detailed explanation:**

[INDENT]**#0=Front-left**
**#1=Front-right**
**#2=Rear-left**
**#3=Rear-right**
**#4=Center**
**#5=LFE (woofer)**
[/INDENT]
[INDENT]**ttable.0.0 1** (copy from front-left to front-left 100% of volume)
**ttable.1.1 1** (copy from front-right to front-right 100% of volume)
**ttable.0.2 1** (copy from front-left to rear-left 100% of volume)
**ttable.1.3 1** (copy from front-right to rear-right 100% of volume)
**ttable.0.5 0.5** (copy from front-left to LFE 50% of volume)
**ttable.1.5 0.5** (copy from front-right to LFE 50% of volume)[/INDENT]

Start your mp3 player and start playing a stereo mp3 file. You should here music on all speakers except the center one. You don't have to configure anything, because all the players will use alsa default device, which we modified. If you previously selected another device in your player (like for instance **"surround51"** or **"plug:surround51"**), just select **default** (in alsa plugin).

-----------------

[SIZE="3"]**2. Second problem: While playing AC3/DTS 5.1 movies, only 2 front speakers are working.**[/SIZE]

**[SIZE="3"][COLOR="Red"]Solution:[/COLOR][/SIZE]**
For this to work, you just have to configure your video player.
**Here are some of the player's configurations:**

**[COLOR="Red"]Mplayer (Updated)[/COLOR]**
Mplayer will automatically select the best output if you select **driver default** in the alsa plugin:
**Preferences->Audio**, Select **alsa**, **Configure driver**;
for **Device** select **driver default**.

**[COLOR="Red"]Xine and derivates[/COLOR]**
I recommend Xine player and other players that use xine engine (Kaffeine), because xine can use different alsa devices for different audio files.
Open Xine **Settings->Setup** (or in Kaffeine **Settings->xine engine parameters**), go to **audio** and configure these parameters:
[INDENT]**driver:** alsa
**Speaker arrangement:** 5.1 surround
**device used for mono output:** default
**device used for stereo output:** default
**device used for 5.1-channel output:** plug:surround51:0
[/INDENT]Push OK, and everything is setup.

**[COLOR="Red"]VLC[/COLOR]**
In VLC **Settings->Preferences**, **Audio->Output modules** (enable **Advanced otpions**), for **Audio output module** select **ALSA audio output**; then in **Output modules select** go to **ALSA**, and make sure that for **Default** is selected fo **ALSA Device Name**.


When playing a stereo file, you don't have to do anything, because VLC automatically selects stereo output, but when playing a 5.1 surround movie, while the movie is playing you have to select: **Audio->Audio Device->5.1** (every time you stop and start the playback, you have to do this again).

**[COLOR="Red"]Other mp3 players(XMMS, Audacious)[/COLOR]**
Just select the **ALSA output plugin** and make sure that the alsa device selected is **default**.

That's the end of this HOWTO, I hope it helps someone out there :)




**[SIZE="2"][COLOR="Red"]Changelog:[/COLOR][/SIZE]**
15.08.2008. Changed configuration of Mplayer

---

### Post by gibz85 on 2008-07-08
Thanks yaar... Man i have been looking for this... Awesome... Cool keep up the good work dude:popcorn:

---

### Post by toemos on 2008-08-13
hey, im still not able to get 5.1 with vlc. When the movies playing there's no 5.1 option in audio device.

anyone know why this is?

---

### Post by kustodian on 2008-08-14
> **toemos said:**
> hey, im still not able to get 5.1 with vlc. When the movies playing there's no 5.1 option in audio device.

anyone know why this is?

The movie must have 6 channel audio, like AC3, DTS or AAC. If it's stereo the option doesn't appear :(

---

### Post by glaze on 2008-08-15
> **kustodian said:**
> 
**[COLOR="Red"]Mplayer[/COLOR]**
I don't recommend you to use this player for watching stereo movies, because you will always have to change settings for thestereo/5.1 to work correctly

You don't have to change settings if you put a line **ac=hwac3,** in your ~/.mplayer/config. That line means that mplayer will try to output AC3 first, and if there is none, then it falls back to stereo. Remember the comma after hwac3!

---

### Post by kustodian on 2008-08-15
> **glaze said:**
> You don't have to change settings if you put a line **ac=hwac3,** in your ~/.mplayer/config. That line means that mplayer will try to output AC3 first, and if there is none, then it falls back to stereo. Remember the comma after hwac3!

This didn't work for me, I just got bad sound for movie with AC3, but I found a solution to this.
You don't have to change anything in settings, look it up in the how to, just made the change :)

---

### Post by d.marcu on 2008-09-24
I created the .asoundrc and after a reboot i get a message that : xine was unable to initialize any audio drivers. and i don't get any sound at all. 
I have a creative audigy ls sound card and  system setting is recognized as CA0106. I'm using Kubuntu 8.04.

---

### Post by kustodian on 2008-09-24
> **d.marcu said:**
> I created the .asoundrc and after a reboot i get a message that : xine was unable to initialize any audio drivers. and i don't get any sound at all. 
I have a creative audigy ls sound card and  system setting is recognized as CA0106. I'm using Kubuntu 8.04.

This "How to" is primarily for EMU10K1 driver, and you have Audigy LS which doesn't have this chip, it has Ca0106 :(

---

### Post by davidw89 on 2008-09-24
Hi there. I'd like to say that this worked because i am using a 5.1 channel (not digital, analogue, the coloured plug) and it's working great. All 5 speakers are working great and soudns great on youtube. It's a shame Ubuntu volume section can't enable 5.1 by default. But thanks!!

---

### Post by Hero of Time on 2008-10-11
> **kustodian said:**
> This "How to" is primarily for EMU10K1 driver, and you have Audigy LS which doesn't have this chip, it has Ca0106 :(
I have a Create SoundBlaster Live! 24 bit, however, lspci says it's an Audigy (Windows does the same too, even though I installed the latest driver for Live! 24 bit) and it only works with (s)mplayer. No sound for Audacious, flash and any other application.

Any idea how to solve it? Once I rename the .asoundrc file, I have sound again but only on two speakers and not 4.

---

### Post by Hero of Time on 2008-10-13
Ok, after lots of tinkering and messing with settings, I decided to install PulseAudio. I followed a couple of howto's and finally one worked like a charm.

Following [http://ubuntuforums.org/showthread.php?t=776739&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulseaudio) I got most of it working. As I use Xubuntu, the daemon does not start automatically. I had to create an autostart launcher like this:
```
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=PulseAudio
Comment=
Exec=pulseaudio
StartupNotify=false
Terminal=false
Hidden=false
```
Note that the name of the file and the name of the entry (in this case PulseAudio) must be the same, including upper and lower case, else it won't show up in the list.

Now I also had to change some config files next to the guide. In /etc/pulse/daemon.conf, I changed the 'daemonize' line, so it looks like this now:
```
daemonize = yes
```
Almost at the bottom of the file, I changed the default-sample-channels to 6, as that is how many speakers a 5.1 set has (5 satelite and one LFE).

Now all you have to do, is set every player to use Pulse and you're done. Wine should be set to Alsa, but if that gives some problems, you can try OSS instead.
If you use Audacious and it won't play through Pulse, remove it completely, including config (apt-get remove --purge audacious*) and remove the files and folders in your home folder. It might be enough to just remove the config in your home folder though.

Note: Do this if the above mentioned does not work for you, as it didn't for me. I have a Creative Soundblaster Live! 24 bit, shown as an Audigy LS with the card CA0106.

---

### Post by bikoholic on 2008-11-06
i have an audigy sound card, i am using ubuntu, i edit the .asoundrc
and in mplayer i configured alsa driver but when i try to play a file there is an error "[AO_ALSA]Unable to find simple control 'PCM',0 "
what settings should i have in sound preferences? now all of them are audigy 1S [SB0160]......(alsa)

---

