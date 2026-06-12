---
title: "Pulse Audio: Is it really successful or a disaster?"
date: 2009-02-03
forum: Recurring Discussions
---

### Post by buntu_hugenewbie11 on 2009-02-03
I see constant problems with Pulse Audio and experience many myself.
I want to see what other's experiences have been like with pulse audio.
Disaster
Bit of Work
Seamless
I didn't even know Pulse Audio existed because it runs so well.

---

### Post by Gipi on 2009-02-04
I wish more people would vote on this poll, I'm using Ubuntu 8.10 on 3 different computer (1 laptop) and pulseaudio has been a complete failure on all of them.

Very unhappy with it... :(

---

### Post by buntu_hugenewbie11 on 2009-02-04
Well it's good to know others are experiencing these problems.

I have never gotten Pulse to work properly.
I have tried various directions and have just given up and accepted that proper functioning sound is a pipe dream.
I use KDE 3.5  kubuntu hardy 64 bit.
No KDE sounds.
1 application at a time can use sound.
Skype output will only go to 1 speaker (people blame this on skype but there was no problem in Fiesty).
Rythmbox fails.

---

### Post by comandrei on 2009-02-04
I use Ubuntu 8.10 on 2 computers (1 laptop) and I installed Hardy on a friend's computer and didn't experience any problems.

---

### Post by wkulecz on 2009-02-04
I can say I'm only a minimal sound user and Pulse Audio has worked well on some systems but been full of problems on others.  

To me it was a complete disaster introducing it in an LTS release and if sound was critical I'd have had to roll back to 6.06.  Recent updates do seem to have automagically fixed the most annoying issues, and since sound is only "nice" not critical to me, 8.04 otherwise has been a very worthwile upgrade.

I fail to see any benefits to Pulse Audio, where it works I don't see any difference over 6.06 so I have to ask why bother?

I'd like to know what Pulse Audio brings to the party to justify all the problems it causes on many systems.
At least the Compiz and other eye candy can just be turned off and stop bothering me when it causes problems.

--wally.

---

### Post by markbuntu on 2009-02-04
I have a two sound cards, a usb headset and a usb webcam with a mic. Pulseaudio is the only way I found to use them all in any reasonable fashion. 

The biggest problem with introducing pulseaudio was the hairbrained idea to leave the pulseaudio volume control out of the desktop seed and configuring the default sound setup to guarantee conflict between alsa oss and pulseaudio applications trying to use the sound hardware. It is probably the dumbest thing Ubuntu has ever done. So don't blame pulseaudio for this one, blame Ubuntu.

Anyway, once you do get everything set up properly, which can be done in about 15 minutes, pulseaudio is great.

---

### Post by Melcar on 2009-02-04
I see Pulseaudio as a band-aid to the problem rather than a fix.  Linux sound system is a mess, and the advent of Pulseaudio makes me think that no one is really interested in fixing it.  Knowing this, it is in fact, good that a thing like Pulseaudio is available, in so far end users are concerned.
Personally, I like it.  It nearly eliminates all sound related hassles and makes working with multiple sound devices/streams much easier than before.  To bad it's buggy and unstable, but it should get better with time.

---

### Post by stderr on 2009-02-04
Some soundcards I've tried work fine with Pulseaudio; with many, however, I've encountered too many problems to try and fix, and I use ALSA instead (which Pulse all too often still likes to interfere with).

Like Melcar says, Pulseaudio **is** a good idea... but at the moment, things are pretty bad. Maybe in a couple of years it will be improved to the extent that I can use it on the majority of systems "seamlessly". It's a heck of a long way away from reaching that stage though, so far as I can see.

I love the concept though :D

---

### Post by binbash on 2009-02-04
There are too many problems with pulseaudio but it will be good.

---

### Post by gutties on 2009-02-04
Pulse audio is the reason I went back to windows, and I HATE windows

---

### Post by wolfen69 on 2009-02-04
> **gutties said:**
> Pulse audio is the reason I went back to windows, and I HATE windows

all you had to do is uninstall it and use alsa. that hardly qualifies as a good reason to go back to windows.

---

### Post by wolffangalchemist on 2009-02-04
everything works great for me in Ubuntu 8.10 haveing two machines running it my compaq cq50-103nr notebook and my emachines w3502 desktop.
though in 8.04lts i had only one sound channel at a time but that was fixed for me when i upgraded to 8.10.
i might not have issues with it, but seeing as some ppl have problems with it still it clearly needs some work and can be great if ppl will put lots of time into it.

---

### Post by gozzerd on 2009-02-07
For me, pulseaudio has been a pain that just keeps going and going and go....

I have an audigy2 platinum, and after all the wonderful 'how to's' in the forum, and pulseaudio's own perfect set up description, on 8.04 the best I could do was get to having 5.1 in dvd playback for a few moments until the pa server shutdown with the "soft cpu time limit" message. The troubling thing was that working through the 'how-to's' generated a parade of errors that had existed back in 2007.

I tried to  help, because I really, really want this all to work perfectly, so I read how to run gdb and tried to begin to do some systematic testing, but gdb crashed with a bug message every time. I finally gave up on 8.04 and stopped pa. But the 3 easy guides for that all left me in silence. There was one posting that focused on showing all the gnome configurations relating to pulse audio and sound, and that one helped the most. There were like 6 places configurations had to be manually changed to get alsa to work again. 

But I heard pa was well configured in Intrepid. I did a clean install of 8.10amd64 on a new machine, and  . . .  no sound. Back to the 'how-to's'. But first I installed the pa device chooser applet, to check the installation. The daemon was running, but no apps were registering. sigh. Back to psyke83's wonderful guide, and I got all the way to apps registering, but 2 channels, and still no sound. Then I discovered something very odd that was different now, and I hadn't read anywhere before. The traditional problem for audigys, the analog/digital jack toggle, was now defaulting to off, instead of on. I thought "Oh boy, an easy one" and switched it on. Nothing. Then I switched it back off. BOOM. Sound. So the toggle had to switch from off to on and back to off again. Sounds like stacked toggles or something.

After continuing to manually change things, I got all the way up to 5.1 surround for a few moments in any of 3 different dvd players, totem-gstreamer, totem-xine, and vlc, before pa shuts down with the "soft cpu time limit exceeded" message, same as in Hardy. I am going to turn it off for now and wait. 

I think pulseaudio is a wonderful piece of software, and no doubt choosing it as a distro's main sound platform is a very good thing for the future of sound in Linux. But the world of sound on consumer grade stuff is such an adhoc aglomeration of bailing wire and chewing gum, that it's hard to believe that a  thousand guys working for 2 months could sort out all the driver issues in sound, and create a set-up that 'just works' for everyone. I am kind of a heavy sound user, being a former musician and wanting my 5.1 in movies, and wanting to do midi, sequencing and such. So I am quite frustrated by another delay in getting a high-end easily set-up platform. But I am hopeful. I think pulseaudio will be really good and really cool. It should make some wonderful applications easy to write, and smooth the way into the virtual desktops that are coming.

---

