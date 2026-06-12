---
title: "Which (cheaper) printers work with ubuntu 12.4"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-07-23
Given nobody replied to my thread about my AW10 Advent printer my guess is it is just not compatible and so it will need to be relegated to being a photocopier. 

If I got a printer it needs to be linux compatible and work with Ubuntu 12.4 so it would probably be useful to more than me to know of any easy to set up printers that actually work. Cost is a factor here so to know of cheaper versions would be useful.

The emphasis is easy to set up.

---

### Post by bobsan on 2012-07-23
I think most epson or HP will work. But do some research for the models just to be sure.

---

### Post by Jackalyn on 2012-07-23
Thanks - have sworn never to buy another epsom but HP is cheap enough and that would make sense. Now all I need to do is hope I get a salesperson who does not look at me blankly when I say 'Ubuntu' or linux...........Thanks:popcorn:

---

### Post by Bufeu on 2012-07-23
All printers I have had works with Ubuntu. It's no guarantee, but I think all HP-printers will work.

---

### Post by colin.p on 2012-07-23
I have an HP Officejet 6500 E709n Wireless that installed automatically in precise, as well as a cheap Cannon Pixma MP495 that all it took was a downloaded driver fron Cannon to work. I think if you stick to known brands instead of rebranded, a quick search will find a thread on how to make it work.

---

### Post by David Andersson on 2012-07-23
> **bobsan said:**
> But do some research for the models just to be sure.

> **Jackalyn said:**
> Now all I need to do is hope I get a salesperson who does not look at me blankly when I say 'Ubuntu' or linux...

You misunderstand. Doing research is reading the [internets]("https://help.ubuntu.com/community/Printers"). Not asking a [salesperson]("http://www.funnyordie.com/videos/0b8c6482ec/speaking-meteorically-where-is-my-iphone-5"). Never ask a salesperson anything. You must already know everything you need to know when you enter the store. (You may ask a salesperson questions where you know the answers. For fun, of politeness, or to evaluate competence.)

My limited experience with printers in ubuntu:

* HP: Really easy install
* Brother: Read the instructions on their website carefully, then relatively easy
* Lexmark: Impossible

---

### Post by sanderj on 2012-07-23
> **Jackalyn said:**
> 
If I got a printer it needs to be linux compatible and work with Ubuntu 12.4 so it would probably be useful to more than me to know of any easy to set up printers that actually work. Cost is a factor here so to know of cheaper versions would be useful.

The emphasis is easy to set up.

I only buy printers if the box says "Linux". That's not only to be sure it works with Linux, but also to reward the printer company / product manager to explicitly support Linux (and not leaving a driver to the revers-engineering community).

My last buy was a cheap black-white laserprinter: Brother HL-2030. Just plug it in, and it works.

Oh, not my buy, but it works flawlessly: Samsung CLP-310 color laser printer.


BTW: I prefer laser over inkjet; laser printers always work, also after not using them for a longer time.

HTH

---

### Post by techvish81 on 2012-07-23
most hp printers would work with linux, i've used three different models and all of them worked. 
epson may work but my experience is horrible with them, so i would go with hp.

---

### Post by Jackalyn on 2012-07-23
> **David Andersson said:**
> You misunderstand. Doing research is reading the [internets]("https://help.ubuntu.com/community/Printers"). Not asking a [salesperson]("http://www.funnyordie.com/videos/0b8c6482ec/speaking-meteorically-where-is-my-iphone-5"). Never ask a salesperson anything. You must already know everything you need to know when you enter the store. (You may ask a salesperson questions where you know the answers. For fun, of politeness, or to evaluate competence.)

LOL! You are probably right but just sometimes on the law of averages one of them may have heard of linux. Or EVEN use it. The word is out and spreading. 

My limited experience with printers in ubuntu:

* HP: Really easy install
* Brother: Read the instructions on their website carefully, then relatively easy
* Lexmark: Impossible 

OK so the ones not to use are Advent and Lexmark so far.

---

### Post by mastablasta on 2012-07-23
samsung (at least some models) also work great. they come with linux drivers, but it's better to use a PPA instead as it fixes some issues with original drivers.

---

### Post by Zill on 2012-07-23
> **sanderj said:**
> ...My last buy was a cheap black-white laserprinter: Brother HL-2030. Just plug it in, and it works.
Same here with the Brother HL-2130 - it just worked straight out of the box, automatically installing the drivers needed. :-)

Inkjets are, IMHO, far too unreliable and expensive to run.  Lasers, while being slightly more expensive to buy, generally are far cheaper to run.

---

### Post by sanderj on 2012-07-23
> **mastablasta said:**
> samsung (at least some models) also work great. they come with linux drivers, but it's better to use a PPA instead as it fixes some issues with original drivers.

AFAIK, the Samsung CLP-310 worked without any manual installation of drivers on Ubuntu. Just plug in, and print.

---

### Post by kurt18947 on 2012-07-23
Brother has a script which makes installing their printers no-brainers.  Scanning can be a little more involved.  I would steer clear of Lexmark personally, and Canon's linux support seems spotty.  I have no experience with Samsung, Kodak etc. For me it's HP & Brother.  Brother ink cartridges don't contain any electronics so it's easier to refill them or get refillable cartridges.   Some but not all HP  printer cartridges have the heads built into the cartridge so you don't have to worry about expensive printhead repairs, new ink=new print head which is sweet.

---

### Post by Cheesemill on 2012-07-23
There is a compatibility database here:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

---

### Post by Derek Karpinski on 2012-07-23
I would stick with HP.  I had an all-in-one that scanned and printed flawlessly.  

I'd also stay away from Canon.  My i2700 worked without any fuss, but I cannot for the life of me get the colors to look right.  Everything looks so washed out.  Messing around with color profiles became more that it was worth.  

The quality of the hardware is suspect with all cheap printers.

---

### Post by Jackalyn on 2012-07-23
Hmm I tried the Advent AW10 again and all was well! -Except it printed blank pages but then I checked and despite having recently replaced it there was no black ink. I guess I need to get some and try it but I am pretty certain that it does work after all.
Not sure why nothing happened yesterday but I put everything back to printer settings so hopefully instead of a white elephant it is an 'out of the box' option. Hopefully cheaper than buying a printer! (The inks don't work unless all four are present).

---

### Post by paulnewall on 2012-07-23
Since the Advent AW10 is a kodak printer in disguise, it should be possible to print using the package c2esp, and to scan using the sane backend kodakaio.
 
c2esp should be in ubuntu.
but if not, you can get it  here :
[https://sourceforge.net/projects/cupsdriverkodak/files/](https://sourceforge.net/projects/cupsdriverkodak/files/)
 
The best way to get kodakaio is to download sane from git. There is a howto at the site above.
 
Do bear in mind that these are reverse engineered drivers. Also there is currently no way to get and install any firmware upgrades in linux.

---

