---
title: "hardy sound issue"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by denver38 on 2008-04-24
hey
I just upgraded to hardy, and the first that I noticed was that  there was no sound. So I went to System settings and enabled 'the sound system'. Atm I do have sound, but it's only very silent. When I play a song with amarok/mplayer I can adjust the volume a bit with the volume-bar. But changing the volume with Kmix has absolutely no effect :s

thanks in advance

---

### Post by swoll1980 on 2008-04-24
could try to change the audio output in amarok to pulse.Maybe?

---

### Post by denver38 on 2008-04-25
thanks for your response

I installed and configured pulseaudio using this manual:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
however, when I highlighted
pulse, pulse-access and pulse-rt in 'manage groups' in order to be able to have access to sound, amarok gave this error message:
xine was unable to initialise any audio drivers
and there was no sound at all.
When I deselected it I was able to hear (a little) sound again.
are you sure pulseaudio is also something for kubuntu?

---

### Post by Xiong Chiamiov on 2008-04-25
Try running alsamixer (in the terminal, you may have to apt-get install it first), and make sure your levels are turned up at least somewhat.

---

### Post by denver38 on 2008-04-26
hmm that's not even in the repos
I think I have to change something like a configuration option...

---

### Post by BSAB_80 on 2008-04-26
I have a similar problem.

I can get sound fine and change the volume with, say, Amarok or Youtube's volume controls, but Kmix just doesn't work, if i try to change the volume as i always did before the upgrade, nothing happens.

I purged kmix and reinstalled, but no luck,

---

### Post by fabiomb on 2008-04-27
xine doesn't works for me, no problem with gstreamer, mplayer and vlc

---

### Post by denver38 on 2008-04-27
> **BSAB_80 said:**
> I have a similar problem.

I can get sound fine and change the volume with, say, Amarok or Youtube's volume controls, but Kmix just doesn't work, if i try to change the volume as i always did before the upgrade, nothing happens.

I purged kmix and reinstalled, but no luck,

if you manage to fix your problem, please post the solution in this thread
tnx

---

### Post by Eisenwinter on 2008-04-27
Open up terminal, and type **asoundconf list**, post the output here.

---

### Post by BSAB_80 on 2008-04-27
> **Eisenwinter said:**
> Open up terminal, and type **asoundconf list**, post the output here.

Dunno if that was for me or for one of the other fellas.
As for me:

```
asoundconf list
Names of available sound cards:
Intel

```

---

### Post by denver38 on 2008-04-27
> **Eisenwinter said:**
> Open up terminal, and type **asoundconf list**, post the output here.

I have the same output as BSAB_80

---

### Post by cornelis spronk on 2008-04-30
Names of available sound cards:
SI7018
UART
CS46xx

I am having no success in changing the sound levels of mplayer.  Mplayer automatically is chosen as the player for BBC radio.

The master volume (next to the date) has no effect.

Also some sound sources cannot be hear at all  It appears that ALSA has no effect.  I am puzzled. Any tips would be appreciated.

---

### Post by mormor on 2008-04-30
nvm this post:P mistook this for another problem, to tired I guess. but atleast it has to do with sound and alsa: )

> Originally Posted by Joshua Netterfield View Post
The best way I have found to fix this problem is just to run alsaconf. Ubuntu doesn't include it, because it has a way cooler system which always works except for when it doesn't. Nice. We will need to install it ourselves.

1. Open up a terminal. (Applications->Accessories->Terminal)
2. Type "gedit ./alsaconf.sh" (without the quotes)
3. Go to [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf), select everything (ctrl+a) and copy it (ctrl+c)
4. Go to the gedit window. Paste what you copied (ctrl+v)
5. Save it.
6. Go back to the terminal and run:
Code:

chmod +x ./alsaconf.sh
sudo ./alsaconf.sh

7. Follow the instructions
8. It should work. But it still might not...


"Chmod +x" makes the program runnable, and "sudo ./alsaconf.sh" runs it.
The script detects the sound cards that you have and gets them ready for use.

Good luck!

Edit: Oh ya. Source is [http://www.ubuntux.org/sound-card-not-detected](http://www.ubuntux.org/sound-card-not-detected) . You should thank them if it works (; 

try it? worked on my travelmate.

---

### Post by denver38 on 2008-05-02
A simple "sudo /etc/init.d/alsa-utils reset" did the job for me.
([http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/))

---

### Post by Kannon on 2008-06-02
> **denver38 said:**
> A simple "sudo /etc/init.d/alsa-utils reset" did the job for me.
([http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/))

This fixed another problem I was having with xine and amaroK after installing pulseaudio. Nothing through the xine engine had any audio, and now it all works fine, and that's the only thing I changed. (Note, that you have to change the output plugin under "Configure Amarok" > "Engines" to "autodetect" then it works fine.)

---

### Post by abn91c on 2008-06-02
did you make sure in Kmix the PCM slider is up and the radio button is green?

---

