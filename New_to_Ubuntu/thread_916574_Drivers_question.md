---
title: "Drivers question"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by ExplicitViper on 2008-09-11
i am seriously considering installing Ubuntu onto this PC. i want to get completely rid of Windows XP. What i am wanting to know, is when i delete windows XP from my harddrive, and install Ubuntu, will i be able(and if so how) to install my drivers for my motherboard, videocard, soundcard, etc..etc..

this is pretty much the only thing holding me back from installing ubuntu right now.

---

### Post by SunnyRabbiera on 2008-09-11
Actually you may not needf the drivers as Ubuntu works with most hardware  out there, can you give us your specs just in case?

---

### Post by szymon_g on 2008-09-11
hi.
in most cases, after successful installation of ubuntu, you will have no need to install additional drivers (with exception for graphic card)- they are included into kernel, should work out of box.
the best thing is to test your pc's configuration by running Ubuntu/Kubuntu LiveCD - it wont harm data stored on harddisk, and you will know that your soundcard/ethernet card work out-of-box.

anyway, you can also give a details of your hardware specification- maybe someone has the same :?

////////////
eh, i've been to late ;p

---

### Post by ExplicitViper on 2008-09-11
Asus A8N-SLI Deluxe
AMD 3500+
Western Digital Raptor
2Gig OCZ Ram
Nvidia 8800GT
Creative SB X-Fi

those are SOME that i can think of off the top of my head, if you need anymore just post

---

### Post by Bucky Ball on 2008-09-11
You will find that the linux drivers exist for your hardware. Post the specs of your machine and we can have a look. Most things work straight 'out of the box.' Unless you have something *really* exotic, doubtful you will have any problems. There are very few devices that don't work and if windoze drivers are required, there are ways around that to (ndiswrapper and the like). Wireless cards can be a little problematic but that it about it.

Validated hardware here:

[http://webapps.ubuntu.com/certification/](http://webapps.ubuntu.com/certification/)

More extensive list here:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

As for cpus and RAM, not a problem. Dive in! :)

Try this. Do a search for:

**your_hardware_device ubuntu**

in your favourite search engine. IE:

**nvidia geforce ubuntu**

---

### Post by SunnyRabbiera on 2008-09-11
> **ExplicitViper said:**
> Asus A8N-SLI Deluxe
AMD 3500+
Western Digital Raptor
2Gig OCZ Ram
Nvidia 8800GT
Creative SB X-Fi

those are SOME that i can think of off the top of my head, if you need anymore just post

Looks fine to me, the only one i would worry about is the creative card as creative cards suck even under windows (they make terrible drivers and cards, give me realtek anyday)

---

### Post by Bucky Ball on 2008-09-11
[quote=ExplicitViper]Asus A8N-SLI Deluxe
AMD 3500+
Western Digital Raptor
2Gig OCZ Ram
Nvidia 8800GT
Creative SB X-Fi[/quote]

My advice ... start installing!

As for the Creative card, doesn't look like an issue:

