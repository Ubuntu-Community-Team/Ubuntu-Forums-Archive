---
title: "So, I'd like it laid out for me. Multimedia Codecs."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Roasted on 2008-07-10
For full blown around the globe support of audio/video codecs and multimedia, I'm trying to establish a list of things that I should install.

Now, granted, I'm not completely new to Ubuntu, in fact I've used it for about 3 years. But I've never really taken the time to figure out EXACTLY what is needed. I always just added stuff until things worked and that was it.

Is this all that is needed for full blown dvd playback/audio/video support?

Medibuntu Repository - (medibuntu.org, followed the install guide)
Ubuntu Restricted Extras - (add-remove programs, selected all available programs)
GStreamer Plugins - (add-remove programs, selected all available programs)
Libdvdcss2 - (terminal, apt-get)
w64codecs - (terminal, apt-get... for 64 bit systems)
Flash

Is that all that is needed? That's all I installed and everything seems to work, but like I said, I just want to get down an actual list I can refer to so I can just... BAM BAM BAM, done.

---

### Post by tjwoosta on 2008-07-10
> Medibuntu Repository - (medibuntu.org, followed the install guide)
Ubuntu Restricted Extras - (add-remove programs, selected all available programs)
GStreamer Plugins - (add-remove programs, selected all available programs)
Libdvdcss2 - (terminal, apt-get)
w64codecs - (terminal, apt-get... for 64 bit systems)
Flash

i think you nailed this one


thats everything i installed and i have never found any legit media that i cant play

---

### Post by Roasted on 2008-07-10
The one thing I question is, I was watching an embedded video somewhere... and the audio was out of sync with video. Not badly, but enough to notice. I wish I could find that site again and track down what kind of player they used and what codecs I should look at... 

But in reality, it's not a big deal. 99% of what I watch is flash based, which flash is always in sync for me. This other video was definitely not flash...

---

### Post by Dynaflow on 2008-07-10
I usually use [this stickied thread]("http://ubuntuforums.org/showthread.php?t=766683") as my bam-bam-bam list when I'm setting up a newly Ubuntu'ized machine.  

You already seem to be covering most everything, but I would personally replace the Java that comes with the restricted extras with the Sun version.

---

### Post by swisscow on 2008-07-10
> **Dynaflow said:**
> I usually use [this stickied thread]("http://ubuntuforums.org/showthread.php?t=766683") as my bam-bam-bam list when I'm setting up a newly Ubuntu'ized machine.  

You already seem to be covering most everything, but I would personally replace the Java that comes with the restricted extras with the Sun version.

This thread is the dogs danglies (sorry, English colloquialism for great) with multimedia stuff.

---

### Post by wolfen69 on 2008-07-10
i have my own computer business. my sit has to work. you can listen to me, or be a fool. after i install, remove totem. every instance of it. do the medibuntu repo thing. download mozilla-mplayer and vlc. then libdvdcss2. you're done. why does this work on every computer? because im good. it's that simple.

for lessons on how to uninstall totem, add medibuntu, ask someone who cares.

---

### Post by Bigtime_Scrub on 2008-07-10
> **Dynaflow said:**
> I usually use [this stickied thread]("http://ubuntuforums.org/showthread.php?t=766683") as my bam-bam-bam list when I'm setting up a newly Ubuntu'ized machine.  

You already seem to be covering most everything, but I would personally replace the Java that comes with the restricted extras with the Sun version.

I follow that stickied thread religiously on new installs and I have never had any problem with media. 

Also, i don't mean to highjack the thread so please excuse me, but what is a 'dogs danglies'?? I have to say, I've never heard that one.

---

### Post by DezSP on 2008-07-10
> **Bigtime_Scrub said:**
> I follow that stickied thread religiously on new installs and I have never had any problem with media. 

Also, i don't mean to highjack the thread so please excuse me, but what is a 'dogs danglies'?? I have to say, I've never heard that one.

[http://en.wikipedia.org/wiki/List_of_British_words_not_widely_used_in_the_United_States#D](http://en.wikipedia.org/wiki/List_of_British_words_not_widely_used_in_the_United_States#D)

:)

---

### Post by swisscow on 2008-07-10
> **DezSP said:**
> [http://en.wikipedia.org/wiki/List_of_British_words_not_widely_used_in_the_United_States#D](http://en.wikipedia.org/wiki/List_of_British_words_not_widely_used_in_the_United_States#D)

:)

