---
title: "new to linux and tryin to follow steps for WoW"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by WaTdaFUNK on 2008-06-02
I got tired of Windows cause the technical support sucks since my "XP Media Center license expired" and i have to pay $50 just to talk to someone about it...

sooo i said screw it and got my friend to help me get hardy heron on my laptop... its all good, but now im tryin to get World of Warcraft: Burning Crusade to run properly on it...

i have followed a ton of the posts on here and got WoW:BC installed... it runs and plays the intro movie... but it just goes to a black screen with some of the icons on the desktop showing through the black... 

i noticed some posts about the icons showing through and altering the config.wtf file.... this file doesnt exist on my computer because i havent loaded a character yet... which another post said to do to make the file show up.... 

so im stuck at trying to figure out what to do to make it work because i need to alter a file that doesnt exist... and im trying to alter it to make wow work to make the file show up to alter the file...

you get my confusion?!?!?!?!

can someone please help me????

---

### Post by SunnyRabbiera on 2008-06-02
well I am no world of warcraft expert as I dont play it, but telling us your the model of your video card is a good start.

---

### Post by WaTdaFUNK on 2008-06-02
> **SunnyRabbiera said:**
> well I am no world of warcraft expert as I dont play it, but telling us your the model of your video card is a good start.

yeah.. guess it would help... lol

its some stupid integrated crap...Intel GMA 900

the laptop is a "stock" dell xps m140......

---

### Post by SunnyRabbiera on 2008-06-02
> **WaTdaFUNK said:**
> yeah.. guess it would help... lol

its some stupid integrated crap...Intel GMA 900

the laptop is a "stock" dell xps m140......

To be honest intel cards are not that bad in my opinion, mime seems to perform quite well.
Post other specs too, as it helps us know your hardware specs.
I may not be able to fully help you but I can get you started at least on the checklist that others will need to help you.

---

### Post by WaTdaFUNK on 2008-06-02
Processor
    Intel Pentium M 770 / 1.73 GHz
Data bus speed
    533 MHz
Chipset type
    Mobile Intel 915GM Express

Type
    L2 cache
Cache size
    2 MB

RAM -- 1GB




Hard Drive
    80 GB - 5400 rpm



Graphics Processor / Vendor
    Intel GMA 900





 Intel PRO/Wireless 2200BG

---

### Post by jasontu on 2008-06-03
[http://ubuntuforums.org/showthread.php?t=654681&highlight=world+of+warcraft+x700](http://ubuntuforums.org/showthread.php?t=654681&highlight=world+of+warcraft+x700)

The config file attached to the first post in the link above.  It has helped me a lot.  It's good and stable, and it's a good thing to revert to if you start to see crashes or hangs in the game because you accidentally clicked some option you shouldn't have.

I'm new to this to, so I know how frustrating can be.  I hope this works!  Also record/document what you do so you can recall it if you ever have to do it again.

---

### Post by WaTdaFUNK on 2008-06-03
> **jasontu said:**
> [http://ubuntuforums.org/showthread.php?t=654681&highlight=world+of+warcraft+x700](http://ubuntuforums.org/showthread.php?t=654681&highlight=world+of+warcraft+x700)

The config file attached to the first post in the link above.  It has helped me a lot.  It's good and stable, and it's a good thing to revert to if you start to see crashes or hangs in the game because you accidentally clicked some option you shouldn't have.

I'm new to this to, so I know how frustrating can be.  I hope this works!  Also record/document what you do so you can recall it if you ever have to do it again.

WOW!  That fixed the whole problem with it not running...

Now i just need to download the patches and find a way to get the FPS some... because if its as bad as the title screen its going to be a pain to play... lol

---

### Post by starcannon on 2008-06-03
post the output of 
```
glxinfo | grep render
```

---

### Post by WaTdaFUNK on 2008-06-04
> **starcannon said:**
> post the output of 
```
glxinfo | grep render
```

glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2


i did some fps tweaks from some of the other posts and have gotten the fps up a lot... i finally got all the patches dled... but when i go into the game, the ground is not generated right... i can see through the ground and down into nothingness... haha...

---

### Post by NoFearDJB on 2008-06-04
I have a laptop with the same integrated graphics. I personally wouldn't recommend using integrated gfx with Ubuntu to play WoW. On my windows partition for the laptop WoW barely runs anyway! 

I wish you good luck in you endeavors but I can tell you from my experience that it isn't really playable with Ubuntu and integrated GMA graphics like your setup.

---

### Post by WaTdaFUNK on 2008-06-04
> **NoFearDJB said:**
> I have a laptop with the same integrated graphics. I personally wouldn't recommend using integrated gfx with Ubuntu to play WoW. On my windows partition for the laptop WoW barely runs anyway! 

I wish you good luck in you endeavors but I can tell you from my experience that it isn't really playable with Ubuntu and integrated GMA graphics like your setup.

hmmm... that blows... it ran perfect when it was windows... shrugs, oh well..

ill figure out how to get it to run better...

---