[http://lne.byexamples.com/?p=39](http://lne.byexamples.com/?p=39)

Hardware compatibility improves continually BTW as more manufacturers get on board and/or developers come up with new drivers and workarounds.

---

### Post by ExplicitViper on 2008-09-11
> **Bucky Ball said:**
> My advice ... start installing!

so when i install Ubuntu, i will NOT have to put in my (i.e. Motherboard/VideoCard disk) to install the drivers? like in windows xp?

---

### Post by SunnyRabbiera on 2008-09-11
> **ExplicitViper said:**
> so when i install Ubuntu, i will NOT have to put in my (i.e. Motherboard/VideoCard disk) to install the drivers? like in windows xp?

yes, and lucky for you Ubuntu comes with something called a Live CD, a live CD is sort of like a virtual mode where you can see if Ubuntu will pick up your hardware, its not guesswork like in windows where you pray things work.
Most of the time if something works on the live it will work on a full install.

---

### Post by ExplicitViper on 2008-09-11
> **SunnyRabbiera said:**
> yes, and lucky for you Ubuntu comes with something called a Live CD, a live CD is sort of like a virtual mode where you can see if Ubuntu will pick up your hardware, its not guesswork like in windows where you pray things work.
Most of the time if something works on the live it will work on a full install.

badass. im going to install first thing in the morning when i get a CD to put it on xD

---

### Post by SunnyRabbiera on 2008-09-11
> **ExplicitViper said:**
> badass. im going to install first thing in the morning when i get a CD to put it on xD

Well actually for beginners I would suggest a dual boot, and of course back up files you want to keep before reformatting your system.

---

### Post by ExplicitViper on 2008-09-11
> **SunnyRabbiera said:**
> Well actually for beginners I would suggest a dual boot, and of course back up files you want to keep before reformatting your system.

funny thing is, i reformat like 5 times every 3 months. so everything is like SUPER easy to get back onto my pc. and i have been researching to see if **** was available for Linux. and so far i havnt found anything that i cant get for Linux that i use right now. my biggest thing is my games that i play (Age of Conan, Combat Arms). but i found a thing called Cedega that lets me run Age of Conan. Hopefully soon it will be able to run Spore. or ill just figure out how to make it run :D

---

### Post by SunnyRabbiera on 2008-09-11
Well there is actually wine too, that can run games better then cedega, you may want to do your homework before committing linux to games as a lot of games wont work under linux.
This is more of an issue with the developers of the games then linux, no linux native ports dont help and wine has its limitations.
If you are a gamer a dual boot is definitely advised.
I have heard spore does work under wine, but so far only one report on it.
i would read up on your games on the forums by preforming searches and checking out the wine section of the forum.

---

### Post by ExplicitViper on 2008-09-11
> **SunnyRabbiera said:**
> Well there is actually wine too, that can run games better then cedega, you may want to do your homework before committing linux to games as a lot of games wont work under linux.
This is more of an issue with the developers of the games then linux, no linux native ports dont help and wine has its limitations.
If you are a gamer a dual boot is definitely advised.
I have heard spore does work under wine, but so far only one report on it.
i would read up on your games on the forums by preforming searches and checking out the wine section of the forum.

could i not download both wine and cedega? i have read that WineX is the best one to get, is that true?

---

### Post by SunnyRabbiera on 2008-09-11
> **ExplicitViper said:**
> could i not download both wine and cedega? i have read that WineX is the best one to get, is that true?

yes you can get both wine and cedega together.
As for WineX, Cedega is WineX.

---

### Post by ExplicitViper on 2008-09-11
> **SunnyRabbiera said:**
> yes you can get both wine and cedega together.
As for WineX, Cedega is WineX.

THATS WHERE I WAS GETTING CONFUSED!! when i googled WinX, Cadega was all i was getting xD.

---

### Post by ExplicitViper on 2008-09-11
oh would a Zboard be a problem? or a Razor Copperhead mouse?

---

### Post by SunnyRabbiera on 2008-09-11
> **ExplicitViper said:**
> THATS WHERE I WAS GETTING CONFUSED!! when i googled WinX, Cadega was all i was getting xD.

Right, WineX became Cedega later.
But to be honest Cedega isnt worth it these days, there is just too much controversy and little development these days.
Wine has caught up to it for the most part, and probably has surpassed it too.
If you are still unsure try crossover games, crossover games is made by codeweavers who actually contribute to the wine project as opposed to cedega, check it out:
[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

remember both Cedgega and crossover are NOT free, but I feel corssover is more worth it because most of the improvements crossover makes goes to wine.

---

### Post by ExplicitViper on 2008-09-11
> **SunnyRabbiera said:**
> remember both Cedgega and crossover are NOT free, but I feel corssover is more worth it because most of the improvements crossover makes goes to wine.

thats what torrents are for xD

---

### Post by SunnyRabbiera on 2008-09-11
> **ExplicitViper said:**
> thats what torrents are for xD

Yes though if you wish to contribute it helps you know.
Most of us here do not encourage such behavior as its not entirely "legal"
though some of us dont care anymore (like me)
But in cases like this I would proudly pay for crossover games as it goes to wine development in the long run.

---

### Post by ExplicitViper on 2008-09-11
> **SunnyRabbiera said:**
> Yes though if you wish to contribute it helps you know.
Most of us here do not encourage such behavior as its not entirely "legal"
though some of us dont care anymore (like me)
But in cases like this I would proudly pay for crossover games as it goes to wine development in the long run.

alrighty,thank you so much for your help

---

### Post by SunnyRabbiera on 2008-09-11
Uh huh but still in the long run for you a dual boot still might be best as even crossover has limitations, you can just use ubuntu as you main everyday use system and use windows for gaming.
Most people do this

---

