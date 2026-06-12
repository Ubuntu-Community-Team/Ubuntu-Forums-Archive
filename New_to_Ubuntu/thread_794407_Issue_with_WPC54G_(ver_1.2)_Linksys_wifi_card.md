---
title: "Issue with WPC54G (ver 1.2) Linksys wifi card"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by mavimao on 2008-05-14
Hello, just gave new life to a laptop by installing xubuntu, and I can't get the pci wifi card to work. The wiki says the following:

"Get recognized in the setup process, but unable to use it. After setup completes, the card is shown in the network interfaces (as eth0, all hardware details are shown too), but the system is unable to activate it. Updating the firmwares (link broken) fixes the problem. To do this when Ubuntu starts, open the restricted drivers management and enable bcm43xx"

It pretty much sums up my problem. The computer recognizes it, but can't find any wireless networks. I can't find the restricted drivers in xubuntu. It's using a Broadcom (BCM4306 rev3) chip if that's any help.

---

### Post by shifty_powers on 2008-05-14
have you tried using ndiswrapper and the windows driver?

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

(should be in synaptic as well iirc)

---

### Post by mavimao on 2008-05-14
The laptop in question doesn't have an ethernet. Just a modem. So I went and downloaded the ndiswrapper from my mac, and with a pen drive put the file on my Xubuntu desktop along with the windows driver I found. Now what? How can I install ndiswrapper and install the driver?

Sorry to be such a noob.

---

### Post by shifty_powers on 2008-05-14
go [http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk)

it will give you a link to download ndisgtk, the gui for ndiswrapper.

don't forget to follow the links for the dependencies.

they will all download as .deb files, which is much easier. just double click on them.

install the dependencides first ;)

if you get stuck, just holler ;)

oh and if you are using 32-bit ubuntu, then grab the i386 versions ;)

---

### Post by shifty_powers on 2008-05-14
btw, what you downloaded were the source files, which invloves going on the command line and compiling them. i'm assuming that wasn't waht you wanted to do.

.deb files are package files that are similar to .exe installer files on windows ;)

---

### Post by mavimao on 2008-05-14
what are dependencies?

---

### Post by mavimao on 2008-05-14
> **shifty_powers said:**
> btw, what you downloaded were the source files, which invloves going on the command line and compiling them. i'm assuming that wasn't waht you wanted to do.

.deb files are package files that are similar to .exe installer files on windows ;)

Yeah! Indeed, I was a little confused. My experience with computers is pretty limited to Macs (drag and drop installation) and PCs. Linux is a brand new thing to me and I'm trying to understand its quirks and such.

---

### Post by shifty_powers on 2008-05-14
heh, when you install a program, it may need libraries and various other types of program to run properly, bit like dll files in windows and such like. look up good old dll-hell on wikipedia ;)

basically ndisgtk will need those programs installed for it to run. so download and install those .deb files first and then install ndisgtk.

the beauty of synaptic and apt-get on the command line when you have a working internet connection, is that they will work out the dependencies and install them all for you. Sooooo much easier ;)

---

### Post by shifty_powers on 2008-05-14
> **mavimao said:**
> Yeah! Indeed, I was a little confused. My experience with computers is pretty limited to Macs (drag and drop installation) and PCs. Linux is a brand new thing to me and I'm trying to understand its quirks and such.

heh well when you're internet connection is working, then it is all so much easier. bit chicken and egg kind of thing right now though, eh;)

linux just has a slightly different way of doing things though. however it is really cool. i LOVE synaptic and apt-get. i love the fact that if i need a program to do something, i just look in the vast database in synaptic and it will download and install it for me automatically. how cool is that ;)

---

### Post by nicedude on 2008-05-14
This wireless adapter is supported by bcm43xx-fwcutter package.

Here is a link to how to get it to work in Ubuntu Hardy but this should also work for Xubuntu as well since its just a deference of Desktop managers.

[http://ubuntuforums.org/showthread.php?t=735444](http://ubuntuforums.org/showthread.php?t=735444)

If you can't figure it out feel free to PM me ( just click my name and send PM ) and I will help advise you what to do.

Ndiswrapper should be someones last ditch choice if nothing else works since it uses windows drivers and never supports cool modes for your wifi ( like monitor mode - my favorite ).

Glad you found a new life for your old laptop.

---

### Post by shifty_powers on 2008-05-14
meh, i've found ndiswrapper to be a lifesaver in the past and found it very easy to use. as for fancyt modes, personally as long as it connects me to the internet, couldn't care less. but meh, thats just me ;)

---

### Post by mavimao on 2008-05-14
I am writing you to all from my Xubuntu laptop!

It took a while to find the right dependencies but I got them, installed the program and the driver, restarted the computer and the network aplet saw my network right away! Thank you all so much! You've all been really kind and helpful. 

But one quick question: I was transferring documents from my pen drive but I couldn't find a progress bar or anything to tell me if the file had been fully transferred. Is this normal?

---

### Post by shifty_powers on 2008-05-14
so are you using ndiswrapper and the windows driver?

if so, feel free to give me thanks ;) just click on the medal symbol underneath one of my posts ;)

heh if not, well i'm glad to help anyways :P

---

### Post by shifty_powers on 2008-05-14
hehe, cheers, little hobby to collect  thanks ;)

looks good on your posts as well ;)

---

