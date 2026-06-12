---
title: "New Users to Ubuntu - Problems with Browser Flash &amp; HTML5"
date: 2015-01-16
forum: New to Ubuntu
---

### Post by Bhavin_Prajapati on 2015-01-16
Hi Everyone! 

I'm new to the Linux OS, specifically Ubuntu, it was my New Year's resolution to use Ubuntu as my primary operating system this year and so far I am loving the experience. In the past I only used Linux distros for maybe a week at most. So far it's been a month. The forum has been really helpful so far, I used it to calibrate my mouse (RAT5) properly with the operating system and worked out great! :) 

I am however having problems with my flash player on Chromium. It just seems really choppy, anytime I go above 360p, it just starts lagging. I tried Chrome as well, no dice. I understand Adobe doesn't officially support flash in the same capacity. But even with HTML5, when I full screen, it is still choppy. I started to think it was my graphic card but I was able to play a 1080p movie on VLC beautifully. So my graphic card seems to be working to my knowledge and experience. Does anyone have any insight? I tried the forums but I wasn't able to find anything. 

I have a theory it might be a weak wifi connection to my computer. I am going to try connecting to Ethernet later tonight. 

Desktop Specs: 
Pentium D 830 3.0 ghz 
4 GB of Ram (32 bit so 3.5 GB) 
120 GB 10 000 RPM drive
Geforce 9500GT 1 GB Graphic Card 
D-link wireless 
Monitor: 27" IPS display at 2560 x 1440 
Dual booting with Windows 8.1 and Ubuntu 14.04 

I know it's an old computer, soon to be 10 years this May, but it is really been a champion computer. Can't game but does everything else so well. It's like a classic muscle car, you know it's terrible on gas but it's your classic.

---

### Post by sudodus on 2015-01-16
Welcome to the Ubuntu Forums :-)

Firefox and flashplugin-installer will usually make things work (provided you have a good connection).

Install only that package with

```
 sudo apt-get install flashplugin-installer
```

or a lot of non-free software for multimedia etc including flashplugin-installer with

```
 sudo apt-get install ubuntu-restricted-extras
```

I guess you are using some kind of GPU acceleration to play the 1080p video. vdpau? I don't think it will be used with the linux version of flash. You may succeed better if you use a lighter desktop environment than standard Ubuntu: medium-light Xubuntu or ultra-light Lubuntu.

You can either install separate systems (dual or multi boot) or install those desktop environments into Ubuntu and select session at the login screen.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by DuckHook on 2015-01-16
Hi Bhavin_Prajapati and welcome to Linux, Ubuntu and the Forums.

I know *exactly* how you feel. I love bringing old HW back to life using Linux and have done so for dozens of old boxes and laptops over the years. It's fun seeing the look on friends' and families' faces when that old thing they were about to consign to the junk heap can suddenly start running like a champ again.

But there are limitations. Yesterday's technology is still yesterday's technology, no matter how many coats of paint, restoration work and tender loving care we put into our precious little antique.

For a ten-year old box, your specs are spectacular. You must have either spent a fortune for it originally and bought it fully decked out, or you have been upgrading it since. It is fully capable of running the latest distros in full 3D and there ought to be no reason it would choke on a small flash video. Moreover, if you have Chrome installed, then you should also have the latest Google-supported *Pepperflash* plugin installed as well, and this will usually do the trick. Please be aware that Chromium is the FOSS version of Chrome and does not come with native *Pepperflash* support unless you take special measures to install it. But if you say that Chrome was also no dice, then the lack of *Pepperflash* is unlikely to be the problem.

So do as *sudodus* suggests and try installing native flash support first. If that doesn't solve the problem then let's look at other things like WIFI, system loads and even installing *Pepperflash* standalone.

---

### Post by Bhavin_Prajapati on 2015-01-16
> **DuckHook said:**
> Hi Bhavin_Prajapati and welcome to Linux, Ubuntu and the Forums.

