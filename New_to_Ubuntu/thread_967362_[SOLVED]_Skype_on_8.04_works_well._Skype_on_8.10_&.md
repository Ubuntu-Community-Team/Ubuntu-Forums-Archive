---
title: "[SOLVED] Skype on 8.04 works well. Skype on 8.10: &amp;amp;amp;quot;Problem with Audio Playba"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by hanzj on 2008-11-02
Hello,  While using Skype on 8.04 Ubuntu, Skype was working just fine. But I've just done a fresh clean install of Ubuntu 8.10 and Skype (from Skype repository) says:  "Problem with Audio Playback"   Could you please help me diagnose the problem?   Please do NOT just tell me to try this or try that. I want to know first the _Cause_ of the problem before installing this or modifying that.   Thank you.

---

### Post by ashmew2 on 2008-11-02
I wont tell you to try this or try that. I had the same problem myself (both with playback and recording). All i did was Go to 

Skype Options => Sound Devices => Sound out

and set it to : pulse

That worked for me , but you can try any other devices in the drop down list both for Sound IN and Sound OUT to get Skype to work!

---

### Post by hanzj on 2008-11-02
ashmew2  I _tried_ what you said but that didn't work.  Nice _try_. 8-)

---

### Post by MockY on 2008-11-02
I'm in the same boat. Skype is extremely buggy in Ibex. After to many changes in sound devices, it completely freezes and makes ALL sound on the system to get muted. I then have to restart my computer in order to get my sound back. Though the rest of the system appears to be working, no Skype is a show stopper and I have to go back to Gutsy (Hardy works very poorly on my system) if there is no solution to the problem.

---

### Post by dunbrokin on 2008-11-03
> **ashmew2 said:**
> I wont tell you to try this or try that. I had the same problem myself (both with playback and recording). All i did was Go to 

Skype Options => Sound Devices => Sound out

and set it to : pulse

That worked for me , but you can try any other devices in the drop down list both for Sound IN and Sound OUT to get Skype to work!

I had the same problem...your solution worked for me..

---

### Post by stevenyu on 2008-11-03
I am having the same problem, by changing the sound out to pulse fixed the audio playback issue, but I can never get the Mic to work.  I am running ASUS M51S laptop.

I might consider rolling back to 8.04, I have been testing this more than 6 install between vista, ubuntu 8.04, 8.10, opensuse, mandriva...  driving me crazy!  :confused:

---

### Post by o.besner on 2008-11-03
Hey,

Had the same problem with Skype, and I found something that works. 