Thanks - been at work not had a chance to explain. Dogs ******** is a good one as well, not heard of the mutts nuts!

---

### Post by Roasted on 2008-07-10
Sweet deal. Thanks guys.

Question, though - I was dealing with scratchy audio before. It was pretty bad. I got fed up, formatted, fresh install, followed this guide, everything is perfect now. Great!

But I question one thing.. when you guys crank the volume on the applications you use for video/music, does your sound quality get real staticy? 

Audacious does a great job of avoiding this. I cranked the onboard program volume level to 100% and it was still clear.

Amarok and VLC got insanely distorted when I cranked their volume. However, if I keep their onboard volume at the default level (or a little less... VLC = 50%, Amarok = 80%) and just crank my system volume, it doesn't distort then. So I guess it's program related...

Just curious if anybody else noticed this.

---

### Post by sydbat on 2008-07-10
Not yet. I have Amarok, VLC, etc all cranked to 100% and they are all clear. Might be you sound card?

---

### Post by Roasted on 2008-07-10
Do you have speaker levels and system volume levels all cranked too?

I can crank all levels to 100% and get great feedback, EXCEPT VLC and Amarok's onboard volume controller. That I have to keep low.

The reason I thought it was program related was because, VLC in Win XP Pro on my laptop... it does the same exact thing my desktop does in VLC on Ubuntu Hardy 64.

My sound card is onboard. MSI K8N Neo4 Platinum motherboard. About 3 years old.

EDIT - so I logged into Win XP Pro on my desktop and loaded VLC. I only use XP for getting on games. The second I quit a game, I reboot to Ubuntu, so I never had anything set up. I set up VLC and played an mp3 through it... in fact, the same mp3 that I tested on Ubuntu. At 100%, I had scratchy audio at VERY high notes and if my volume was absolutely maxed. However, VLC performed a bit better in terms of higher volume and clarity in XP than Ubuntu. Not by much, but enough to be noticable.

Is there any way I can even these two up? I obviously have all of the latest codecs and medibuntu package and stuff. Am I just stuck with what I got? Perhaps a new sound card?

---

### Post by DezSP on 2008-07-11
Essentially your sound card is receiving signals that are too loud for it to deal with, so it clips them and you receive distortion. Either keep the levels down low or buy a better soundcard...

---

### Post by Zack McCool on 2008-07-11
> **Roasted said:**
> 
Amarok and VLC got insanely distorted when I cranked their volume. However, if I keep their onboard volume at the default level (or a little less... VLC = 50%, Amarok = 80%) and just crank my system volume, it doesn't distort then. So I guess it's program related...

Just curious if anybody else noticed this.

I don't have an issue with either of these apps on my Desktop or Laptop.

---

### Post by Roasted on 2008-07-11
> **DezSP said:**
> Essentially your sound card is receiving signals that are too loud for it to deal with, so it clips them and you receive distortion. Either keep the levels down low or buy a better soundcard...

Do you think even a 30 dollar soundcard would be a significant enough difference to justify it over my current onboard card?

---

### Post by DezSP on 2008-07-11
That really depends on the quality of the on-board one. Any idea what it is?

---

### Post by Roasted on 2008-07-11
> **DezSP said:**
> That really depends on the quality of the on-board one. Any idea what it is?

Not really... I mean, it was an 80 dollar motherboard 3 years ago. Socket 939, single core AMD 64 bit... I can't imagine it SUCKS, but I also can't imagine it's worth much of anything in comparison to today's cards either... I'd just like to know if it'd be a wise upgrade...

---

### Post by Roasted on 2008-07-12
Is there a reason why every time I open a song in audacious or something, if I check my PCM level, it's maxed?

I'd like to set the default lower so I don't have to deal with hearing the crappy audio. It sounds great if I have it down a bit.

If you look at the settings in alsamixer (terminal) it sounds best if I have 1 red spot or less (in the green) for PCM.

Considering on looking at a decent PCI sound card...

edit - my motherboard has this onboard sound card. RealTek ALC850.

---

### Post by DezSP on 2008-07-12
RealTek cards tend to be low-end solutions, so I'd say it'd most likely be beaten by a half-decent offering from Creative.

---

