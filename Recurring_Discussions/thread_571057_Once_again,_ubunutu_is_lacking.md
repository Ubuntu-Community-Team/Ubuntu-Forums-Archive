---
title: "Once again, ubunutu is lacking"
date: 2007-10-08
forum: Recurring Discussions
---

### Post by Beve Stallmer on 2007-10-08
I must be a masochist I guess, bec I keep trying this stuff. Every few years I give Linux a go, each time I end up walking away shaking my head in disbelief.

This time I tried the new Live beta disc on my 4 year old Dell laptop. To my amazement it loaded perfectly, so I installed it, using the whole disk.

I was soon listening to mp3s and watching videos, although I noticed that it kept wanting to load huge updates from the Internet (very slowly btw, 28kbps max) and transfers from my other laptop running Vista were awful (10 mins to transfer a 10MB mp3 file!)

Another problem I noticed was that the default wireless settings were not saved (set it to WPA2 personal, and every time I come back to it it's reverted to WPA personal).

Anyhoo, messing about with the desktop settings, I saw that I was offered several setting for the video card, from basic effects to advanced settings. 

Now this laptop has a Nvidia FX Geforce 5200 card, but I was not able to select anything but the most basic screen effects (ie no effects at all). I then saw that the drivers installed were for the "new" NVidia cards, which mine is not. So I foolishly but innocently went to the add/change update manager and deselected the "new" driver and selected the ordinary nvidia drivers, hoping this would allow me to use the card a bit better. I did not select the legacy driver.

It complained a bit about "first uninstall/delete that before you download this", so I followed that, then before downloading the new drivers I put the lappy into Hibernate.

Coming back the next morning, I tried to wake it up and ended up with a screen that was just lines and weird slowly changing colors, like the screen was burning!

From that point on it kept rebooting itself, unable to get into X, spent 2 hours trying all the advice on this forum, running commands from the CLI to reconfigure, still no startx, and when I eventually tried to re-install the whole shebang from the Live CD, it also now just gives me diagonal lines across the screen after the first few screens, which means it's probably damaged the card, because it never did that the first time.

So it's still amateur hour with Linux, but I do detect some improvements.

---

### Post by Pumalite on 2007-10-08
That's Linux; you can fool around with it until you break it.

---

### Post by Beve Stallmer on 2007-10-08
Changing the video driver shouldn't break it. Never has with the other OSes I've used. :(

---

### Post by Pumalite on 2007-10-08
Sure you can do it installing the wrong driver or not installing it right. You had a working system. What happened?.

---

### Post by Beve Stallmer on 2007-10-08
Read above; tried to use the right driver for the card, disaster. Not an uncommon experience, looking at other threads.

---

### Post by Beve Stallmer on 2007-10-08
Re-installing the Redmond Beast OS on the Dell as we chat here ... looking at the bloody Windows waving corporate flag as a write, lol.

Oh Linux, you are a disappointment.

---

### Post by BLTicklemonster on 2007-10-08
It's a new driver. I have the fx 5200 and use the nvidia-glx-new drivers and everything is fine here. Not sure what you ran into, but don't give up.

---

### Post by Shazaam on 2007-10-08
> **Beve Stallmer said:**
> Read above; tried to use the right driver for the card, disaster. Not an uncommon experience, looking at other threads.

So installing the wrong (by your admission) video driver isn't supposed to break X? How does that work in ANY distro?
Oh, and Uncle Bill is laughing all the way to the bank.

---

### Post by picopir8 on 2007-10-08
So let me summarize. You download the BETA version of ubuntu and then complain about problems and that there are lots of updates.

Do you mix up cake mix then eat it before it goes in the oven and complain that its to soggy?  Do you show up to work 2 hours early and complain that nobody else is at work?

BTW...
Changing a video driver will not break any flavor of Linux.  You can always boot to a command line, uninstall the bad driver, then install the correct driver.  If the wrong driver gets installed in any other OS, the same procedure is needed (ie booting to safe mode with windows).  If you truly had a wrong video driver loaded in Windows, there is no possible way you would have a display unless the wrong driver was compatible with your video card.

---

### Post by Beve Stallmer on 2007-10-08
This beta is almost a final version. The uninstall at command line stuff didn't work for me. Yes, changing the driver DID break this installation, and I'm NOT the only one to have this happen. LOL, the denial is amazing!

Give it another go? I tried, but this time the installation CD could not get the screen to work, just shows diagonal lines when it tries to start the window manager. It must be picking up some bad config data off the hard drive, bec. it never did that the first time!

---

### Post by etxkesa on 2007-10-08
I have an Nvidia 5200 on my desktop. In order to get the correct video resolution for my CRT display, I downloaded the Linux driver package from the Nvidia web site, stored it somewhere I could access it from the comand line, and then followed the instructions (i.e. sh nvidia...). It goes away and happily builds the drivers and installs them automatically. Only problem I've had is that I have to repeat the process each time the kernet gets upgraded. 




> **Beve Stallmer said:**
> I must be a masochist I guess, bec I keep trying this stuff. Every few years I give Linux a go, each time I end up walking away shaking my head in disbelief.

This time I tried the new Live beta disc on my 4 year old Dell laptop. To my amazement it loaded perfectly, so I installed it, using the whole disk.

I was soon listening to mp3s and watching videos, although I noticed that it kept wanting to load huge updates from the Internet (very slowly btw, 28kbps max) and transfers from my other laptop running Vista were awful (10 mins to transfer a 10MB mp3 file!)

Another problem I noticed was that the default wireless settings were not saved (set it to WPA2 personal, and every time I come back to it it's reverted to WPA personal).

Anyhoo, messing about with the desktop settings, I saw that I was offered several setting for the video card, from basic effects to advanced settings. 

Now this laptop has a Nvidia FX Geforce 5200 card, but I was not able to select anything but the most basic screen effects (ie no effects at all). I then saw that the drivers installed were for the "new" NVidia cards, which mine is not. So I foolishly but innocently went to the add/change update manager and deselected the "new" driver and selected the ordinary nvidia drivers, hoping this would allow me to use the card a bit better. I did not select the legacy driver.

It complained a bit about "first uninstall/delete that before you download this", so I followed that, then before downloading the new drivers I put the lappy into Hibernate.

Coming back the next morning, I tried to wake it up and ended up with a screen that was just lines and weird slowly changing colors, like the screen was burning!

From that point on it kept rebooting itself, unable to get into X, spent 2 hours trying all the advice on this forum, running commands from the CLI to reconfigure, still no startx, and when I eventually tried to re-install the whole shebang from the Live CD, it also now just gives me diagonal lines across the screen after the first few screens, which means it's probably damaged the card, because it never did that the first time.

So it's still amateur hour with Linux, but I do detect some improvements.

---

### Post by picopir8 on 2007-10-08
> **Beve Stallmer said:**
> This beta is almost a final version. The uninstall at command line stuff didn't work for me. Yes, changing the driver DID break this installation, and I'm NOT the only one to have this happen. LOL, the denial is amazing!


I have met several people who SCREWED UP their Window manager by installing the wrong driver, but I have NEVER heard of anyone BREAKING their OS by installing a bad video driver.  In every case has been recoverable.

What "Didnt Work" with the command line?  Were you somehow not able to boot to the command line? Were unable to change the driver once at the command line?

---

### Post by Beve Stallmer on 2007-10-09
Sorry, guys, no time to analyse why this happened, no the OS was not broken completely but enough to make me spit the dummy, haven't got time to delve into all the arcane commands to get it all working again once the *sudo dpkg-reconfigure -phigh xserver-xorg* didn't work, just want you to know that I'm a fairly knowledgeable user in other ways (Windows expert, and ex-mainframe programmer from way back) so I shouldn't be getting stumped with significant technical difficulties every *freaking *time I try this OS. And why on earth would it not install from the CD 2nd time round? That's very odd, considering it should be ignoring any borked data on the HDD.

But I am pleased to see progress in things like writing NTFS and WiFi recognition, also USB working much better these days. Keep it up, I'll probably permanently join you within 5 years.

---

### Post by Jimmey on 2007-10-09
> **Beve Stallmer said:**
> . LOL, the denial is amazing!

We have working Linux installs, you don't. Us 1:0 You.

> so I shouldn't be getting stumped with significant technical difficulties every freaking time

The solution to your problem has been posted in this thread, so if you're still having difficulties, you must be a few sandwiches short of the full picnic. 

> Windows expert, and ex-mainframe programmer from way back

Wow. No-one cares. It got you no-where this time, did it? 

> Keep it up, I'll probably permanently join you within 5 years.
Wow, we feel so priviledged. Do "we" even want you to "join us"? Forget it.

You know, you'd be suprised how many threads like this we get.

> I'm going back to Windows. Linux is poor, because I've been experiencing [insert easily solveable problem here], and because my first experience was like this, that means that every Linux distro in the world is **not ready for the desktop!**

Some of the more patient people have tried to help you.

I say, yawn. If you're happy with Windows, stick with it, Mr Expert - We don't need you in these forums!

---

### Post by Vorian on 2007-10-09
> **Beve Stallmer said:**
> 
 Keep it up, I'll probably permanently join you within 5 years.

OK, see you then :)

Thread Closed

---

