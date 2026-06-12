---
title: "What media player to use?"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by spa21788 on 2012-08-28
Hello! 

I was wondering if someone could help me choose a media player for ubuntu 12.04. I have tried several and I might just be being picky, but none of them really suit all of my needs (well wants! :P). 

When I used Windows I used winamp for it's playlist options, equaliser, plugins (exfm, song of the day, lost.fm) and general custimisation options.

I have used Rythmbox (of course!)
Pros: 
I love that songs crossfade even when skipped.
I absolutely adore the party mode (F11) option!

Cons:
It might be my own stupidy but I can't seem to get any sort of equaliser
The majority of the plugins in the menu don't seem to work and last.fm(?) only gives a 30 day free trial.


I then switched to Exaile after a forum suggestion.
Pros:
I liked the amount of options available regarding plugins.

Cons:
The vast majority of the plugins are unstable, slow and literally cause the player to freeze for the first 25-40 seconds of every song.
I really disliked the interface.


Last night I moved to Audacious.
Straight to the Cons on this one:
Disliked the interface.
I have a large music collection, 250Gb stored locally, and every time I tried to add my music folder it crashed. 
I added 150 songs from one of my Rythmbox playlists, it played 2 tracks, crashed, I relaunched, it crashed again before playing a complete song, and now crashes between every song change.

Really what I'm asking if anyone can suggest a Rythmbox/Winamp hybrid, or just a media player that avoids as many of the cons listed as possible! 

Thanks!

---

### Post by PhantomTurtle on 2012-08-28
> **spa21788 said:**
> Hello! 

I was wondering if someone could help me choose a media player for ubuntu 12.04. I have tried several and I might just be being picky, but none of them really suit all of my needs (well wants! :P). 

When I used Windows I used winamp for it's playlist options, equaliser, plugins (exfm, song of the day, lost.fm) and general custimisation options.

I have used Rythmbox (of course!)
Pros: 
I love that songs crossfade even when skipped.
I absolutely adore the party mode (F11) option!

Cons:
It might be my own stupidy but I can't seem to get any sort of equaliser
The majority of the plugins in the menu don't seem to work and last.fm(?) only gives a 30 day free trial.


I then switched to Exaile after a forum suggestion.
Pros:
I liked the amount of options available regarding plugins.

Cons:
The vast majority of the plugins are unstable, slow and literally cause the player to freeze for the first 25-40 seconds of every song.
I really disliked the interface.


Last night I moved to Audacious.
Straight to the Cons on this one:
Disliked the interface.
I have a large music collection, 250Gb stored locally, and every time I tried to add my music folder it crashed. 
I added 150 songs from one of my Rythmbox playlists, it played 2 tracks, crashed, I relaunched, it crashed again before playing a complete song, and now crashes between every song change.

Really what I'm asking if anyone can suggest a Rythmbox/Winamp hybrid, or just a media player that avoids as many of the cons listed as possible! 

Thanks!

The music player made by the Elementary OS team, Beatbox has an Equaliser. It also has last.fm scrobbling(not sure if this works because I don't have last.fm). Try Beatbox. You can read about it [here]("http://www.omgubuntu.co.uk/2012/05/beatbox-music-player-sees-new-release-on-ubuntu") and [here]("http://www.omgubuntu.co.uk/2012/05/beatbox-music-player-sees-new-release-on-ubuntu"). That website also has install instructions.

---

### Post by ajgreeny on 2012-08-28
Have a look at vlc to which you can add a multitude of different skins.

However you say that winamp is your choice when using windows, but you don't like the interface of audacious.  Are you aware of the winamp interface for it as shown in my screenshots, and that there are several skins for the winamp interface?  You can either show the player window alone or also the equaliser, and/or the playlist window, as shown.

Have you started audacious from terminal to see if any errors show which could explain the crashes you are getting?  I find audacious very good; it's simple, small resource requirement, and so far for me, never lets me down.

---

### Post by d4m1r on 2012-08-28
Have you tried;

1) VLC
2) Rythembox
3) Clementine

?

---

### Post by GreatDanton on 2012-08-28
+1 for VLC.

Nobody mentioned Amarok :D

Regards.

---

### Post by AlanR8 on 2012-08-28
VLC for video and Clementine for music.

All that you need!!!

---

### Post by RedRat on 2012-08-28
I use VLC for video and Audacious for my mp3 collection and have not have any of the problems that you describe.

