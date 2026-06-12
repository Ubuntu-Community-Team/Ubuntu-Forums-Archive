---
title: "no apps in dash"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-10-01
normally use gnome 3, giving unity a try, no apps or files in dash.

none.

nada.

zip.

known issue ?

solution ?

---

### Post by effenberg0x0 on 2011-10-01
Unity or its dependencies might not be installed / properly installed. I'd for for a reinstall. This packages will also reinstall zeitgeist which might be involved in this behavior.

sudo apt-get install --reinstall unity unity-common unity-lens-applications unity-lens-files unity-lens gwibber unity-lens-music unity-place-applications unity-place-files unity-scope-musicstores unity-services unity-2d unity-2d-launcher unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-asset-pool unity-greeter 

sudo lightdm restart

Regards,
Effenberg

---

### Post by flipper T on 2011-10-01
the odd thing is, working fine 2 days ago.

may wait before any reinstall.

---

### Post by effenberg0x0 on 2011-10-01
Yes, updates some time crash things at this point of development (beta)... Its usual.

Regards,
Effenberg

---

### Post by flipper T on 2011-10-01
thx for your time and effort (have saved your reinstall code for future reference), but reboot did the the trick.

"have you tried turning it off and on?"...ahhh the wisdom of tech supports around the globe


:)

---

### Post by effenberg0x0 on 2011-10-01
hahahaha.....

You know what dude, I always think of too complicated scenarios when trying to help people. I forgot the basics. Thank you for reminding me. On/Off is **always** great advice.

Regards,
Effenberg

---

