---
title: "Installing 8.1 Now?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by oxsyn on 2008-10-28
The 8.1 rc is available for DL now.  If I go ahead and install that now, am I going to have to reinstall on friday, when the official is released?  

Should I just wait?

---

### Post by mkvnmtr on 2008-10-28
I don't think you will have to reinstall but it is really just you choice. I believe I will wait and then try an upgrade about 10 o'clock at night in case speeds are slow.

---

### Post by oilchangeguy on 2008-10-28
> **F4RR4R said:**
> The 8.1 rc is available for DL now.  If I go ahead and install that now, am I going to have to reinstall on friday, when the official is released?  

Should I just wait?

no you won't have to reinstall. but if it were me, i'd just wait until the final is ready.

---

### Post by drakeman007 on 2008-10-28
Hhehe, hey, wait a little more, just 1 day and half more! what is that? heehe...
REgards!

---

### Post by oxsyn on 2008-10-28
But I want it now ...

---

### Post by zvacet on 2008-10-28
If you want it now install it.Updates will lead you to the final release,so you don´t have to reinstall.Just keep your system up-to-date.

---

### Post by oxsyn on 2008-10-28
So, the only difference between the version I would download today and the version I will download on thursday are two days worth of updates?

---

### Post by gjoellee on 2008-10-28
I would actually recommend to do a clean install of Intrepid instead for upgrading. Many people do get bugs when the are upgrading with the update manager...

---

### Post by jerome1232 on 2008-10-28
> **F4RR4R said:**
> So, the only difference between the version I would download today and the version I will download on thursday are two days worth of updates?

In a nutshell yes. The RC is what get's released unless any major bugs are found.

---

### Post by aktiwers on 2008-10-28
> **F4RR4R said:**
> So, the only difference between the version I would download today and the version I will download on thursday are two days worth of updates?

Yeah..

---

### Post by oxsyn on 2008-10-28
> **jerome1232 said:**
> In a nutshell yes. The RC is what get's released unless any major bugs are found.

Thanks dude, I'm gonna install it now then (a clean install alongside vista)!

---

### Post by ad_267 on 2008-10-28
Yeah install it now! 8.10 Intrepid is running great.

---

### Post by oxsyn on 2008-10-28
Crap, will the i386 version recognize 4GB of ram, or do i need to go with the 64 bit again?

---

### Post by Victormd on 2008-10-28
pretty much, yeah!
I've been using the Beta version, it's really sweet!

---

### Post by ad_267 on 2008-10-28
If you have 64 bit then give the 64 bit version a go. I'm not using it myself (only have 32 bit) but I hear it keeps improving.

---

### Post by Victormd on 2008-10-28
> **F4RR4R said:**
> Crap, will the i386 version recognize 4GB of ram, or do i need to go with the 64 bit again?

You should be Ok with the i386. There was a bug using HIMEM4G in the alpha version (a work around is available) and that should be have been fixed... otherwise, just use the workaround for it [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269").

---

### Post by jerome1232 on 2008-10-28
32 bit will only see ~3.4GB of the ram, I'd also say go for 64-bit I've ran it since 7.10 and don't have any 64-bit specific problems.

---

### Post by Shadowmeph on 2008-10-28
I have this running on VM and for some reason I after I installed the fglrx drivers I get this
```
fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  145 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```
the reason I am running this on VM ( in case anyone wants to know) is because of a major problem that I had with Hardy, after I upped my Ram to 4 gb I couldn't have the FGLRX drivers running with the 4 gb ram, it was either I run  just 2 gbs ram or no fglrx. The funny thing is, I don't have any problems on any other Linux distros Just Ubuntu has problems, this is vary unfortunate because I Like Ubuntu the most out of every Linux distro that I have tried.

---

### Post by jerome1232 on 2008-10-28
Well a VM doesn't have 3d accelerated graphics so graphics drivers won't do anything there.

---

### Post by oxsyn on 2008-10-28
> **jerome1232 said:**
> 32 bit will only see ~3.4GB of the ram, I'd also say go for 64-bit I've ran it since 7.10 and don't have any 64-bit specific problems.

Awesome, that's what I was thinking.  64bit it is.  Also, I hate how they label the releases amd64.  Why do they do that?  I have a core 2 duo ...

---

### Post by jerome1232 on 2008-10-28
Because it's amd64 technology, intel copied it :)

---

### Post by oxsyn on 2008-10-28
> **jerome1232 said:**
> Because it's amd64 technology, intel copied it :)

lol ... is that true?  If it is, then I assume the naming scheme is Ubuntu's stab at Intel :)

---

### Post by hermes0710 on 2008-10-28
I suggest you wait until the release date. Bugs are being fixed till the last moment... Patience...

---

### Post by jerome1232 on 2008-10-28
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Intel had it's own 64 bit architecture at first but ditched it for amd64's and  renamed it to Intel 64.

---

### Post by billgoldberg on 2008-10-28
> **F4RR4R said:**
> So, the only difference between the version I would download today and the version I will download on thursday are two days worth of updates?

yes

--

If you decide to install, do a clean install from cd, don't upgrade.

---

### Post by louieb on 2008-10-28
I've done everything from upgrading  when the release was is alpha stage to skipping a release and doing a fresh install of the next.

Upgrade early and you'll wind up downloading more updates, the same package(s) may get updated several times before the final release. The good news is If you keep up with the updates you''ll be one of the 1st to have the final version. And you'll avoid the traffic jam of a bunch of people trying to upgrade on release day.

I'm going to upgrade my laptop a week or two after the release. And unless intrepid  has some wow factor I'm keeping Hardy on my desktop.

---

### Post by thomascj on 2008-10-28
i've already upgraded... and unless I missed something, my ati drivers dont work anymore.  I'm constantly being warned about it starting in "low graphics mode".. no fglrx, no compiz.. but other than that it seems fine.

it appears the drivers are all installed in synaptic, but I get the following error on an `fglrxinfo'

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

anyone have any suggestions?

---

### Post by ad_267 on 2008-10-28
What does it say under System - Administration - Hardware Drivers?

---

### Post by thomascj on 2008-10-28
says there are no proprietary drivers and use -- and offers none to enable.

any idea what the correct package for the driver is?  or do i need to grab it from ati's website?

---

### Post by tuxxy on 2008-10-28
Ibex is really polished already, found only 1 or 2 major bugs so far but one was an effect of upgrading, only 1 day to go now too :guitar:

---

### Post by ad_267 on 2008-10-28
You could try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to reconfigure your X server.

---

### Post by oxsyn on 2008-10-29
Mother of god.  

Shrunk my vista partition (took 3 hours).  

Installed ubuntu (took another hour).  

Booted into ubuntu for the first time, audio driver crashed, then gtk-jockey.  

Tried to activate the nvidia driver, wouldn't take.  

Rebooted.  

Computer responded with angry beeps for about 30 seconds until I unplugged it.

Booted back into Ubuntu.

Black screen, then nothing for about 5 minutes.

Hard shutdown.  Started back up.  Booted back into Ubuntu.  Now its loading?

---

