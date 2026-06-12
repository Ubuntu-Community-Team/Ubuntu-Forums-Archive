---
title: "[SOLVED] Easy question for those who know about 64 bit Ubuntu"
date: 2008-12-10
forum: Recurring Discussions
---

### Post by Chris Watts on 2008-12-10
I have just realised that most of my fav apps are kde ones and have realised I should have originally downloaded Kubuntu instead.
I tried to download KDE4 using the Add/Remove GUI tool but it says KDE 4 doesn't support AMD64... are all 64 bit kernels called AMD64 as my CPU is a Centrino Duo in a Toshiba A200 Laptop !?!

---

### Post by taseedorf on 2008-12-10
KDE works on 64 bit Ubuntu.

go to terminal and type
sudo apt-get install kde4

---

### Post by Chris Watts on 2008-12-10
back to the command line again... forget it... I'll just go back to XP
Has anyone told linux users that if they want to use a command line then they shouldn't need a GUI. I don't find that concept confusing at all and yet Gnome seems to revolve around the command line.... Is KDE4 that antiquated?

---

### Post by AnonCat on 2008-12-10
If you don't want to use the command line, just to go to system>administration>synaptic and install from there.  The command line is much faster though.  It doesn't take much time to load the terminal and cut and paste a command into it.

---

### Post by taseedorf on 2008-12-10
yeah, you don't NEED to use the command line, but it's easier.

just do what the guy said, go up to the top to system, than go to administration, than to synaptic....

than search for kde, and install it...
should be kde4.325453 or some random numbers..not sure right now.

if you wanted to try and install a new display manager in windows, you would have to do ALOT MORE than copy/paste a command into a terminal.  be happy that its this easy in linux.

---

### Post by Chris Watts on 2008-12-10
k... will try it... I don't understand the Synaptics package manager - the package system was why I left linux eight years ago and although you seasoned Ubuntu users may know the command line I can only remember bits and pieces... but it does seem easier than Synaptics Package manager I must admit. 
I like the add/remove option in the Applications menu... this is the first time it hasn't worked properly. If Synaptics package manager will let me install KDE4 then surely it just means that some part of the add/remove system hasn't been updated with the proper information yet?

---

### Post by hyper_ch on 2008-12-10
> **Chris Watts said:**
> back to the command line again... forget it... I'll just go back to XP

Bye bye ):P):P):P):P):P

---

### Post by Chris Watts on 2008-12-10
And there right above me is the pompous type of individual that causes so many problems for windows users migrating to linux.

Anyway, disregarding those who won't help, here is what happened with the command line:

:~$ sudo apt-get install kde4
[sudo] password for bilbo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde4

---

### Post by hyper_ch on 2008-12-10
> **Chris Watts said:**
> And there right above me is the pompous type of individual that causes linux to remain the black sheep.

Anyway, disregarding idiots,

Congratulations: You're now one of the selected few who made it to my ignore list ;)

---

### Post by jamesrl on 2008-12-10
Install kde4 by installing kdebase (which is kde 4 in 8.10 and possibly 8.04)
e.g.,
sudo apt-get install kdebase

---

### Post by prshah on 2008-12-10
> **Chris Watts said:**
> 
:~$ sudo apt-get install kde4
[sudo] password for bilbo: 
E: Couldn't find package kde4

Here's another nice little command line```
sudo apt-get install kubuntu-kde4-desktop
``` that will install KDE4 desktop for you.

However, for command-line-phobics, I don't know if the above advice is good enough. You may also need:

```
df -h
``` to check if you have enough disk space.
```
sudo apt-get update && sudo apt-get update
``` makes sure all your current programs are upto date before attempting to update; this is a necessary step, or you _may_ end up with a broken desktop requiring more command line jiggery-pokery.

I too am an idiot just like hyper_ch. Let's see how far you get by disregarding this piece of advice.

---

### Post by scottuss on 2008-12-10
There's no need for this people! Linux isn't easy to switch to for some people and we should try to help out where we can!

OK, so go back to the terminal and do the following

sudo apt-get install kubuntu-desktop


That will install KDE for you. If you need any more help, let me know!

:guitar:

---

### Post by scottuss on 2008-12-10
> **prshah said:**
> Here's another nice little command line```
sudo apt-get install kubuntu-kde4-desktop
``` that will install KDE4 desktop for you.

However, for command-line-phobics, I don't know if the above advice is good enough. You may also need:

```
df -h
``` to check if you have enough disk space.
```
sudo apt-get update && sudo apt-get update
``` makes sure all your current programs are upto date before attempting to update; this is a necessary step, or you _may_ end up with a broken desktop requiring more command line jiggery-pokery.

I too am an idiot just like hyper_ch.

Darn, posted just before me :p

---

### Post by taseedorf on 2008-12-10
LOL

Linux for black sheep??

LOL

NSA, Google, NASA, etc.... a few "black sheep" using Linux.

---

### Post by sdennie on 2008-12-10
Keep it civil, please.

Also, command line solutions are common on these forums because they are exact and language independent.  It's much easier to copy/paste both a command and its output than it is to describe how to use a gui and then posts its output if it doesn't work.

---

### Post by scottuss on 2008-12-10
I guess some people only judge how popular an O/S is by how many use it, not who uses it. Linux has some very important real world applications, it's just a shame that the most common one of those is not as the desktop O/S of choice (One day soon! lol)

---

### Post by jamesrl on 2008-12-10
The benefit of not using the command line and going to synaptic instead, is that you can (more easily) search for packages you don't know with synaptic and see the description etc prior to install.  [You can do all that from the command line but you have to know more syntax.]

---

### Post by Helios1276 on 2008-12-10
> **Chris Watts said:**
> back to the command line again... .... Is KDE4 that antiquated?

Antiquated? ..I think your in the wrong place, seek the nearest Mac vendor.

---

### Post by Chris Watts on 2008-12-10
> **taseedorf said:**
> LOL

Linux for black sheep??

LOL

NSA, Google, NASA, etc.... a few "black sheep" using Linux.

Ah you want figures... ok well I am one of the 98% of all computer users having trouble with switching to Linux. I mentioned XP in a moment of frustration... I hardly think this piousness so frequently found in these forums is becoming of the keepers of the new technological revolution. Now can we lay down our guns and just try to get through another day. (much harder for me than you who have the experience already)

---

### Post by scottuss on 2008-12-10
People are only trying to help you through that day, yes some Linux users can seem a little harsh to newbies, just as some Windows and Mac fanboys get irate about their chosen platforms. 

Some of your comments were just taken in the wrong way I think, the suggestion of going back to XP just because you had to enter a few commands in the terminal does frustrate advanced Linux users because we don't see the problem with doing so. Copying and pasting isn't hard! 

If you sit back and look, Windows requires more effort to do simple tasks than Linux does in many cases. The terminal is nothing to be affraid of, it's just a new concept! 

Microsoft does well to hide technical stuff behind fancy GUI's, sometimes this is bad practice as people get used to fluffly GUI's to do everything. In the Linux world there aren't so many fluffy GUIs, but that isn't a bad thing!!

Sorry if that went on! :-)

Edit: Actually there are GUIs for nearly everything, again these aren't difficult to use.

---

### Post by bapoumba on 2008-12-10
Moved to Recurring Discussions..

---

