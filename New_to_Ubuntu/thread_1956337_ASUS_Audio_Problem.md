---
title: "ASUS Audio Problem"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by baruch60610 on 2012-04-10
I've got an ASUS UL80J laptop running Kubuntu Oneiric.  For some reason, occasionally the sound doesn't work properly.  I'll try to play something and not get the expected music or other sound.  This is after booting up.

Fortunately, I can almost always just go to the KMix audio program and correct the problem.  When I do this, I find that the "Internal Audio Analog Stereo" option is muted, with the sound level all the way down to zero and the sound itself turned off.  Unmuting the sound and then correcting the level is usually all it takes to fix it.

So - what's going on here?  I have tried to figure this out on my own.  I don't see any pattern.  I might not experience this problem for weeks at a time, dozens of reboots.  And then I might get a string of them, or maybe just one here and there.  It doesn't seem to have any connection with any other sound-related activities such as playing videos or music.  It just seems random.

Anyone have any ideas of what's going on, or how to fix this?

---

### Post by Daveth on 2012-04-11
this is sort of related, if only tangentially
[http://ubuntuforums.org/showthread.php?t=1671161](http://ubuntuforums.org/showthread.php?t=1671161)
Might be worth exploring further.

---

### Post by idoitprone on 2012-04-11
maybe this thread may work

[http://www.mp3car.com/linuxice/13839...t-startup.html]("http://www.mp3car.com/linuxice/138398-pulseaudio-defaults-to-mute-at-startup.html")

or this

[http://superuser.com/questions/73401...ots-up-in-mute]("http://superuser.com/questions/73401/ubuntu-boots-up-in-mute")

then try this thread

[http://ubuntuforums.org/showthread.php?t=1145603&page=2](http://ubuntuforums.org/showthread.php?t=1145603&page=2)
problem when ubuntu botch pule audio config

or to remove pulse audio
maybe this will help?

[http://forum.kde.org/viewtopic.php?f=19&t=84411](http://forum.kde.org/viewtopic.php?f=19&t=84411)

---

### Post by baruch60610 on 2012-04-11
@Daveth and @idoitprone:

Thank you both for those links.  I'll check them out.  If I find a solution, I'll post it here and mark this thread "Solved."

Thanks again...

-B

---

### Post by baruch60610 on 2012-04-11
It appears that the solution was to remove pulseaudio from my system.  From the information at [http://forum.kde.org/viewtopic.php?f=19&t=84411](http://forum.kde.org/viewtopic.php?f=19&t=84411), KDE doesn't use pulseaudio and is incompatible with it.

While it is gratifying to finally have a solution to this problem, I am puzzled over why pulseaudio gets installed in the first place, if KDE doesn't use it.  I installed Kubuntu.  I didn't install Ubuntu and then switch to KDE, which would explain the presence of stuff that might no longer be useful.

So why would Kubuntu even install pulseaudio in the first place, if it doesn't use it?

But again thanks to @Daveth and @idoitprone for their helpful suggestions.

---

### Post by idoitprone on 2012-04-12
> **baruch60610 said:**
> It appears that the solution was to remove pulseaudio from my system.  From the information at [http://forum.kde.org/viewtopic.php?f=19&t=84411](http://forum.kde.org/viewtopic.php?f=19&t=84411), KDE doesn't use pulseaudio and is incompatible with it.

While it is gratifying to finally have a solution to this problem, I am puzzled over why pulseaudio gets installed in the first place, if KDE doesn't use it.  I installed Kubuntu.  I didn't install Ubuntu and then switch to KDE, which would explain the presence of stuff that might no longer be useful.

So why would Kubuntu even install pulseaudio in the first place, if it doesn't use it?

But again thanks to @Daveth and @idoitprone for their helpful suggestions.

because alsa is a piece of crp and pulse audio is meant to hide alsa

---

