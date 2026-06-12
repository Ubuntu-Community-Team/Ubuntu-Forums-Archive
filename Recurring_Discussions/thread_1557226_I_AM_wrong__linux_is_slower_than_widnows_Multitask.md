---
title: "I AM wrong ? linux is slower than widnows Multitasking ?"
date: 2010-08-20
forum: Recurring Discussions
---

### Post by Objectivity on 2010-08-20
Hi,

 I do not know WHY I feel like linux is a bit slower than windows when I am running multiple programs ! even some programs crash sometimes.

 I am wrong ?

 If someone can tell me the technical details I would thank her/him.

---

### Post by darolu on 2010-08-20
It's hard to tell you a possible reason without more information. What are your hardware specifications? what version of OS/apps do you use?

Right now, all I can recommend you is to run a full memory scan as one (or more) of your memory cards (or mobo slots) may be damaged.

---

### Post by MrWES on 2010-08-20
do you have visual effects turned on? If so, try turning it off and see that improves performance.

Bill

---

### Post by kaldor on 2010-08-20
> **MrWES said:**
> do you have visual effects turned on? If so, try turning it off and see that improves performance.

Bill

Compiz caused so many crashes for me way back when I used it.

---

### Post by Objectivity on 2010-08-20
> **darolu said:**
> It's hard to tell you a possible reason without more information. What are your hardware specifications? what version of OS/apps do you use?

Right now, all I can recommend you is to run a full memory scan as one (or more) of your memory cards (or mobo slots) may be damaged.

 Thank you Darolu.

 I have Sager Laptop NP 570TU :
 Core 2 Extreme 3.47 Mhz
 4 Gig ram
 Graphic Card Nvidia GTX M280 

 OS version ? I think is You are using Ubuntu 10.04 LTS .

 Seriously I feel like it is damn slower .

 Could you plz tell me how I can do full memory scan ?

---

### Post by Objectivity on 2010-08-20
> **MrWES said:**
> do you have visual effects turned on? If so, try turning it off and see that improves performance.

Bill


 I will today ! but I love it when is on.

---

### Post by Objectivity on 2010-08-20
> **kaldor said:**
> Compiz caused so many crashes for me way back when I used it.

 I use Compiz. I will turn it off and let you know. Thank you .

---

### Post by Objectivity on 2010-08-20
> **Objectivity said:**
> I use Compiz. I will turn it off and let you know. Thank you .


 WOW ! I turn it off and I would say 30% improved ! it is interesting to see that Compiz indeed makes your computer DAMN slower.

 THANK YOU ! solved I THINK.

I am impressed indeed.

---

### Post by kaldor on 2010-08-20
Hahaha, yep... Compiz might look awesome but it sucks :)

---

### Post by Objectivity on 2010-08-20
> **kaldor said:**
> Hahaha, yep... Compiz might look awesome but it sucks :)


 TOTALLY AGREE ! I feel like my laptop NOW can breathe finally lol

---

### Post by bodhi.zazen on 2010-08-20
> **Objectivity said:**
> Hi,

 I do not know WHY I feel like linux is a bit slower than windows when I am running multiple programs ! even some programs crash sometimes.

 I am wrong ?

 If someone can tell me the technical details I would thank her/him.

Moved to recurring discussions as the title is framed as a Linux vs Windows thread and so invites trolling.

If you want technical assistance, please start a technical thread, we need to know your hardware and what hardware drivers you are using.

If the system feels slower, then it probably is. Applications crashing indicate a problem on any OS.

Could be anything from graphics to wireless drivers.

Open a terminal and open apps from the terminal. If (when) they crash you may get an error message. Post any error messages you get, although you may not understand them, others here may.

---

### Post by pqwoerituytrueiwoq on 2010-08-20
Compiz runs fine for me (it makes desktop recording crap though for me)
anyway i noticed you have an Nvidia card
so i wanted to make sure you have the best driver 
system->administration-> hardware drivers

---

### Post by kaldor on 2010-08-20
Problem was already solved, Bodhi. And I think it was a legitimate question. Compiz was the problem and now things appear smooth... there was no trolling, just a comparison!

Hardware drivers were nothing to me. You couldn't even run 3d effects on open source nvidia way back on Hardy.

...wow, I feel old again; "Way back on Hardy".

---

### Post by pizza-is-good on 2010-08-20
> **kaldor said:**
> Hahaha, yep... Compiz might look awesome but it sucks :)

Compiz was a problem for me too. It is nice, but it is full of bugs and uses up too many resources. I still use it. Can't part from 'the cube'.

---

### Post by uRock on 2010-08-20
> **kaldor said:**
> Problem was already solved, Bodhi. And I think it was a legitimate question. Compiz was the problem and now things appear smooth... there was no trolling, just a comparison!

Hardware drivers were nothing to me. You couldn't even run 3d effects on open source nvidia way back on Hardy.

...wow, I feel old again; "Way back on Hardy".
I am sure that within a few hours the trolling would have started with such comments as..... (we can use our imaginations.)

---

### Post by Austin25 on 2010-08-20
Compiz is awesome, but only if your hardware can back it up.

---

### Post by MrWES on 2010-08-20
Definitely an over reaction. Many times users are drawn to Compiz and as it may run, they really don't have the vid card to run it smoothly. I didn't take it a trolling.

Bill

After-thought: why does the install default to Compiz | Normal?

---

### Post by CraigPaleo on 2010-08-20
> **MrWES said:**
> 

After-thought: why does the install default to Compiz | Normal?

It shouldn't. I had to enable desktop effects myself, and it wouldn't let me do it until I installed a graphics driver.

---

### Post by saphil on 2010-08-20
When I have something important to do, I turn off my graphics effects.   When I am doing less useful things, I turn them on. I like the Dali look when you move a window around. :KS

---

### Post by dragos240 on 2010-08-20
Meh. I tend to not use compiz. Technically I COULD, but I really don't feel like it. My system uses about 100mb of ram when browsing and such. It's nice having 90% of your ram avalible for use.

---

### Post by KirbySmith on 2010-08-21
One other possible cause became apparent to me a several days ago when h.264 decoding became very bad after replacing a bad power supply.  Up until then Ubuntu 9.10 seemed to have only marginally less performance under VLC for this than the Windows 2k I have abandoned.

I had set the multiplier in the BIOS from AUTO to a mis-remembered, too low multiplier.  Setting the CPU multiplier in my BIOS from AUTO to the correct multiplier has brought the apparent performance up to the Windows level.  Ubuntu now whines at me after rebooting that "Frequency Scaling is Unsupported," but I ignore it.

I think Ubuntu may be capable on some motherboards of adjusting the clock multiplier with CPU load, but whatever it does is not sufficient to get h.264 decoding to operate at full performance on mine.  Forcing the full (not-overclocked) multiplier fixed it.

kirby

---

### Post by PhilGil on 2010-08-21
I'm not a Compiz expert, but I think you can also set operations like opening menus, minimizing/maximizing windows, workspace switching and the like to occur slowly (to better view the effects) or quickly (for snappier performance).

---

