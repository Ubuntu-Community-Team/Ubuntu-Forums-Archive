---
title: "USB audio device problems with swapping"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by fogelfink on 2008-05-11
I have real difficulties to set up my system so that I can hot-swap my USB audio card (Griffin iMic).

Though my device manager immediately recognises when I plug the iMic in, I couldn't get any sound on it.  The USB card shows up in the alsa mixer, but no sound.

I followed this thread: [http://seehuhn.de/pages/alsa](http://seehuhn.de/pages/alsa) and managed to get the iMic working as default device - but now I can't switch back to the internal soundcard.  When I unplug the USB soundcard, I get playback errors.
The strange thing that happened when I rebooted without the iMic plugged in, the welcome sound splash played half the way on my internal speakers (!!!) and then stopped. From that moment on I can only get sound through the iMic.

I tried the  ```
sudo asoundconf list
``` and then choose my default card with ```
sudo asoundconf set-default-card
```, but no success.

I looked at [http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto)](http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto)), but am simply not sure what to do with that information.

Please can someone help me to create a setup that allows me to switch between internal and external soundcard.

---

