---
title: "Netscape no longer connects"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by Withanie on 2012-05-18
Very newbie-ish question here...

I've just installed 12.04.  It worked beautifully.  Read through the security threads a bit and decided to enable UFW with recommended settings (deny all).  Shut down for the night with a feeling of peace.

Next day: Netscape cannot connect to anywhere.  My Internet connection is fine (tested with another computer). Ubuntu reports that my network adaptor is fine and connected. I can go to the Ubuntu software list and browse for programs...   I just can't surf.  

I've run, sudo ufm allow outgoing.
I've run, sudo ufm reset.

I've tried to install Chromium in the hope that it would look after it's own configuration, but it doesn't seem to finish the installation - certainly won't run.

I'm hoping that someone with more experience will recognize my error and say, "Silly newbie, just do this...".  Please?

---

### Post by lukeiamyourfather on 2012-05-18
Have you tried disabling UFW completely to know if that's the issue?

---

### Post by choppyfireballs on 2012-05-18
You had the right idea to attempt to install another browser. However I would recommend chrome not chromium. chromium is a development release meaning it's a.) not stable, and b.) doesnt come with packages and flash support that chrome does. 

on a computer with internet go to google.com/chrome click on the browser tab go to support, then go to install chrome select the debian linux version then put it on a flash drive and install it on your linux box and see if that fixes your issue.

---

### Post by Withanie on 2012-05-18
> **lukeiamyourfather said:**
> Have you tried disabling UFW completely to know if that's the issue?

I was a bit afraid to try that.  (I'm a newbie)  But, I do plan to attempt it tonight. Thanks for the suggestion.

---

### Post by choppyfireballs on 2012-05-18
> **Withanie said:**
> I was a bit afraid to try that.  (I'm a newbie)  But, I do plan to attempt it tonight. Thanks for the suggestion.

it's not hard it's a .deb file all you need is the file 

put the file on your computer and run it in software center and it will install automatically (without internet I think i'm not sure)

---

### Post by Derek Karpinski on 2012-05-18
> **choppyfireballs said:**
> You had the right idea to attempt to install another browser. However I would recommend chrome not chromium. chromium is a development release meaning it's a.) not stable, and b.) doesnt come with packages and flash support that chrome does. 

on a computer with internet go to google.com/chrome click on the browser tab go to support, then go to install chrome select the debian linux version then put it on a flash drive and install it on your linux box and see if that fixes your issue.

Chrome is closed sourced and includes what some might call 'spyware'.  Chromium is open source and doesn't include that.  Both are good, and I've never had an issue with stability in chromium.

---

### Post by Peripheral Visionary on 2012-05-18
Netscape is now [Seamonkey]("http://www.seamonkey-project.org/"). Works awesomely on 12.04!

---

### Post by pablo180 on 2012-05-18
> **Withanie said:**
> I was a bit afraid to try that.  (I'm a newbie)  But, I do plan to attempt it tonight. Thanks for the suggestion.

Try installing the GUI for the firewall:

```
sudo apt-get install gufw
```

Or if you'd prefer, open the Software Centre and search for 'gufw' or 'Firewall Configuration' and install that (both the same thing). 

Then just type Firewall into Unity's dash and open it. Much easier to configure and it let's you turn it off with a switch.

---

### Post by jtarin on 2012-05-18
Let's diagnose your connection. The keys Ctrl+Alt+T will open a terminal. In the terminal type ```
ifconfig
``` copy and post the results here between the "#" code lines. The "#" button is located in the menu above your Advanced Reply box.

---

### Post by Withanie on 2012-05-19
All fixed!   It turned out to be a DNS problem.   I found that I could open an IP address but not a named address.  

Found instructions on Google for using their DNS server (with specific instructions for Ubuntu! :) ) and all is well. 

Thanks for your help, everyone who replied.

---

### Post by Peripheral Visionary on 2012-05-19
> **Withanie said:**
> All fixed!   It turned out to be a DNS problem.   I found that I could open an IP address but not a named address.  

Found instructions on Google for using their DNS server (with specific instructions for Ubuntu! :) ) and all is well. .

Wonderful! Be sure to mark this thread as **[SOLVED]** (see "thread tools") so thers can see it and benefit from what you've learned. And thanks for sharing what you learned with the rest of us!

---

### Post by Withanie on 2012-05-20
Update:   Upon further research, the problem turned out to be a duplicate of an earlier:

[http://ubuntuforums.org/showthread.php?t=1865152&highlight=1861105](http://ubuntuforums.org/showthread.php?t=1865152&highlight=1861105)

---

### Post by choppyfireballs on 2012-05-21
> **Derek Karpinski said:**
> Chrome is closed sourced and includes what some might call 'spyware'.  Chromium is open source and doesn't include that.  Both are good, and I've never had an issue with stability in chromium.

I understand this and while you may not have had stability issues with it doesn't mean that it's more or as stable because the chrome/ium browsers are extremely stable to begin with. The reason that I use chrome over chromium is the continuous flash updates and that it works better with my android, i have had issues with apps in chromium using apps that benefit my android.

---

### Post by choppyfireballs on 2012-05-21
[e

---

### Post by Derek Karpinski on 2012-05-21
> **choppyfireballs said:**
> I understand this and while you may not have had stability issues with it doesn't mean that it's more or as stable because the chrome/ium browsers are extremely stable to begin with. The reason that I use chrome over chromium is the continuous flash updates and that it works better with my android, i have had issues with apps in chromium using apps that benefit my android.

No problem.  Just pointing it out in case the OP didn't know.  You're free to use whatever floats your boat. :D

---

### Post by choppyfireballs on 2012-05-22
> **Derek Karpinski said:**
> No problem.  Just pointing it out in case the OP didn't know.  You're free to use whatever floats your boat. :D

agreed use whatever you want that's why we're here

---

### Post by jtarin on 2012-05-22
> **choppyfireballs said:**
> agreed use whatever you want that's why we're here
Now you tell me.:p

---

### Post by choppyfireballs on 2012-05-23
> **jtarin said:**
> Now you tell me.:p

Well you know how these things go one drink leads to another, and another, and another, and the next thing you know we're not using windows anymore. Lawl glad you got your issue fixed.

---

