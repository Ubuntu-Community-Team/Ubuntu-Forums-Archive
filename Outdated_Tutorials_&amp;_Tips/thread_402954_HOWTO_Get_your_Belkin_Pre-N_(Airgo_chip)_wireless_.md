---
title: "HOWTO: Get your Belkin Pre-N (Airgo chip) wireless card working with Feisty"
date: 2007-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by wyth on 2007-04-06
First the details: This works on 32-bit machines, and is for getting your Belkin Pre-N card to work with ndiswrapper.  The Pre-N cards (and possibly others in the N line) aren't being picked up automatically.  They can work with the current ndiswrapper that's available in the repositories.

Thanks to Danni, who first showed [how to get your Belkin Pre-N working on Dapper]("http://ubuntuforums.org/showthread.php?t=262465").

I won't be supporting this actively, but will check in on occasion.  It should work; I have some middle-aged hardware, and it's working for me without a hitch.  I do suggest using "aptitude install" as opposed to apt-get or synaptic, just to keep things tidy.

So: here's how to get the standard Feisty ndiswrapper working:

First, if you have a previous version, remove it.  If you used aptitude, no problem.  if you compiled ndiswrapper from sourceforge, you may want to remove everything, just to be safe.  [See the instructions here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall").  If you installed via apt-get or synaptic, the previous instructions will show you where to check for leftover files. 

Second, at the command line, do the following:

```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```


[Grab the drivers if you don't have them]("http://kbserver.netgear.com/products/WPNT511.asp").  Then install:
```
sudo ndiswrapper -i NETANI.INF
```

Check to see if it installed:
```
ndiswrapper -l
```

You should see something like:
```
netani : driver installed
        device (17CB:0001) present
```

Load up the module:
```
sudo depmod -a
```

NOW: To get modprobe to work, need to use module-assistant:
```
sudo module-assistant prepare
sudo module-assistant auto-install ndiswrapper
sudo modprobe ndiswrapper 
```

Make sure you have ndiswrapper in /etc/modules

Reboot and enjoy your wireless.


Note: I tried the latest version on sourceforge, to no avail.  That was 1.41.  The Feisty one is 1.38, which works perfectly well.  In fact, it seems to be working better on Feisty than it did on Edgy (when I compiled it).

---

### Post by TwoBit on 2007-04-13
I don't understand your "Grab the drivers if you don't have them" link. The link takes you to a page for a Netgear wireless adapter but the page has nothing to do with drivers.

---

### Post by TwoBit on 2007-04-13
Also, this command:
[INDENT]sudo module-assistant auto-install ndiswrapper[/INDENT]

results in trying to compile something and gives the following error:
[INDENT]dh_clean: cannot read debian/control: No such file or directory[/INDENT]

and after that I can't tell if the command aborted or what, as I was merely returned to the command prompt.

---

### Post by wyth on 2007-04-14
TwoBit: To get the card to work, you need the right drivers.  The Belkin Pre-N drivers won't work with ndiswrapper.  But the Netgear drivers *do* work.  So you need to download those drivers and unzip them.  The NETANI.INF file is what you want; I believe it's in the  Utility/Drivers folder.

I'm not sure about the dh_clean problem; here's a few things to try:

```
sudo modprobe ndiswrapper
```and/or, check

```
tail /var/log/messages
```for any errors.

This guide was built off [an original one for Dapper]("http://ubuntuforums.org/showthread.php?t=262465") that required compiling ndiswrapper from source.  The current ndiswrapper in the Feisty repositories is up to date and works.

---

### Post by jnorris235 on 2007-06-15
(Note: I put this on the wrong thread so am reposting here!)
I spent so many hours trying to get ndiswrapper to work that I just gave up with Dapper.
Thinking Feisty might be better I tried again.

Thank you (and I DO mean that!) to this guy for taking the time to try to help.
But...
Yet again - failure.

I went to get that package as he suggested. Unzipped it.
In console drilled to the Driver folder and typed
sudo ndiswrapper -i netani.inf
and I get
driver netani already installed

Then
ndiswrapper -l
and I get
invalid driver

I was doing this online of course but then wondered if you had to have the actual hardware in place before installing the drivers.
So went off line, switched the network card to the Belkin and back to Terminal - same results.

I.m trying to use a Belkin Wireless Pre-N Notebook Network Card in the little frame that holds it, in my Desktop. Part FSD8010
Windows used to note that there was a faulty hardware device and you could Add Drivers. I haven't found a similar place in Ubuntu....if you dont mind me talking dirty for a minute!

Any ideas - desperately need the preN to drive through stone walls!

---

### Post by wyth on 2007-06-15
I responded on the other thread.

---

### Post by jcbwalsh on 2007-06-30
Whenever I run the step "sudo modprobe ndiswrapper" the machine locks up and has to be hard rebooted. Any suggestions?

---

### Post by wyth on 2007-07-01
Try re-installing module-assistant and module-init-tools.   I'm not sure why it would lock your system, but if it's a problem with modprobe, maybe one or both of those packages are broken.

---

### Post by justinmiller87 on 2007-08-12
> **TwoBit said:**
> I don't understand your "Grab the drivers if you don't have them" link. The link takes you to a page for a Netgear wireless adapter but the page has nothing to do with drivers.

Try this link:

[http://kbserver.netgear.com/products/WPN511.asp](http://kbserver.netgear.com/products/WPN511.asp)

---

### Post by wesb on 2007-10-15
n/m

---

### Post by S4T4N4S on 2007-12-12
Hello,

I've the same problem and have solved with the instructions in this site:
[http://welcometoubuntu.blogspot.com/...i-enabled.html](http://welcometoubuntu.blogspot.com/...i-enabled.html)

... but with the Belkin original drivers found in the CD.

I've uploaded the files here:
[http://77.91.202.10/~alpoimco/Satana...n_pre-n.tar.gz](http://77.91.202.10/~alpoimco/Satana...n_pre-n.tar.gz)

If you follow the instructions change this instruction:
sudo ndiswrapper -i tmimo3P.inf

to ...

sudo ndiswrapper -i NetAni.inf

Hope you solve your problem too...

Sat

---

### Post by justinmiller87 on 2008-02-24
Just to let you know, I updated the link above me (also in my sig) to reflect the information. Try that out if you are having issues. The guide works for Edgy through Gutsy and has online and offline instructions.

[HOWTO: Get Airgo-Based WiFi Enabled Using ndiswrapper](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

---

