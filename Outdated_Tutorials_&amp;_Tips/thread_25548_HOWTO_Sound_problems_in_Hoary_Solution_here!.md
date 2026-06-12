---
title: "HOWTO: Sound problems in Hoary? Solution here!"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Spif on 2005-04-10
This quick-guide should enable you to hear multiple sounds at once in Hoary and fix a "bug" where only people with OSS output could hear sound in games. 

Fire up a terminal and type

*sudo apt-get install libsdl1.2debian-all*

Universe must be enabled to install this package.

---

### Post by rwabel on 2005-04-10
I've version debian-alsa installed. Which one is the better, or what is the difference.  Multiple sounds is working fine for me. xmms, totem, muine etc all playing sounds at the same time.

But I cannot tell about games.

---

### Post by Joh_ on 2005-04-10
[QUOTE=Spif]This quick-guide should enable you to hear multiple sounds at once in Hoary and fix a "bug" where only people with OSS output could hear sound in games. 

Fire up a terminal and type

*sudo apt-get install libsdl1.2debian-all*

Universe must be enabled to install this package.[/QUOTE]
Doesn't this only install support for all currently supported sound servers with SDL? I don't think this one mixes any sounds, just gives support for sound servers that does.

Only thing I can think of that makes you able to hear multiple sounds by installing this is that you use alot of SDL applications and when you've installed this, SDL starts using esd, arts, or whatever it feels fit, and both esd and arts are software mixers.

This will only apply to SDL applications though. If you're having trouble getting sound to work for all your applications, [read this](http://www.ubuntuforums.org/showpost.php?p=102814&postcount=29), posted by myself. You might not need to do the alsamixer part though, but on some chipsets you apparantly have to, like mine for example.

---

### Post by Thorongil on 2005-04-10
[QUOTE=Joh_]Doesn't this only install support for all currently supported sound servers with SDL? I don't think this one mixes any sounds, just gives support for sound servers that does.

Only thing I can think of that makes you able to hear multiple sounds by installing this is that you use alot of SDL applications and when you've installed this, SDL starts using esd, arts, or whatever it feels fit, and both esd and arts are software mixers.

This will only apply to SDL applications though. If you're having trouble getting sound to work for all your applications, [read this](http://www.ubuntuforums.org/showpost.php?p=102814&postcount=29), posted by myself. You might not need to do the alsamixer part though, but on some chipsets you apparantly have to, like mine for example.[/QUOTE]
 Yeah, seems so, but the "alsa" variant should couple directly with alsa, which usually won't work, if esd and arts are running the same time.

So using the library variant, which uses "any soundserver available" would use a running esd or arts instead of getting blocked by them...

---

### Post by Joh_ on 2005-04-10
[QUOTE=Thorongil]Yeah, seems so, but the "alsa" variant should couple directly with alsa, which usually won't work, if esd and arts are running the same time.

So using the library variant, which uses "any soundserver available" would use a running esd or arts instead of getting blocked by them...[/QUOTE]
This is true but because of my definition of system, this won't let my **system** play multiple sounds, only programs that uses either sdl, esd, arts or another sound server capable of playing multiple sounds. To say your **system** can play multiple sounds, you'd have to be able to play sounds with alsa while both arts and esd are running, maybe even oss using aoss. And that is what I gave a solution for.

Note that this is just my point of view on this and I'm not saying you are wrong, quite the opposite. All I did was give a solution on how to be able to play sounds with alsa while esd is running.

---

### Post by connellr on 2005-04-11
First a little disclaimer -- Im using Kubuntu (KDE), but I believe this information would apply to Gnome also...

I tried both of the above methods as well as the method listed in the Warty forums, and even another method from a Gentu forum.  With all the methods I tried I noticed I was unable to hear system sounds such as the KDE startup sound, error wav, etc. (though I could play music with Kaffene, mPlayer, and XMMS all at the same time).

I found this a little frustrating so I pulled my old SoundBlaster Live 5.1 from my closet, blew the dust off it, threw it into an empty PCI slot, and disabled my onboard sound.  I then set all of my settings back to the default that comes with Ubuntu, and Presto! it worked like a charm (System Sounds, mPlayer, XMMS, kaffene, aplay, etc all playing at the same time!)  

