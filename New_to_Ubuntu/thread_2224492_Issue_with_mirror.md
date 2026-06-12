---
title: "Issue with mirror"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by moaz2 on 2014-05-16
ok i m using linux for the first time well ubuntu 14.04 ...and each time i try to install something i get this msg at the end 
Err [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) trusty/multiverse amd64-microcode amd64 2.20131007.1+really20130710.1
  403  Forbidden
E: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/pool/multiverse/a/amd64-microcode/amd64-microcode_2.20131007.1+really20130710.1_amd64.deb](http://bd.archive.ubuntu.com/ubuntu/pool/multiverse/a/amd64-microcode/amd64-microcode_2.20131007.1+really20130710.1_amd64.deb)  403  Forbidden

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
am i doing something wrong...have been looking into various youtube and beginners guide for help with no result. 
I really do learn to learn linux plz help...
Thank you in advance.

---

### Post by QIII on 2014-05-16
I edited your title.  Many will just pass right by "Help me!" threads.  Please use descriptive subjects.

Your problem is due to an inaccessible URL on your repo mirror.  I suggest changing to another mirror.  If you need help with that, let us know.

Cheers.

---

### Post by moaz2 on 2014-05-16
err how to change mirror...i already told in the post i just started using linux.....thank you for identifying the problem though....

---

### Post by moaz2 on 2014-05-16
my laptop config is dual core 8gb ram with ati gfx card.....my screen is lagging....i think this is due to grafix driver....

---

### Post by deadflowr on 2014-05-16
> **moaz2 said:**
> err how to change mirror...i already told in the post i just started using linux.....thank you for identifying the problem though....

Open the dash menu.
(That's the top most icon in the launchers, that are on the left side panel. It looks like the Ubuntu logo)
Then enter a search for "Software and Updates".
Open that program, and in go to the part that says, "Download From".
Click on the dropdown menu and select other.
Then in the new window, select a new mirror, or try Find Best Server.
When the new mirror is selected, click ok, and then rerun the softwareupdater, or the apt-get update command.
from a terminal
```
sudo apt-get update
```
See if the new mirror works.

---

### Post by moaz2 on 2014-05-16
how to check ram grafix card and other stuffs ...to see if they were detected properly....and if not how to update them......

---

### Post by moaz2 on 2014-05-17
i need a power level indicator for my laptop...whatever given in stock ubuntu doesnt show the right thing...

---

### Post by sandyd on 2014-05-17
Hi, you would be better off starting a new thread for your issues

---

### Post by moaz2 on 2014-05-17
but i want all my issue in this thread:(

---

### Post by deadflowr on 2014-05-17
> **moaz2 said:**
> but i want all my issue in this thread:(

The people who would be best to help you with your other issues, won't be looking at this thread.
And having too many problems within a thread can/does cause confusion.

---

