---
title: "Running Foobar2k uner Wine - How well does it split tracks?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by paker on 2008-08-31
Has Anyone Been Able To Split CD-length FLAC or MP3 To Individual Tracks Using Foobar2000 Under Wine?

I have the specific need of splitting a cd length FLAC to individual tracks. I am using Foobar2000 in wife's Vista laptop. It works beautifully, splitting tracks and transferring tags.

But my main computer is Ubuntu desktop. I tried Foobar2000 under Wine. It runs, but not quite. It fails to split cd-length file to individual tracks. I used the same file, same CUE, same stroke, but on Ubuntu desktop, it just doesn't work. Anyone who has been able to split?
Thanks.

PS: I know I can use line commands in Termical like shnsplint or mp3splt. But I just want to know for sure that in Ubuntu I must use 4 or 5 different programs and line commands to achieve the functionality of Foobar2000 in Windows.

---

### Post by gpilkay on 2008-08-31
I would recommend posting this in the forum's WINE section itself, as you can get a much more informed crowd there.  WINE is very much its own beast (hence its own forum).  Sorry I wasn't much help, I'm not familiar with the setup.

Here's the WINE section!
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Also, nutty as it sounds, the GAMERS section is a great place to find WINE info, as those guys have gotten almost anything to work under it!

---

### Post by paker on 2008-08-31
Thanks. Will post there and mark this thread as SOLVED.

---

### Post by paker on 2008-08-31
> **gpilkay said:**
> I would recommend posting this in the forum's WINE section itself, as you can get a much more informed crowd there.  WINE is very much its own beast (hence its own forum).  Sorry I wasn't much help, I'm not familiar with the setup.

Here's the WINE section!
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Also, nutty as it sounds, the GAMERS section is a great place to find WINE info, as those guys have gotten almost anything to work under it!

THANK YOU for the LINK. It had another link to Hydrogen Audio's how to set up Foobar2000 in Wine. My problem got solved by installing foobar in z:\home\my name\.foobar2000 instead of default c:\windows. Now I have ONE program that meets all my needs.:):):)

---

### Post by billgoldberg on 2008-08-31
There are a thousand and one way to use linux native software to achieve this, why you want to use Wine for this is beyond me.

---

### Post by paker on 2008-09-01
> **billgoldberg said:**
> There are a thousand and one way to use linux native software to achieve this, why you want to use Wine for this is beyond me.
It was a long journey.
I started with Grip to rip cd to mp3. Then I got into flac and needed a  converter from flac to mp3. I posted here. SoundKonverter was recommended. I added SoundKonverter.

Then I got into cd-length flac and cue sheet. I posted here again. Answers were there were no good Ubuntu tools. I googled and found a few line commands that split flac to individual tracks. That's how I got into line commands like shnsplint.

Wait! Tag was missing. I added another line command to transfer tag from cue to mp3. Wait! The line command couldn't handle certain cues.

That's when I gave up all and started to use Foobar2000 and wine. Foobar2k running under wine is not without problems. But at least it provides all the capabilites that I need at the present time.

If you know a better approach, please let me know.

---

### Post by optimix on 2008-09-05
You can use mp3splt-gtk for splitting mp3's. Version 0.5 supports audacious player.

---