So, hopefully someday all sound cards will support all sounds out of the box, but in the mean time you can avoid a lot of headachs by just getting an old Sound Blaster Live card ($10 on eBay).  No install needed, Ubuntu found and used the card immediatly on boot.  Dare I say "Plug and Play"?

---

### Post by wondering_jew on 2005-04-17
[QUOTE=Spif]This quick-guide should enable you to hear multiple sounds at once in Hoary and fix a "bug" where only people with OSS output could hear sound in games. 

Fire up a terminal and type

*sudo apt-get install libsdl1.2debian-all* [/QUOTE]


Worked perfectly! Thanks for the tip!

---

### Post by henriquemaia on 2005-04-18
[QUOTE=connellr]
So, hopefully someday all sound cards will support all sounds out of the box, but in the mean time you can avoid a lot of headachs by just getting an old Sound Blaster Live card ($10 on eBay).  No install needed, Ubuntu found and used the card immediatly on boot.  Dare I say "Plug and Play"?[/QUOTE]

I have this soundcard too, but the microphone mute doesn't work properly.

The thing is: you press mute on the microphone setup and it doesn't do anything, and this is really annoying, because in Skype (or similar), you have your own sound allways on the verge of making feedback, and, as such, you cannot have a decent volume for the other party.

 Anyone knows how to solve this? (on SoundBlaster Live!) - one solution is to use headphones...

I know that it is possible, as I used SuSE just before Ubuntu and the microphone mute worked flawlessly.

Thanks all.

---

### Post by benplaut on 2005-04-18
[QUOTE=connellr]
So, hopefully someday all sound cards will support all sounds out of the box, but in the mean time you can avoid a lot of headachs by just getting an old Sound Blaster Live card ($10 on eBay).  No install needed, Ubuntu found and used the card immediatly on boot.  Dare I say "Plug and Play"?[/QUOTE]

for those of us with laptops...  :roll:

---

### Post by Toddy on 2005-04-18
[QUOTE=Spif]This quick-guide should enable you to hear multiple sounds at once in Hoary and fix a "bug" where only people with OSS output could hear sound in games. 

Fire up a terminal and type

*sudo apt-get install libsdl1.2debian-all*

Universe must be enabled to install this package.[/QUOTE]

Thanks Spif!  Worked a treat!!  My daughter likes Frozen-Bubble, especially with sound...

---

### Post by rickwood on 2005-05-03
I've got cheap AC97 sound built onto my motherboard.  I followed all of the tips for sound in the ubuntuguide (except unchecking sound for events).  That guide helped significantly.  But it still didn't give me sound in Frozen Bubble.  Only by following this tip did I get sound to play in Frozen Bubble:  

[QUOTE=Spif]This quick-guide should enable you to hear multiple sounds at once in Hoary and fix a "bug" where only people with OSS output could hear sound in games. 

Fire up a terminal and type

*sudo apt-get install libsdl1.2debian-all*

Universe must be enabled to install this package.[/QUOTE]

I now have no sound troubles at all, even with cheap AC97 audio.  And I have sound for system events too.  Thanks for the tip.  This tip should definitely be added to the ubuntuguide.

---

### Post by henriquemaia on 2005-05-03
[QUOTE=henriquemaia]I have this soundcard too, but the microphone mute doesn't work properly.

The thing is: you press mute on the microphone setup and it doesn't do anything, and this is really annoying, because in Skype (or similar), you have your own sound allways on the verge of making feedback, and, as such, you cannot have a decent volume for the other party.

 Anyone knows how to solve this? (on SoundBlaster Live!) - one solution is to use headphones...

I know that it is possible, as I used SuSE just before Ubuntu and the microphone mute worked flawlessly.

Thanks all.[/QUOTE]

Oddly enough, this now is corrected and I don't even know why. I was playing with configuring xinerama and I started a session with two monitors (not xinerama). The sound went mute and I had to find out what happened in gnome-volume-control. PCM was muted, don't know why. When I turned it on, everything was ok and mic mute was working... bizarre.

---

### Post by duk on 2005-05-04
I'm running a HP nc8000 and for some reason gnome hogs the soundcard upon login, I have to run 'fuser -k /dev/dsp' so other programs can use the soundcard. However only one application can use it at one time still, and gnome sounds does'nt work.

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

---

