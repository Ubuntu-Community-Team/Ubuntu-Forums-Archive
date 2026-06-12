---
title: "Word Processor OS"
date: 2008-01-16
forum: Other OS Talk
---

### Post by ed_agamemnon on 2008-01-16
Ok. So I have a little bit of a problem with distractions. Everything on my lovely linux distracts me from working! I have so many wonderful things to mod, hack and fool around with, that word processing too often gets neglected.

This has to change!

Only, I know I won't be able to kick the habit of a lifetime of computer-tinkering.

What I really need is an OS with nothing but a word processing program. I can't be doing with a terminal based one either. It's got to be X based, or at least framebuffer capable. It's got to be able to save as .txt and .doc, and that's about it.

I just want to work!

So, first of all - is there such a thing as a dedicated word processing OS. If not, can I hack the hell out of Ubuntu to make a no-distractions Abiword-only (or even gedit-only) work paradise?

I hope someone has an answer.

---

### Post by jrusso2 on 2008-01-16
How about a typewriter or an old wang word processor?

---

### Post by wolfen69 on 2008-01-16
do a command line install of ubuntu and add only a word processor. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by ed_agamemnon on 2008-01-16
I actually have both already, but they have severe disadvantages:

The keyboards on those electronic word processors are terrible, and the crummy un-backlit 30 character limit LCDs are almost totally useless.

As for typewriters propper, I seem to find myself forever reinking the ribbon. Although, a far more serious problem with these things is the absence of a delete key.

I don't want to go back to the stone age, I just want to stop my mind from wandering!

Could I maybe just apt-get remove EVERYTHING except for Abiword? I don't want GNOME either (somehow I find drawing boxes on the desktop even better than typing!). I just want a blank white screen with a cursor, a save button, a print button, actually - that'll about do me!

---

### Post by darrelljon on 2008-01-16
[NaNoWriMo]("http://www.murga-linux.com/puppy/viewtopic.php?t=1343") is a Puppy derivative designed for writers.

---

### Post by K.Mandla on 2008-01-17
If you really want to cut the distractions, don't install any graphical system and do all your writing from nano. :shock:

What's that other console word processor-type program? Antiword? I forget now.

---

### Post by dptxp on 2008-01-17
Why not just remove everything else, even Menus ? Just keep one Word Processor. Make one desktop icon. And only 2 partitions, / and SWAP.

Or maybe remaster a Distro like Puppy !!!

---

### Post by Bungo Pony on 2008-01-17
Get yourself a nice Coleco Adam computer

[IMG]http://mo5.com/blogs/media/adam.jpg[/IMG]

It has a built in word processor and a high speed tape drive to save your data on. It'll plug right into a monitor (that has a video in) or even a TV. It also comes with a daisywheel printer. Noisy as hell, but it gets the job done.

And if you find some old Colecovision cartridges, you can play games on it :D

---

### Post by dptxp on 2008-01-17
To the OP-

You can see that people are working really hard to help you.:)

---

### Post by maybeway36 on 2008-01-17
You could do a command-line Ubuntu install and
```
sudo apt-get install xorg abiword icewm
```
And also install wdm or similar if you want a graphical login.

---

### Post by Darkhack on 2008-01-18
When I read the subject, I thought this thread would be asking for a minimal OS due to computer resources.  If you are so easily distracted that you actually have to modify your operating system by removing applications, then I think something more serious is going on that would require ADD medication.  Also, what is to stop you from reinstalling a new OS or just apt-getting all the neat toys again?

---

### Post by Whiffle on 2008-01-18
If I were that desperate, I'd make another X session in GDM that just runs your word processor.  IT wouldn't do me any good, since I usually am referring to more than just one window, but it might work for you.  

I know what you mean though, its tough to get working sometimes, linux is like a big free amusement park with short lines.

---

### Post by ljsmithx on 2008-01-18
After I installed 7.10 stuffed around with compiz and other useless things for a few days... but my mum thinks i have ADD lol so maybe the same goes for the thread starter

---

### Post by init1 on 2008-01-18
> **ed_agamemnon said:**
> Ok. So I have a little bit of a problem with distractions. Everything on my lovely linux distracts me from working! I have so many wonderful things to mod, hack and fool around with, that word processing too often gets neglected.

This has to change!

Only, I know I won't be able to kick the habit of a lifetime of computer-tinkering.