A word of caution: I found that Amarok, for some unknown reason, cannot get out of mute, it will not speak to my speaker outputs (speaker or headphone jacks), same goes for Guyadeque. Have not tried Clementine. 

I access my music collection stored on a USB attached FreeAgent 1.5 Tb NTFS drive, the music collection is in excess of 50Gb. I am running Ubuntu 12.04 using the Gnome Classic interface (don't think the interface, e.g., Unity, makes any difference, but offered for what it's worth).

---

### Post by Frogs Hair on 2012-08-28
System wide EQ:[http://askubuntu.com/questions/72679/is-there-any-sound-enhancers-equalizer](http://askubuntu.com/questions/72679/is-there-any-sound-enhancers-equalizer)

---

### Post by Raphicerus on 2012-08-28
Another good thread. I'm not sure I like RhythmBox either, so will be watching this with interest.

---

### Post by edeneen on 2012-08-28
> **GreatDanton said:**
> +1 for VLC.

Nobody mentioned Amarok :D

Regards.

I like how Amarok displays the lyrics to almost any song

---

### Post by GreatDanton on 2012-08-29
I just tested Clementine. It contains equalizer, and it looks good. 

Regards.

---

### Post by TheFusionIcon on 2012-08-29
MPlayer is a solid choice too. I believe it is in the Ubuntu repositories by default.

If you are using Ubuntu, this command should get you setup:

sudo apt-get install gnome-mplayer

---

### Post by SeijiSensei on 2012-08-29
> **TheFusionIcon said:**
> MPlayer is a solid choice too. I believe it is in the Ubuntu repositories by default.

If you are using Ubuntu, this command should get you setup:

sudo apt-get install gnome-mplayer

I recommend [SMPlayer]("http://smplayer.sourceforge.net/") as a GUI front-end for mplayer, especially for watching videos.  It gives you access to most of mplayer's commands and configuration options, and you can add any other ones you need in the configuration dialogs.  It's especially good with Matroska files with multiple audio and subtitle streams.  The "S" in "SMPlayer" actually refers to its handling of subtitles.  You can install it from the repositories.

---

### Post by sid0972 on 2012-08-29
> **edeneen said:**
> I like how Amarok displays the lyrics to almost any song

and wikipedia information too
those are the main reasons i switched to amarok
only thing is its heavy
how is audacious?

---

### Post by Rob Sayer on 2012-08-30
Another vote for smplayer for video.  It's played files for me that vlc (whose reputation as the "play anything" program is a bit overrated) won't.  The reverse has only happened once.

Smplayer also has the best video filters I've ever seen.  They're pretty intuitive ... I've never missed the nonexistent docs ... and extremely useful.  I use the dithering ("add noise") all the time with lower bit rate video.  Why the hell does every video player not have this?

vlc makes a pretty good audio player ... the playlist is very good, it lets me organize it the way I want to do it ... but I've found the output configuration buggy.

Finding an audio player has been harder because they're so damn many of them.  It seems like some linux geek puts out a new one every 3 or 4 days.  And most of them aren't impressive.

I've settled on clementine too though.  It has just as good playlist features as vlc if not better.  I absolutely need good playlist tree support and it has it.

Plus, on my 12.04 setup clementine with the output module set to ALSA sounds *awesome*.  Best I've ever heard.

---

### Post by brw on 2012-08-30
> **alanr8 said:**
> vlc for video and clementine for music.

All that you need!!!

+1

---

### Post by eldudorinio on 2012-08-30
I'm also currently in the search for the media player to use. Mostly for the music part.

So far tested:

[LIST=1]
[*]Amarok: Really like it. Been using it a lot in the past in   Ubuntu and other KDE distros. Only problem is that I also find it a bit heavy, since my machine is old. I have read that is runs a lot better on KDE.

[*]Banshee: I have read really good stuff about this player. I used it for a few hours and experienced a few crashes :( It has lot's of plugins as well so it can become heavy as well.

[*]Clementine: Really love the old Amarok look that they are using. Seems a lot lighter than Amarok as well and is pretty much fully equipped.

[*]Exaile : This is what I am currently using. A lot simpler than all the above but works fater than the above, so far. I seems to be using a lot of memory (583MB at the moment). Don't know if it's because I have my entire library in a single playlist.

[*]Audacious : It seems very light and quick, but haven't played with it a lot yet.
[/LIST]

Has anyone else had experience with Clementine and large music libraries/playlists? I'm talking about a library of about 32k songs.

---

