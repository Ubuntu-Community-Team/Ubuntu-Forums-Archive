---
title: "Ubuntu 8.04 Several Issues"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by PhysicsNerd on 2008-05-05
I was told that linux is necessary in order to work in a science field, so I had one of the grad students I was working with install Ubuntu 8.04 the day it was released.

But since then I've been having some issues with regular software.  Sometimes the sound will work, and other times it won't, either after I've restarted, or if I start up from sleep.

Also, every time I open one of the 2 media players I have (the one that comes with it and Amarok) the player no longer seems to think my song files exist, and depopulates the playlist.  I'm not sure if this is because they are in folders on the windows part of my machine or not, but I'd rather not have to have 2 copies of all my songs.
Similar to this, sometimes when I try to play movies in Ubuntu there is either no sound again, or the player will open the player, appear as though its about to play the movie, but will just sit at 0:00 without moving.

Any suggestions?  I'm not the most computer knowledgeable person, even in Windows.

Thanks.

---

### Post by mormor on 2008-05-05
The soundproblem is something I have at times, I have tried several guides to rebuilding the alsamixer, but that has not eliminated the problem with sound sometimes(very few) missing after boot. But I can live with that as the reboot-time is so short.

The movie-issue: Have you installed the restricted extra packages so that you have all the avaivable codecs? There should be a multimediaguide on the forum under guides. You can search for 'codec' or 'restricted extra' to find them I think.

With the mediaplayer I cant really help as I no longer have windows.

Sorry if it does not help much. Best of luck.

---

### Post by nowshining on 2008-05-05
have u tried logging out and back in?

anyway about ur songs problem, is ur other parition/hd set-up to start/mount on boot-up? Also u could create a shortcut/system link to the folder :)

---

### Post by PhysicsNerd on 2008-05-06
I haven't tried logging out and in, just restarting, and then sometimes the sound problem persists.  And the song file problem occurs every time I restart anyways.

And I'm not sure how my other partition is set to boot up, not sure how to find that out either.  How do I go about doing this?

---

### Post by peakshysteria on 2008-05-06
Can you tell us a bit more about your setup and specs? Are you using Gnome or Kde? What players are you using? Amarok or Rhythmbox or something entirely different? What graphic card do you have, is the resolution right etc..

Not sure about the sound issue. But i sounds like it's because you are playing files from your windows partition. Meaning the partition mounts when you open your player and then locates the files. You should make the automount at boot.

Try to install Mplayer and/or Vlc player to play your videofiles. This sounds like a codec issue. Mplayer and Vlc can play just about anything you can trow at them. You find them via System --> Administration --> Synaptic. Then search for Mplayer and Vlc and install them. Then tell us how it went.

---

### Post by PhysicsNerd on 2008-05-06
Sorry, I actually don't even know what gnome or kde are...are they different versions of Ubuntu?

My graphics card is a ATI Mobility Radeon HD 2400 XT.  The resolution seems good.

The players I was trying to use were Amarok and Rythmbox, I just couldn't remember the name of Rythmbox before.  How do I make the automount at boot?

I really don't know how to do much beyond completely basic things.

---

### Post by c4v3m4n on 2008-05-06
I'm sorry that you had to get started on 8.04, it's been causing some problems.  I ended up reinstalling gutsy after upgrading to hardy.  Still too many bugs.

---

### Post by kcox5342 on 2008-05-06
> **PhysicsNerd said:**
> Sorry, I actually don't even know what gnome or kde are...are they different versions of Ubuntu?

When I was first learning Linux, it helped immensely to realize that I could look up most of these acronyms on Wikipedia.

Gnome:  [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

KDE:  [http://en.wikipedia.org/wiki/Kde](http://en.wikipedia.org/wiki/Kde)

---

### Post by tjwoosta on 2008-05-06
to solve the music problem you could configure ubuntu to automatically mount the windows partition at boot

here is a link to a post i made a couple of weeks ago  

note: this thread is about making a desktop icon to link to windows partiton, but the part about adding stuff to /etc/fstab is what youl need to make ubutnu automatically mount your windows partition at boot

[http://ubuntuforums.org/showthread.php?t=782363]("http://ubuntuforums.org/showthread.php?t=782363")

---

