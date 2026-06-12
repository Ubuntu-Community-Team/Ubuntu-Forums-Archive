---
title: "Exaile, Amarok, and Songbird fail to play music"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-04-28
This is weird. I have Ubuntu 8.04 fresh install. I've installed the ubuntu-restricted-extras.

I've tried Exaile, Amarok, and Songbird. ALL of them fail to play music. But sound works; I just rickrolled myself to test it :P

Exaile and Songbird have the same symptom. The music stays at 0:00 and doesn't move and doesn't play the music.

Amarok stays at 0:00 but after several seconds freezes completely and I have to do xkill to quit out of it, then go to a terminal and do a killall amarokapp to completely get rid of it.

Help! :(

EDIT: Now for some reason Exaile is working... I don't know what's wrong. This is weird. I haven't had a chance to try out Songbird or Exaile extensively but Amarok has this weird thing where it randomly works then if I reboot, it doesn't work.

---

### Post by elmer_42 on 2008-04-28
Are you sure that the file is valid? You may want to take it to another machine and test it out there.

---

### Post by evozniak on 2008-04-28
i dont know the contens of ubuntu-restricted-extras, anyway try to install mp123 and mp321

you listen ubuntu login sound?

---

### Post by akiratheoni on 2008-04-28
> **elmer_42 said:**
> Are you sure that the file is valid? You may want to take it to another machine and test it out there.
Yeah, my edit said that Exaile just started playing one of my songs. Exaile works, Amarok and Songbird still don't. Exaile might decide to stop playing music after I reboot (I don't really want to check... I lieks my music)

> **evozniak said:**
> i dont know the contens of ubuntu-restricted-extras, anyway try to install mp123 and mp321

you listen ubuntu login sound?

I don't have the sound turned on when I log in. But yes, sound works.

What do you mean by mp123 and mp321? They aren't in the repositories...

---

### Post by elmer_42 on 2008-04-28
I know that when I tried to play an MP3 for the first time in Rhythmbox it asked me if I wanted to download MP3 packages. I'm sorry I don't remember what they were, but try to open it in Rhythmbox and see if you get the message I did.

---

### Post by akiratheoni on 2008-04-28
Okay well I did open it up in RhythmBox. It gave me the message about the codecs but when it searched it didn't find anything. I get the same result when I hit Play; the music doesn't play and it stays at 0:00.

---

### Post by enigmaniac23 on 2008-04-29
I don't know if you have the codecs and everything you need installed, but I have had a similar problem twice now.  The first time I thought it was a fluke, but then I saw your thread and experienced the problem a second time.

- All of the proper codecs are installed on my system.  I can play mp3's fine, and watch DVD's with no problem.  

- Then, for some unknown reason, I start to have problems like you described.  I try to play a song, and it will not play.  It just sits at 0:00.  I am trying Amarok, Exaile and Rythmbox.  Today, I noticed that I can also not hear sound on my DVD.  

Amarok showed an error about my audio device being busy, but I can hear system sounds, and when I watch a movie on YouTube, I can hear sound.  

Logging out and back in seems to have resolved it this time, but I'm going to see if I can reproduce this with a certain set of circumstances and post back.  

Please let us know if you have the proper codecs installed and if you have ever been able to playback an mp3 on this installation?

---

### Post by Hamchan on 2008-04-29
I get the same error, but only when Rhapsody is streaming music. I got a package called pulseaudio device chooser that lets me create virtual channels and combine sound which lets several programs use sound at the same time, but it only seems to work for the music programs.

---

### Post by akiratheoni on 2008-04-29
> **enigmaniac23 said:**
> I don't know if you have the codecs and everything you need installed, but I have had a similar problem twice now.  The first time I thought it was a fluke, but then I saw your thread and experienced the problem a second time.

- All of the proper codecs are installed on my system.  I can play mp3's fine, and watch DVD's with no problem.  

- Then, for some unknown reason, I start to have problems like you described.  I try to play a song, and it will not play.  It just sits at 0:00.  I am trying Amarok, Exaile and Rythmbox.  Today, I noticed that I can also not hear sound on my DVD.  

Amarok showed an error about my audio device being busy, but I can hear system sounds, and when I watch a movie on YouTube, I can hear sound.  

Logging out and back in seems to have resolved it this time, but I'm going to see if I can reproduce this with a certain set of circumstances and post back.  

Please let us know if you have the proper codecs installed and if you have ever been able to playback an mp3 on this installation?

Yeah, I have the proper codecs installed -- in fact, I have the ubuntu-restricted-extras, kubuntu-restricted-extras, and the xubuntu-restricted-extras all installed. I HAVE been able to play mp3s and OGGs on my installation but like you it only works sometimes; if I reboot (not sure about log in/out) it either stops working or works.

I'm not at home right now but when I get home I'll test it out a bit more and I'll post back here.

---

