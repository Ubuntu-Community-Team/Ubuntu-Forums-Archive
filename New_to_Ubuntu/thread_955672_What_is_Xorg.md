---
title: "What is Xorg?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by pluekiller on 2008-10-22
My newly installed ubuntu is suffers from massive slowdowns just by using firefox!

It seems like Xorg is always at 100% when i suffer these slowdowns.

Am i doing anything wrong?

---

### Post by icanfly0307 on 2008-10-22
I seriously don't know what's going on but........

to answer your question: Xorg is basically the X window system used in linux. It's the base of the graphical environment for your computer. If X slows down when you're using Firefox, you could try to switch over to a more light weight desktop environment like Fluxbox. Install it by issuing the command: 

[FONT="Courier New"]sudo apt-get install fluxbox[/FONT]

Try to see if this helps.

---

### Post by icanfly0307 on 2008-10-22
I seriously don't know what's going on but........

to answer your question: Xorg is basically the X window system used in linux. It's the base of the graphical environment for your computer. If X slows down when you're using Firefox, you could try to switch over to a more light weight desktop environment like Fluxbox. Install it by issuing the command: 

[FONT="Courier New"]sudo apt-get install fluxbox[/FONT]

Try to see if this helps.

btw, what are your system specs?

---

### Post by Elfy on 2008-10-22
I would start with checking whether there is a graphics driver available - look in Hardware Drivers in the System Admin menu

Would be good to have system specs

---

### Post by pluekiller on 2008-10-22
If my system can't handle web browsing smoothly on ubuntu, i'm going back to windows right now :(

I have a core 2 duo running at 1.9Ghz, 9600M GT, and 2GB of ram..

---

### Post by Elfy on 2008-10-22
So did you look in hardware drivers? There will be a driver there for it I suspect

---

### Post by pluekiller on 2008-10-22
Yes i did... It's already enabled..

---

### Post by billgoldberg on 2008-10-22
> **pluekiller said:**
> If my system can't handle web browsing smoothly on ubuntu, i'm going back to windows right now :(

I have a core 2 duo running at 1.9Ghz, 9600M GT, and 2GB of ram..

lol

Sounds like a driver issue or a bug.

Do as forestpixie suggested.

Btw, people who are shouting "I'm going back to windows" usually don't get much help.

We are here out to help the community, most don't appreciate "threats".

---

### Post by icanfly0307 on 2008-10-22
WHOA! hold it right there!

don't give up on ubuntu! and don't move back to windows; it's worse.

what's your graphics card model? with system specs like that, ubuntu would be SUPER FAST!

are you using the right device driver?

---

### Post by mali2297 on 2008-10-22
Check if the problem persists if you disable the desktop effects.

---

### Post by pluekiller on 2008-10-22
did it sound like a threat? I'm sorry. It was more of a... sigh of resignation.

okay i'll try it with desktop effects off..

---

### Post by pluekiller on 2008-10-22
I don't seem to get the problem with desktop effects turned off...

Graphics driver problem?

---

### Post by icanfly0307 on 2008-10-22
Are you really that desperate about Desktop Effects? I know they're nice and everything, but do you really need them? If you would prefer not to have them enabled, then you're problem is solved!

---

### Post by Elfy on 2008-10-22
Ok, you say you've newly installed - is it hardy or have you gone for the intrepid beta. Also are all the updates applied to it

---

### Post by jerome1232 on 2008-10-22
I vote graphics driver problem, how did you install them initially? May want to try installing the latest via envy or from nvidia's website (envy being easier to do)

---

### Post by bull205 on 2008-10-22
You could try to install envyng to manage your graphics drivers...I'm the new guy, so someone call me on it if this is wrong.

sudo apt-get install envyng

Its a nice GUI tool that will help you manage the correct NVIDA/ATI drivers.

More info at [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by pluekiller on 2008-10-22
It's a newly installed hardy..

Okay i'll try envy.

Its not a MUST that i have desktop effects.. But I would prefer it :)

---

### Post by Elfy on 2008-10-22
> **jerome1232 said:**
> I vote graphics driver problem, how did you install them initially? May want to try installing the latest via envy or from nvidia's website (envy being easier to do)

I'd go for that too - disable from the hardware drivers first reboot and then run envyng

---

### Post by pluekiller on 2008-10-22
Seems to have worked. Thanks all =)

---

### Post by bull205 on 2008-10-22
Please mark the thread as solved....i think the administrator's dig that sort of thing.

:guitar:

---

### Post by billgoldberg on 2008-10-22
> **pluekiller said:**
> I don't seem to get the problem with desktop effects turned off...

Graphics driver problem?

Most likely.

What driver do you have installed?

Edit: these kinds of post happen when you don't mark your problem as solved.

---

### Post by wasd591 on 2009-12-20
Yah, with a computer like that it shouldn't be slow. If you have compiz or Desktop Effects running in the background, it shouldn't be that slow. Make sure you don't have too many terminal or even calculator windows open. Open Office slows the computer down big time. :( Here's what to do. 
**1**
[INDENT]Open **Terminal** (Applications > Accessories > Terminal) and type in *top*.[/INDENT]

**2**
[INDENT]Take a screenshot of the window (full screen may help :)) and post in this thread.[/INDENT]

