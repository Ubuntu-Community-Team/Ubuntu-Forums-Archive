---
title: "Skype 4.0.0.8"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by mdavis1231 on 2012-10-13
I've read many posts over the Internet, and none of them seem to work.  Here's my concern.  When using Ubuntu 10.04 LTS, I purged PulseAudio so that I could choose custom outputs for Skype (i.e. startup sound and ringing through my speakers, input and output through my Logitech USB headset).  Purging PulseAudio in Ubuntu 12.04 LTS doesn't seem to work so well.  If I purge PulseAudio, then DVD's won't play in Totem any longer.  Also, Amarok will refuse to play through my USB headset.

Has anyone figured out a way to customize the input & output options in Skype 4.0.0.8 without removing PulseAudio?  Currently, I'm using pavucontrol, but now ALL sounds coming from Skype are going through my headset.

I would like for the startup sound and the ringing to come through my computer speakers, and for the output and microphone to be set to my USB headset.  Any help would be appreciated.

---

### Post by arochester on 2012-10-13
Yes, I have sorted it. I have a desktop with a webcam, headset and plug-in speakers and a laptop which has different  inputs and outputs.

At first I had problems with my desktop. I removed the webcam because it has a microphone. I had to play about a bit with S button>Options>Sound Devices>Open Pulse-Audio Volume Control until it worked.

There is not much point telling you the settings that worked for me because you might have different ones...

Experiment....

---

### Post by mdavis1231 on 2012-10-13
> **arochester said:**
> Yes, I have sorted it. I have a desktop with a webcam, headset and plug-in speakers and a laptop which has different  inputs and outputs.

At first I had problems with my desktop. I removed the webcam because it has a microphone. I had to play about a bit with S button>Options>Sound Devices>Open Pulse-Audio Volume Control until it worked.

There is not much point telling you the settings that worked for me because you might have different ones...

Experiment....

So you actually have Skype ringing through your computer speakers, but have output and microphone running through your USB headset?

---

### Post by mdavis1231 on 2012-10-14
I actually got this working by installing Skype 2.2.0.35-1 and PulseAudio Preferences.  I have PulseAudio installed, and my Skype startup sound and ringing are coming through my speakers, but my microphone and audio output are coming through my USB headset.

Unfortunately, it refuses to work with Skype 4.0.0.8.  I guess I'll just wait and see if Skype is going to do something to remedy this with it's newest version.

---

### Post by mdavis1231 on 2012-10-14
> **mdavis1231 said:**
> I actually got this working by installing Skype 2.2.0.35-1 and PulseAudio Preferences.  I have PulseAudio installed, and my Skype startup sound and ringing are coming through my speakers, but my microphone and audio output are coming through my USB headset.

Unfortunately, it refuses to work with Skype 4.0.0.8.  I guess I'll just wait and see if Skype is going to do something to remedy this with it's newest version.

OK, it seems that this didn't work as I had quite planned.  The Skype startup sound and ringing was very staticy and garbled.  However, I have found the perfect solution for anyone who doesn't mind using an older version of Skype (i.e. 2.2.0.35-1), and doesn't want to give up Totem Movie Player for playing DVD's.

First, I created a new configuration file for PulseAudio by typing 'sudo gedit ~/.pulse/client.conf' in terminal, and posting 'autospawn = no' inside, and clicking 'Save'.  This will stop PulseAudio from automatically starting upon reboot.  Also check to see that it's not listed in Startup Applications.  This will make ALSA the default sound card without uninstalling PulseAudio and breaking anything.

Now, I'm free to choose the default sound devices that I would like for Skype to use (i.e. Microphone & Speakers = Logitech USB Headset, and Ringing = Default device).  When I want to play a DVD in Totem, I open terminal and type in 'pulseaudio --start'.  This starts PulseAudio, and Totem will play the DVD.  When I'm finished, I simply open terminal again and type 'pulseaudio --kill'.  This turns PulseAudio off again.

Also, if you have Gnome Login Sound enabled, you need to uninstall 'libcanberra-pulse' for it to play through ALSA at startup.

Just thought I'd share this.

---

