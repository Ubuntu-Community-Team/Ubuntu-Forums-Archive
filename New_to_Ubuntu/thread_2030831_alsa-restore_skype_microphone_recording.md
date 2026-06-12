---
title: "alsa-restore skype microphone recording"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-07-21
I was playing with recording settings and managed to wreck the ability for other people to hear me on skype (ie my recorder settings)

Is there a way I can use alsa-restore or some other method to restore the defaults for alsamixer and "PulseAudio Volume Control"

---

### Post by NikTh on 2012-07-21
Hi ,
try ```
 sudo alsa force-reload
``` 

It is not restore command , i don't know how you configured your alsa or pulseaudio files.

You can also try ```
alsamixer
``` from terminal and see if something about record is muted. 

Regards

---

### Post by Kevin McCready on 2012-07-21
thanks
the reload didn't work, even after I turned computer off and on.
The alsamixer settings are all turned on.
I think the "PulseAudio Volume Control" settings might be wrong.
Do you know what the defaults are for each option in each of the five tabs?

---

### Post by NikTh on 2012-07-21
> **Kevin McCready said:**
> 
I think the "PulseAudio Volume Control" settings might be wrong.
**Do you know what the defaults are for each option in each of the five tabs?**

No , but i think that if you purge pulseaudio and remove the hidden .pulse file and then re-install pulseaudio , it will returns to original settings.

So you can try 
```
sudo apt-get purge pulseaudio pavucontrol 
rm -rf ~/.pulse 
sudo apt-get install pulseaudio pavucontrol
```Regards

---

### Post by Kevin McCready on 2012-07-21
yep that worked. Thanks sooooo much.

It would be great now to be able to capture sound off youtube. Which is what I was trying to do when I managed to wreck things.

---

### Post by NikTh on 2012-07-21
> **Kevin McCready said:**
> yep that worked. Thanks sooooo much.
Hi ,
Glad that worked. 

> **Kevin McCready said:**
> It would be great now to be able** to capture sound off youtube.** 
I do not understand (sorry but my English are in lower state) exactly what you mean by that i have bolded.

Regards

---

### Post by Kevin McCready on 2012-07-21
When I listen to youtube music I want to record it. I used arecord in the terminal, but it sounds awful. Maybe the parameters for arecord are not right. When I use Audacity or "sound recorder" the sound is also bad.

---

### Post by Kevin McCready on 2012-07-21
PS what languages do you speak? I speak a little mandarin and can read chinese.

---

### Post by NikTh on 2012-07-21
> **Kevin McCready said:**
> When I listen to youtube music I want to record it. I used arecord in the terminal, but it sounds awful. Maybe the parameters for arecord are not right. When I use Audacity or "sound recorder" the sound is also bad.

Hi , 

hmm .. ok , i cannot tell you how you can download music from you tube , its against forum rules. [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

You can google it to find more info.

Also you can mark this **thread as solved **from **thread tools.**
Regards

---

### Post by Kevin McCready on 2012-07-21
no no no
I didn't mean to say youtube in particular. I meant any website. for example:
[http://www.aspenideas.org/session/china-and-democracy](http://www.aspenideas.org/session/china-and-democracy)

---

### Post by Kevin McCready on 2012-07-21
PS Who would possibly want to break the rules and offend google? Me? No no no.

---

### Post by Lyfang on 2012-07-21
Plug in a 3.5 mm audio cable in the in and out jacks. See also: [Audacity record what you hear]("https://answers.launchpad.net/ubuntu/+source/audacity/+question/133969")

---

### Post by Kevin McCready on 2012-07-21
thanks
I didn't plug in anything but I did follow the instructions which said:
"Install the pavucontrol package. Start recording in audacity. Open pulseaudio volume control (pavucontrol), on the tab "recording application", change audacity to take its input from "Monitor of <your soundcard name>". Now you're all set up to record "what you hear"."

On my version of "PulseAudio Volume Control" I went to the recording tab and selected "Monitor of Internal Audio Analog Stereo" where it asked "Alsa Capture from".

Of course I would never record from youtube and upset the good google. No no no. Hey they'll just cut me off from the internet altogether as soon as they've amasssed enough power. I'm sure they would do no evil. I'm really sure.

---

