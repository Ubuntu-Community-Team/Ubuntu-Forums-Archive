---
title: "login screen bad resolution"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by freebeer on 2008-04-30
Hi folks!

I've been having an issue with 8.04's login screen.  Either the resolution's off or the assumed refresh rate.  Not sure, exactly.  Once I log in, the screen resolution and refresh rate resets just fine (I was able to set them previously).  It's just the login screen (splash screen?) that's all fuzzy (for lack of a better description).

---

### Post by herbster on 2008-04-30
You mean the GDM? Where you enter your username/password? Like this:

[img]http://www.gnome.org/projects/gdm/images/2-GDM-Theme-Default-Style.png[/img]

---

### Post by akiratheoni on 2008-04-30
> **freebeer said:**
> Hi folks!

I've been having an issue with 8.04's login screen.  Either the resolution's off or the assumed refresh rate.  Not sure, exactly.  Once I log in, the screen resolution and refresh rate resets just fine (I was able to set them previously).  It's just the login screen (splash screen?) that's all fuzzy (for lack of a better description).

Same here! My native screen resolution is 1680x1050 but my login screen defaults to something like 1280x768. It's not a big deal but back in Feisty it was fine (it's been that way since Gutsy AND Hardy). I just wanna fix it, lol. The login screen kinda annoys me.

We need helpppp! :)

---

### Post by freebeer on 2008-04-30
Yeah.  GDM, eh?  Ok... I wasn't sure what to refer to it as.  I need to brush up on my components knowledge.  :lol:  If I knew that, then I would have been able to perform a more exact search as I'm sure this question has come up before.

---

### Post by Fire_Chief on 2008-04-30
What video card are you using (ATI, Nvidia, other)? That will help pinpoint the fix method.

Cheers!

---

### Post by freebeer on 2008-04-30
> **Fire_Chief said:**
> What video card are you using (ATI, Nvidia, other)? That will help pinpoint the fix method.


I'm pretty sure it's an old (and I mean old) Nvidia card.  (16 megs, I think)  It's on an old machine, too. (Celeron 733) I don't have access to the machine right now to verify.  I'm running the default Gnome for now, I may go with a lighter GUI later as the speed is quite sluggish.

BTW, this machine is for my 74 year old father who's finally given in to the idea of having a computer, so I want to make this as simple for him as possible.

---

### Post by Fire_Chief on 2008-05-01
Are you using the restricted driver for the Nvidia card? (Check in Administration -> Hardware Drivers)

This issue sounds the same as one I've seen in another thread. See here [http://ubuntuforums.org/showthread.php?t=763107]("http://ubuntuforums.org/showthread.php?t=763107")

The fix there worked for me and several others. Not completely sure about your case since the card is so old but it's worth a shot.

Cheers!

---

### Post by freebeer on 2008-05-01
> **Fire_Chief said:**
> Are you using the restricted driver for the Nvidia card? 


Yep, the restricted driver is loaded and working (on this machine I'll take any extra acceleration I can get!) ;)

Thanks for the link!  I'll have a look through that and see if it helps.

---

### Post by bobbocanfly on 2008-05-03
If your still having problems there might be something wrong with the 'Virtual' directive in your X Windows settings.

Can you post the output of:

```
cat /etc/X11/xorg.conf
```

---

### Post by Helios38 on 2008-05-03
i am also having this problem with an intel chip.

---

### Post by drawsmcgraw on 2009-04-29
After reading through <a href="https://wiki.ubuntu.com/X/Config/Resolution">this X document</a> I learned about xrandr.

Long story short (and I know this is a bit late for you...), you need the following command in one of your init scripts in /etc/gdm. I chose /etc/gdm/Init/Default:

```
xrandr --output LVDS --mode 1024x768 --rate 75
```

and modify that as you need. I've been trying to fix the refresh rate on my login screen for *months* now and just now got it taken care of.

---

