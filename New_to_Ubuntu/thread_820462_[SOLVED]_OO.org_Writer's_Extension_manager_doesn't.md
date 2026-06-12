---
title: "[SOLVED] OO.org Writer's Extension manager doesn't respond"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by al.adab on 2008-06-06
hello,

I'm using OO.org 2.4.1 on Linux Ubuntu Hardy Heron 8.04. I'm not using the version provided with the Ubuntu installation CD: I replaced it with that found at [http://openoffice.bouncer.osuosl.org...&version=2.4.0](http://openoffice.bouncer.osuosl.org...&version=2.4.0) and updated to 2.4.1, as I understood it's a good idea to have OO always updated...and maybe it wasn't such a great idea, after all...

The Extension Manager (OpenOffice.org Writer>Tools>Extension Manager) doesn't respond when I click on it. It worked in the version provided by Ubuntu. Initially I thought something went wrong with my fresh installation, so I re-installed it (after cleaning up). It still doesn't respond. Nor it does if I right-click on (for instance) ccooo.oxt and choose "Open with Office...Extension Manager".

I checked OpenOffice.org Writer>Options>Java (if it matters at all) and "Java Options>Use a Java Runtime environment" is ticked. In the list, I see "Sun Microsystems Inc 1.6.0_06" (ticked) and "Sun Microsystems Inc 1.6.0 with accessibility" (unticked).

I also posted this at the Open Office support's forum, but I thought it'd be of interest over here as well. 

Thanks for your help.

---

### Post by al.adab on 2008-06-06
Here's the solution (provided through OO.org forum):

1) go to Home Folder
2) hit ctrl-H (to have hidden files pop up)
3) look out for a folder named .openoffice.org2 (there'll be a dot preceding the name)
4) change the name to openoffice.org
5) start openoffice.org writer (it'll start as if it's the first time>all the personal settings will have to be manually restored)
6) extension manager should now be working. 

That's it.

---

