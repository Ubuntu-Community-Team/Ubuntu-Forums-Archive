---
title: "brother mfc-5440cn printer installation"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by KeithF40 on 2008-08-24
i have it set up as a network printer plugged into my router so i can use it on my desktop and wireless laptop, which works fine in xp on both machines.

i went to their site and there were no linux drivers but i found a link on google to their linux driver site.

there were two offerings, one for redhat/suse/something else and then one for debian, im pretty sure that is the one i was supposed to download so i did.

it is a .deb file so i ran it and it went through the package thing, not really sure what is going on there so some insight would be nice too.

anyway i guesses it finished whatever it had to go but it is not showing up in printers.  when i go to add a new printer the specific printer i got, brother mfc-5440cn is not one of the choices.  there is an option to select a ppd file i believe, no idea where to find that.

---

### Post by kattman on 2008-08-24
Go to Synaptic and search for "brother"
you need the 4 files

brother Cups Wrapper common
brother Cups Wrapper extra 
brother-lpr-drivers common
brother LPR drivers for extra

---

### Post by KeithF40 on 2008-08-25
cool

how was i supposed to know to do this

---

### Post by KeithF40 on 2008-08-25
am i correct in that running the install file from brother put the packages in that list?

and then you go to the package list and select the packages you want to install?

then you go to add printer and select the package you installed?

---

### Post by Sonny2 on 2008-12-19
> **kattman said:**
> Go to Synaptic and search for "brother"
you need the 4 files

brother Cups Wrapper common
brother Cups Wrapper extra 
brother-lpr-drivers common
brother LPR drivers for extra

Thanks! It worked like a charm

---

