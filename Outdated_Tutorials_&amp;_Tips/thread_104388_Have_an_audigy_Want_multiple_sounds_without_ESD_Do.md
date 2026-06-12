---
title: "Have an audigy? Want multiple sounds without ESD? Do this!"
date: 2005-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by BoyOfDestiny on 2005-12-16
Hi, this is for folks with an audigy running under Breezy (may work with other soundcards... feel free to add on to this thread if it does).

Here ya go, my first how-to here:

Using synaptic,
install alsa-oss and libsdl1.2debian-all

Next step (this one may be optional, I just hate the gnome sounds and ESD)

Go To System -> Preferences -> Sound
uncheck Enable Sound Server at start up and gnome system sounds

Next step
Go To System -> Preferences -> Multimedia Systems Selector

Set the default sink input and output to ALSA

If you did choose to not have esd, open up a terminal and type sudo killall esd. Or if you are more gui oriented log in and out of ubuntu.

Now, if you are lucky, open up xmms, fceu, beep, zsnes, dosbox, audio overload, vlc, etc etc. 

You should hear multiple sounds like nobody's business. Remember, if any of these apps were manually set to use ESD as default ouput, use their respective guis to set it to alsa or oss (only if alsa isn't an option).

---

### Post by TechSonic on 2006-01-27
Didn't work for me, Might for others.  Although I don't think it means all sound cards it will work. But for Sound Blaster Live! 24bit, this tutorial will not solve you're multi sound problem.

New Problems, Totem plays parts of audio tracks really fast.
Multiple sound applications such as totem and xmmx will still fight each other, same goes for any other mix.  America's Army, XMMS or Totem playing music, Game still without sound.  That goes for Teamspeak and Game, still no sound for both at once.

Gnome sounds enabled with ESD, totem plays music smooth again and Gnome sound effects play at the same time.

Sound Blaster Live!24bit has 7.1 channels.  In order to steam line them all into one output for those on 2.1 speaker sets, better luck next driver update.  Although if you were able to disable the other "Unused" or use the unused for regular playback into the same line.  A driver needs made where all channels will communicate with the one output.

---

### Post by benplaut on 2006-01-27
so... which is the prefferred sound server? ESD or ALSA?

i'm not sure if i should try and get ALSA to work...

---

### Post by RaptorRaider on 2006-01-28
By "no multiple sounds", do you also mean that sound in games like Enemy Territory doesn't work?

I have an Audigy 2 ZS and I'm still struggling to get even that to work. :neutral:

---

