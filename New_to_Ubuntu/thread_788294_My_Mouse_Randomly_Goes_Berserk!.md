---
title: "My Mouse Randomly Goes Berserk!"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-09
Sometimes when I'm using ubuntu my mouse randomly shoots around the screen and clicks things and exits programs or gets me killed in games (and no this is not just because I'm rubbish at the games:lolflag:) Can anyone tell me why this is and how to fix it?

Thanks in advance

---

### Post by hotchkikr on 2008-05-09
does it do this in other operating systems? well you might want to try a different mouse first, because actually fixing this problem could be tricky...

---

### Post by ACJarrett on 2008-05-09
Sounds like you need to get a mouse trap :p

Have you tryed pluging in another mouse and see if the problem prosists?  or is it a track pad?

---

### Post by kamitsukai on 2008-05-09
No well it is possible its the mouse as it's only a £5.99 set off ebuyer but i have never had this problem with XP...and before everyone thinks I'm some tight scrooge I'm getting a better keyboard and mouse when my cash flow improves:)

---

### Post by hotchkikr on 2008-05-09
mice aren't that expensive. You can get a $10 (don't know how that translate to euros) mouse that runs well for 2+ years (which is great)

it probably just has a more mature driver for windows though

---

### Post by kamitsukai on 2008-05-09
> **hotchkikr said:**
> mice aren't that expensive. You can get a $10 (don't know how that translate to euros) mouse that runs well for 2+ years (which is great)

it probably just has a more mature driver for windows though

That's OK euros would be useless to me as well, we don't use them in the UK:lolflag:

---

### Post by JohnnyC44 on 2008-05-09
Well, Kamitsukai, it may not be your mouse.  My cursor has seizures periodically such as you describe, and I use a new US$40 Logitech.  Not as drastic a problem, though; mostly just wandering off to one random corner of the screen or another -- or I'll be whacking away on the text for an email and look up to see that I'm changing my signature now.

So, this really is an issue, and has nothing to do with buying your mouse on eBay and *hoping* the problem is solved with a more expensive device.

Anyone else seeing this?

---

### Post by wootah on 2008-05-09
Is it an optical mouse? Perhaps the sensor is slightly dirty? You could grab a q-tip (cuetip?) and some alcohol (the rubbing kind :P) and try cleaning it up a bit.

To JohnnyC44: I have had this problem in Windows before and the solution I listed (along with cleaning the mouse pad) seemed to clear up the issue.

---

### Post by JudgeFudge on 2008-05-09
This is a common problem when using laptop keyboards which have a trackpad (even if a mouse is plugged in). Your hand brushes the trackpad and moves the cursor. It bothered me for months before I found out what the problem was as I didn't realise what was going on.

There is a utility called syndaemon that more or less fixes this.

---

### Post by kamitsukai on 2008-05-09
i suppose that could be the problem as my room is very dusty...

ps: if i dont reply its because i have stuck the cuetip through my mouse's laser LOL

---

### Post by wabbster on 2008-05-09
Optical mice can have their own quirky little problems, can't they? It could be a dusty sensor, or it could be a shiny mouse pad.. They kind of reflect light and make the pointer go exactly where you did not intend it to. Been there, suffered that. :(

---

### Post by wootah on 2008-05-09
> **kamitsukai said:**
> i suppose that could be the problem as my room is very dusty...

ps: if i dont reply its because i have stuck the cuetip through my mouse's laser LOL

Oh crap! Good luck! :D

---

### Post by kamitsukai on 2008-05-14
Its definatley something to do with ubuntu because if i press "Esc" on my keyboard it stops it and it goes back to normal...

---

### Post by Iowan on 2008-05-14
Different problem (and OS), similar results.  I have a Windows laptop that will do strange (bad) things if I power it up with something attached to serial port.  Apparently it thinks serial port is another mouse - incoming data really drives mouse wild.  Dunno how this helps your problem, though.

