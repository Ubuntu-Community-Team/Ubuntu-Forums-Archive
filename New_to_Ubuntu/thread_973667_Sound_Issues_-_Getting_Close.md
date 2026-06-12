---
title: "Sound Issues - Getting Close"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Stratty on 2008-11-06
First time Ubuntu user and loving it so far!  Have one last issue to take care of, sound.

I am using a Plantronics DSP headset (USB connected).

I have tried a few walkthroughs and fixes found on various forums but I cant quite seem to get everything going but I think I am close.

During login I hear the start up music.  At the tail end of the start up the sounds goes statically and I believe it is clipping out.

From that point on no sound.  

I am thinking its some sort of device conflict that happens during startup but I am unsure how to move forward w/ troubleshooting.  Any suggestions or help would be very appreciated.  

Thanks,

Stratty

---

### Post by kostkon on 2008-11-07
> **Stratty said:**
> First time Ubuntu user and loving it so far!  Have one last issue to take care of, sound.

I am using a Plantronics DSP headset (USB connected).

I have tried a few walkthroughs and fixes found on various forums but I cant quite seem to get everything going but I think I am close.

During login I hear the start up music.  At the tail end of the start up the sounds goes statically and I believe it is clipping out.

From that point on no sound.  

I am thinking its some sort of device conflict that happens during startup but I am unsure how to move forward w/ troubleshooting.  Any suggestions or help would be very appreciated.  

Thanks,

Stratty
Assuming that you use 8.10 (or 8.04) then you could install the *PulseAudio Device Chooser* utility. The package's name is *padevchooser* and you can easily install it using *Synaptic*.

When you run it (it creates a menu entry in *Applications -> Sound & Video*) its icon will appear on your taskbar. Left-click on it and then select *Volume Control*. In the *Output Devices* tab you should see your USB headset and your soundcard (if you have one, you did not specify). Right-click on your headset and enable the *Default* option. This will make your headset the default audio device.

This utility is very useful since it gives you access to more features of *PulseAudio*.

For example, it will allow you to move the audio of an application from one device to another, e.g. from your headset to your soundcard (i.e. speakers), if you want. You can do it if you go in the *Playback* tab then you right-click on the application stream you want to move, and select *Move Stream...*. In the list that appears you should see all your audio devices (headsets, soundcards, etc.). Select the one you want.

It also offers you individual volume levels per application and some other stuff.

If you want to have the *PulseAudio Device Chooser* to start automatically every time you login, then there is such an option in its preferences (i.e. left-click on its icon and select *Preferences*).

Hope that helps you...

If you have any question regarding the above, don't hesitate to ask here.

---

### Post by Stratty on 2008-11-08
Thanks for the reply: Using PulseAudio I have the following as the only option: ALSA PCM on front:1 (USB Audio) via DMA.

Some Additional information:

```
jason@Jason-Linux:~$ lsusb
Bus 002 Device 002: ID 047f:0ca1 Plantronics, Inc. USB DSP v4 Audio Interface
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  


```


```
jason@Jason-Linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
jason@Jason-Linux:~$ 
```


```
jason@Jason-Linux:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Headset

```

As you can see I only have 1 sound device (my USB headphones) and this is correct.  Still sound stops shortly after the ubunto startup sound plays.

Looking for additional guidance on this.

Thanks,

Stratton

---

