---
title: "Odd errors when using apt-get"
date: 2005-03-11
forum: Repositories &amp; Backports
---

### Post by terasurfer on 2005-03-11
It seems like nearly every package i install with apt-get (and likewise synaptic), i see one if not several assertion errors similar to this: 

** (process:4326): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

I would probably be able to hunt this down myself, but i have no clue what "egg_desktop_entries" are.

Packages seem to install and function properly, but it sort of concerns me to see 'CRITICAL' error messages so frequently.  Any ideas what is causing this?

*edit* Wrong forum, mods...please move to 'Ubuntu Repository Support' if necessary.

---

### Post by raydoo on 2005-03-26
hi got the same errors no clue neither  :( 

as far i am not experience any special trouble , you ?

---

### Post by WW on 2005-03-26
It's ugly, but it is harmless.  It is a known bug.  I'm running warty--does this still happen in hoary?

---

### Post by Telep on 2005-03-26
I'm running Hoary and it definately is happening. Can't remember seeing that before whith Warty.

---

### Post by ubuntu_demon on 2005-04-04
I'm having it also on a box of a friend of mine I just upgraded it from warty to hoary

---

### Post by Colsta on 2005-04-10
Hi folks,
I DID see this error when running Warty,  I can't say it was "only" isolated to totem, but apt would certainly spit this message out when I was trying to install (and re-install) totem and totem-xine.  I never managed to satisfactorily resolve this issue and get a 'good' install of totem.  Problems that arose were sound files played using totem would truncate before they finished - sometimes the app itself would hang.  Video media would get 'static' over the image, which was not apparent when played  using vanilla Xine.

I upgraded to Hoary yesterday, hoping to cure this weirdness, and like you, I noticed several instances of this same message during the install.
Having tested totem, it still truncates sounds played, and for an added bonus I now find WAV files are loud and distorted (curiously, MP3 are fine).
I am in the process of seeing what else is different before I can even begin to try and isolate cause/effect.

Would be interested in others findings.
Cheers.

---

### Post by ubuntu_demon on 2005-04-11
[QUOTE=Colsta]Hi folks,
I DID see this error when running Warty,  I can't say it was "only" isolated to totem, but apt would certainly spit this message out when I was trying to install (and re-install) totem and totem-xine.  I never managed to satisfactorily resolve this issue and get a 'good' install of totem.  Problems that arose were sound files played using totem would truncate before they finished - sometimes the app itself would hang.  Video media would get 'static' over the image, which was not apparent when played  using vanilla Xine.

I upgraded to Hoary yesterday, hoping to cure this weirdness, and like you, I noticed several instances of this same message during the install.
Having tested totem, it still truncates sounds played, and for an added bonus I now find WAV files are loud and distorted (curiously, MP3 are fine).
I am in the process of seeing what else is different before I can even begin to try and isolate cause/effect.

Would be interested in others findings.
Cheers.[/QUOTE]
 that friend of mine doesn't any issues whatsoever excluding the apt-get messages during upgrade.

---

