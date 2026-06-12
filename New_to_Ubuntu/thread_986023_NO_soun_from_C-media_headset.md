---
title: "NO soun from C-media headset"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by superrfly on 2008-11-18
MY operating system is Ubuntu 8.10 and soundcard is C-media (integrated sound card).I dont have speakers only USB headset.But i cant hear any sound.something wron in my settings(please look attachment asetukset.png)
i have tried also alsamixer but it didnt help anything.  
And headset model is: C-media USB headset   :guitar:

---

### Post by kostkon on 2008-11-19
You can set your sound playbacks in sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to your USB headset instead of *Autodetect*.

But if this does not work, or if you want more flexibility, leave it as it is (i.e. *Autodetect*) and install the *PulseAudio Device Chooser* (its package name is *padevchooser* and you can easily install it using *Synaptic*) instead.

It will create a menu entry in *Applications &#8594; Sound & Video*. Run it and it will its icon in your taskbar. Left-click on it and select *Volume Control*.

In the *Output Devices* tab you should see your headset listed. Right-click on it and enable the Default option to set it as the default. Do the same in the *Input Devices* tab. This will make all of your applications to use your USB headset to output their sound.

In the *Playback* tab you will see the audio streams of the various applications you are running (e.g. *Flash*, *Totem*, etc.). You can individually set their volume levels. You can also right-click on each of them and select the *Move Stream...* option. In the list that will appear you should see all of your audio devices listed (in your case only the USB headset). You can then select the device that this application will use to send its sound output. You will need this in case your add more audio devices in the future, for example if you buy USB speakers, etc.

Hope that helps.

---

