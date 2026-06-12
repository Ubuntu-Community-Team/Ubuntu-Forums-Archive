---
title: "Choppy video and sound and crashing problems"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Optimus_Jazz on 2008-11-21
Hi everyone, i am at my wits end with ubuntu and am going to switch to windows(unfortunatley) unless of course someone can give me a helping hand.This is my last attempt to give ubuntu another go,,and after 2 months i really want to keep using it as its a great os,but its giving me so many problems.

Before i start can i only understand the basics of ubuntu,and thats more than likely why i am having these problems.

1.Videos : Youtube and similar sites:

-Videos are very choppy

-video will play but a grey screen will appear instead of the video player

-No video player will appear and a white screen will be displayed,no sound nothing..



2.Web Browsing : I am using firefox.

- As i scroll down its very stop start/choppy and this is horrible.

- The browser keeps fading to grey,its happening alot today.It will stay like this for a few seconds,return to normal and happen again.Sometimes i need to force quit.


3. Music : Music is becoming choppy also,very annoying as its skipping when i try tcroll down web pages.


4.IT CRASHES WHEN IT FEELS LIKE IT :

Randomly the screen flashes and goes black,then the following script appeares :



* Starting anac(h)ronistic cron anacron [ok]
* Starting deffered execution scheduler atd [ok]
* Starting Periodic command scheduler crond [ok]
* Running local boot scripts ( /etc/rc.local ) [ok]


Can anyone out there help end my nightmare!!?:confused:

---

### Post by Therion on 2008-11-21
> **Optimus_Jazz said:**
> Can anyone out there help end my nightmare!!?
Well, maybe.  First a little background would be good.  

What version of Ubuntu are you running and can you tell us anything about the specs of the PC you're running Ubuntu on?

---

### Post by PocketDog on 2008-11-21
First, using Synaptic, remove flash-plugin-nonfree. Then get the Flash 10 .deb file from Adobe. Install that, and restart Firefox. This worked for me. Then I uninstalled Firefox and now I only use Opera. That worked for me too

---

### Post by Tony Flury on 2008-11-21
The window going grey is not just Firefox (and it is not a bug) : it is the Gnome windows manager telling you that the system is so busy (not sure if other managers does similar) and that the application owning the window is currently not taking input (that includes mouse clicks).

When the system is busy on Windows - you get a similar state (and probably more often), but the main difference is that the WIndows often gives you no indication  - or an hourglass pointer if you are lucky - so you end up clicking on a window and getting no response - or a very slow one.

Basically a window going grey is an indication that maybe your system is overworking - what is your system spec and what else might you be running at the time.

---

### Post by Optimus_Jazz on 2008-11-21
cool ill try that now,

Im running on

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

with a Compaq presario v5000 laptop.
AMD turion 64 bit processor,ati graphics card..

---

### Post by HavocXphere on 2008-11-21
I'm a linux noob too, but I reckon the common cause to all this is the graphics/driver/acceleration.

The choppy music often happens when the CPU is maxed out & no cycles/RAM bandwidth is available for decoding the music. I'd guess that the gfx card isn't accelerating the drawing of the scrolling window. Same thing happens in windows if one doesn't install gfx drivers and the CPU isn't powerful enough to handle both the scrolling & decoding.

Same thing with the scrolling in FF.

I'd guess the video decoding in youtube is also suffering for similar reasons.

Not sure about the crashes...that can be a lot of things.

I've got no idea how to fix the video issues...but I'm 80% sure that a misconfigured GFX is the root cause of all this.

---

### Post by philinux on 2008-11-21
Have you checked in System>admin>hardware drivers. Check you graphics card driver is installed.

---

### Post by Optimus_Jazz on 2008-11-21
Yes graphics card is installed,I dont see wht my laptop cant handle ubuntu i thought it was more efficient than xp and my laptop could handle that no problem

---

### Post by markjensen on 2008-11-21
> **Optimus_Jazz said:**
> Yes graphics card is installed,I dont see wht my laptop cant handle ubuntu i thought it was more efficient than xp and my laptop could handle that no problem

Ok, your card is "installed", but is it actually using the accelerated drivers?   If not, then your CPU will be doing all the effects rendering (transparencies, shadows, etc).

Can you open a terminal and post the output of the following command:```
glxinfo | grep render
```You can select the text above with your mouse, then just middle-click in an open console/terminal.   I am hoping it says "no", meaning you can just activate the proprietary ATI driver to fix your issue.

Plus, in my opinion, Ubuntu is more like a Vista than XP.  If you want an XP (or lighter) type of weight, I might recommend Xubuntu with the lighter XFCE desktop.   But that isn't necessarily what needs to be done here - just my opinion on the relative overheads of the aforementioned OSes.

---

### Post by wolfen69 on 2008-11-21
why not give ubuntu 8.10 a try? some people that had media problems in hardy report that 8.10 is better. there are also other distros to try that might work great. ubuntu is not a 1 size fits all solution. if you had dual booted xp and linux, you could have saved a bunch of headaches until you found the right distro. i have learned that when 1 distro does not work, another one will. match the right OS to the right hardware. good luck.

---

### Post by Keen101 on 2008-11-21
Could compiz be interfering or not working right?

you could try disabling compiz in >System >Preferences >Appearance
hope that helps.

also, i want to give you encouragement not to give up yet. If you overall decide to go to windows that's fine, i wont stop you. But, the problems you are describing really don't sound that serious, and I'm positive that we can help you find a solution somewhere.

---

### Post by michande03 on 2008-11-21
well I have had similar problems, and what you describe is most certain hardware and driver related, as it is a laptop I will abruptely assume you have amd or ati graphic card, and that there is help for, but there is some trixing to it :) but fresh install of 8.10 and total fresh install of graphics driver should solve it, if you don't want to do it fresh, you have to remove open source drivers for graphics card and/or remove older fglrx drivers and install the new ones.

At least that way did it for me, and search on your graphic card name on ubuntuforums and you will probably find more info on how to tweak it in to your xorg.conf file for best performance

---

### Post by lifestream on 2008-11-21
> **wolfen69 said:**
> why not give ubuntu 8.10 a try? 

Yup, but PLEASE burn 8.10 to a CD at the lowest speed possible.

PLEASE don't upgrade to 8.10 from the Update Manager :P

You'll be sorry.

I wonder also if you have Tracker search enabled?
You might want to uninstall it *cough* It loves making your PC slow.

---

### Post by Keen101 on 2008-11-21
> **lifestream said:**
> Yup, but PLEASE burn 8.10 to a CD at the lowest speed possible.

PLEASE don't upgrade to 8.10 from the Update Manager :P

You'll be sorry.

I wonder also if you have Tracker search enabled?
You might want to uninstall it *cough* It loves making your PC slow.

I don't quite agree with him. My system upgraded just fine from 8.04 to 8.10. So, i don't think "you'll be sorry". But, since your system is not working, then maybe a 8.10 fresh install is best. Just because some people have problems upgrading doesn't mean everyone will "be sorry".

---

### Post by michande03 on 2008-11-21
yup for me aswell, but driverwise it might be easier

---

### Post by altonbr on 2008-11-22
Just throwing this out there: did you actually install Ubuntu or is it constantly running from a LiveCD? (e.g. you can only run Ubuntu if you have the CD in).

What are the specs on your computer if not? You said Ubuntu can run more efficiently than XP - which it should - but how old is this computer? What processor is in it, how much RAM?

I've seen XP run abominably with 256MB of RAM on an IBM Thinkpad R50, but I've also seen Ubuntu run amazingly smooth on a laptop with 128MB of RAM.

---

