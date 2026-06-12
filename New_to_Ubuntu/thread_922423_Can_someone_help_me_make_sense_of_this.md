---
title: "Can someone help me make sense of this?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-09-17
Hey Im trying to install my wireless card. I found this guide on here earlier but am having alot of trouble making sense of it.

I put in the commands and stuff but nothing happens -_- The window just closes for the most part.

I installed the program off of the Ubuntu Live CD that was recommended but I still cant seem to make anything work.



[http://ubuntuforums.org/showthread.php?t=170306](http://ubuntuforums.org/showthread.php?t=170306)


I have the drivers for the card on CD, so I dont need to download them I dont think.

---

### Post by aeiah on 2008-09-17
hmm the window shouldnt be closing. you are typing these commands into the terminal arent you? (menu > accessories > terminal)

which bit isnt working? what happens when you do ```
sudo apt-get install ndiswrapper-utils
```

find your drivers on the cd and copy them to the desktop like it suggests, then follow the rest of the commands.

---

### Post by Vendettaseve on 2008-09-17
Oh, no lol, I was typing them into the alt+F2 window


Also I dont understand this part


cd ~/Desktop
sudo ndiswrapper -i PRISMA02.inf
sudo modprobe ndiswrapper


Primarily the first one, since the ~ dose not make a ~

---

### Post by jken146 on 2008-09-17
> **Vendettaseve said:**
> Primarily the first one, since the ~ dose not make a ~

~ stands for /home/yourUserName.

---

### Post by Vendettaseve on 2008-09-17
so type in

cd/home/vendettaseve/desktop

And it should look there when I type in the next set of commands? Instead of looking in the usr/sbin folder?

---

### Post by jken146 on 2008-09-17
Yes, if I understand you.  cd stands for Change Directory, so it forgets about wherever you were before and starts working in ~/Desktop.

---

### Post by Vendettaseve on 2008-09-17
Ah, ok :) Good :D

---

### Post by aeiah on 2008-09-17
> **Vendettaseve said:**
> so type in

cd/home/vendettaseve/desktop

And it should look there when I type in the next set of commands? Instead of looking in the usr/sbin folder?

when you open a terminal it actually starts off first in your home directory, so really to change to your desktop folder you'd just need ```
cd Desktop
``` in that instance, since you'll already be in home. the only reason it asks you to change directory to the desktop is because it asks you to copy the driver file(s) from the CD or internet to the desktop, so you need the terminal to be in that direction before proceeding with the other commands

---

### Post by Vendettaseve on 2008-09-17
When I type it in it just says no such file or directory :(

---

### Post by northern lights on 2008-09-17
Specs on the wireless card and the type of encryption might be of help. Can you please post the outputs of ```
sudo lshw -C network
``````
ifconfig
```and```
iwconfig
```
Thank you.

---

### Post by Vendettaseve on 2008-09-17
> **northern lights said:**
> Specs on the wireless card and the type of encryption might be of help. Can you please post the outputs of ```
sudo lshw -C network
``````
ifconfig
```and```
iwconfig
```
Thank you.

I just need to get the driver installed. I have the guide from here about that specific card and am just having trouble putting in the proper commands. Thanks for reading.

---

### Post by northern lights on 2008-09-17
If by "the guide" you mean the link supplied in the first post, you might want to notice it's age. This is from Dapper times.

With the rapid development of GNU/Linux and a six month release cycle as is the case for Ubuntu, two year old instructions will almost 90% of the time be obsolete.

The "proper commands" no one can really come up with without the proper information.

I'm not going to beg for the outputs, I can live without 'em. If however, you want adequate help, that'd be a start.

---

### Post by Vendettaseve on 2008-09-17
Ah, right


Will it even tell me anything about the card since there is no driver? The lights are not on currently and is showing no activity.

---

### Post by northern lights on 2008-09-17
Yes it will - most likely at least, that is.

Open a terminal (Applications > Accessories > Terminal) and run the three commands. The first one, 'sudo lshw -C network' is the most vital.

---

### Post by Vendettaseve on 2008-09-17
the command sudo lshw -c network did nothing, just brought up a list of commands that did not pretain to my networking thing, regardless of what I typed it just brought up the same list of commands over and over.


As I suspected, it did not read my card. Iwconfig brought up a thing that said no wireless extensions twice.

if config brought up alot of info but it was primarily just 0s for everything.

I think you might be mistaken about what Im doing here. Im on 2 different computers right now, this one is a VISTA comp connected to the net, the other one is 2 storys down and is not connected. 

How can I run the program that will install the proper config from the Prism02 file for my usb network tooth.

---

### Post by Vendettaseve on 2008-09-17
Anyone?

---

### Post by northern lights on 2008-09-17
> **Vendettaseve said:**
> the command sudo lshw -c network did nothing, just brought up a list of commands that did not pretain to my networking thing, regardless of what I typed it just brought up the same list of commands over and over
If 'lshw -C network' had given no output, you could safely assume that your network device(s) are not being recognized. Since it returned some, either of two things is the case:
1. Your interpretation as to the out put is wrong.
2. You entered it with lower-case 'C'. The shell is case-sensitive. 

Again, just post the darn outputs.

---

### Post by philinux on 2008-09-17
**Copy and paste **the commands that Northern Lights gave you.

A lot are case sensitive.

---

### Post by Vendettaseve on 2008-09-17
Ah, that was probly it. 


Iether way, Iv decided to reverse my system and wire my router directly to my computer, put the wireless tooth on my other computer. 

Will this work?

---

### Post by Vendettaseve on 2008-09-17
Ah, that was probly it. 


Iether way, Iv decided to reverse my system and wire my router directly to my computer, put the wireless tooth on my other computer. 

Will this work?

---

