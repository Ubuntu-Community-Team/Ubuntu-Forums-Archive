---
title: "Ubuntu Hardy and a few beginner issues..."
date: 2008-10-07
forum: New to Ubuntu
---

### Post by night-wing on 2008-10-07
Hello.
I just came to Ubuntu after using Mandriva for about two years.
But do not misunderstand - I still feel as a beginner, because I only used it - not often worked in the console. Because I do not have any experiences with debian based distros and some of the things are going another way as in mandriva, I have some questions and hope, you may help me here. 

First, my machine is an
HP Notebook Pavilion dv9805 (17", NVIDIA 8400G Video card) with
and AMD X2 Chip with 2,1 GHz. Audio card is an conexant chip.

I use the 32Bit - Ubuntu (should this be a fault?).

My issues are:
- Sound is working, both in the game, I tested (openarena) and
  playing mp3s. But what I do not have is system sound (startup,
  shutdown and so on.) But I have playable wav-Files on the pc
  and have assigned it in the Audio-Preferences. Why doesn't play
  it Ubuntu? Mandriva also used pulseaudio and all worked fine.
- Often, when I start openarena, the sound crackles
  (not every time). As I read here in the community, this may be
  a pulseaudio issue. Is there a way to get it fixed. 
- Is there a legal (!) way to play DVDs? I heard, this libdvd...
  is not allowed (maybe only here in germany). Does anyone have
  some experiences with this powerdvd, which canonical offers in
  the ubuntu online shop?

Regards
nightwing
from germany

---

### Post by Thelasko on 2008-10-07
> **night-wing said:**
> 
- Sound is working, both in the game, I tested (openarena) and
  playing mp3s. But what I do not have is system sound (startup,
  shutdown and so on.) But I have playable wav-Files on the pc
  and have assigned it in the Audio-Preferences. Why doesn't play
  it Ubuntu? Mandriva also used pulseaudio and all worked fine.

The startup sounds are played in a program called [aplay]("http://en.wikipedia.org/wiki/Aplay")(at least they were in Gusty).  Check to see if aplay can play your soundfiles.

---

### Post by billgoldberg on 2008-10-07
Don't worry about the dvd codecs.

I'm pretty sure they are legal in Germany.

If you need a push in the right direction, think "medibuntu" repository.

If the German authorities are only going after illegal file sharers when exceeding 250gb of uploaded files, I'm pretty sure that if it should be illegal to use those codecs, nobody will care. Not even the authorities. That is **if** it is illegal, which I doubt.
--

I heared powerdvd is great on Windows, so I assume it will be pretty good on Linux as well.

--

If you are having problems with PulseAudio, it's extremely easy to switch to ALSA.

The implementation of PulseAudio is Hardy Heron is a bit shaky.

It's much better in Intrepid Ibex (beta).

---

### Post by night-wing on 2008-10-07
> **Thelasko said:**
> The startup sounds are played in a program called [aplay]("http://en.wikipedia.org/wiki/Aplay")(at least they were in Gusty).  Check to see if aplay can play your soundfiles.

I'll check this out today evening (I am still at work) and give your reply. Thanks.

---

### Post by night-wing on 2008-10-07
> **billgoldberg said:**
> If you are having problems with PulseAudio, it's extremely easy to switch to ALSA.

The implementation of PulseAudio is Hardy Heron is a bit shaky.

It's much better in Intrepid Ibex (beta).

How can I switch to alsa? And... why is it that shaky in hardy? In fedora and mandriva it already works well.

---

### Post by night-wing on 2008-10-07
The command line tool   aplay  plays my sounds without problems!

---

### Post by Thelasko on 2008-10-07
> **night-wing said:**
> The command line tool   aplay  plays my sounds without problems!

That rules out a few things.

---

### Post by Thelasko on 2008-10-07
When you changed it, did you use System>Preferences>Sound in the menu?

From there you should be able to test all of you settings, and select your sound files and test them.

---

### Post by night-wing on 2008-10-08
> **Thelasko said:**
> When you changed it, did you use System>Preferences>Sound in the menu?

From there you should be able to test all of you settings, and select your sound files and test them.

Yes, the sound works there perfect. But when the event appears, on which the sound should be played (startup, shutdown, button click...), no sound plays...

---

### Post by night-wing on 2008-10-08
bump

---

### Post by Thelasko on 2008-10-08
The only thing I can think of is that it might be a permissions issue.  Make sure the permissions for that sound file allow all users to read it.

---

### Post by night-wing on 2008-10-09
permissions were ok. Meanwhile I do have sound, but only the same one nevertheless I assingned others to other system events. Startup and Shutdown ist still without sound...

---

### Post by WWSmith36 on 2008-10-09
The implementation of Pulse Audio is a little shaky in Hardy.  You could try setting the sound from auto-detect to ALSA.  BTW are there any other sound issues - can you listen to mp3 while playing OA?

---

### Post by night-wing on 2008-10-09
Hello.

No, I can't hear mp3 parallel. But I never wanted to do so. And I already have changed in the menu from auto detection to also. It makes no difference.

---

