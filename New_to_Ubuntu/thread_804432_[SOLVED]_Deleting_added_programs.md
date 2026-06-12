---
title: "[SOLVED] Deleting added programs"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-23
I tried loading several programs that were not in the synaptic repositories that I found on the web.  I do not recall the names of the two programs I was trying to load since this was a week or two ago.  I had to compile these programs and they required several packages like gtk to be installed.  I would now like to remove these extra packages, but can't remember what I had to load before compiling.  I used make uninstall to remove the original compiled programs, but this did not unload all the added packages.

Is there a way other than going threw synaptic and looking at all loaded packages and hunting out what I believe was installed and uninstalling them.  My only problem I have with this is how would I know what ones to remove without knowing what I added.

I basically want to get Ubuntu back into the original condition before trying to load those programs.

---

### Post by sdennie on 2008-05-23
I would check /var/log/dpkg.log.  It has timestamps and should give you the info you are looking for.

---

### Post by TeoBigusGeekus on 2008-05-23
There is an option in Synaptic that will check dependencies and clear all unused packages. I'm on an xp machine right now, so I can't remember how you would do this exactly, but if you fiddle around with the buttons (i.e. installed packages, broken packages etc.) I think you 'll find it.

---

### Post by sdennie on 2008-05-23
Also, now that I think about it, if you were installing packages to satisfy build dependencies, you were probably just installing -dev packages.  They are most likely just header files so if you leave them there, they will take up a small amount of space but otherwise not have a detrimental effect on the system.

---

### Post by alienexplorers on 2008-05-23
From what I remember most were -dev files, but there were some other files.  I just don't want the system throwing a hissy fit one day because of having these packagges loaded.  Also, from what I remember some of the packages I loaded also loaded dependency packages with them.

---

### Post by sdennie on 2008-05-23
You could look at what you installed with /var/log/dpkg.log and uninstall those things but, I honestly wouldn't worry about it too much.  If disk space is not an issue, it's unlikely that you have installed anything that has or will cause you any problems if you used apt-get or synaptic and are using the default repositories.

---

### Post by alienexplorers on 2008-05-23
That answers my question.  As long as they won't harm anything I will just leave them as is.  I would hate to go into synaptic and delete something that I should not delete.  Thanks for the info.

---

