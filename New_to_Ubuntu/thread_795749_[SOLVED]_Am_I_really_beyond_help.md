---
title: "[SOLVED] Am I really beyond help?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by volkswagner on 2008-05-15
First let me apologize for posting here, and multi posting.  I have been using Ubuntu for about a year.  This is my first linux experience.

I have posted my audio problems in mythbuntu, and multimedia forums.  I am trying to learn so I don't see the value in reinstalling when there is a problem.

I have altered so many files and configurations with the same result.  I have unanswered thread here.

[http://ubuntuforums.org/showthread.php?t=787317]("http://ubuntuforums.org/showthread.php?t=787317")



Just talking to myself here.
[http://ubuntuforums.org/showthread.php?t=771281]("http://ubuntuforums.org/showthread.php?t=771281")

I have had a lot of lookers but little help here.

[http://ubuntuforums.org/showthread.php?t=753433]("http://ubuntuforums.org/showthread.php?t=753433")

To summarize I have sound problems playing multichannel content. 

Mythbuntu 7.10AMD64 with all updates including mythtv .21.  This is my master backend which had working SPDIF passthrough working via optical out onboard ATI HDA SB.

Mythbuntu 7.10 i386 with all updates including mythtv .21 no longer plays HD recordings.  This includes via backend and recorded locally on Kworld 110.  I can usually play live TV via local Kworld 110, and via backend firewire SA3250HD.  The recordings get nvp pauses and create unwatchable sound and video jerks/freezes.  Oddly the live HD tv get buffer underrun errors but plays well.

I have frontend installed and laptop running UUE 1.6, mythtv .21 which exhibits same problem.  I can usually watch live HD tv, but not prerecorded.

I have tried the 8.04 live cd as a frontend with similar results.  

Just today I tried MythTV media player for windows.  I ran this on my windows MCE 2005 box.  Low and behold I can watch live HD, and pre recorded without issue.  I will need to see how to get logs in this player.

Long wind.
Anyone willing to contribute?

My feeling is Alsa updates are possible cause.  Or there is a problem with mythtv .21

---

### Post by billgoldberg on 2008-05-15
> **volkswagner said:**
> First let me apologize for posting here, and multi posting.  I have been using Ubuntu for about a year.  This is my first linux experience.

I have posted my audio problems in mythbuntu, and multimedia forums.  I am trying to learn so I don't see the value in reinstalling when there is a problem.

I have altered so many files and configurations with the same result.  I have unanswered thread here.

[http://ubuntuforums.org/showthread.php?t=787317]("http://ubuntuforums.org/showthread.php?t=787317")



Just talking to myself here.
[http://ubuntuforums.org/showthread.php?t=771281]("http://ubuntuforums.org/showthread.php?t=771281")

I have had a lot of lookers but little help here.

[http://ubuntuforums.org/showthread.php?t=753433]("http://ubuntuforums.org/showthread.php?t=753433")

To summarize I have sound problems playing multichannel content. 

Mythbuntu 7.10AMD64 with all updates including mythtv .21.  This is my master backend which had working SPDIF passthrough working via optical out onboard ATI HDA SB.

Mythbuntu 7.10 i386 with all updates including mythtv .21 no longer plays HD recordings.  This includes via backend and recorded locally on Kworld 110.  I can usually play live TV via local Kworld 110, and via backend firewire SA3250HD.  The recordings get nvp pauses and create unwatchable sound and video jerks/freezes.  Oddly the live HD tv get buffer underrun errors but plays well.

I have frontend installed and laptop running UUE 1.6, mythtv .21 which exhibits same problem.  I can usually watch live HD tv, but not prerecorded.

I have tried the 8.04 live cd as a frontend with similar results.  

Just today I tried MythTV media player for windows.  I ran this on my windows MCE 2005 box.  Low and behold I can watch live HD, and pre recorded without issue.  I will need to see how to get logs in this player.

Long wind.
Anyone willing to contribute?

My feeling is Alsa updates are possible cause.  Or there is a problem with mythtv .21

There is a way to roll back updates if I am correct (google is your friend).

Now on a long shot, have you tried pulseaudio instead of alsa *(in theory it's a lot better than alsa, but it's still setting it first steps)*.

I'm not skilled enough on the subject to give further advice.

---

### Post by volkswagner on 2008-05-16
It seems I would need apps installed to roll back updates.

I will give pulse a try.  It does not look promising as others running 8.04 have had trouble with HDA sound.

---

### Post by dca on 2008-05-16
Not that I'll be any help but what codecs are req'd to display HD broadcasting?  If Windows is able to play it but Mythbuntu can not, that's where I'd start my search.  The only way to guarantee (which would end up being a time waster) is to install and alternative to Mythbuntu like Mythdora or SuSE's version of it to confirm...

---

### Post by volkswagner on 2008-08-03
Finally got it sorted.

[http://ubuntuforums.org/showthread.php?p=5516332#post5516332]("http://ubuntuforums.org/showthread.php?p=5516332#post5516332")

---

### Post by anewguy on 2008-08-03
Glad you got things going.  Be forewarned I'm not here with any advice, rather just a little fun.

Going from your thread title, and from what you seem to know and getting your problem fixed, I think the answer to the question is "NO, your NOT beyond help by a long way!".

And, I speak from experience being someone who IS beyond help!!  :):)

---

