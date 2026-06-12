---
title: "Sound Problem - Weird as hell..."
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Syndacate on 2008-07-30
Hey, I recently got an error with hardy, not sure if this was part of the recent firefox update, or what exactly caused it, though the problem is as follows:

I have 2 sound cards in this computer, one's the Intel sound card on the motherboard, the second is a sound blaster live.

Before, they both worked, I just used the Intel sound card because it could go louder, even though it had interference when you scrolled *shrugs*.

Now, if I plug into the sound blaster, I get sound in firefox's flash plugin, but no sound in kaffeine (or any other video or music player, VLC, Totem, Xine, etc.).

Fine, so I usually use the Intel sound card anyways, but when I do that, I get sound in kaffeine, VLC, etc. (video players), and sound players (totem), but no sound through firefox's flash plugin.

So right now, it's either:
-  Plug into sound blaster and get flash plugin sound.
-  Plug into Intel onboard sound and get sound in video and audio players, but not in flash..

Weird as **** problem, somebody help plz?

I didn't have this problem until last night when it updated (I hadn't been in ubuntu for a few days)..

---

### Post by eightmillion on 2008-07-30
I would try going to System>Administration>Sound and setting everything to alsa.

---

### Post by Syndacate on 2008-07-31
> **eightmillion said:**
> I would try going to System>Administration>Sound and setting everything to alsa.

I just tried that - I don't get any sound with anything on Alsa.

Youtube isn't caching videos either, I suspect this is a problem with flash, since my browser (firefox) cache is at 200Mb.

Though youtube sound works fine on my SoundBlaster Live!, so that kinda rules out my previous theory.

Gah, anything else?

---

### Post by Syndacate on 2008-07-31
*Bump, help plz :(

---

### Post by Syndacate on 2008-08-02
*bump

I really need help on this..

---

### Post by cariboo on 2008-08-02
I'd go into the BIOS and turn off the internal sound card. Then set your soundblaster as the defaut sound card.

JIm

---

### Post by Syndacate on 2008-08-02
> **cariboo907 said:**
> I'd go into the BIOS and turn off the internal sound card. Then set your soundblaster as the defaut sound card.

JIm

I guess I can give that a shot out of pure desperation, but I've been running it like this for awhile, and didn't have any problems until Firefox updated from I guess 3.0.0 to 3.0.1.

Last time I tried using the Sound Blaster Live! not only is the audio max not loud enough, but local media's audio didn't work either.  I'll give it a whirl, though.

---

### Post by Syndacate on 2008-08-02
Well I wasn't about to disable the best audio card I have - but you gave me an idea.

I removed the sound blaster, I figured Ubuntu is getting confused between the two in the settings someplace (though I can't find it anywhere) - so I pulled the SoundBlaster Live! out it and it works fine now.

Not my ideal solution, but it works..gotta put it back in when I boot into windows, ha...

Oh well, thanks anyways, too bad I can't find the setting :(.

---

### Post by markbuntu on 2008-08-02
There is an issue with the way pulseaudio finds your sound cards. It uses hal-detect, which will make the first sound card it finds the default, usually the built in one. 

You can change the default device in the PA Volume Control and you can change the device each application uses but it will not persist through reboot because in

/etc/pulse/default.pa 

there is this line:

```

load-module module-default-device-restore

```

which will restore the faulty defaults you have fixed during your session. So, if you have been wondering why you have to change everything around after every time you reboot, this is part of the problem.

---

### Post by Syndacate on 2008-08-02
I don't have to change everything everytime I reboot, this problem just started showing up, though I'm sure it has something to do with what you said about it selecting the 1st sound card it finds.

Oh well, now that I removed the sound blaster it defaults everything, both flash and local media to the Intel, so it's "patched" I guess.

Maybe I'll be able to find the drivers for it for windows so I don't have to plug the sound blaster in every time I wanna play a game.

^_^

---

### Post by markbuntu on 2008-08-05
There is another thing you can try, in the PulseAudio Volume Control, see if your soundblaster card is listed in output devices. You can right click on it and make it the default. It seems to work for me through reboots lately. 

I have 3 sound cards and ALSA sees them all but PulseAudio only sees 2 of them. Since I don't use the one PA does not see, it is no big deal and I can change to it with Default Sound Card (asoundconf.gtk) for alsa apps.

---

