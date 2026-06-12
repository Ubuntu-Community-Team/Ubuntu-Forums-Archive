---
title: "gnome-shell screensaver bug needs me toos"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-10-06
here is the ( or one of the ) bug for the gnome-shell screensaver blanking very quickly , it needs some me toos to get some attention .
bug# 869401

---

### Post by Quackers on 2011-10-06
Done.
Would this same bug cause the screen to black out when watching a movie in full screen mode, if the mouse isn't moved?

---

### Post by ronacc on 2011-10-06
I don't know about that , for me it blanks about 5 seconds after I stop moving the mouse no mater what I'm doing .

---

### Post by Quackers on 2011-10-06
oops, maybe I shouldn't have me too'd then :-)  My screen doesn't black out until about 15 mins have gone by.

---

### Post by ronacc on 2011-10-06
I think it's still part of the same problem , they took away the way to configure it .

---

### Post by sgage on 2011-10-06
> **ronacc said:**
> here is the ( or one of the ) bug for the gnome-shell screensaver blanking very quickly , it needs some me toos to get some attention .
bug# 869401

Hmmm... I'm not experiencing this.

---

### Post by ronacc on 2011-10-06
I'm on gnome-shell 64 bit , I don't think it affects unity .

---

### Post by paul_in_london on 2011-10-06
Did you guys try these things?

In **xorg.conf**:

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection
```

and in **dconf-editor** **un**checking:

```
org --> gnome --> desktop --> screensaver: **idle-activation-enabled**
```.

---

### Post by ronacc on 2011-10-06
thanks the dconf-editor thing got it for me .

---

### Post by paul_in_london on 2011-10-06
> **ronacc said:**
> thanks the dconf-editor thing got it for me .

That's good to know :)

---

### Post by Quackers on 2011-10-06
I've tried gconf, dconf and the server flag section. gconf and dconf seem to work but don't and the server flag section entry stops my system booting.

---

### Post by paul_in_london on 2011-10-06
> **Quackers said:**
> I've tried gconf, dconf and the server flag section. gconf and dconf seem to work but don't and the server flag section entry stops my system booting.

Hmm. Sorry to hear that mate. Is this using a laptop? I only have a desktop. When you say gconf/dconf seem to work, do you mean only until after a reboot or something?

---

### Post by artemeas on 2011-10-06
```
setterm -blank 0 -powerdown 0 && xset -dpms && xset s off

```


you can create a file e.g. disable_display_off.sh in /usr/bin/ with 
```
#!/bin/bash
setterm -blank 0 -powerdown 0 && xset -dpms && xset s off

```

then chmod +x it and add it to startup by adding an entry in ```
gnome-session-properties
```

you are welcome!

p.s. when it doesn't work automatically, just execute `disable_display_off.sh` after a session login

---

### Post by sammiev on 2011-10-07
Not sure why I read post as of such. Can it be related to a graphic card or so. I use GS and have a few laptops on it as well and all are set to to stay alive for 1 hour. I'm using 11.10 and haven't saw this bug yet. Watching movies is a must here. :)

Here are the setting I use.

---

### Post by Quackers on 2011-10-07
> **paul_in_london said:**
> Hmm. Sorry to hear that mate. Is this using a laptop? I only have a desktop. When you say gconf/dconf seem to work, do you mean only until after a reboot or something?

Yes it's a Sony Vaio AR51SU
gconf and dconf set properly but don't change anything. The delay is currently set to "never" but it blacks out after 15 minutes.


This installation is an upgraded Natty installation and I have the ricotz ppa enabled. It could be that there are some config files that are not fully in sync, which could be a possible cause.
It is only this week that suspend started to work, but only when chosen from the user menu. It doesn't work when closing the laptop lid, though it is set to do so.

---

### Post by fooman on 2011-10-09
> **Quackers said:**
> 
This installation is an upgraded Natty installation and I have the ricotz ppa enabled. It could be that there are some config files that are not fully in sync, which could be a possible cause.


i've been using 11.10 on and off from one of my spare drives for awhile now and so far things have come along pretty smoothly.  i did however notice some weird glitches while using compiz (cube and wobbly windows mostly).  i thought possible causes could be some config conflicts from prior installs on this partition, etc.,  i remembered ubuntu-tweak having some options for cleaning up unnecessary/redundant packages, kernels, cache and config files.  so i installed it and ran those options (under package cleaner in the program) and i do think it may have helped as things seem to be running noticeably better (though that could be attributed to recent updates as well).

just thought i'd mention that as an option you might want to try to tidy things up a bit. :)

---

### Post by dino99 on 2011-10-09
There is no "screensaver" for Oneiric, its deprecated, and will not.
If you want to clean your system ,bleachbit is a must have (to use with care)

---

