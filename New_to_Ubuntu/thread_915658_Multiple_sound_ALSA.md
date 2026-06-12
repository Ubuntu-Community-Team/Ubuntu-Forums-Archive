---
title: "Multiple sound ALSA"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-10
Why can't I play multiple streams of audio at once?

---

### Post by skippuff54 on 2008-09-10
make sure alsa supports ur card and chipset, u have all the right drivers installed, and u've unmuted all the sound options in ur sound control.

---

### Post by Elephantman5 on 2008-09-10
> **skippuff54 said:**
> make sure alsa supports ur card and chipset, u have all the right drivers installed, and u've unmuted all the sound options in ur sound control.

I can play any program's sound.
I just can't do multiple programs at once.

---

### Post by skippuff54 on 2008-09-10
right, i noticed that too. beyond the scope of my knowledge...maybe u can tweak the alsa config? might need to actually get in the alsa config file and add/delete/update some entries

check alsa's site for documentation

---

### Post by Elephantman5 on 2008-09-10
> **skippuff54 said:**
> right, i noticed that too. beyond the scope of my knowledge...maybe u can tweak the alsa config? might need to actually get in the alsa config file and add/delete/update some entries

check alsa's site for documentation

I'm looking at this.
[http://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once](http://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once)

---

### Post by skippuff54 on 2008-09-10
looks like u'd need to manually adjust some config files. if u do that, it's always good to save a backup of the original

---

### Post by darthmob on 2008-09-10
what version of ubuntu are you using? I experienced the same problem with 8.04 and pulseaudio (which is the default for audio in that release) and **_[this]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")_** solved it for me. now multiple sound sources are possible and combined with the flash beta 10 there are no crashes of firefox anymore, too.

the only problem which remains is with ETQW which does not seem to like pulseaudio.

PS: I guess this will most likely not work if you are using ubuntu 7.10 or older.

---

### Post by Elephantman5 on 2008-09-10
> **darthmob said:**
> what version of ubuntu are you using? I experienced the same problem with 8.04 and pulseaudio (which is the default for audio in that release) and **_[this]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")_** solved it for me. now multiple sound sources are possible and combined with the flash beta 10 there are no crashes of firefox anymore, too.

the only problem which remains is with ETQW which does not seem to like pulseaudio.

PS: I guess this will most likely not work if you are using ubuntu 7.10 or older.

Well that guide screwed my computer up.
I'm using 8.04, x64. And installed the getlibs-all. Now I can't login to a session. :)

That'd be wonderful if someone could help me now, that this problem has escalated to my not being able to even log on.
I get an error message telling me that my session lasted for less than 10 seconds, and the error file says some audio crap couldn't be loaded.

---

### Post by Elephantman5 on 2008-09-10
etc/gdm/xsession: beginning session startup
Setting IM through im-switch for locale-en-us
Stat IM through /ec/xll xinit/xinput.d /all_All linked to /etc/xll xinit /xinput
usr/bin/searhorse-agent:error while loading shared libraries
libasound.so.2: cannot open shared object file

-
reinstall seahorse (whatever that is)
reinstall all ALSA crap in synaptic.
-
Now I can see my desktop. That's good.

___
I'm not seeing much.
[http://ubuntuforums.org/showthread.php?t=866924](http://ubuntuforums.org/showthread.php?t=866924)
-
I already have: [http://ubuntuforums.org/showpost.php?p=4804377&postcount=4](http://ubuntuforums.org/showpost.php?p=4804377&postcount=4)

----edit
Looks like [http://ubuntuforums.org/showpost.php?p=4808309&postcount=7](http://ubuntuforums.org/showpost.php?p=4808309&postcount=7)
is about to do the trick.
Just have to find out how to implement that into CrossOver's audio. Or would that be wine's?
-
Not possible.

---

### Post by Nepherte on 2008-09-10
It's a pulseaudio problem. To fix it, see: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by civillian on 2008-09-10
Another fix is to go to the 'sound' menu under preferences or in the control centre, and under that (provided your motherboard/soundcard is supported by alsa) change all the settings to ALSA, and ensure that the 'device' you have enabled is the ALSA mixer, for example mine reads 
> HDA Nvidia (ALSA Mixer)

I did this and can get multiple audio streams at once (for example, youtube with audio and quod libet simultaneously)

---

