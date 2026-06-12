---
title: "Some questions about Ubuntu audio"
date: 2009-08-20
forum: Recurring Discussions
---

### Post by bostonjoe311 on 2009-08-20
Linux is lacking in the everyday user department, especially audio and video.  I have no problem with the professional applications, i.e. Perl, Java, MySQL, Office, etc., but I think programs aimed at the average user pale in comparison to Windows.  My beef today is with audio software (I solved my video problems by switching to Nvidia).

In particular, I am looking for a TOTAL Winamp replacement, not just a simple clone like audacious.  So if someone could point out 1 audio player that has ALL of the following properties that would be awesome.

1. Playlist generator by acoustic fingerprint
2. Media library layout similar to Winamp/Rhythmbox, especially feature that list the number of tracks per artist, album, etc.
3. Plugins for the headphone user that make the sound more ambient
4. Online radio
5. Ability to read flash drives (not mp3 players) within the audio player

---

### Post by shiggydiggy on 2009-08-20
have you tried songbird?
[http://getsongbird.com/](http://getsongbird.com/)

---

### Post by CatKiller on 2009-08-20
> **bostonjoe311 said:**
> Linux is severly lacking...

Don't use it, then. No one's forcing you.

Sheesh...

> 
1. Playlist generator by acoustic fingerprint
2. Media library layout similar to Winamp/Rhythmbox, especially feature that list the number of tracks per artist, album, etc.
3. Plugins for the headphone user that make the sound more ambient
4. Online radio
5. Ability to read flash drives (not mp3 players) within the audio player1. I'm not entirely sure what you mean by that. Banshee and Listen will both construct their playlists around similar songs, although I don't know the mechanism by which they do so.
2. Meh. Most interfaces are customisable. And when I last used Winamp (a looong time ago) it looked nothing like Rhythmbox. Pick one you like the look of.
3. Some media players will let you change the audio stream themselves, but that's probably something that you'd be best off doing at a lower level. Any audio system that lets you manage streams (JACK, PulseAudio) can be routed through any arbitrary LADSPA plugin. It gives you the feature (should you want it) that all headphone audio gets some reverb, while the speaker output is unmolested. But I like fiddling, and I'm a sound engineer, so I probably don't find that as intimidating a prospect as many people might.
4. That's pretty much all of them. And if you have a URL for the stream you can manipulate it how you want with something like MPlayer.
5. That would be all of them. Flash drives will be mounted, so that you can access the files. Which means they're in the filesystem, the same as any other file that you might use. Probably under /media.

FWIW, I currently use Amarok and like it very much. I've previously used Rhythmbox, Banshee and Listen, and I liked all of those too. I absolutely detested the look of Winamp when I used it, which means that I pretty much detested the look of XMMS too. You might like it, though. Some people like Songbird, but I've never tried it.

---

### Post by bostonjoe311 on 2009-08-20
Hey, Catkiller, thanks for the quick reply.  By the way, the thread title was just bait.  Too be honest I am quite satisfied with Linux.  I use all those programs I listed, but like to listen to music on my headphones while I use them.  Rhythmbox is my current audio player, but I think it is a bit lacking and a little too simple.

Amarok, which I downloaded last night, seems to be close to what I am looking for, but I have a couple of questions.  First can you set it up to list the number of tracks?  Second, can you point me in the right direction to setup my headphones for "binaural-like" listening?  Thanks for all you help.

---

### Post by llamabr on 2009-08-20
Ya, I don't understand most of your requests either, but I've never found anything mplayer can't do that I want it to do.  Also look at vlc, if you havn't.  And then xine.

---

### Post by arvevans on 2009-08-20
Don't feed the self-admitted troll.  He is just wasting your time and energy.  Some people get a perverse type of satisfaction from baiting others into a response.

---

### Post by bostonjoe311 on 2009-08-21
I don't think I'm a troll.  I have legitimate questions that I need help with, which I have posted once before but passed without reply.  Maybe you could help me out.  I am especially interested in plugins that improve the headphone experience since that is mostly how I listen to music.  Anything would be appreciated.

---

### Post by cabrey on 2009-08-21
How about XMMS? I haven't used it myself, but a lot of what you would call advanced Linux users like it.

---

### Post by CatKiller on 2009-08-21
> **bostonjoe311 said:**
>  Amarok, which I downloaded last night, seems to be close to what I am looking for, but I have a couple of questions.  First can you set it up to list the number of tracks? 

In which section? The Collection, Playlist and Now Playing sections can all be configured to display different things. Also, there was a big interface overhaul between 1.4 and 2.0, so some things will be different.

> Second, can you point me in the right direction to setup my headphones for "binaural-like" listening?Ah, you got me :) I've only personally done it temporarily with JACK when playing with multitrack stuff (which generally supports JACK natively). That's pretty trivial; you load up something like JACK Rack to manage the effects that you want and simply use JACK's Connections window to connect whichever JACK device is making the sound that you want to modify to JACK Rack.

Unfortunately, I don't know how to make Ubuntu use JACK system-wide, and I don't think many of the media player applications use JACK natively. I'm pretty sure that you can get Ubuntu to use JACK for all sounds, I just don't know how. If you can find that step out, you can use the easy procedure I outlined above. JACK is pretty sweet for arbitrary connections, and there's lots of tools to connect JACK clients to LADSPA effects because if you're using JACK then it's probably because you're doing audio production and having lots of effects available is what you want.

Otherwise, you're using PulseAudio. This is quite easy to set up (you're probably using it now, since it's installed by default). Any (sensible) application will work with PulseAudio, because it can pretend to be OSS or ALSA as far as any application is concerned. PulseAudio is also quite powerful, but - partly because it's new and partly because people that want effects are already using JACK - I haven't yet spotted anything graphical that lets you route PulseAudio streams through LADSPA effects. It's still possible but, as far as I can tell, it involves editing your ~/.asoundrc to add an ALSA device that has the effect added, or loading a module in ~/.pulse/default.pa. Once you've got your effects set up, you can move an audio stream from one sink to another with the PulseAudio Volume control. Unfortunately, either of these edits are black arts that I haven't learned yet.

Actually, I've just learned of the existence of the PulseAudio modules module-jack-sink and module-jack-source that let you use PulseAudio with JACK. I haven't tried them yet, but if you can get those to work, all the PulseAudio stuff will be routable through JACK, so you can use something like JACK Rack to get the effects that you want. I think.

---

### Post by bostonjoe311 on 2009-08-21
I downloaded songbird last night at shiggydiggy's suggestion, and I must say I was quite impressed.  It looks really cool.  As for the sound plugin, I will take your suggestion catkiller, and try to setup JACK.  It seems a bit daunting right now, but I think I can get it.  Thanks.

---

### Post by greg.9 on 2009-08-21
The reason they are different is the essence and the beauty of linux and a distro like ubuntu, it is because they are FREE for all and largely contributed and maintained by fellow users. Things take a bit more effort and commitment to get the best out of your system with linux. If you want 'out of the box' whistles and bells then pay microsoft £150 for your OS and then more for each piece of software you add.
Stick with it and you will find you dont miss MS at all.

---

### Post by SunnyRabbiera on 2009-08-21
Running Winamp under wine also works.
But truth be told I think winamp is dead, plenty of other multimedia players have surpassed it in my opinion.
I suggest you also try exaile.

---

