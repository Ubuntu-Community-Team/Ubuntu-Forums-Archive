---
title: "PIC Microcontroller / PICKIT2 / USB"
date: 2007-08-06
forum: Programming Talk
---

### Post by sullivan.t on 2007-08-06
I have, on Windows, done some fun assembly work with the Microchip 12F(675 I think) microcontroller, using the PICKIT2 USB Programmer dev kit / board.

Has anyone used this in Ubuntu?  I am ok with programming assembly, but C would be groovy, too.  I am in a bit of a "programmers block" and nothing these days seems fun (though that is another thread) so I figured I would try to get the pickit2 programming on my new wonderful ubuntu install.

I suppose I could use Wine with the PICKIT2 programming software. (MPLAB I think it's called...)

Does the USB device natively work with Ubuntu?

-- I should note that I have found a bunch of linux specific links on the web - some old, some not so old.  Some pointing me in circles, and some that don't seem totally complete.  Maybe that's what I should do, just get something packaged and working the same way every time. :P

---

### Post by digilink on 2007-08-06
Nice to see another PIC fiddler :p

I've toyed a little bit with PIC's myself, but ran into the same frustrations you have with finding a suitable development environment under linux. 

Check out [http://piklab.sourceforge.net/](http://piklab.sourceforge.net/)

It's pretty decent, I don't believe there is a native C compiler that is robust enough anyhow, SDCC comes to mind, it's open source, but I don't think it's developed enough yet. I've never used it so I can't say for sure....

Personally, I've moved on to Atmel devices. They seem to be better supported under a linux environment and there is a GNUC compiler port specifically for them. 

Lots of good stuff here if interested: [http://www.avrfreaks.net](http://www.avrfreaks.net)

Not sure on your programmer, I think Piklab might support it: [http://piklab.sourceforge.net/progs.php](http://piklab.sourceforge.net/progs.php)

Give it a whirl and let us know how you turn out.... I'm interested in this as well.

---

### Post by sullivan.t on 2007-08-06
I'll check those out when I get home tonight.  I think atmel may have more IO, robustness, and general "good stuff on the inside" to play with... but I have pic hardware on my desk at home, and can't jump into a new (read: money) setup at the moment.  

But yeah, the thought of leaving pic to something that has a broad base on the linux os is a good thought, indeed.

I don't mind writing my own asm - at least I know what's in there in the end.  I will do my best to keep good logs of what works, what works well, and what doesn't work at all... reminds me of the days of this lib needing that lib and that one needing this one that hasn't been around for 10 years... :P

---

### Post by digilink on 2007-08-06
If you ever decide to go with Atmel and need a cheap programmer:

[http://www.sparkfun.com/commerce/product_info.php?products_id=13](http://www.sparkfun.com/commerce/product_info.php?products_id=13)

That's what I use and it works great. You may even be able to build one from scratch for less. 

I keep going back and forth on the whole use a PIC versus Atmel thing. Personally, I'm extremely fascinated by microcontrollers and their capabilities, but I have yet to do anything besides make a couple LED's blink, I suppose that's a start!

---

### Post by sullivan.t on 2007-08-06
> **digilink said:**
> I have yet to do anything besides make a couple LED's blink, I suppose that's a start!

Heh, it is indeed a start.  That is in fact what I want to use this 12F PIC for!  (I'm a volunteer fireman) What I want to do is make a blue-light flasher, and like the dork I am, fit the "controller" for it in an altoids tin.  There are some *really* beautiful blue LEDs mounted on heat-sinks around there on the web... Luxeon, etc... and I know I can control them easily with the PIC.  Either view one IO and high going to led a and low going to led b, or two IOs, etc... on the 8 pin chip there are still plenty of resources.  Could probably monitor the temp via the analog in and shut it down if it gets too hot... etc. :P

---

### Post by sullivan.t on 2007-08-06
Oh and thanks for the links!!

---

### Post by digilink on 2007-08-06
> Heh, it is indeed a start. That is in fact what I want to use this 12F PIC for! (I'm a volunteer fireman) What I want to do is make a blue-light flasher, and like the dork I am, fit the "controller" for it in an altoids tin. There are some *really* beautiful blue LEDs mounted on heat-sinks around there on the web... Luxeon, etc... and I know I can control them easily with the PIC. Either view one IO and high going to led a and low going to led b, or two IOs, etc... on the 8 pin chip there are still plenty of resources. Could probably monitor the temp via the analog in and shut it down if it gets too hot... etc. :P

LOL, that's cool! Best of luck with it. Altoids tins are great for all kinds of electronics projects and cheap! 

> Oh and thanks for the links!!

Your welcome, anytime :) Glad I could help.

---

### Post by sullivan.t on 2007-08-07
I was able to get pickit.sourceforge.net to install - one of the steps in the howto (which is here and linked from pickit) gives a pretty good lowdown on installing pickit.

It mentions making a symlink to some libraries and hardcodes version .11. into the symlink.  apt-get gets version 12 of those, so notice that when making the symlink.

This reply, #11, is *great* and I followed that to a T and got the pickit2 programmer noticed by my system: 

[http://ubuntuforums.org/showpost.php?p=1010143&postcount=11]("http://ubuntuforums.org/showpost.php?p=1010143&postcount=11")

Once I got that done, I noticed it was of firmware > 2.0.0.  Which is *not* supported by piklab.  Blah.

So tonight I will try an older firmware and go from there! But seriously, I am happy I got the usb device noticed by the machine and an ide and compiler installed. (The IDE is great at noticing which ones I have on my machine already...)

---

### Post by hvymtlsteve on 2007-08-16
I've been beating around the bush about getting my PICKit 2 to work on Ubuntu as well.. I used to have an old Windows XP laptop, which I fired up every time I wanted to whip up or change a PIC program. 
However, said laptop fell victim to a beverage spill and I was unable to save it in time, I think. Luckily I was able to rip out the hard drive and hook it up to an IDE/USB converter and salvage my precious PIC ASM files! 
At any rate I need to get my PICKit back up and running, but I inadvertently upraded it to the version 2 firmware a few months back when I downloaded the newest windows soft to a PC at work that didn't have it, which forced the firmware upgrade. 

There is a program out there called pk2, a few months ago they said they'd have support for the new protocol by spring, but no dice yet. 
Should I just downgrade the firmware?

I do have a couple of Atmel chips kicking around, been meaning to check 'em out, there are some things about 'em that would motivate me to choose them over PIC. 
However, I have to pay money for those... the chips with lots of I/O and memory are a few bucks a pop! Microchip is one of those nice companies that pretty much gives handfuls of samples to anyone.. if I need a few more of my favorite chips, I fill out a sample order and have 'em in a couple days. They don't seem to care what, either, I've gotten for free some of their more expensive chips, no questions asked. I've heard Atmel is not so generous on that :(

---

### Post by DexterLB on 2009-03-17
In my case MPLAB installes perfectly, CCS C compiler works perfectly, everything is perfect, except PICKit2. No matter how I plug it, MPLAB says > PICKit2 not found.. Do you think there's any way to make it work under wine? Actually, does wine support USB devices? I've tried pikdev, piklab and some other linux proggies, but they all support only firmware 1.x, and I need v2. And it'd be great to have the debugger working in MPLAB. Any ideas?

---

