---
title: "Finding the best music player."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Raziel-chan on 2008-05-25
I know that there have been similar threads, but most of them have been archived and didn't help me at all...

Anyway, I am trying to find the best Linux media player for me. On Windows XP, from where I came, I was using Winamp, Winamp and a thousand times Winamp, so it's understandable that I want a player that can replace it appropriately.

What I've tried and what was wrong with it:

1. Wine (1.0RC2) + Winamp (5.531) - well, I thought that it may work and it did... Though not perfectly. For starters, the modern skin is pretty much unusable, its functionality broken completely. Moving on to the sentimental classic skin, then.
The classic skin works almost perfectly, together with the the taskbar icon (!). My only gripe is that for some reason Wine starts some mysterious second window together with Winamp that can be closed with alt-f4 and does seem to be affecting Winamp's work as long as it's there.
Oh, and moving Winamp is kind of broken too, or at least moving the main window/the whole player - when grabbing the main window, it - or the whole player, if the other windows were docked to it - randomly shakes and changes its position, sometimes glitching in the strangest ways or hopping outside the desktop.
Other than that, it works a-okay, together with minimal CPU usage.

2. Audacious 1.5.0 (1.5.1. tried and compiled, but uninstalled due to the fact that 1.5.0 extra plugins from the repos failed to work with it) - pretty good player, with lots of plugins and many features I like. It beats winamp by that it has an OSD plugin and can be minimized by clicking on the taskbar.
Still, it phails in four other categories: setting preamp in the equalizer higher than 1/4 from the bottom with any of the other setting going over the middle causes heavy distortions and sound garbage; it has high cpu usage, ranging from 15 to 32%; unlike many other players, if the CPU usage reaches ~100%, it starts stuttering; when switched on it is unable to play the last song played before it was closed. The song must be reopened for it to play it.

3. XMMS - almost perfect, not featuring any of Audacious's flaws (maybe except the sound stuttering at high cpu usages), but it has fewer, harder to install plugins and he base OSD plugin doesn't work as I want it to (displays only text, without any frame/background).

4. Amarok - a very nice player, but has just as high cpu usage as Audacious and doesn't allow me to change the method of playing files. I'm aiming at a winamp like behavior - the double-clicked file shoudl be played instantly and all the previous contents of the playlist should be erased. Amarok does neither of these.

5. Exaile - while it does automatically play the double-clicked file, it still leaves the previous song in the playlist.

6. Bmpx - same as Exaile.

7. Aqualung - for some reason it always indicates that all the devices are busy and doesn't start.

8. Listen - sometimes has problems opening, but they seem to be less frequent now. It's got almost all I want, except for an equalizer, but it's written on the website that it'll contain that module in version 0.6. For some reason, though, I can't download the newest development source. T_T

Listen Music Player has a good chance of becoming my player of choice once it's got an equalizer.

9. Juk - doesn't seem to be reacting to files selected to be opened with it from konqueror. No equalizer or OSD.

10. XMMS2 + some gui - Umm, tried Esperanza... And it seems pretty limited, plus I don't really know how to tie it to double-clicked music files.

11. MPD + some gui - Uhh... I may be stupid, but I couldn't get it to work. If anyone has some good guide, please post it here. :3

Maybe you know other players? Maybe you know how to remedy the flaws I pointed out above? Maybe you just want to advise me? Well, I'm eager and listening. :3

cya
Raziel-chan

PS. I'm using Kubuntu (well, Ubuntu with the Kubuntu-desktop package, so I can switch between both environments) Hardy on: Athlon 64 3500+ (2.2 GHZ, single core), 2GB DDR2-800 ram from OCZ, Geforce7600GT.

---

### Post by sayakb on 2008-05-25
I use Banshee since I usually keep it minimized to the tray.

---

### Post by rage-against-windows on 2008-05-25
I used winamp also , Ive tried em all and banshee is by far the best of em. (my opinion anyways).

---

### Post by Raziel-chan on 2008-05-27
I've tried Banshee, but it seems to have issues with opening files externally - to be exact, it's broken.
In the 0.99 version from Ubuntu's repositories, when I open a file by double-clicking it in konqueror (or selecting 'open with>Banshee') it does indeed open Banshee and play the file, but when I open another file that way when Banshee is still playing, it opens a new instance of Banshee.
Ver. 1.0 is even more useless, as doing that opens the player without adding the track to the playlist or playing it.

As for Listen, it seems that it can't be started with a song (double-clicking a song when the player is off), as it doesn't start then. It needs to be first opened by the menu shortcut/command line and THEN I can play songs in it by double-clicking. ._.

Quod libet is fun, but it has the same problem as Banshee 1.0 - double-clicking a file or selecting open with>Quod Libet only starts the player, without adding the song to the playlist or playing it.

cya
Raziel-chan

---

### Post by sayakb on 2008-05-27
I have 0.13.2 in my repos. I think 0.99 isn't stable. Try 0.13.2. It works, opens files on double clicking.. ;)

---

### Post by billgoldberg on 2008-05-27
I use bmpx and exaile.

The reasons you are giving for not liking it are a bit trivial, and I think you can even disable that behavior.

---

### Post by sayakb on 2008-05-27
> **Raziel-chan said:**
> In the 0.99 version from Ubuntu's repositories, when I open a file by double-clicking it in konqueror (or selecting 'open with>Banshee') it does indeed open Banshee and play the file, but when I open another file that way when Banshee is still playing, it opens a new instance of Banshee.


Yepp.. confiremed.. opens in the same instance of Banshee for 0.13.2
How did you manage to get 0.99 in the repos. I'm sure you added some 3rd party repository.

