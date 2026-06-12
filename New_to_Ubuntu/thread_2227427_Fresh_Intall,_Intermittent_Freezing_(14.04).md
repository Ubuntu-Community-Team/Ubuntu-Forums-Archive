---
title: "Fresh Intall, Intermittent Freezing? (14.04)"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by juin-roet on 2014-06-02
_**Brief:**_
Finally cobbled together the willpower to buy a proper PC, hadn't used Ubuntu in a long time so I thought I'd try out the latest LTS (I've only ever dabbled though so consider me largely a beginner/casual user). However I haven't even tried anything weird like running terminal commands I don't understand or unnecessarily encrypting the home folder, but the whole system seems to freeze randomly! I need to find out what the problem is/if the problem is software related before my window of return/refund on my components runs out, or if I'm going to have to buy Windows 8.1 to test/enjoy my hardware....

_**Specs:**_
VGA - Radeon R7 265 [Gallium 0.4 on AMD PITCAIRN]  (using X.org driver at the moment)
RAM - Corsair Vengeance DDR3 2x4 8 GB (memtest'd OK)
MOBO - ASUS M5 A99FX PRO R2.0 (Factory bios I think, haven't messed with it if that matters)
CPU - AMD FX(tm)-8350 Eight-Core Processor × 8 
HD - 2 TB Seagate Barracuda
PSU - Corsair CX750M (750W)
OS/Distro - Ubuntu 14.04 LTS (Up to date, checked again just earlier today)

_**Problem:**_
_At intermittent intervals Ubuntu 14.04 completely freezes_; does not thaw with time. No luck with Ctrl+Alt+Tab+F2/Ctrl+Alt+Tab+F7 (something I read somewhere for getting out of program freezes).

_**Theories/Additional Information:**_
Changing the VGA drivers from the proprietary flglrx(?) to the x.org/native one seems to make the freezing happen less frequently, suspect it's a problem related to the card but couldn't find anything solid about it anywhere.  Additionally it only seems to tend to have trouble in a spectrum of lower-mid resource demand (TF2/Europa Universalis(?) IV on Steam tends to run fine once launched (a little sluggish to start, but with nice frame-rates :o), but occasionally browsing a photo-gallery or having 2-3 tabs of say Youtube open in Firefox or trying to launch the system monitor does the trick of freezing everything) though this is not always the case.  

+Caught something about GNOME running better and installed Flashback, running the system in GNOME Compiz (?) seems to have also helped.

---

### Post by LastDino on 2014-06-02
Does problem persist with nomodest boot option as well?

You should probably try to look at logs in /var/log to and post if found anything specific.

---

### Post by juin-roet on 2014-06-02
> **LastDino said:**
> Does problem persist with nomodest boot option as well? [...] 
I've only read up on this feature just now, followed [the instructions here]("http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782#38782"). So we'll see if that helps.

> **LastDino said:**
> 
[...]You should probably try to look at logs in /var/log to and post if found anything specific.


Found the directory, but I am uncertain what I am looking for exactly.

---

### Post by NoBugs! on 2014-06-02
You could bring up system log from dash search, see if it prints something out just before "freeze" each time.

---

### Post by rahul4557 on 2014-06-02
are you using a 64bit Ubuntu?
I have AMD APU with R7 everything is working pretty fine.

x86 gave me problems on my laptop with Intel Core2Duo + Nvidia 9200M, later installed x64 now everything is working fine.

Also while installing additional drivers for R7 install only (proprietary,tested)

---

### Post by juin-roet on 2014-06-02
No luck with 'nomodeset'

> **NoBugs! said:**
> You could bring up system log from dash search, see if it prints something out just before "freeze" each time.
Been looking it over, nothing seems to be out of the ordinary (that I can detect).  I can post it all if you think it'll help though.

> **rahul4557 said:**
> are you using a 64bit Ubuntu?
I have AMD APU with R7 everything is working pretty fine. x86 gave me problems on my laptop with Intel Core2Duo + Nvidia 9200M, later installed x64 now everything is working fine.

Also while installing additional drivers for R7 install only (proprietary,tested)

I went with-32 bit because I thought it'd have less issues, but I'll look into upgrading to 64-bit and see how that goes.

---

### Post by juin-roet on 2014-06-08
UPDATE:
Reinstalled with 64 bit variant, things running better.
_**Still freezes**_, though less frequently.
Proprietary video card drivers seem to freeze console more frequently.

Also, proprietary drivers do this weird thing where the desktop doesn't full screen; there's about a half inch (~1.3 CM I guess) unmanifested boarder. The purple Ubuntu screen and everything before Ubuntu loads/the drivers initialize don't have this problem.

---

### Post by veddox on 2014-06-09
A number of people have reported this random freezing on 14.04, I've had it myself too. It's slowly getting better, it seems like the developers are fixing the bugs. Hopefully they'll have all of them out by the July/August, when 14.04.1 comes out. Until then, if you want/need a really stable system, perhaps you should consider downgrading to 12.04 (download [here]("http://releases.ubuntu.com/precise/")).

---

### Post by nulty on 2014-06-13
I've got the same issue. It freezes every 20 - 40 minutes maybe. I Just use the Ctrl-Alt-F6/Ctrl-Alt-F7 key strokes to switch to another terminal and back again and its works again.


_**Specs:**_
[COLOR=#000000]VGA - Nvidia GeForce GTX 765M (driver => nvidia-331-updates version 331.38)
[/COLOR][COLOR=#000000]RAM - Kingston DDR3 1x8GB[/COLOR]
[COLOR=#000000]MOBO - ASUS M5 A99FX PRO R2.0 (Factory bios I think, haven't messed with it if that matters)[/COLOR]
[COLOR=#000000]CPU - Intel i7-4710MQ[/COLOR]
[COLOR=#000000]HD - Samsung 840 EVO 250GB[/COLOR]
[COLOR=#000000]OS/Distro - Ubuntu 14.04 LTS

So am i to understand its probably nothing to do with the hardware configuration? And theres nothing that the end user can do until the developers find a solution?

Regards[/COLOR]

---

### Post by nulty on 2014-06-13
Ignore: Repost

---

