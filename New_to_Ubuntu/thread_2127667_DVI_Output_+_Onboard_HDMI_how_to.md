---
title: "DVI Output + Onboard HDMI how to?"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by lolocoian on 2013-03-20
Hello, im extremely new to Ubuntu, just installed it and i loaded the Nvidia Drivers for my GTS450 which has an non working HDMI output. In Windows i have extended the screen from my monitor to my Samsung TV. The LG Monitor is connected to my GTS450 DVI output and my TV is connected to my Motherboards HDMI output and it works just fine. How can i get this set-up in Ubuntu. Thanks in advance for your help. This is my first Thread in Ubuntu Forums.

---

### Post by AlecJ on 2013-03-20
My GT520 has to have the TV turned on and on the HDMI input before you bootup as it need to "see" the monitor at boot.
In system tools Administration you will find "Nvidia X server setting" where you can set up the screens etc

---

### Post by lolocoian on 2013-03-21
Thanks I looked there but it the thing is the HDMI in my GTS450 is dead so in windows i have to use my onboard HDMI output instead. I can extend my screen to the TV but not via the Nvidia Control Panel (Win). I have to do it via the normal menu (left click in background - properties). Is this possible in Ubuntu? 2 different video cards one ONboard HDMI output and a monitor via DVI and still extend the screens?

---

### Post by DuckHook on 2013-03-21
Hi and welcome to the forums.

> **lolocoian said:**
> ...i have to use my onboard HDMI output instead... Is this possible in Ubuntu? 2 different video cards one ONboard HDMI output and a monitor via DVI and still extend the screens?

The short answer is "no". Not with all of the eye candy at any rate. You may be able to kludge something together using Xinerama (I've never tried it), but you won't have compiz, therefore no Unity 3D. Linux support for spanning the DE across multiple video cards is not good. Spanning across the same video card works well but the choke point is multiple cards.

If you want to pursue this further, you need to post far more info. Please read through [this]("http://ubuntuforums.org/showthread.php?t=1422475") sticky and post the recommended output defining your hardware. However, I should alert you that it likely won't change the answer. With the price of video cards these days, why not just buy a new or used card that supports dual channels: DVI & HDMI? 512 MB is likely all you need unless you are a gamer. Probably available for us little as $20 on ebay.

---

### Post by lolocoian on 2013-03-22
Ok, i changed my video card to a GTS250 i have now set up the twinview and i have the monitor extended! but im missing audio output thru HDMI. and i want to trim the screen a bit so it fits just right. Any Ideas?

---

### Post by DuckHook on 2013-03-22
Will have to research the audio aspect as I funnel all audio through system audio rather than HDMI.

Do you need twinview? Did you install the proprietary driver? If so, does your card support simply bridging your Desktop from one display to the next without twinview? This would be simpler, which is always better.

By trimming screen, I take it that you mean the edges of your desktop are not visible due to TV overscan? If so, then the solution is to turn off overscan on your TV. Most TVs will have a setting to do this, but it is called different things by each manufacturer. On my Sharp it's called "dot-for-dot". On others it may be called "computer mode" or similar. You will have to read your TV docs to see.

If this doesn't work, you can install the proprietary driver and use nvidia's overscan compensation mode in the N-Vidia Settings Manager app. Some drivers will have this option, some won't depending on your card and the driver you installed. If no such option, you can also try:```
sudo apt-get install nvtv
```which might allow you to set overscan on (I've never used it, so you will have to go through the man page, learn and configure it yourself).

---

### Post by DuckHook on 2013-03-22
Re: Audio

A Google search turned up [this]("http://askubuntu.com/questions/112512/ubuntu-refuses-to-output-audio-via-hdmi"), [this]("http://askubuntu.com/questions/226090/how-do-i-output-audio-through-hdmi") and [this]("http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/"), which may be relevant. You may have more results if you Google yourself. Of these, the simplest and least disruptive for you would be to do:```
sudo apt-get install pavucontrol
```open *pulse audio volume control*, navigate to "Configuration" tab and select the HDMI profile. This is might create the HDMI profile that you could then access through your standard sound settings app.

---

### Post by lolocoian on 2013-03-23
Thanks! I adjusted it from my tv and it was just right! :D 

now i just have the audio problem. I have video but no audio.

---

### Post by lolocoian on 2013-03-23
I installed pavucontrol and it only shows me SPDIF as an output. No HDMI configuration. im Clueless.

---

### Post by DuckHook on 2013-03-23
> **lolocoian said:**
> I installed pavucontrol and it only shows me SPDIF as an output. No HDMI configuration. im Clueless.

I'm also out of my league here, but try SPDIF (which means digital audio). If that doesn't work, then you must provide info that I asked for earlier: are you using proprietary drivers or the open source drivers? To my knowledge, you must have proprietary driver running to get HDMI audio because it is the video driver that provides the HDMI audio functionality, which the open source video driver does not have, although I could be wrong.

As I mentioned, this is new ground to me and I hope someone more knowledgeable jumps in here.

---

