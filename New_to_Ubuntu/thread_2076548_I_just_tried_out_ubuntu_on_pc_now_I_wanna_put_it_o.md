---
title: "I just tried out ubuntu on pc now I wanna put it on my powerpc -help plz-"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Redzky on 2012-10-26
Ya, I like it. Pretty clean and it's crazy to think that it's free too. No wonder the dl site is so pushy about donations.

Anyway, I spent the past 2 days trying to figure out a way to do a usb drive boot install on my older Aluminum Powerbook g4 1.5ghz but I finally gave up. I was trying to convert an .iso to .img on terminal but when the file got converted to .img file would disappear write before the next step. 

I think I'm just gonna go out and buy a DVD-rw tomorrow and burn mintPPC or lubuntuPPC on it for my mac.

I got a question though. Am I going to have any problems if I download the PowerPC .iso on my pc, burn to disk then install on my mac or do I have to download on my mac?

I know it's a newbie question. Either way I'm buying a DVD-rw, so I can burn over it if it flops. Just curious to know for personal sake. Thanx.

---

### Post by Lars Noodén on 2012-10-26
Sometimes it works just to use dd to write the ISO image to the USB stick.  

About burning the CD RW or DVD RW, it is a standard so it does not matter which machine you download and burn it on.  It should be the same regardless. 

Lubuntu will run nicely on your PPC.  With the latest version, 12.10, there can be a little strangeness during the installation for some graphics cards.  So it might be necessary to boot with special parameters to get things going during the installation.  Other than that, the installation goes smoothly.

---

### Post by DougieFresh4U on 2012-10-26
You may find better help [here]("http://ubuntuforums.org/forumdisplay.php?f=328")

---

### Post by Redzky on 2012-10-26
Alright, It's on there. I deleted os x because I honestly never enjoyed it that much. All the programs on my PC seem better anyway. 

Lubuntu is cool though. I'm downloading backtrack5 r3 via torrent for my next project. I'm gonna replace the ubuntu.iso file on my flash drive with it. That way I can boot live and do some penetration testing. 

Well, thanx for the help guys. I'll start another thread about the backtrack5 scoop if I need to. See ya :guitar:

---

### Post by Lars Noodén on 2012-10-26
Good that it went smoothly.  By the way, do you know what kind of graphics it uses?

```

sudo lshw -sanitize -class display

```

---

### Post by Redzky on 2012-10-29
> **Lars Noodén said:**
> Good that it went smoothly.  By the way, do you know what kind of graphics it uses?

```

sudo lshw -sanitize -class display

```

I put that into terminal and it said it has RV350 (Mobility Radeon 9600 M10)

---

