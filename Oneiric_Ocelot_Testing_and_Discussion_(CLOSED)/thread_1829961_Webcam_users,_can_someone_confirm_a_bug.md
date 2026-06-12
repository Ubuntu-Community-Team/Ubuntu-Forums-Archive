---
title: "Webcam users, can someone confirm a bug"
date: 2011-08-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-08-21
I have a logitech webcam pro which works excellently with oneiric with the uvc drivers, there seems to be a small bug with ubuntus sound settings though, if i go to sound preferences it detects the webcams input channel and if i switch to it on the input tab then it works perfectly but the next time i start my computer the input will have changed back to 'internal audio analogue stereo' which actually only gives output and has no mic, and i have to change back to the webcam for input to be able to use the mic, basically it doesnt save my settings, does anyone else find this

---

### Post by rbrick49 on 2011-08-22
my sound works ok but no video ok working now after a lot of fiddling around and a couple of reboots

---

### Post by cariboo on 2011-08-22
When I setup skype on this system, I set the sound input to the webcam, trying it today, the input is still set to the webcam. So unfortunately I can't confirm your bug.

The output of lsusb gives me this:

> Bus 001 Device 005: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks

---

### Post by rbrick49 on 2011-08-23
> **cariboo907 said:**
> When I setup skype on this system, I set the sound input to the webcam, trying it today, the input is still set to the webcam. So unfortunately I can't confirm your bug.

The output of lsusb gives me this:mine is ok now just some settings needed adjusting and unpluging webcam and repluging might have helped also

---

### Post by CaptainMark on 2011-08-23
@cariboo907 what does the sound preferences menu say your using as an input channel though, i dont have a problem with app specific settings just the main settings menu,

for example:

i use google+ for webcam chats with my friends, if i go the the google+ settings i can change the audio input from 'default device' to 'webcam pro 9000' and this will save my settings no problems and it will always seek to get input straight from the webcam, 

however i should be able to leave google+ settings as 'default device' so long as under ubuntu's sound settings i have set the default audio input as 'webcam pro 9000' 

this is where my problem lies, ubuntu's sound settings change the audio input back to 'internal audio analogue stereo' everytime i turn off my pc,

incidently this shouldnt be detected as an input anyway because the pc has no built in mic and this channel is actually output only, but thats a seperate issue altogether

ps, please dont think im having silly issues, i know i can work around at my end, i just need to switch the hardware settings to detect only the audio for the internal analogue, i have no problems i need support with, i was just wondering if i should make a bug report, lets face it if canonical want to try and make ubuntu easy for beginners we need to make it as 'works out of the box' like as possible

---

### Post by cariboo on 2011-08-23
@CaptainMark

Well it seems I was wrong, after a reboot with the webcam connected, input in sound preferences goes back to Internal analog stereo. It's only when the webcam is hot plugged that it automagically selects the webcam microphone as input.

---

### Post by cheleb on 2011-08-23
The problem here seems to be that you have more than one hardware device with audio input capabilities. As far as I can tell, pulseaudio prefers "real" audio devices to usb devices (your webcam). The workaround here is to disable input on every device except the webcam. To do this, you have to select the correct profile for each device at the bottom of the "Hardware" tab in the sound preferences .

For example, I have three devices listed in the sound preferences under the "Hardware" tab:

1) GF104 High Definition Audio Controller
-----------------------------------------

This is my HDMI Monitor with integrted speakers. It doesn't have a microphone and i don't use it for playback so i just set the profile to "Off"

2) Internal Audio
-----------------

This is my main Soundcard, which has a lot of Analog/Digital/Stereo/4.0/4.1/5.0/5.1/7.1/Input/Output options. I only need one of the Stereo options because I don't have a surround sound system. The Stereo options listed for this device are:

- Analog Stereo Input, which is input only
- Analog Stereo Output, which is output only
- Analog Stereo Duplex, which is in- and output

If I choose any profile with input capabilities here, it will be listed in the "Input" tab of the sound preferences as "Internal Audio Analog Input" and be chosen as the default input device after a reboot. To avoid this, I simply restrict this devive to an "output only" profile by choosing "Analog Stereo Output" here.

3) Quickcam Vision Pro
----------------------

Not much to say here. With the above changes, this is the only input device left in my system. If i choose the profile "Analog Mono Input" here, it is listed in the "Input" tab as the only option named "Quickcam Vision Pro Analog Mono".

So after a reboot, pulseaudio has no other choice as to pick up my webcam as the default input device.

Hope this helps!

---

### Post by CaptainMark on 2011-08-23
its odd that it defaults to use the hardware profile of internal audio input and output when my pc has no built in mic, when it uses these settings (as it does by default) then it pipes the output from the speakers straight back to the input channel and any program recording will just detect any music im currently playing, ive sorted it, but this is defintely a bug, should i report it on launchpad or wait until the beta has been launched

---

### Post by cheleb on 2011-08-23
> **CaptainMark said:**
> its odd that it defaults to use the hardware profile of internal audio input and output when my pc has no built in mic

Nothing odd here. Your soundcard probably has a microphone connector, which is an input source. If you connect a headset there, that microphone is used as input and the default profile makes perfect sense.

However, it is still strange that we can not set the default device in the input tab. Not necessarily a bug - but still a missing feature.

---

### Post by CaptainMark on 2011-08-24
actually good point, i dont have a sound card but my motherboard may have input for a mic and its detecting that,

i think it is a bug as this doesnt happen on natty, i change the dafault device to webcam and it stays set to webcam permanently

---

