---
title: "only 1 sound input"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Kedster on 2008-05-11
ok lets say when i am watching a you tube vid and i go decide i want to listen to music i have to totally close my youtube vid( the whole internet browser actually even if it were tabbed) then open the music player other wise the music player will not play  and vice-versa with all audio players or whatever

---

### Post by Ptero-4 on 2008-05-11
You need to enable the "multi-stream" support in PulseAudio.

---

### Post by Kedster on 2008-05-11
well ok i dont have accses to my comp right now probly not for the next week 
 its broke 
but how would i do this

---

### Post by Kedster on 2008-05-11
hey any one have any idea how i can do this

---

### Post by Kedster on 2008-05-12
were can i do this

---

### Post by Kedster on 2008-05-12
bump bump please help

---

### Post by inportb on 2008-05-12
btw, PulseAudio is the default audio layer on Ubuntu Hardy. If you're on Gutsy (as your profile indicates), you might need to configure something different. I've always used Kubuntu, so I cannot tell you exactly how to do this.

Also, bumping your thread multiple times a day won't help you get answers any faster.

---

### Post by Kedster on 2008-05-13
sorry about the multiple bumps and sorry that i hadn't changed my profile (i just hadn't remembered that that was a feature on here)so yes i am on hardy but i were do i find "multi-stream" for pulse audio  actually were do i find pulse audio setting n the first place

---

### Post by Awareness on 2008-05-14
Ive got the exact same problem... :/

And even more... coz i dont have sound in several games even tho ive got everything closed...

The only game i have sound is open arena... all the others (thats it nexuiz, urban terror, tremulous alien arena, or wop) no sound at all... 

All the others aplications (thats it, listen to music, web surfing, gaming or watching movies...) just one at a time!

:(

i wonder if its a problem with the configuration or an issue with the sound card...

any help? plz? :)

---

### Post by Awareness on 2008-05-15
Im still trying it out... but [THIS]("http://www.linux.com/feature/119926") should be of some help... i hope i can figure it all out, coz im not really an expert ;> ](*,)](*,)](*,)

---

### Post by jukarnarius on 2008-09-09
So... I don't know is this information steel needed but... I also had the same problems... for exampled I was not able to play the music and do some Skype calls... 

maybe this way works only on my hardware configuration but I use Ubuntu 8.04, 64-bit, on intell chipset p45... also I use GNOM...

you have to do the next:

System -> Preferences -> sound
than choose the 'ALSA- Advanced Linux Architecture'
choose this option wherever it is possible...(and test it of course)

I do not change Default Mixer Tracks,

after that chose subPage 'sounds' and check 'enable software sound mixing (ESD) (maybe this last one do not need but anyway)

I hope this way helps you...

ps pardon for my English...

---

### Post by whitethorn on 2008-09-09
> **jukarnarius said:**
> So... I don't know is this information steel needed but... I also had the same problems... for exampled I was not able to play the music and do some Skype calls... 

maybe this way works only on my hardware configuration but I use Ubuntu 8.04, 64-bit, on intell chipset p45... also I use GNOM...

you have to do the next:

System -> Preferences -> sound
than choose the 'ALSA- Advanced Linux Architecture'
choose this option wherever it is possible...(and test it of course)

I do not change Default Mixer Tracks,

after that chose subPage 'sounds' and check 'enable software sound mixing (ESD) (maybe this last one do not need but anyway)

I hope this way helps you...

ps pardon for my English...

That's not using Pulse audio, that would be using ALSA. A lot of ppl have had a hard time using pulse, since it's pretty new.  It's a new kind of sound server.  It allows you to send multiple streams to it, and it kinda mixes it all together and give it to your sound card.  ALSA only allows 1 stream at a time, which is why pulse audio is useful.  ESD is the old system.  Neway, to get pulse audio to work properly you might want to check out this site first

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

System -> Preferences -> Sound

and set everything in there to PulseAudio except the Default Mixer Tracks Device you should set that to whatever soundcard you are using (usually the Alsa mixer).  That way the programs will be using Pulse, and Pulse will use your sound card.  Kindof like a funnel.  Now since pulse is new there are a bunch of programs which have problems with it, on the website you'll see a list of them with possible work arounds.  The other programs you are using for examble vlc, mplayer, amarok you have to go into the preferences and set the output plugin (you'll usually get a list) set it to Pulseaudio. 

Since some programs don't work with pulseaudio, you can still get them to work using the Alsa mixer (output = alsa) problem is, when you're running them no other sound will work.. 

Hope this helps a bit, and clears up some questions.

---

