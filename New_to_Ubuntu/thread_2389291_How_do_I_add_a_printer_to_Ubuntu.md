---
title: "How do I add a printer to Ubuntu"
date: 2018-04-14
forum: New to Ubuntu
---

### Post by dave1956 on 2018-04-14
Hi all
I need to do some printing before I switch over to Ubuntu Mate in May

I have attached to this computer via a USB cable a HP Photosmart 5524 printer..
In the Ubuntu Software I found a thing to Configure printers, I click on Launch, which brings me to Printers Localhost with a message There are no printers configured yet. I then click on ADD  where I am asked to Enter device URI ?

I have no idea what it is looking for or what to put into it ?

Dave

---

### Post by TheFu on 2018-04-14
[https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html](https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html) is for 17.10.

---

### Post by dave1956 on 2018-04-14
> **TheFu said:**
> [https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html](https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html) is for 17.10.

Thankyou TheFu.. for the link,, done all that before I started this thread, and that is why I asked "How do I add a printer to Ubuntu"

Dave

---

### Post by TheFu on 2018-04-14
Which version of Ubuntu do you have?  
Which DE are you using? 

For GUI questions, those are always good to know.

For my printers (not HP), I use IPP URLs.  Mine is : ipp://172.22.22.4:631/classes/laser which was set by the **system-config-printer** program.  If the computer you are on is the same as the one with the printer, you can use ipp://localhost:631/... without the IP, after CUPS is setup.  My USB printer is connected to a different Linux machine which makes it available to any other system on my network.

I had to reload my OS a few months ago after an SSD failed.  What I remember about the printer setup was how trivial and non-eventful it was to get the network setup done.

For HP, there are HP specific tools on my system.
```
$ hp-{tab}
hp-align               hp-info                hp-probe
hp-check               hp-levels              hp-query
hp-clean               hp-logcapture          hp-scan
hp-colorcal            hp-makeuri             hp-setup
hp-config_usb_printer  hp-pkservice           hp-testpage
hp-doctor              hp-plugin              hp-timedate
hp-firmware            hp-plugin-ubuntu
```
I would start with **hp-config_usb_printer** and/or **hp-setup** and see if those work.
My google-fu failed to find anything more recent than 2014.  Have you looked on youtube?

Those are all the ideas I have.
Hopefully someone else with a similar HP model will respond.  If you can edit the title to something like "HP 5524 printer on 16.04 Unity help", that might get more eyes.

---

### Post by leunam12 on 2018-04-14
Try the HPLIP toolbox from the software center

---

### Post by jim Kane on 2018-04-14
yes i have also used  HPLIP toolbox to install a HP printer and it worked quite easy

---

### Post by dave1956 on 2018-04-15
> **leunam12 said:**
> Try the HPLIP toolbox from the software center

No application found

That's what I get from the software centre

Dave

---

### Post by dave1956 on 2018-04-15
> **TheFu said:**
> Which version of Ubuntu do you have?  
Which DE are you using? 

For GUI questions, those are always good to know.

For my printers (not HP), I use IPP URLs.  Mine is : ipp://172.22.22.4:631/classes/laser which was set by the **system-config-printer** program.  If the computer you are on is the same as the one with the printer, you can use ipp://localhost:631/... without the IP, after CUPS is setup.  My USB printer is connected to a different Linux machine which makes it available to any other system on my network.

I had to reload my OS a few months ago after an SSD failed.  What I remember about the printer setup was how trivial and non-eventful it was to get the network setup done.

For HP, there are HP specific tools on my system.
```
$ hp-{tab}
hp-align               hp-info                hp-probe
hp-check               hp-levels              hp-query
hp-clean               hp-logcapture          hp-scan
hp-colorcal            hp-makeuri             hp-setup
hp-config_usb_printer  hp-pkservice           hp-testpage
hp-doctor              hp-plugin              hp-timedate
hp-firmware            hp-plugin-ubuntu
```
I would start with **hp-config_usb_printer** and/or **hp-setup** and see if those work.
My google-fu failed to find anything more recent than 2014.  Have you looked on youtube?

Those are all the ideas I have.
Hopefully someone else with a similar HP model will respond.  If you can edit the title to something like "HP 5524 printer on 16.04 Unity help", that might get more eyes.

Thankyou for your reply TheFu

What version of Ubuntu am I using ? Ubuntu 16.04 LTS 
Which DE am I using ? Don't know what a DE is, sorry

But I have no idea what most of that is or indeed what the rest of your answer is, 
"ipp://172.22.22.4:631/classes/laser which was set by the **system-config-printer** program" don't have a clue of any of that.. sorry

All I know is that, I upgraded from Ubuntu 12 which I think may have been LTS to 16.04 LTS which turned into a disaster.  I am going to do a clean install to Ubuntu Mate LTS in mid May Ubuntu Mate looks more like the old version that I was running

Dave

---

