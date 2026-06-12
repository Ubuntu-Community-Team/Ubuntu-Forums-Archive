---
title: "[SOLVED] Last.fm: The ALSA soundsystem is either busy or not present."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by bhadotia on 2008-08-01
The Last.fm software used to work fine when I first installed it but now it seems to be having some problem - may be because of something I did. I sometimes get the error message in the title and sometimes it works fine .
What could be wrong ? Any suggestions?


Many thanks in advance!

---

### Post by bhadotia on 2008-08-01
Also I recently noticed that the 'system sounds' I enabled in System>Preferences>sound are also not working.

---

### Post by bhadotia on 2008-08-01
Found the solution on this [thread]("http://ubuntuforums.org/showthread.php?p=5356294"). Sorry , I should have tried a google search before posting here:)

---

### Post by bhadotia on 2008-09-04
Although its got the last fm to play if another music player is also running ; but I've completely lost sound in flash (youtube videos). So I had to delete the configuration file to get the sound back in flashplayer.

But the problem still remains lastfm player  (or any other player using alsa) cannot play while another similar player is also running.

I'm also  gonna post in the original post above now to see if I come upwith some solution.

---

### Post by bhadotia on 2008-09-19
Alright, as no replies are coming I guess I will have to mark  the thread as solved (even though we have not solved it:)).

---

### Post by nowshining on 2008-09-19
i would of helped but u don't have KDE am i correct?? if you had kde I would of shown you a solution. :)

---

### Post by bhadotia on 2008-09-20
> **nowshining said:**
> i would of helped but u don't have KDE am i correct?? if you had kde I would of shown you a solution. :)
Actually I have got KDE 4.1 from the launchpad repos. So if you can really help please do so :-)

P.S.: Marking the thread as unsolved now:popcorn:

---

### Post by Qinjuehang on 2008-09-20
Try launching Last.fm in terminal, and placing pasuspender in front of it.
```
pasuspender lastfm
```

---

### Post by bhadotia on 2008-09-20
> **Qinjuehang said:**
> Try launching Last.fm in terminal, and placing pasuspender in front of it.
```
pasuspender lastfm
```
Actually I'm now giving up on lastfm. I think we should better leave it to the developers to solve the bug.

I an still listen to lastfm through rhythmbox and amarok ; the only reason I wanted lastfm to work flawlessly was that it had a nice look and this error just spoiled all the fun.

Still thanks or the replies:popcorn:

Marking the thread as solved now:)

---

