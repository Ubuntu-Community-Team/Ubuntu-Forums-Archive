---
title: "[SOLVED] Error activating XKB configuration"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by styphon on 2008-05-23
I notice the GBP symbol (SHIFT+3) wasn't working on my keyboard, just producing a 3 instead, so I tried changing the keyboard to the HP one (I have an HP laptop) and now every time I login I get this:
```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

**The result of xprop -root | grep XKB**
```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "", ""
```

**The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**
```
 layouts = []
 model = hpzt11xx
 overrideSettings = true
 options = []
```

I've tried switching to several different keyboard options but always get the same result. Please help.

---

### Post by styphon on 2008-05-24
*bump* Any help please?

---

### Post by loveunit on 2008-05-27
well - I've spent a few days searching and trying things - and I can't say that I've fixed or really improved the problem.

I'm for sure a nu-bee to linux - using Ubuntu 8.04 - dual booting with windows - I've got a pretty standard set-up, but want to be able to use spanish and english keyboard layouts or at least have a way to produce spanish accents - I've got a number of issues, which I don't seem to be able to pick a way out from.

I've tried to add spanish as a second language via the keyboard preferences option - but get the fault:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090...

and so forth - I've read a lot about this and the need to edit the xorg.conf file - which I've tried, but no luck..

I added the keyboard indicator to a panel - right clicking and asking 'show current layout' produces an empty screen.

I have what I guess is a related problem ( and possible cause? ) which is that I develop php and deal with many European languages and their specific (foreign) accents and characters - most of the code I use was developed on windows XP - before my switch to Ubuntu - however once opened and edited - this code becomes muddled after I upload to my server.

to give a bit more info - I have tried a number of code editors - screem, kate, bluefish.. and others - some open the scripts and display the foreign characters, others replace them with a diamond with a question mark. I did try manually adding new language packs via the synaptic manager to try and correct this - however I deal with more languages all the time - so was not sure if this is the way to go - also I do remember making some changes or additions to xserver while I did this - perhaps a start to the further problems...?

as a couple of side notes - I can upload the problem files via FTP from a drive I share with my XP install and they are fine - the issues with lost and muddled character encoding comes when I open and edit the files on Ubuntu.

here is the output of the requested:

xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "en", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "en", "", ""

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
layouts = [en]
model = 
options = [grp	grp:alts_toggle,grp	grp:lwin_switch]
overrideSettings = true

sorry if this is a bit or a ramble - but I'm at the end of my wits and to my shame about ready to boot up windows and go back to my comfort zone...

thanks in advance and for all the great work on this OS.

---