1 - Install the Medibuntu repository (you've probably already done it, since it's the only way of seeing Skype in synaptic.

2 - Purge the previous Skype install, and install the package skype-static-oss (OSS stands for Open Sound System, so you kinda bypass pulse audio)

3 - check your sound settings first -- open a console and type "alsamixer". Does everything look normal ? Is your microphone muted ?

4 - Curse Skype for not caring at all about a decent Linux release. Skype should work now. It's kinda buggy since you have to close every other audio application while you are using it but hey - I'm not gonna watch a movie while I talk with my friends right ?

---

### Post by joris1977 on 2008-11-03
I have been struggling with skype in intrepid as well. 

I posted in another thread how i fixed it here: [http://ubuntuforums.org/showthread.php?t=956302&highlight=skype+intrepid](http://ubuntuforums.org/showthread.php?t=956302&highlight=skype+intrepid) but i will repeat it here in this thread.  

My problem was the Microphone, but you have to check the same things to troubleshoot the rest of the audio settings. 

After i noticed skype wasn't working. I started with this guide: [http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid](http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid)

but it might not be necessary to follow this guide. 

After following the thread mentioned above my MIC would still not work in skype. pretty frustrating...

What I did next?

Open up Pulse Audio device chooser to be found under -> Applications -> Sound & Video. (If it is not there, install:  padevchooser with synaptic package manager.) 

Now there should be a new icon on the panel; the pulse audio icon. Click on it and there you can open Volume Meter (Recording) Try to speak through your MIC and watch if it registers any sound,the meter should go up a lot if you speak, if yes Pulse Audio is working. Than you problem is the skype settings. See down in this post.

If not, just as in my case. The volume meter didn't register my voice. Open up the Gnome volume control. It is the small speaker on your panel. You might have used it before to contol your sound. Click on it with the right mouse-button. and select open volume control.

In Gnome volume control: Device should be something similar to 'HDA Intel' (Alsa Mixer). Click on preferences and make sure all the tracks are visible. Make sure all of them are up and nothing is muted. Try if you have sound from your MIC on the Pulse audio volume meter.

If not. Click on the next tab, probably something like 'recording' and do the same.

If not. Check under options. In my case there were two Input sources. In my case Front MIC was selected. That looked good, because i was using the Front MIC, but really you should try the other options. Look at the Pulse Audio Volume meter if it registers any sounds. I am using the Front Mic, but when i changed it to MIC, i noticed The Pulse audio volume meter was registering my voice.

If that works than the next step is to start skype. Go to options -> sound devices. Select for sound Out and for Ringing: Pulse. For Sound in you choose one of the options that will look like, at least in my case, HDA Intel (hw:Intel,4) There are probably more options that look similar like this. Test them all with the skype test call. If the Pulse Audio Volume Recorder is registering your voice than there is probably a way to make skype work with your MIC.

If i write it down, it actually sounds not to difficult, but it wasn't, at least not for me. Hope this helps you to make skype work with intrepid.

---

### Post by Symmetric on 2008-11-03
To add my experiences to the group, I'm having the same problem - at first I got the "Problem with audio playback" error. After changing all of my audio drivers to Pulse in Skype, the call will start, but there is no sound recorded.

I've tried using the PulseAudio device chooser, and there's no input registered from my mic. This seems to suggest that the problem is within Ubuntu. Any ideas on other ways to verify this?

Thanks,
P

---

### Post by o.besner on 2008-11-04
> **Symmetric said:**
> To add my experiences to the group, I'm having the same problem - at first I got the "Problem with audio playback" error. After changing all of my audio drivers to Pulse in Skype, the call will start, but there is no sound recorded.

I've tried using the PulseAudio device chooser, and there's no input registered from my mic. This seems to suggest that the problem is within Ubuntu. Any ideas on other ways to verify this?

Thanks,
P

Yeah, I had the same problem tonight when I dropped the -static-oss version and came back to the original skype. Don't use pulse as the Sound In source, but directly use your microphone. It should be in the list. Mine was called "Nvidia CK804 (hw:CK804,0)". Using this instead of pulse made it work all right. Now it's 100% fine. (yay !)

---

### Post by hanzj on 2008-11-04
o,besner,
Thank you. Thank you. Thank you.

I changed my Sound In source to the the one exactly like yours: "Nvidio CK804 (hw:CK804,0)"
For "Sound Out" and "Ringing", I left them the way the are: "Default Device (default)".

Please see attached screenshot.



(Using Skype 2.0.0.72, from Skype.com's repository)



[COLOR=Red]Nov 4, 9:30 am UPDATE: After rebooting, Skype no longer works again.
[/COLOR]

---

### Post by hanzj on 2008-11-04
I shut down the computer. I needed to go back online to make some calls on Skype and thus powered back on the computer. 

Guess what? Skype is not working again, even with the change of "Sound In" from "Default" to "Nvidia CK804 (hw:CK804,0)".

Aagh.

---

### Post by hanzj on 2008-11-04
I experimented with "Audio Devices" tab in Skype. 

Here is now what works:
Sound In: NVidia CK804 (hw:CK804,0)
Sound Out: pulse  [COLOR=Magenta][this is the most recent change, from Default device ][/COLOR]
Ringing: Default device (default)




...I wonder what will happen the next time I shutdown -- power-on.

---

### Post by o.besner on 2008-11-04
I have the exact same configuration and it works even after reboot. You need the Nvidia to get the microphone working and pulse to make it work even after reboot. I can't say why, but that's what I figured out after a while. Your skype should now work correctly :)

---

### Post by rugburns499 on 2008-11-05
> **o.besner said:**
> Hey,

Had the same problem with Skype, and I found something that works. 

1 - Install the Medibuntu repository (you've probably already done it, since it's the only way of seeing Skype in synaptic.

2 - Purge the previous Skype install, and install the package skype-static-oss (OSS stands for Open Sound System, so you kinda bypass pulse audio)

3 - check your sound settings first -- open a console and type "alsamixer". Does everything look normal ? Is your microphone muted ?

4 - Curse Skype for not caring at all about a decent Linux release. Skype should work now. It's kinda buggy since you have to close every other audio application while you are using it but hey - I'm not gonna watch a movie while I talk with my friends right ?
Thanks, that worked well for me.

---

### Post by frigaut on 2008-11-19
check this thread: 
[http://ubuntuforums.org/showthread.php?t=959541](http://ubuntuforums.org/showthread.php?t=959541)

---

### Post by james.wilde on 2008-11-19
> **ashmew2 said:**
> I wont tell you to try this or try that. I had the same problem myself (both with playback and recording). All i did was Go to 

Skype Options => Sound Devices => Sound out

and set it to : pulse

That worked for me , but you can try any other devices in the drop down list both for Sound IN and Sound OUT to get Skype to work!

Thanks ashmew2, that workd for me, too, but only after I had also set Sound in to pulse.

//James

---

### Post by james.wilde on 2008-11-19
Hm, I was a bit premture there.  I didn't go through the whole Skype Call Test.

Everything worked, but I thought th eplayback was pretty poor sound quality.  I notice that, wherever I had set the Capture slides under Recording in the Volume Control window, it zoomed down to zero as soon as the girl's voice started.  Then, when I was speaking, the sound quality was good as long as I moved the slider back up, but as soon as I let it go it began to slide down to zero again.

Any ideas, anyone?

TIA

//James

---

### Post by GandalfTheNerd on 2008-11-28
Not solved for me, alas.  PulseAudio Volume Meter shows a nice level, irrespective of the settings in Volume Control.  It says "Showing signal levels of ALSA PCM on hw:2 (USB Audio) via DMA, which all looks lovely.

However, none of the (many) "sound in" settings in Skype work.  Sound out is OK (set to "pulse").  Sound Recorder is happy - I can record and play back to my heart's content.  It sounds as if Skype should be set to "HDA Intel (hw:Intel,2)" given the PulseAudio display, but this doesn't work.  No error message - just no audio.

---

### Post by hanzj on 2008-11-28
GandalfTheNerd,
My skype won't work sometimes if I have Firefox browser open or an audio player (e.g. Totem, Rhythymbox) running. Try closing those.

---

