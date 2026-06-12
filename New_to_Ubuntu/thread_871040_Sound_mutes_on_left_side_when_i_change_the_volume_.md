---
title: "Sound mutes on left side when i change the volume (usb headphones)"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by darkline on 2008-07-26
I have a slightly odd and very annoying problem atm. 

Whenever i change the volume on my headphones (logitec uusb ones) the left side turns itself all the way down, and wont come up again (if i click higher up on the volume controller, it goes up i get a burst of sound then it resets itself to 0 again).

How can i get it to change to where i want it?
Is there anything i can post to help get this problem solved?
I cant find anything to help on forums/google:(


As i workaround for me, is it possible to set it so when i insert my headphones the sound is on full volume rather than half?
Then i could set the volume in pulse audio and it would be fine!:D

thanks for any help

---

### Post by northern lights on 2008-07-26
This happened with ALSA and my external USB sound card also.

Do the following:

Install the ALSA Pulse plugin and the PulseAudio deamons & tools```
sudo apt-get install "pulseaudio-*" paprefs pavucontrol pavumeter paman padevchooser libasound2-plugins

```

Edit your 'asound.conf' (might be empty/nonexistent)
```
gksudo gedit /etc/asound.conf

```
and append it by```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```Save & exit gedit.

Navigate to "System > Administration > Users & Groups", unlock and select "Manage groups".

Edit the properties of these 3: pulse, pulse-access, pulse-rt check the box next to your username.

Reboot / restart session.

---

### Post by gjoellee on 2008-07-26
it might also be just your headset...(I don't know)

---

### Post by northern lights on 2008-07-26
> **gjoellee said:**
> it might also be just your headset...(I don't know)
It's a bug with USB audio devices and the pulse audio tools fix it.

---

### Post by darkline on 2008-07-26
I should probably have mentioned, my headset works fine in windows:P sorry
I'm trying your solution now northen lights.

---

### Post by darkline on 2008-07-26
Well, i tried doin all that, however now when i insert my headphones it starts with full volume on the right side and none on the left (which is what it was on when i did your solution). I still cannot unfortunatly move the left side above 0.

What exactly does your solution do? coz atm it seems just to be remebering what i had before and putting those volume levels back on when the headset is reconnected.

Thanks for the try, i will keep looking:)

---

### Post by northern lights on 2008-07-26
Are you certain you did everything verbatim as posted above?

In your notification are, do you see the PulseAudio Applet?

As device don't choose 'USB Headset (Alsa mixer)', but 'ALSA PCM ... via DMA (PulseAudio Mixer)'.

---

### Post by darkline on 2008-07-26
I definitly did everything verbatim, all copyied and pasted, i dont however see a pulseaudio thing in notification area.

I open the pulse voolume manager thing by "pavucontrol" then right click and select ALSA PCM on front:1(USB audio) via DMA,
the volume there is 100% both channels fine, the problem comes in the alsa mixer. (from double clicking the volume manager applet)

---

### Post by darkline on 2008-07-27
I have found a workaround now, although it does not solve the problem,


After doin what has been suggested above, if both channels are turned right down then i can put the left one up without it goin to 0 again. Then i can put the right one up to match.

Very odd and i have no idea why it works but it seems to.

Since the problem isnt resolved i wont mark the thread as solved but thanks for the help anyway

---