For a ten-year old box, your specs are spectacular. You must have either spent a fortune for it originally and bought it fully decked out, or you have been upgrading it since. It is fully capable of running the latest distros in full 3D and there ought to be no reason it would choke on a small flash video. Moreover, if you have Chrome installed, then you should also have the latest Google-supported *Pepperflash* plugin installed as well, and this will usually do the trick. Please be aware that Chromium is the FOSS version of Chrome and does not come with native *Pepperflash* support unless you take special measures to install it. But if you say that Chrome was also no dice, then the lack of *Pepperflash* is unlikely to be the problem.

So do as *sudodus* suggests and try installing native flash support first. If that doesn't solve the problem then let's look at other things like WIFI, system loads and even installing *Pepperflash* standalone.

> **sudodus said:**
> Welcome to the Ubuntu Forums :smile:

......

I guess you are using some kind of GPU acceleration to play the 1080p  video. vdpau? I don't think it will be used with the linux version of  flash. You may succeed better if you use a lighter desktop environment  than standard Ubuntu: medium-light Xubuntu or ultra-light Lubuntu.

You can either install separate systems (dual or multi boot) or install  those desktop environments into Ubuntu and select session at the login  screen.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

Hey Duckhook and Sudodos! 

Haha I don't think some of those parts were even available at the time of purchase. I'll break it down for you :) ... 

[LIST]
[*]Graphic Card upgrade $15 for a used 9500 GT... I thought it was a steal!
[*]Hard drive from 250 GB 7200 RPM... another $80 (clearance price) got me a WD 10 000 RPM drive
[*]Ram was $50 in total for the ugprade, I added another 3 GB more
[*]Bought a new case for $40... came with 5 fans (it was a buy because the Pentium Ds were notriously hot)
[/LIST]

Considering the type of upgrades and how much it costs, they were all great add ons for it's 10 year history. I did however tell myself that if the desktop breaks, I have to buy a new one. No more repairs/upgrades. 

As for vdpau, yes I used VLC media player to play the HD movie I had on my hard drive. 

Okay so I installed Pepper flash, or I should say, reinstalled it, I had it before. On Firefox (which will probably turn into my default), the flash plug in works great. I just can't full screen HD videos but in the browser, it was the first time I saw it play without any lag/gitters. I guess that is the trade off I am willing to make, just no full screen videos. Otherwise everything else works. Chrome and Chromium both work but I notice a choppy lag/line when the video plays in HD, Firefox doesn't have it. 

I have to still try using ethernet instead of wifi, but this requires me to move the PC, I may try it later on. I also install all the updates Ubuntu had, incase it was a system glitch. 

So in summary, here is where I am at 
-Firefox and HTML5 videos work fine with no lag or choppiness in the browser 
-All browsers including Chrome and Chromium lag in full screen but VLC does play everything I need in HD so I know it is isolated towards the browsers 
-I am pretty sure I installed Pepper Flash because in all the plug ins, it says Adobe Flash Version 16 etc etc 
-Overall, I think I can live with it if this is the best I can get 

Do you think it is just a hardware limitation with Ubuntu? 

PS - thanks again for your welcome and your help of course :)

---

### Post by mooreted on 2015-01-16
You didn't mention whether you installed the Nividia drivers. The Nouveau open source drivers are still a bit weak. As you mentioned, make sure you have a fast, stable Internet connection as well.

---