---

### Post by Raziel-chan on 2008-05-27
Yyyeah, I mistakenly named 0.13.2 - 0.99. I've used 0.13.2 and that version is always opening a new instance when I open a file from konqueror.
Additionally, it gives me a dbus error on startup - 'dbus is not available'.
The 0.99.2 or 1.0beta gives me no errors, but doesn't even play the file that way. >_>

> I use bmpx and exaile.

The reasons you are giving for not liking it are a bit trivial, and I think you can even disable that behavior. 

Listening to music is trivial - you don't need it to function physically, do you? :3 Music is all about trivial things.
Believe me, if it'd be possible to disable the behaviors I don't like in these players, I would do it. Maybe I missed something. If so, feel free to correct me, I won't mind. :D

Plus, is there even an OSD plugin for banshee?

Currently, Exaile is the closest thing to a perfect player I found. If only I'd know the way to make it remove previous songs from the current playlist when I double-click on a file in konqueror...

cya
Raziel-chan

---

### Post by sayakb on 2008-05-27
I use Banshee because its low on resources :)
Anyway, you should you whatever makes you feel comfortable. 
And regarding your "opens in new instance" problem, it might be because Banshee is designed for Gnome. Though this is a lousy excuse, but this is what it says here:
[ATTACH]71773[/ATTACH] ;)

---

### Post by vishzilla on 2008-05-27
Banshee and Rhythmbox are far the best music players in GNOME. I personally use Rhythmbox

---

### Post by Glucklich on 2008-05-27
> **vishzilla said:**
> Banshee and Rhythmbox are far the best music players in GNOME. I personally use Rhythmbox

+1

---

### Post by Raziel-chan on 2008-05-27
> I use Banshee because its low on resources
Anyway, you should you whatever makes you feel comfortable.
And regarding your "opens in new instance" problem, it might be because Banshee is designed for Gnome. Though this is a lousy excuse, but this is what it says here:

Yeah, I know. I started with Ubuntu and I used Amarok and kTorrent on Gnome without problems... Then I switched to KDE and thought that it would be okay the other way around as well. >_>

As for Rhythmbox, I've tried it at first, but it was stuttering each time the cpu usage spiked, like when doing something else. I may try it again, maybe now it'll be better.

cya
Raziel-chan

Ps. As of now I feel the best using Exaile. It has pretty much everything - low cpu usage, no stuttering, good OSD, buttons in tray and play-the-double-clicked-song-NOW option :3. The only gripe I have about is that I can't seem to find any option for it to simply reset the playlist with each externally-added file (I mean like winamp - you double-click on a file and it removes all the songs from the playlist, leaving only the selected file).

---

### Post by Raziel-chan on 2008-05-27
Agh, more problems...

While all the apps I mentioned are pretty okay in terms of audio quality, the problems start when I want to use the equalizer...

In most cases everything is okay. Unluckily, three apps aren't okay with that.

Audacious, Mplayer and Exaile.

Audacious's built-in equalizer produces horrible distortion unless I set the preamp to almost minimum. It also happens only if the preamp isn't set to low AND any of the other bands are set above the medium value.

Exaile
S.A.A. Only the distortions seem to be more severe and setting preamp down in the setting.ini file doesn't work nearly as well as in Audacious. And even all that only in the BZR version. The normal (stable 2.13) version still produces occasional distortions (directly linked with the percussion in the played song), yet otherwise the equalizer has no effect.

Mplayer seems to be ding a similar thing to what Exaile does.

I've resorted to using the LADSPA equalizer.

cya
Raziel-chan

---

### Post by bbc on 2008-05-28
exaile is swell.

---

### Post by adam_kimber on 2008-05-30
Once you have faffed about with getting MPD to work its great and Sonata is the best little player around. I find Amarok, Rhythmbox etc to be bloated and full of stuff that I will never use.

---

### Post by vprasaj on 2008-06-02
You can lower the CPU usage with changing interpolation engine to ZOH interpolation. On my 3000+ AMD chip it uses 6% minimized to tray and 8% maximized. PulseAudio below 2% in both cases (I use "default-sample-channels=6" in "/etc/pulse/daemon.conf" for 5.1 sound).

For equalizer I use LADSPA plugins. Install packages tap-plugins and fil-plugins. Then you enable LADSPA host (properies->plugins->effects) in audacious. Then hit configure. You will find two equalizers and one 4-band parametric filter(i use this one). Add one or more and than you can adjust it to your needs. It is not hard to do it. Just be careful with gain to avoid clipping. This is from this thread: [CLICK]("http://ubuntuforums.org/showthread.php?t=802131").

---

### Post by praxis_guy on 2008-06-14
agreeing with Raziel-chan.  Rhythmbox gets gittery when i stream radio stations and spends far too much time scanning and re-scanning my music collection (at least i think that's what it's doing).  slowly making the switch to exaile - seems generally more streamlined... but i'll miss the plug in for my mp3 player...

---

### Post by aktiwers on 2008-06-14
I used to use Xmms alot, but now I switched to Quod Libet. Pretty nice player!
The only thing I don't like that much is the search function, but it still gets the job done.

Check out the screenshot:

Edit: it has some nice plugins as well :)

---

### Post by timo1023 on 2008-06-14
Quod Libet can't be beaten when it comes to scanning, updating, and searching extremely large libraries (or just any collection). I'm not sure what the above poster meant when he said the search function was poor; Quod Libet supports regular expressions!

The only downside of Quod Libet is that it is not actively being developed. I'm told that a few changes occur every once and a while, but I wouldn't expect to see cutting edge features with it. Personally, it does everything I need it to.

---

