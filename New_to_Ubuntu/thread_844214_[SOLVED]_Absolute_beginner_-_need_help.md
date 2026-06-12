---
title: "[SOLVED] Absolute beginner - need help"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by RICARDO MENDES on 2008-06-29
I would like to install ubuntu 8.04 on my computer, I'm running windows xp pro, have one partition (100GB) with windows, second partition (150gb) with files. 

I tried wubi and also using alternate cd, both come up with the same problem:
(69.176.381) IO-APIC + timer doesn't work.

the boot command line after booting from CD reads "initrg.gz quiet"



What should I do?

---

### Post by hyper_ch on 2008-06-29
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by TWO on 2008-06-29
> **hyper_ch said:**
> it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

Hyper_ch, way to introduce someone with their first thread on the Ubuntu Forums. :mad: Title aside, I think the content of their thread is enough information for someone who knows how to help them. No need for the sarcasm. With the amount of posts that you have, I imagine that you are either likely to have the answer through experience or you are just a keen poster.

Either way, not a good way to welcome someone at all. 

(To Ricardo Mendes: Sorry, I don't know the answer either, so my post is no more valid than the last, but hopefully you'll get help soon...)

---

### Post by diablo75 on 2008-06-29
To the OP, you should check to make sure that your BIOS is as up-to-date as possible.

---

### Post by cozmicharlie on 2008-06-29
Try the following:

You could try the live cd - see if Ubuntu works using the live cd (just to be sure it runs on your computer).  If it does try to install from the safe graphics mode.  

Or, alternatively, try this:
While you are in bios, turn off acpi and try to install again from the alternate cd

If that does not work - press f6 at the grub screen and tell us what it says. 

Provide more info on the computer also.

---

### Post by hyper_ch on 2008-06-29
> **TWO said:**
> Either way, not a good way to welcome someone at all.
One could also say not a good way to introduce themselves either ;)

Just imagine if everybody would just post a thread with a title like: "Noob here" or "help needed"... what would this forum be like then?

---

### Post by xelcius on 2008-06-29
I have the same problem also, 

I have tried to install xubuntu on my dell inspiron 1000 laptop. 

it has xp pro running already with 30 GB hard drive and 256 mb Ram. But when i run the CD it says you need atleast 256 mb memory.

If someone understand this problem please help me out.

---

### Post by Canis familiaris on 2008-06-29
> **hyper_ch said:**
> One could also say not a good way to introduce themselves either ;)

Just imagine if everybody would just post a thread with a title like: "Noob here" or "help needed"... what would this forum be like then?

If you want to advise him forum rules, PM him instead it would help him more.
Is this the way you have got so many posts? :lolflag:

@OP:
EDIT: Did you try disabling ACPI through GRUB options.

---

### Post by xelcius on 2008-06-29
> **Anurag_panda said:**
> 

@OP:
Did you try disabling ACPI in the BIOS.


how you do that?

---

### Post by Canis familiaris on 2008-06-29
> **xelcius said:**
> how you do that?

Oh sorry! I screwed up. I meant disabling ACPI through GRUB options.
Stupid me.:-&

---

### Post by hyper_ch on 2008-06-29
> **Anurag_panda said:**
> If you want to advise him forum rules, PM him instead it would help him more.
Is this the way you have got so many posts? :lolflag:
If I would pm him, then nobody else could learn of this ;)
yes, it how I got so many posts... got a problem with this?

---

### Post by Canis familiaris on 2008-06-29
> **hyper_ch said:**
> 
Yes, It How I Got So Many Posts... Got A Problem With This?
No!

---

### Post by cozmicharlie on 2008-06-29
> **xelcius said:**
> how you do that?

Go into the bios when you start (it is usually done by pressing f2 or f10 or f12 when you first start the computer.  That should take you to settings and look in your settings for a way to turn it off. 

These instructions came from this thread ([http://ubuntuforums.org/showthread.php?t=843053&highlight=noapci](http://ubuntuforums.org/showthread.php?t=843053&highlight=noapci)) - you may want to read through this to get a better feel for what this is doing. 

Turn off apci in grub:  When you're still in GRUB, and your Linux OS is highlighted, hit the 'e' key. This will take you to a different menu where you can edit some options before you boot in. Scroll down until you highlight the line that begins with "boot". Again, hit the 'e' key to edit this line. This will take you to the end of this line and show you a blinking cursor, allowing you to edit stuff.

Here's what you do. First of all, see the words "quiet splash"? Delete those two words. What this does is, instead of giving you a pretty splash screen and hiding all the diagnostic messages from you, when you go to boot the system, it will spew a lot of information to the screen while the system is booting. Even if disabling the services (which I am about to get to) will not help, this extra information will help others tremendously in helping you solve the problem.

We're not done editing yet, though. You deleted 2 words, but you will add a few others instead. For starters, add these three words:

noapci noapic nolapic

See if this helps.  Again, you may want to ry the live cd in safe graphic mode first.

---

### Post by lukjad on 2008-06-29
> **hyper_ch said:**
> One could also say not a good way to introduce themselves either ;)

Just imagine if everybody would just post a thread with a title like: "Noob here" or "help needed"... what would this forum be like then?

> **hyper_ch said:**
> If I would pm him, then nobody else could learn of this ;)
yes, it how I got so many posts... got a problem with this?

> **TWO said:**
> Hyper_ch, way to introduce someone with their first thread on the Ubuntu Forums. :mad: Title aside, I think the content of their thread is enough information for someone who knows how to help them. No need for the sarcasm. With the amount of posts that you have, I imagine that you are either likely to have the answer through experience or you are just a keen poster.

Either way, not a good way to welcome someone at all. 





Hey! *Hey!* ***[SIZE="5"]HEY![/SIZE]*** You and you: time out! Take it outside. ;) Yes saying help needed is not a good way to get help but here is not a place to start a flame and counter-flame war about it. This is a place for love and kindness and "humanity to others." 

Peace on earth and to all a good install.

---

### Post by Papa-san on 2008-06-29
You have to have a minimum of 256k of memory for the graphic installer to work... in most cases. Sometimes 256 is NOT enough to make it through the install process. I had this problem with my old Dell c-610 laptop. If you can get a copy of the 'Alternate Install' CD, you can install it without the graphic installer. It takes a bit of understanding what you are doing, so research it first!

When you get to the partitioning part, I would strongly suggest setting up 3 new partitions: 
1 - /home (this is where your personal data will be stored - keeps from having everything get wiped when you upgrade or re-install due to problems), 2 - swap (2x the size of available memory), and 
3 - ./ (root - this is where the OS files are kept.)

Good luck, and welcome to a better way!

---

### Post by kansasnoob on 2008-06-29
This guide may be of help:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I know it's lengthy, but since it sounds like using the alternate CD may be your best option it has great detail .............. after all you don't want to hose anything:)

---

### Post by xelcius on 2008-06-30
Thank you guys, i will definitely follows your guide and let you know how it worked out.

---

