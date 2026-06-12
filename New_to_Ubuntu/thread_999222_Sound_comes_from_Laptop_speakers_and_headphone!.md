---
title: "Sound comes from Laptop speakers and headphone!"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Mularkey23 on 2008-12-01
Sound comes from my laptop speakers even when I have headphones plugged in (in this case, going to external speakers) 

Before upgrading to Hardy, sound would play from my external speakers and my laptop speakers, but when I hit mute, my computer speakers would shut off.  Now, if I hit mute the external speakers mute too.  I don't want my shitty laptop speakers to play anymore!:(  I have a lenovo, and I've tried everything in this thread:

[http://ubuntuforums.org/showthread.php?t=965073&highlight=lenovo+speakers&page=2]("http://ubuntuforums.org/showthread.php?t=965073&highlight=lenovo+speakers&page=2")

Also, when I go into alsamixer, there is no bar allowing me to adjust the volume for the headphones.

Any help is greatly appreciated! :)

---

### Post by lhb1142 on 2008-12-01
Hi. I had the same problem until I figured out what to do. Go to the top of your screen and right-click on the Volume icon (reads Master: 100% [or a different percentage]). Click on Open Volume Control. Go to Edit and make sure everything is checked.

Then go to the Playback tab and open it. You will see a slider marked 'Front.' Click on the very bottom icon below this; this will mute that control.

That's it. You will hear sounds from your headphone jack and NOT from your computer speakers.

I hope this helps you.

---

### Post by YetiConfetti on 2008-12-02
Lo

I'm having this same problem on my Sony Vaio SZ series with Ubuntu 8.10.  I have headphones plugged in, yet I hear sound through the speakers.

In my volume control, I only see Master and PCM.

Anyone have any ideas?  Any help is appreciated.

---

### Post by lhb1142 on 2008-12-02
This is from my previous post:

"Go to the top of your screen and right-click on the Volume icon (reads Master: 100% [or a different percentage]). Click on Open Volume Control. Go to Edit and make sure everything is checked.

"Then go to the Playback tab and open it. You will see a slider marked 'Front.' Click on the very bottom icon below this; this will mute that control."

Perhaps I did not make myself clear: when you go to Edit within the Volume Control, you first click on Edit and Preferences will appear. You click on Preferences. Then, in the dialog box which appears ("Select tracks to be visible"), make sure EVERYTHING is checked.

Then, after you have done this and closed the dialog box, in the Playback section of the Volume Control you will indeed see that 'Front' indicator. Merely mute that control as indicated above (a red 'X' will appear over its 'sound' icon) and you will no longer hear any sound from your computer speakers. But you WILL hear sound via your headphone jack. You can use this jack for headphones or amplified computer speakers.

Should you ever wish to re-enable your computer speakers again, merely 'unmute' the 'Front' slider control by clicking on the sound icon. The red 'X' will disappear and the internal computer speakers will function once again.

---

### Post by YetiConfetti on 2008-12-02
Right, I read your above post but there is no 'edit' in my volume control.  I click on Preferences, and there are only two things to check: Master and PCM, both of which are checked and already visible under playback.  There is no 'Front' slider.

---

### Post by lhb1142 on 2008-12-03
Are you right-clicking on the Volume icon in the upper right corner of the computer screen? When you do so, you will certainly see Preferences - but that is NOT - repeat NOT - what you must select. Instead, select 'Open Volume Control.' Within THAT, you will indeed see an 'edit' choice through which, once you click on it, you will find the proper 'Preferences' to select and then you can follow the rest of my instructions. Re-read them carefully.

I am running Ubuntu 8.04 'Hardy Heron' but I should think that my instructions would apply to all current versions.

---

### Post by liqwiz on 2009-02-07
I had already figured your steps out by myself, still the problem continues to exist.
I can mute and unmute the "**Front**" as I like, **it mutes All sound** (not just the speakers).

In the past I had solved this by adding some lines of text to a config file (from Alsa) telling it in detail what model soundcard I have. I can't find this solution anymore and since the problem is well known by now I hoped to find it solved with 8.10 or with this topic atleast.

Thanks for the feedback the others where given (and helped with) already, it just doesn't do it for me. I'm left behind.

---

### Post by gogetakame on 2009-11-04
Okay i have an hp dv6-1353cl with ubuntu 9.10 full release now.
I was having trouble with the sound as well. i would plug in earphoens and sound would play from both earphones and speakers.
so i opened up alsamixer in terminal and i messed around with the settings
so with your earphones plugged in. all u hafta do is set Speaker to 0.
then sound should only come from the headphones. if the sound is soft, then change up the scales for Master, PCM, and Front till you find a suitable combo.
for me i hav PCM and Front at 100 and i adjust Master up and down to get it to increase volume.
this is a hassle but it does work for me at least...
hope this helps...

---

### Post by stoned94 on 2010-03-28
I had the same problem with Ubuntu 9.10.
This is how I finally got it fixed: I installed "Genome Alsa Mixer" with Synaptic Package Manager: search for **gnome-alsamixer**. 
When done, open it from the menu: Application -> Sound & Video -> GENOME ALSA Mixer.
There is a check box under the sliders "Headphone Jack Sense". When checked, the internal speakers of my laptop just went mute, and the sound still came out of the external speakers connected to headphone jack - Et voilà!

I hope this will help others who (like me) found this thread with this problem!

The strange thing is that this option was mentioned in other threads, but in the System/Preferences/Sound interface. Maybe it was there in previous Ubuntu releases. Also IMO muting the internal speakers when headphones are plugged in should be the default behavior.

---

### Post by duke.tim on 2010-04-06
[https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

This should help I have a dv6 and this has solved a problem similar to this. you also might want to check the alsamixer settings
```
alsamixer
```
to exit press "ctrl c"

---