---

### Post by UnknownFear on 2009-12-20
The OP has in fact solved his issue and just needs to mark it as [SOLVED] so more users can focus on other threads.

---

### Post by FormatSeize on 2009-12-20
> **icanfly0307 said:**
> I seriously don't know what's going on but........

to answer your question: Xorg is basically the X window system used in linux. It's the base of the graphical environment for your computer. If X slows down when you're using Firefox, you could try to switch over to a more light weight desktop environment like Fluxbox. Install it by issuing the command: 

[FONT="Courier New"]sudo apt-get install fluxbox[/FONT]

Try to see if this helps.
I wondered what Xorg was as well, but never really researched it. Under Slackware, there's X11 (or something like that, someone correct me), and the command
[FONT="Courier New"]startx[/FONT]
will take me to a graphical environment. So is Xorg something that makes the environment that I see when I use Ubuntu?
Also, if I install Fluxbox to try it out, will it be pretty easy to uninstall, or will it be something I wouldn't want to do unless I planned on using it permanently?

---

### Post by tuahaa on 2009-12-20
Wasn't this thread ditched last year?:confused:

---

### Post by NiGhtMarEs0nWax on 2010-03-06
:popcorn:

---

### Post by kleskjr on 2010-05-20
:guitar:

---

### Post by myrtlebeach2000 on 2010-11-30
> **pluekiller said:**
> If my system can't handle web browsing smoothly on ubuntu, i'm going back to windows right now :(

I have a core 2 duo running at 1.9Ghz, 9600M GT, and 2GB of ram..

I agree with you. I found this forum searching for reason my system was so stressed using Ubuntu. This is my 3rd new install (not upgrades) of various versions of Ubuntu over the past 3-5 years and this is the first version that took all my resources to operate. 
When I read about Xorg, I went to System - Preferences - Remote Desktop Preferences and deselected "Allow other users to view your desktop". 
My CPU  is down to about  20-30% most times. Maybe 30-40% with Firefox running approximately 8 tabs. 
I have a Toshiba with X2 dual core AMD Turon processor and 3 gb ram.
I have Vista, Windows 7, and Ubuntu 10.10. 
I boot into Ubuntu, not Windows as I installed it on a new partition. 
Also, the previous versions of Ubuntu did not take abnormal percenage of resources.

Since disabling Remote Desktop, I have not problem. 
Why would this option be enabled by default? It seems to be something to be enabled by the user when they know what they are enabling.

Try changing your setting and not going back to Windows.

MyrtleBeach2000

---

