---
title: "Sound Skipping in too many programs"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by durundal on 2008-09-14
I'm using a 64-bit 8.04 ubuntu installation and nearly every program skips with sound.  The only programs that don't seem to skip are Movie Player (when I can use it), Firefox and steam games running through wine.

VLC skips when another sound source is open, such as youtube in firefox, even when the video is not playing.  The emulator pSX gives the constant error "sound: underrun" in the terminal as the sound skips for every rom I've used.  The sound is also always choppy in DosBox for every game I've played.

In 32-bit xubuntu this was not a problem at all, at least for VLC and DosBox.  Any idea on possible solutions?

---

### Post by R_T_H on 2008-09-14
> **durundal said:**
> I'm using a 64-bit 8.04 ubuntu installation and nearly every program skips with sound.  The only programs that don't seem to skip are Movie Player (when I can use it), Firefox and steam games running through wine.

VLC skips when another sound source is open, such as youtube in firefox, even when the video is not playing.  The emulator pSX gives the constant error "sound: underrun" in the terminal as the sound skips for every rom I've used.  The sound is also always choppy in DosBox for every game I've played.

In 32-bit xubuntu this was not a problem at all, at least for VLC and DosBox.  Any idea on possible solutions?

It *might* be pulseaudio, if the 32-bit Xubuntu was prior to 8.04 (because it used to use ALSA as default).

---

### Post by markbuntu on 2008-09-14
If you are having problems with sound skipping, there is some adjustments you can make that may help here:

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

and here:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Lutherian on 2010-01-08
Fix skipping / choppy sound in dosbox in Ubuntu was easy, but the solution was unexpected.

If you open up the dosbox default configuration file ~/dosbox/. dosboxconf (can't remember the exact name ... sorry)

In any event, open the dosbox configuration file with a text editor and scroll down to the sound output section.
You'll see that by default, dosbox outputs audio at a frequency of 22500 (Hz or 22.5 kHz)

For the technically minded folk, that seems like a good thing - right? Dos box is only using half of what even the cheapest low end sound card outputs which is normally 44 000 (Hz or 44 kHz)

WRONG

I changed my output setting from 22500 to 44000 - and it worked perfectly. (On Ubuntu 9.10 with current version of dosbox)

It would seem, for the best results, the dosbox output frequency must match your sound card's default output frequency.

If I had not found this out - I too would naturally have started investigating PulseAudio settings, as it's been a frequent offender in the past (and it might still have something to do with it, for all I know) - but for the quick and dirty solution, change the dosbox config file - and see what happens.

---

### Post by das280zx on 2010-02-03
I did what you said Lutherian and it appears to work great.  Sound in doom now is almost perfect with only an occasional skip.

---

### Post by tkoco on 2010-03-21
Your fix is correct. Some additional tweaks which smooth out the sound for DOSBOX:
In [mixer] section -
  Set "rate" to 44100
  Set "blocksize" to 2048
  Increase "prebuffer" to 100

To get DOSBOX sound working on my machine, I commented out the soundblaster section and enabled the GUS section. The rate was set to 44100 as described below. The applications (games) were configured to use the GUS sound card.

> **Lutherian said:**
> Fix skipping / choppy sound in dosbox in Ubuntu was easy, but the solution was unexpected.

If you open up the dosbox default configuration file ~/dosbox/. dosboxconf (can't remember the exact name ... sorry)

In any event, open the dosbox configuration file with a text editor and scroll down to the sound output section.
You'll see that by default, dosbox outputs audio at a frequency of 22500 (Hz or 22.5 kHz)

For the technically minded folk, that seems like a good thing - right? Dos box is only using half of what even the cheapest low end sound card outputs which is normally 44 000 (Hz or 44 kHz)

WRONG

I changed my output setting from 22500 to 44000 - and it worked perfectly. (On Ubuntu 9.10 with current version of dosbox)

It would seem, for the best results, the dosbox output frequency must match your sound card's default output frequency.

If I had not found this out - I too would naturally have started investigating PulseAudio settings, as it's been a frequent offender in the past (and it might still have something to do with it, for all I know) - but for the quick and dirty solution, change the dosbox config file - and see what happens.

---

### Post by wingnux on 2010-05-11
Thank you very much! I was having this same problem on dosbox 0.73 running on my Ubuntu 10.04 64bit! =)

---

### Post by 45acp on 2010-07-12
Thanks, I been trying to find a fix for this for awhile.

---

