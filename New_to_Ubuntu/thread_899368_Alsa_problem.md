---
title: "Alsa problem"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by hofa on 2008-08-24
I have a problem with my ALSA server.
I can only get sounds to work from one application at a time.

example:
When I'm listening to music with MPD and I want to watch something on youtube. I first have to stop mpd, restart firefox, go to the page and only then I get the sound. Also I have twhirl (Adobe Air alpha app) on all of the time and it uses ALSA too. So when I want to listen to MPD, I first have to shut down twhirl, restart MPD and start twhirl again...

Anyone know how to fix this problem?

Also: Didn't they say that Hardy Heron would come with PulseAudio?

---

### Post by linux6994 on 2008-08-24
I have found that vlc works great for everything.

---

### Post by jason6g on 2008-08-24
iirc you may just install pulse audio.

thats what i use currently and sounds mix just dandy!

only issue i see, is with audacity (cannot have other sounds playing) and with wine (same thing, also cannot have other sounds playing)

there are several threads, on here, not sure where exactly to point you to as i do not know too much about sound mixing on ubuntu

edit: try this thread:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by habtool on 2008-08-24
In my case, as per your problem, removing pulse audio fixed the sounds issues for me.

Removing PulseAudio is simple:

  1. Disable Gnome system sounds. (important)
  2. Remove "pulseaudio" and "pulseaudio-esound-compat". Optionally
install "esound" for applications that need it.
  3. Reboot.

[http://ubuntuforums.org/showthread.php?t=876594](http://ubuntuforums.org/showthread.php?t=876594)

---

### Post by DonnieP on 2008-08-24
> **hofa said:**
> I have a problem with my ALSA server.
I can only get sounds to work from one application at a time.

example:
When I'm listening to music with MPD and I want to watch something on youtube. I first have to stop mpd, restart firefox, go to the page and only then I get the sound. Also I have twhirl (Adobe Air alpha app) on all of the time and it uses ALSA too. So when I want to listen to MPD, I first have to shut down twhirl, restart MPD and start twhirl again...

Anyone know how to fix this problem?

Also: Didn't they say that Hardy Heron would come with PulseAudio?
I have the exact same problem with Hardy and would love to hear the answer.  If I'm listening to music in a music player and then decide to pause that and listen to something in firefox, I can't get any sound out of firefox without doing what's described above.

---

### Post by Nepherte on 2008-08-24
There are two main options: you either remove pulseaudio and everything related to it, or you fix pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I recommend the last option.

---

### Post by habtool on 2008-08-24
> **Nepherte said:**
> There are two main options: you either remove pulseaudio and everything related to it, or you fix pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I recommend the last option.

Your advise is probably correct, just a pity the devs did not fix it with a standard download?
Why was it not fixed in 8.04.1?
I did once go thru the whole get pulseaudio working but it never worked with skype and youtube etc at same time.

For me best was just boot out/remove pulseaudio, BUT that was only as I had ZERO need for pulseaudio in the first place.

If puleaudio does something wonderful for you, then by all means try getting it to work, if you dont need it, then just remove it.

maybe it will work better in Intrepid Ibis ;)
Also one can hope that skype bring out a pulseaudio compatible linux client by then too?

---

### Post by Nepherte on 2008-08-24
I'm not sure why the developers didn't fix it. I believe it is already fixed in the intrepid development version.

You should be able to get sound out of skype: [http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype)

---

### Post by habtool on 2008-08-24
> **Nepherte said:**
> I'm not sure why the developers didn't fix it. I believe it is already fixed in the intrepid development version.

You should be able to get sound out of skype: [http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype)

Thanks, I did see that, but it was only a tempory fix as one could not leave skype running all the time, as i need to.

quote:
The work-around, is not to use the "default" sound device. Rather to use a specific hardware device, and use pasuspender to momentarily suspend pulseaudio.

---

### Post by Bucky Ball on 2008-08-24
[QUOTE=jason6g]only issue i see, is with audacity (cannot have other sounds playing)[/QUOTE]

Hey, jason6g, although audacity is extremely lightweight, it is also extremely powerful and flexible for what it is. You will find that you can record (or load) several tracks and *have them play back through various channels and outputs. *Therefore, Audacity probably claims what channels you have when you start it in case you decide to use a custom setup which requires you use 8-16-32 whatever channels on your sound card. :) Probably.

---

### Post by hofa on 2008-08-24
Thanks for your help everyone.
I bookmarked some pages and I'll start working on it when I'm back form spain. It seems like a lot of work and I don't want to start working on it right now.
I'll report back to let you know if it worked or not :) See you guys back in a week

---

