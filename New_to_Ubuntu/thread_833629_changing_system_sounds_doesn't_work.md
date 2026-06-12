---
title: "changing system sounds doesn't work"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by TheSeanKelly on 2008-06-18
I'm trying to change ubuntu 8.04 system sounds.  I've downloaded a theme from gnome-look.  I go to system -> preferences -> sound, ESD and play system sounds are both enabled.  I can hear the selected sounds with the preview buttons, and the login sound plays at startup.  

However, I choose a new sound by browsing and selecting any of the wav files (length is irrelevant) and it does not play when I hit the preview button.  I restart and nothing happens.  I revert back to the default and it plays again with the preview button, and at startup.

Any ideas?  Sorry if this has already been addressed, but I've spent a few weeks looking online and nothing has worked so far.  They all seem to address "upgraded to hardy and system sounds no longer work" - my problem is that they DO work but I can't pick different sound files.

---

### Post by Exsecrabilus on 2008-06-18
Try doing this: (I don't really know what your issue is, but when I had playback issues, this worked for me.)

Go *System -> Preferences -> Sound*. Under *Devices* tab, choose the first four choices as **ALSA - Advanced Linux Sound Architecture** instead of **Autodetect**. Reboot your system.

---

### Post by TheSeanKelly on 2008-06-18
Tried, but I have the same issue.

---

### Post by Exsecrabilus on 2008-06-19
Did you try the sticky: [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)?

---

### Post by TheSeanKelly on 2008-06-19
Yeah I did, and it didn't help.  It seems to deal mostly with broken sound.  Everything works correctly on my computer soundwise, It just won't let me change system sounds.

Also a note - I reinstalled ubuntu last week and I was experiencing the same problem before and after the install.

---

### Post by hefeloce on 2008-06-19
I have the same problem in my desktop and in my laptop.
Well I ran gnome-sound-properties under a terminal and when I choose another file and press the Preview button I get the next error:

(gnome-sound-properties:18228 ) : Gnome-WARNING **: error caching sample <-1>!

but the number changes depending on the file I choose.

for example:

(gnome-sound-properties:18168 ) : Gnome-WARNING **: error caching sample <-1>!

I looked for I but I can't find it.

Note: When I was using Gutsy it plaid the System Sounds without problem

---

### Post by hefeloce on 2008-06-19
Well, I tried changing the System Sound Event server to Alsa  but I get the next error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No se pudo abrir el dispositivo de audio para reproducción. El dispositivo está siendo usado por otra aplicación.

(Something like: Cannot open audio hardware for reproduction. The hardware is being used by another application.)

(I speak spanish if you ask)

Could it have something to see?

---

### Post by hefeloce on 2008-06-20
Ok I found this:

[http://brainstorm.ubuntu.com/idea/5890/](http://brainstorm.ubuntu.com/idea/5890/)

So I used audacity to make the sound file to have less than 2 MB and it worked even when its length is larger than 10 seconds.
Anyway... This is an strange bug isn't it? It worked without problem in Gutsy.

---

### Post by TheSeanKelly on 2008-06-21
that doesn't do it for me, I've got a sound file thats 940kb and 2 seconds long (an ogg i stole from KDE and converted to wav) that isn't working.

---

### Post by TheSeanKelly on 2008-06-21
Just some updates, no progress.

I've done everything I can think of at this point - I've taken ogg's and converted them to wavs, I've observed length requirements, etc etc.  I've created a symlink to the wav file and set it as the startup sound, I've created a symlink to the ogg file and set it as the startup sound.  Nothing works.

This is pretty frustrating!

---

### Post by TheSeanKelly on 2008-06-21
SOLVED!!!

Not even a half hour after my last post, I decided to re-encode the wav to 16 bit instead of 32 bit for the heck of it.  That did the trick!  I literally put my hands up in the air in victory as gnome booted to a new sound.

Thanks for your help all

---

### Post by hefeloce on 2008-06-22
MMM... sounds strange I'm new but let's see I changed all Sound servers to Pulse audio not Auto-detect and I'm using Wav files of 8 bits not 16 bits. Do you have the same configuration?
Oh sorry I didn't saw the last post.

Nice!!!

---

