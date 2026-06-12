---
title: "[SOLVED] Firefox 3 issue."
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ethoxyethaan on 2008-06-20
in title: Firefox 3 issue

i recently upgraded Ubuntu gutsy gibbons into ubuntu hardy heron using the installation cd.

the restricted drivers for my nvidia caused my screen to go black so i installed the nvidia driver directly from there Linux support page. and i got my pc running.

i configured the new firefox for use on my computer using several addons,

here comes the catch...

every time i close Firefox 3, it resets all my settings / history / cookies. (i checked the settings in the options-privacy menu and the Remove private data is not enabled), some addons i installed require for me to configure some things at first startup on firefox (like the suscription list from adblock plus, or the agreement from downthemall) i keep getting the same windows every time i restart firefox. its getting rather anying and i cant fix it myself.

any ideas are welcome.

EDIT: small note, when i start firefox as root it never asks anything but my addons are disabled that way.

---

### Post by john.hall on 2008-06-20
Does ~/.mozilla/firefox exist?

---

### Post by ethoxyethaan on 2008-06-20
> **john.hall said:**
> Does ~/.mozilla/firefox exist?

yes

---

### Post by acidsolution on 2008-06-20
U may take backup of all the important bookmarks and for safety backup of profile that is 
move .mozilla folder from your home directory and than start firefox .
  or u may just move away .mozilla/firefox folder only this must also do for u 

Note : Do this only if u dont want any thing to be imported from u r existed firefox 
i had same problem though i dont need any thing from mine old firefox so i just removed that folder and restart the firefox. 
this worked for me :)

---

### Post by ethoxyethaan on 2008-06-20
> **acidsolution said:**
> U may take backup of all the important bookmarks and for safety backup of profile that is 
move .mozilla folder from your home directory and than start firefox .
  or u may just move away .mozilla/firefox folder only this must also do for u 

Note : Do this only if u dont want any thing to be imported from u r existed firefox 
i had same problem though i dont need any thing from mine old firefox so i just removed that folder and restart the firefox. 
this worked for me :)

excuse me?

what understand from this text is somthing i don't need.

i want my firefox to start up and just have all my default settings, i don't even care for bookmarks.

edit: anyhow im going to remove everything i find with the string "firefox" and "mozila".

using locate, so i can do a 100% fresh install.

---

### Post by ethoxyethaan on 2008-06-20
solved:

how to solve it:

Remove the content of ~/mozilla/firefox/*
reinstall firefox

---

### Post by acidsolution on 2008-06-21
> **ethoxyethaan said:**
> excuse me?

what understand from this text is somthing i don't need.

i want my firefox to start up and just have all my default settings, i don't even care for bookmarks.

edit: anyhow im going to remove everything i find with the string "firefox" and "mozila".

using locate, so i can do a 100% fresh install.

What i told is the same thing what u did. I told to take backup just in case u required it. If i tell you to simply delete this folder than some other people who come to this thread in search for solution may delete that folder directly loosing all their bookmarks and other saved information.
Its up to you if u dont need that u can go and delete ..

---