What I really need is an OS with nothing but a word processing program. I can't be doing with a terminal based one either. It's got to be X based, or at least framebuffer capable. It's got to be able to save as .txt and .doc, and that's about it.

I just want to work!

So, first of all - is there such a thing as a dedicated word processing OS. If not, can I hack the hell out of Ubuntu to make a no-distractions Abiword-only (or even gedit-only) work paradise?

I hope someone has an answer.
FreeDOS would be good if you could find a suitable DOS word processor for it. Edit is good for plain text editing
[www.freedos.org](www.freedos.org)
Edit:
Minix is also a possibility
[www.minix3.org](www.minix3.org)

---

### Post by Bungo Pony on 2008-01-19
> FreeDOS would be good if you could find a suitable DOS word processor for it.

Microsoft Works 2.0! It freezes and crashes sometimes, but it's a word processor.

I used to use one called Windoword. It wasn't too bad, but it doesn't save anything in a standard format (from what I can remember).

---

### Post by chris4585 on 2008-01-26
> **wolfen69 said:**
> do a command line install of ubuntu and add only a word processor. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

+1 install something like openbox or fvwm (not crystal) then run in a terminal "apt-get install abiword abiword-common" fvwm-crystal is good but does come with some software, you might want to try it, its not really alot of software, really its alot nicer to look at then fvwm default

check out my sig for more information

---

### Post by jpkotta on 2008-01-27
> **chris4585 said:**
> +1 install something like openbox or fvwm (not crystal) then run in a terminal "apt-get install abiword abiword-common" fvwm-crystal is good but does come with some software, you might want to try it, its not really alot of software, really its alot nicer to look at then fvwm default

check out my sig for more information

I'm going to have to disagree here.  I waste way too much time hacking my FVWM config.  Go with Crystal, it's already configured.  Or better yet, something that isn't as much fun to play with, like TWM.

---

### Post by chris4585 on 2008-01-27
well in my opinion fvwm-crystal is better, but what i gathered from his question he just wanted to get a system with just a word processor, in fvwm the terminal is already in the menu, so just run that then run abiword via terminal, well whichever works truthfully go with fvwm-crystal its better without suffering much at all, so i do disagree with my last post

---

### Post by enpi on 2008-03-06
Hi, I wanted to point out a *very* small utility I have written to bring back the experience of good old text-based word processors. It works in the console but also under X, and it can be used as a lightweight word processor for the GUI. You edit your stuff in plain text and get versions of it in ps and pdf dumped to your working directory. As of v.0.2 a non-tagged plaintext version of your file will also be saved alongside the ps and pdf ones.

[http://enpiscript.blogspot.com](http://enpiscript.blogspot.com)

I wrote it in a RH8 box with gv as gui viewer. Change it to evince or to your viewer of choice right in the script. Hope you like it.

---

### Post by kerry_s on 2008-03-06
lol, i can't believe no writer has not taken the time to make a writers kiosk setup. it would be simple to have only abiword pop up. than again you could just use a live kiosk and do your writing in google doc's. :)

---

### Post by insane_alien on 2008-03-06
maybe you could get a program to lock out everything but the word processor for a set amount of time(3 hours or so). i'm sure it wouldn't be to hard to create(then again, i'm no programer)

---

### Post by enpi on 2008-03-11
> **init1 said:**
> FreeDOS would be good if you could find a suitable DOS word processor for it.

If you are using FreeDOS you may find this list interesting:
[http://short.stop.home.att.net/freesoft/txtedit1.htm#wordproc](http://short.stop.home.att.net/freesoft/txtedit1.htm#wordproc)

---

### Post by enpi on 2008-07-09
> **enpi said:**
> Hi, I wanted to point out a *very* small utility I have written to bring back the experience of good old text-based word processors. It works in the console but also under X, and it can be used as a lightweight word processor for the GUI. You edit your stuff in plain text and get versions of it in ps and pdf dumped to your working directory. As of v.0.2 a non-tagged plaintext version of your file will also be saved alongside the ps and pdf ones.

[http://enpiscript.blogspot.com](http://enpiscript.blogspot.com)

I wrote it in a RH8 box with gv as gui viewer. Change it to evince or to your viewer of choice right in the script. Hope you like it.

Version 0.2 of the script is available for download from the enpiscript site. My thanks to those who have reviewed and tried enpi. It is a *very, very minor* program if compared to any normal word processor, but it works and it does what it is expected to. Hope you find it useful and fun to write with.

---

