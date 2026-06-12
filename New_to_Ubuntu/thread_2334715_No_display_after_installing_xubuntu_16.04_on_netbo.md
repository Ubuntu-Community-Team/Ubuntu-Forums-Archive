---
title: "No display after installing xubuntu 16.04 on netbook"
date: 2016-08-21
forum: New to Ubuntu
---

### Post by boilingchip on 2016-08-21
Hello guys I'd like some help and advice regarding my issue. I thought about trying out a linux os on an old Packard Bell kav60. Created a bootable usb drive to test out several variations until I got to xubuntu which was surprisingly good when I tested it. So I decided to install it and had no issues there. It asked me to restart after finishing the installation which I did. Got to the text option which ask what os boot on and chose xubuntu. Whilst it was booting up the screen turned itself off for some reason so I turned it back on by pressing the power button. It powered up I was only getting a blank display.  My mistake was force shutting it down during this time and now when I press the power button the display would not even power up. Took out the hard drive and checked it on my laptop and it was fine. Took the ram out to see if I can get a memory error beep and got nothing. It is still powering up but I've got no display so I have no idea if I screwed up the mobo or the cpu. I should point out that I didn't tick the box which asked to install 3rd party drivers (which I should have done). Is there any way to get on the text interface in order for me to diagnose the problem? Have I screwed up the bios because of the force shutdown and basically bricked the netbook?

---

### Post by mörgæs on 2016-08-22
Hi, welcome to the fora.

The KAV60 has a weak Atom processor and I suggest that you try a fresh install of Lubuntu 16.04.1 (not 16.04.0).

---

### Post by grahammechanical on 2016-08-22
When you ran the Try/Live session everything went wel?. And this was the case with several test runs of Ubuntu flavours?

There is one big difference between the live session and an installed session. The live session uses an open source video driver. When we install and tick the box "Install third party software" we get some free but third party audio and video codecs and also a free proprietary video driver.

So, if the live session using the open source video driver works well but the installed session with the proprietary video driver gives you a black screen, I would point the finger at the proprietary video driver.

It might be best for you to re-install and this time do not tick the box "Install third party software." After installation we can install the third party audio and video codecs. They are in a package called Restricted Extras. And the Additional Drivers utility will let us install a proprietary video driver if we want to experiment.

Regards.

---

### Post by boilingchip on 2016-08-22
Thank for your reply. Yes I did get the 16.04.1 and how would I be able to do a fresh install if the display doesn't turn on?

---

### Post by boilingchip on 2016-08-22
> **grahammechanical said:**
> When you ran the Try/Live session everything went wel?. And this was the case with several test runs of Ubuntu flavours?

There is one big difference between the live session and an installed session. The live session uses an open source video driver. When we install and tick the box "Install third party software" we get some free but third party audio and video codecs and also a free proprietary video driver.

So, if the live session using the open source video driver works well but the installed session with the proprietary video driver gives you a black screen, I would point the finger at the proprietary video driver.

It might be best for you to re-install and this time do not tick the box "Install third party software." After installation we can install the third party audio and video codecs. They are in a package called Restricted Extras. And the Additional Drivers utility will let us install a proprietary video driver if we want to experiment.

Regards.

The live session went really well. Got libre writer working and played some videos from youtube which makes it perfect for basic task like internet browsing and word processing. It was a lot more responsive compared to windows xp. I mentioned that I didn't tick the box to install third party software as it was already working quite well. I guess the only issue now is how do I go about reinstalling xubuntu when the display does not even turn on.

---

### Post by boilingchip on 2016-08-22
Okay for some reason when I turned it on today the display worked. Morgaes was right about the os as I downloaded 16.04 and not 16.04.1 from the website (didn't see it until I checked the title of the downloads). Downloading the new one now and I'll let you guys know how I get on.

---

### Post by boilingchip on 2016-08-22
Got it working now although some little issues:

- After choosing to boot up xubuntu, it gets to the xubuntu loading screen and then the netbook goes into sleep mode for a few seconds. I have to wait for a few seconds and push the power button again which then opens up to the interface
- Wifi is a bit temperamental
- Choosing to shut down puts the netbook into sleep mode instead of actually shutting the system down

Apart from that no issues so far. I've tried Zorin and lubuntu out during the live sessions and xubuntu looks a bit quicker compared to other two.

---

