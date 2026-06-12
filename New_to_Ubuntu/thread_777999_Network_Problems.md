---
title: "Network Problems"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by wandman on 2008-05-01
Hi guys,

Please forgive my linux ignorance. I truly am at noob at this.

I decided to revive a dead laptop and install Ubuntu onto it. I had trouble installing 7.1 from the CD so I tried 6.06. It worked fine and I upgraded within Ubuntu to 7.04. That worked fine too. Then I upgraded to 7.10 and started to see problems.

I got an error message at startup stating that my bios was past the cutoff for acpi support. But using the advice in this forum I added a line to the menu.lst kernal acpi=off.

Now I cannot connect to the network. I have tried both wired and a Netgear WG511 wireless card.

All the settings seem correct as far as I can see but I really would appreciate someone guiding me through what steps to take to try and make it work again. I'd like to tell you the system specs but I am unsure how to even find this out.

Thanks in advance to anyone who can help.

---

### Post by superprash2003 on 2008-05-01
please go to the terminal and type ifconfig and post output here

---

### Post by wandman on 2008-05-02
Thanks for assisting me surperprash2003!

I'm trying to paste the results of ifconfig into a document but I cannot put it onto a floppy disc or a removable usb drive. It gives me the error that I do not have permission to write to it.

I've tried this:
[INDENT]cd /media/disk-1
sudo chmod -R a+rw *[/INDENT]

But no luck.

---

### Post by superprash2003 on 2008-05-02
well if you could tell me whether you are getting an ip on that machine.. also if you are able to ping the router or not

---

### Post by frup on 2008-05-02
Your laptop is probably telling you 7.10 is too heavy for it :P

How much ram does it have (I'm guessing not enough to install the LiveCD???)

Also you might have a wireless on off button, is this off? Did no acpi disable the software to turn this on/off? Can you configure it from your bios? Are you able to update your bios?

If you have low ram (256mb or less) I would recommend trying xubuntu. The latest 8.04 might work fine! Instead of doing no apci maybe try the safe graphics option? What video card does the laptop have btw? But maybe the newer kernel of 8.04 could solve your acpi problems?

---

### Post by wandman on 2008-05-02
Thanks superprash and frup,

My Laptop is OLD! (Its an AJP 2200T) I couldn't get LiveCD to work so maybe I'll give Xubuntu a go and hopefully I'll get along better with it. Ubuntu was taking a very long time to load so you are probably right that my computer won't manage it.

Annoyingly the BIOS isn't supported anymore so I cannot upgrade it and I'm not sure how much RAM I have.

Thanks for your help guys. I'm looking forward to getting into Linux.

---

### Post by wandman on 2008-05-06
I've switched to xubuntu and it runs a bit faster and network wasn't a problem. Thanks very much guys.

---