### Post by JeQhdMD on 2015-01-16
What does SpeedTest show?  [http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by Bhavin_Prajapati on 2015-01-17
Good news everyone! I got everything working. Turns out it was a drivers issue. I installed the new Nvidia 340 drivers and it works perfectly. As expected. I can't believe I didn't think of this, it's funny because whenever I reformat/reinstall Windows, the first driver I immediately install are the graphics. Anyways thanks everyone for your help. 

I also discovered my USB D-Link adapter was not working well with my usb hub that I use. So I connected it directly into the PC, my network speed increased from 5 mbps to 20 which is what I would expect. 

In a span of a few days, I probably learned more about Linux/Ubuntu than I did since I first heard about in 2003. Thanks again for all your help everyone! It means a lot, I'm liking Linux more and more as the days go by...

---

### Post by Bhavin_Prajapati on 2015-01-17
I just did a proper test, with a good internet connection I was able to play a 2K Trailer with some latency from YouTube (Godzilla 2014 and Guradians of the Galaxy) but most importantly, 1080p was  flawless.

---

### Post by vasa1 on 2015-01-17
Hi, you may like to mark your thread [SOLVED] as described here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by sudodus on 2015-01-17
> **Bhavin_Prajapati said:**
> Good news everyone! I got everything working. Turns out it was a drivers issue. I installed the new Nvidia 340 drivers and it works perfectly. As expected. I can't believe I didn't think of this, it's funny because whenever I reformat/reinstall Windows, the first driver I immediately install are the graphics. Anyways thanks everyone for your help. 

I also discovered my USB D-Link adapter was not working well with my usb hub that I use. So I connected it directly into the PC, my network speed increased from 5 mbps to 20 which is what I would expect. 

In a span of a few days, I probably learned more about Linux/Ubuntu than I did since I first heard about in 2003. Thanks again for all your help everyone! It means a lot, I'm liking Linux more and more as the days go by...

> **Bhavin_Prajapati said:**
> I just did a proper test, with a good internet connection I was able to play a 2K Trailer with some latency from YouTube (Godzilla 2014 and Guradians of the Galaxy) but most importantly, 1080p was  flawless.

Congratulations :KS

---

### Post by mooreted on 2015-01-17
Awesome, good job. :)

---

### Post by DuckHook on 2015-01-17
> **Bhavin_Prajapati said:**
> ...I don't think some of those parts were even available at the time of purchase. I'll break it down for you :) ... 

[LIST]
[*]Graphic Card upgrade $15 for a used 9500 GT... I thought it was a steal! 
[*]Hard drive from 250 GB 7200 RPM... another $80 (clearance price) got me a WD 10 000 RPM drive 
[*]Ram was $50 in total for the ugprade, I added another 3 GB more 
[*]Bought a new case for $40... came with 5 fans (it was a buy because the Pentium Ds were notriously hot) 
[/LIST]

Considering the type of upgrades and how much it costs, they were all great add ons for it's 10 year history. I did however tell myself that if the desktop breaks, I have to buy a new one. No more repairs/upgrades.You have years of use left on that machine. I'm sure you're proud of the job you've done. Many people these days don't understand the attraction to souping up antiques, but for less than $200, you've kept an old horse running for a period during which most others will have traded for three boxes. Even if you do decide to buy a bright and shiny new toy, I hope you retire Old Daisy to a place of honour: a server of some sort would be appropriate.

Glad you worked everything out and learned so much in the process.

Good luck and Happy Ubuntuing!

---

### Post by Bhavin_Prajapati on 2015-01-17
I actually have a Macbook Pro Retina 15" but I promise you, I use my desktop more... I think the best addition that I didn't add in the list was my mechanical keyboard purchase... 95% of people would never understand and it is the keyboard more than anything that keeps me from working more on the Mac. I am actually going to install Ubuntu on my Mac in a few weeks, I'm excited to see how that goes. Should be fairly straight forward :) 

Thanks again for your help DuckHook

> **DuckHook said:**
> You have years of use left on that machine. I'm sure you're proud of the job you've done. Many people these days don't understand the attraction to souping up antiques, but for less than $200, you've kept an old horse running for a period during which most others will have traded for three boxes. Even if you do decide to buy a bright and shiny new toy, I hope you retire Old Daisy to a place of honour: a server of some sort would be appropriate.

Glad you worked everything out and learned so much in the process.

Good luck and Happy Ubuntuing!

---

