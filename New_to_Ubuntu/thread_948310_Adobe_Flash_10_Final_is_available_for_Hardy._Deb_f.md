---
title: "Adobe Flash 10 Final is available for Hardy. Deb file too."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by philinux on 2008-10-15
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Full screen flash very smooth. When installed it appears as adobe-flashplugin in synaptic.

---

### Post by SunnyRabbiera on 2008-10-15
its about time they offered a .deb installer.

---

### Post by night-wing on 2008-10-15
Link refers to a page, which is not available, when you choose .deb and click "agree and install".

---

### Post by philinux on 2008-10-15
It takes you to a download dialogue box.
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by night-wing on 2008-10-15
This worked. Thank you!

---

### Post by iKonaK on 2008-10-15
i can confirm too, that works smooth...
thanks 4 the "heads-up"....

---

### Post by benvantende on 2008-10-15
duh. 32bit only.

is creating a 64bit version that hard :-(

gRTz

ben

:confused:

---

### Post by cryptecks on 2008-10-15
Yeah is there any way to repackage this to 64-bit?

---

### Post by crjackson on 2008-10-15
This is great news. I hope it comes through as an update also.

---

### Post by kansasnoob on 2008-10-15
Awesome! I've been using the Flash 10 RC for quite a while with no problems!

I think I'll try the apt install - just for fun!

---

### Post by sleepingdragon on 2008-10-15
Can confirm v10 is smooth, even at fullscreen. Whatever they did, it's a decent upgrade.

---

### Post by kerry_s on 2008-10-15
i had to add:
```
XLIB_SKIP_ARGB_VISUALS=1   
export XLIB_SKIP_ARGB_VISUALS=1

```

to my rc file to get it to be smooth, i'm running at 16 colors and this laptops only 450mhz 256mb ram, guess i'm lucky it works at all. :lolflag:
no more choppiness or crashes(when closing a running vid).

---

### Post by SeanBlader on 2008-10-15
Looking for a AMD64 version here myself. The lack of it is a little disappointing.

---

### Post by simtaalo on 2008-10-15
> **seanblader said:**
> looking for a amd64 version here myself. The lack of it is a little disappointing.

+1

---

### Post by happyisland on 2008-10-15
Flash 10 definitely seems to be working a lot smoother. Now we'll see if it can make tonight's presidential debate more interesting than the last one!

---

### Post by jejones3141 on 2008-10-15
> **SeanBlader said:**
> Looking for a AMD64 version here myself. The lack of it is a little disappointing.
In the immortal words of AOLers, "Me too." Seriously, back in the days when exactly one person at Adobe started working on Flash for Linux, there was a fair amount of posting on Adobe blogs about how hard it would supposedly be to write a 64-bit Flash. I suppose they must have it in x86 assembly language tuned to within an inch of its life, written by Mel, the "real programmer" of the story in the Hacker's DIctionary, if it's that difficult.

I just wish that I didn't have to restart Firefox every so often on my 64-bit system when all the Flash embeds turn into featureless gray boxes.

---

### Post by Melk79 on 2008-10-16
For those with 64 bit, when trying to fix full screen Flash for The Daily Show episodes, I ran this [script]("http://ubuntuforums.org/showthread.php?t=891458&page=3") by rashly (post #25).  It's Flash 10 RC, but so far it works for me on YouTube, Comedy Central, etc.  Not sure about the final version.

---

### Post by mtrompeta on 2008-10-16
[Alejandro]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/") wrote a script that will let you dl the latest version of Flash.  Just go to his site and it has instructions on how to do so.

For the lazy:  wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh

To see the code: [http://queleimporta.com/downloads/flash10_en.sh]("http://queleimporta.com/downloads/flash10_en.sh")

FYI, I'm running AMD64 w/ Firefox 3 and it works good.

---

### Post by jerome1232 on 2008-10-16
> **SeanBlader said:**
> Looking for a AMD64 version here myself. The lack of it is a little disappointing.

+22, at least they have a debian package though. It's a step forward.

---

### Post by abdeali on 2008-10-16
seems as if they're biased against 64-bit processors........
processorists?

---

### Post by OutOfReach on 2008-10-16
Nice, works smoothly here.

---

### Post by r3bol on 2008-10-16
SPM says I have Flash version 10, but if I right click on flash content in FF, I'm still using 9. In the FF tools tab there is no option to upgade the plugins. 
How did you guys get it working?
Thanks.

---

### Post by philinux on 2008-10-16
If you are using 32bit then download the deb file, post #4. Remove flashplugin-nonfree, then install the deb file. If it turns up in the repos later I'll do the reverse.

---

### Post by r3bol on 2008-10-16
thanks, that did the job. I noticed version 9 is still there, but I havce disabled it in the plugins. Version 9 doesn't appear in SPM at all. Maybe its something to do with automatix when I installed it in the previous upgrade.

---

### Post by Bloch on 2008-10-16
Will it be included in the normal Ubuntu updates for Hardy?

I don't mind waiting a few days.

---

### Post by philinux on 2008-10-16
Most likely will be backported as an update.
If you have the backports updates on.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

