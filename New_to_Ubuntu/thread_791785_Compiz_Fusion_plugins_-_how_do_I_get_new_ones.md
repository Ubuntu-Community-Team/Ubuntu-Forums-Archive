---
title: "Compiz Fusion plugins - how do I get new ones?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-12
I've heard there are new compiz fusion plugins that do not come with compiz in hardy heron.  How do I get these new ones?

Also, Are there any good animated skydome pictures anywhere other thank gnome-look and compiz-themes.org?  I saw this video on youtube that had this cool lava skydome.

---

### Post by cubeist on 2008-05-12
> **Rukaru said:**
> I've heard there are new compiz fusion plugins that do not come with compiz in hardy heron.  How do I get these new ones?

Also, Are there any good animated skydome pictures anywhere other thank gnome-look and compiz-themes.org?  I saw this video on youtube that had this cool lava skydome.

In synaptic, search for "compiz-fusion-plugins-extra"

That should give you all of them that are stable.  If you want the cutting edge plugins (like the sphere cube), you will have to re-compile from source, which is not easy at all.  I tried manually compiling compiz once and it ended in disaster!  But if you go that route, there are instructions on the compiz site for compiling for linux.

For skydome images just use google to search "animated skydome"

---

### Post by Rukaru on 2008-05-12
> **cubeist said:**
> In synaptic, search for "compiz-fusion-plugins-extra"

That should give you all of them that are stable.  If you want the cutting edge plugins (like the sphere cube), you will have to re-compile from source, which is not easy at all.  I tried manually compiling compiz once and it ended in disaster!  But if you go that route, there are instructions on the compiz site for compiling for linux.

For skydome images just use google to search "animated skydome"

I have the cube....now there's a sphere?  Well, the cube is enough for me.  I don't want to recompile anything. Now this is the second time I've heard synaptic.  Well...I don't exactly.....um....well there's a reason I posted this in "absolute beginner talk".  I don't exactly...know what synaptic is.  Care to explain?

---

### Post by michaelaly on 2008-05-12
Synaptic is the package manager. Menu - System -> Administration ->Synaptic. Click search(after being prompted for the root password) 'compiz-fusion-plugins-extra' and right click on the package listed and choose 'install'. Apply it and you're ready to go.

---

### Post by cubeist on 2008-05-12
> **Rukaru said:**
> I have the cube....now there's a sphere?  Well, the cube is enough for me.  I don't want to recompile anything. Now this is the second time I've heard synaptic.  Well...I don't exactly.....um....well there's a reason I posted this in "absolute beginner talk".  I don't exactly...know what synaptic is.  Care to explain?

Sure, no problem. In Ubuntu there are three ways to get programs.

First use the add/remove in the main menu.  This has lots of programs but wont show library files or extras, etc.

Second, browse the full synaptic library which is located at system/administration/synaptic package manager

Third, is a text-based shortcut for number two using the terminal, for example
sudo apt-get install compiz-fusion-plugins-extra


Also, do you have the ccsm program (compiz config settings manager)?  You can find it in synaptic and it will let you customize compiz to your hearts desire...

---

### Post by Rukaru on 2008-05-12
> **cubeist said:**
> Sure, no problem. In Ubuntu there are three ways to get programs.

First use the add/remove in the main menu.  This has lots of programs but wont show library files or extras, etc.

Second, browse the full synaptic library which is located at system/administration/synaptic package manager

Third, is a text-based shortcut for number two using the terminal, for example
sudo apt-get install compiz-fusion-plugins-extra


Also, do you have the ccsm program (compiz config settings manager)?  You can find it in synaptic and it will let you customize compiz to your hearts desire...

Well I don't know...Is that where you can select effects and stuff and then slightly edit them (like select rotate cube and edit it to make it speed up)...or is the ccsm more than that?  a screenshot would be nice.

Anyway, thanks for explaining it.  That really helps.

EDIT: I found the extra plugins in synaptic.  Apparently it is already installed...since it would only let me uninstall it.  That's weird though.  I don't have the flying window plugin.

---

### Post by philinux on 2008-05-12
> **Rukaru said:**
> Well I don't know...**Is that where you can select effects and stuff and then slightly edit them (like select rotate cube and edit it to make it speed up**)...or is the ccsm more than that?  a screenshot would be nice.

Anyway, thanks for explaining it.  That really helps.

You've got it.

---

### Post by cubeist on 2008-05-12
If ccsm is installed it will be located at system/preferences/advance desktop effects settings.

Also, what is the flying windows plugin... I have never heard of it!

---

### Post by Rukaru on 2008-05-12
> **cubeist said:**
> If ccsm is installed it will be located at system/preferences/advance desktop effects settings.

Also, what is the flying windows plugin... I have never heard of it!

I saw it on youtube.  :p

---

### Post by NIT006.5 on 2008-05-12
Yeah I've got the flying window plugin but didn't get it anywhere in the repos I know. I had to download it from somewhere else, but can't for the life of me remember where.

---

### Post by Kevbert on 2008-05-12
Check this out for some more plug-ins: [http://forum.compiz-fusion.org/showthread.php?t=5303]("http://forum.compiz-fusion.org/showthread.php?t=5303")

Check out the Etch (stable) plug-ins at:
[http://forum.compiz-fusion.org/showthread.php?t=3657]("http://forum.compiz-fusion.org/showthread.php?t=3657")

---

