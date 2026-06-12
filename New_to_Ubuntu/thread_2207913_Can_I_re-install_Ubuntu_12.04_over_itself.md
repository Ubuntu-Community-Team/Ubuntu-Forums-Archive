---
title: "Can I re-install Ubuntu 12.04 over itself?"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Bob_Lade on 2014-02-25
In trying to get Skype working on my 12.04LTS I managed to cause all sorts of problems (for example, Software Center won't open now...) so I have a question...

Can I reload/install from my flash drive over the existing version (and if so, how) or
How do I remove Ubuntu from my computer so I can reinstall it.

It is on a little netbook with Windows XP in another partition.

-Dr. Bob

---

### Post by monkeybrain20122 on 2014-02-25
Yeah sure when you install there is an option to wipe existing OS and install Ubuntu on the whole disk.

---

### Post by Bob_Lade on 2014-02-25
OK, but can I work it so that Windows XP still stays on the computer?

---

### Post by monkeybrain20122 on 2014-02-25
No, not in that way, but you can instead choose "manual" or "advanced" during install and choose to install only over the lubuntu partition.

Edited: XP will be dead in April so I would just get rid of it. :)

---

### Post by ajgreeny on 2014-02-25
The manual partitioning is now called "Something Else" when you get to choosing where to install.

---

### Post by wildmanne39 on 2014-02-25
When you do you should reformat your ubuntu partition or you will have the same issues with the new install.

---

### Post by epikvision on 2014-02-25
To recapitulate from the responses so far, to keep Windows XP intact and re-install Lubuntu, you have to:

[LIST=1]
[*]Boot the USB and go to "Install Lubuntu." 
[*]When you get to the "Wipe" window, click on "Something Else" 
[*]Reformat your Lubuntu partition, so that the same issues don't arise. 
[*]Choose to install over your Lubuntu partition. 
[/LIST]

Hope this helps!

---

### Post by Bob_Lade on 2014-02-26
Thanks guys. Yes, I simply booted from the USB drive and reinstalled over the old version and all is working great! Thanks for all the replies!

-Dr. Bob

---