---

### Post by tszanon on 2008-05-14
I once had an optical mouse that went crazy every now and then. It was definitely a problem in Ubuntu, because it worked fine in Windows.

How wrong I was. In a matter of days, it stopped working. Somehow, the corrupted data sent by the mouse was driving Ubuntu crazy, but windows apparently just ignored them.

So, before trying something that seems hard to do (or involves money), try using another mouse, if available. Maybe it's the problem.

---

### Post by kamitsukai on 2008-05-14
im just saying that if its something to do with my mouse then how come it stops when i press "esc"?

---

### Post by vussvillem on 2008-06-06
Before blaming Ubuntu, read EDIT part first!

I'm having the same problem. Cursor moves to the random corner of display and that's it. I'll have to patiently wait then until I can use my computer again for SOME time. If this has any importance, I'm having Logitech USB-cord-mouse on my Dell D600 laptop.

I also notice that from time to time, when writing a letter or document or in pidgin, cursor just jumps to another place, although I can not exclude that I have touched touchpad by accident in those cases.

**EDIT**:
However, all this started to happen to me in MS Windows as well! So I'll probably try to unable touchpad (because it happens when I do not have mouse attached) and clean my mouse somehow.

I searched for internet and found these:
[http://ubuntuforums.org/archive/index.php/t-345686.html](http://ubuntuforums.org/archive/index.php/t-345686.html)
[http://www.laptopsunlimited.com/dellmouse/dellmouse.htm](http://www.laptopsunlimited.com/dellmouse/dellmouse.htm)

Seems that there is some thing at least with dell laptops.

---

### Post by Duck2006 on 2008-06-06
I had the same problem with a ps2 mouse, and fixed it by getting a USB mouse and works great now.

---

### Post by billgoldberg on 2008-06-06
On both my computers I use "[trust]("http://www.trust.com/")" mouses.

I think they are the cheapest "brand" available and never had a problem with them.

I picked up [a notebook mouse]("http://www.trust.com/products/product_detail.aspx?item=15139") yesterday from them for &#8364;13 (£10.4 | $20).

---

### Post by gug@fnal.gov on 2008-06-06
Hi,
   I once had a hardware failure on my desktop that introduced a software bug on a remote system that was not triggered for days. The code was not invalid as the "interpreter/compiler" did not complain, and it was running successfully in production until the it tripped over the bug. 
   I've had a few experts look at me with puzzled looks over that description. Here is what happened. I was logged in using ssh to various remote systems and had several files opened in xemacs on those nodes. My mouse went crazy suddenly, opening new windows clicking random menu selections, and unknown to me at the time it also pasted in a section of code into one of the files. Now the unlucky file was a python file, but it happened to insert text into the middle of a string variable that still made the code valid python but broke the code under a certain rare error condition. Not knowing the code had changed, and having earlier made changes to that file, I missed the handful of extra characters on one line of code that had unintentionally been changed when this was checked into cvs. Testing failed to catch the error as the piece of code is highly integrated into a large distributed computing system (several layers of services between us and a tape robot system), and we did not have the resources, hardware or personnel, to fully simulate every possible error those systems could throw at us. So the code happily passed all tests, was approved for production, and worked fine until a rare error in system managing transfers to the tape robot was returned to our code. 
   After replacing the mouse I the random click problem never returned (and yes there were intermittent random clicks for months at a low level before it completely went nuts). And yes, even if this had been C or C++ code the compiler would still have been happy as the code was still valid. If the project had the resources we would have had better testing capabilities, we could not test performance as we had insufficient hardware and had to parasitically use the same network as production without impacting production throughput which was 25 MB/s) at time. Most of our unit tests broke once we integrated with the distributed system and moved away from the dummy stub calls which we could code to return various errors (we needed simulator servers for the distributed system and they did not exist). Oh well, in the future I will be more competent and still get tripped up by the unexpected :wink:

---

