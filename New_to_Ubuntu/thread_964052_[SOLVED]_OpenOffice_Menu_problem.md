---
title: "[SOLVED] OpenOffice Menu problem"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by kneewax on 2008-10-30
Hey Folks,

I upgraded from Hardy to Intrepid today.In hardy I was using OOo3 without issue.  After the upgrade I found OOo wouldn't work so I removed the Intrepid version and reinstalled 3.0 from the download.  Now I get a problem where none of the menu items have text in OOo and I cannot type anything.  Also I cannot open any of my previously save OOo 3 files. (see screenshot)

Any ideas?

---

### Post by markharding557 on 2008-10-30
i would completly purge the lot and then try again from intrepids repo

---

### Post by kneewax on 2008-10-31
Thanks for the suggestion.  Actually I did a complete remove - but thatdidn't work.  In the end I removed OOo3 totally from Synaptic, then I deleted all the .OpenOffice folders (there were 3) from my $home folder.  

As OOo3 isn't in the Repos I then installed from the download again - and Hey Presto it worked.

Bit fiddly but at least I got there.

---

### Post by kneewax on 2008-10-31
Thanks for the suggestion.  Actually I did a complete remove - but that didn't work.  In the end I removed OOo3 totally from Synaptic, then I deleted all the .OpenOffice folders (there were 3) from my $home folder.  

As OOo3 isn't in the Repos I then installed from the download again - and Hey Presto it worked.

Bit fiddly but at least I got there.

---

### Post by curran on 2008-11-20
I had the same issue - very strange. I did
sudo apt-get remove openoffice.org-*
sudo apt-get install openoffice.org-writer
no change, still the textless menus: [screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=93488&stc=1&d=1227214959")

Am I doing something wrong? Should I uninstall/install a different way?

---

### Post by kneewax on 2008-11-21
That's what I did the first time.  To fix it I did an apt-get remove,  I then went into the Synaptic Package manager and marked openoffice3 and its dependencies as 'Mark for Complete Removal' (see attached).  Once this was applied  I rebooted (no idea if required, just seemed like a good idea)  then I installed OpenOffice from the downloaded package on the OOo website.

I hope this helps, for whatever reason it worked for me...

---

### Post by tmcmurph on 2008-12-19
I tried all the above but nothing worked for oo2 or oo3 so I tried turning off all visual effects and now I have my menus back. Hope this helps someone else. 

PS. NVidia GeForce 4 card with 128 Meg RAM and using NVidia drivers. Problem only appeared after a fresh install for 8:10 and never had this problem before with the desktop effects.

---

### Post by nienberg on 2008-12-25
> **tmcmurph said:**
> I tried all the above but nothing worked for oo2 or oo3 so I tried turning off all visual effects and now I have my menus back. Hope this helps someone else. 

PS. NVidia GeForce 4 card with 128 Meg RAM and using NVidia drivers. Problem only appeared after a fresh install for 8:10 and never had this problem before with the desktop effects.

Thanks, I had the same issue and your simple suggestion fixed it for me too.  I have the same nVidia card, so maybe that is where the problem lies.

System>Preferences>Appearance>Visual Effects

---

### Post by luminol on 2009-01-02
What did it for me was going to System --> Preferences --> Appearance --> Fonts and clicking Subpixel Smoothing. Worked fine after that.

---

### Post by Eskokk on 2009-01-04
I run into this same problem with Ubuntu 8.10 and Openoffice 2.4 and 3.0.
In my system the drop down menus are shown only as lines and if I hover the mouse cursor over the items the texts appear but are again gone when I use the same menu later.

I use Nvidia GeForce FX5500 card and drivers from Nvidia.
Choosing subpixel smoothing did not help for me but what helped was to turn visual effects ON. They were off before.

---

### Post by zucche on 2009-02-11
I just solved a similar issue by **removing gtk-qt-engine**, after reading 
[http://www.nabble.com/-Bug-44341--NEW:-OpenOffice-with-gtk-qt-engine-td19710447.html](http://www.nabble.com/-Bug-44341--NEW:-OpenOffice-with-gtk-qt-engine-td19710447.html)

give that a try. 

that happened to me on Ubuntu Hardy, with some 3rd party repositories, and a big gnome+kde mess.

---

