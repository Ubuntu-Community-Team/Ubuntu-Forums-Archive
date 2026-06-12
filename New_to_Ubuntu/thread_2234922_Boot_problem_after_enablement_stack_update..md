---
title: "Boot problem after enablement stack update."
date: 2014-07-17
forum: New to Ubuntu
---

### Post by pat4 on 2014-07-17
Running Ubuntu 12:04 (Pangolin) on a 64 bit machine.

I switched the computer on this evening and updates were available. Dialoge box told me that an update was available for my Hardware Enablement Stack. Ran this.

Rebooted after update (as instructed).
System boots to black screen asking for login name and then password.
Entering these gives me "Welcome to Ubuntu.... etc etc.. then a note to tell me that the Hardware Enablement Stack is supported to 2017.
This is followed by a command promt         pat@base-machine:~$

Thats it... I cannot get back to my desktop.  

Can someone please tell me - in step-by-step format what I need to do to resolve this problem please? Bearing in mind that I do not yet know enough about Ubuntu (though I am learning) simple instructions would be appreciated.

Many thanks..

---

### Post by MrSteve on 2014-07-17
had the same problem a few days ago the only way out of it, for me, was to do a clean install of 12.04.4 and then update
i have separate partitions for /, /swap, /home so no data lost just about an hour to reinstall and update ...

---

### Post by pat4 on 2014-07-17
Thanks.. I take it that all data was lost? or is there a way to reinstall 12:04 and preserve data?

---

### Post by MrSteve on 2014-07-17
if you have separate partitions for
/ (root)
/swap
/home

all you do is format / (root) and reinstall
leave the other partitions alone, do not format

if you do not have separate partitions on the drive then use a live ubuntu cd/usb and backup any data you require to be backed up

but i stopped fire fighting the system years ago, i just reinstall and replace everything from backup
its just easier and quicker then fire fighting ...

---

### Post by pat4 on 2014-07-17
Apologies - just re-read your post.. What I should have asked is.... Is there any way to save data?

---

### Post by MrSteve on 2014-07-17
as stated use/run a live linux ubuntu cd/usb and save any data on the drive from there to a usb key drive or upload it to on-line storage  ...

---

### Post by pat4 on 2014-07-17
Steve,
Thanks for that.. I'll give it a go tomorrow.

---

### Post by MrSteve on 2014-07-17
post back and let us know how you got on please, best of luck ...

these links maybe of help
[http://askubuntu.com/questions/208007/how-to-partition-hard-disk-to-save-data-during-ubuntu-reinstallation](http://askubuntu.com/questions/208007/how-to-partition-hard-disk-to-save-data-during-ubuntu-reinstallation)
[http://askubuntu.com/questions/19808/how-to-reinstall-ubuntu-keeping-my-data-intact](http://askubuntu.com/questions/19808/how-to-reinstall-ubuntu-keeping-my-data-intact)

---

### Post by pat4 on 2014-07-18
Thanks once again Steve,
I decided to bite the bullet and did a complete new install and took the opportunity to install alater distro.   I already had a second hard drive installed with little on it that I could afford to lose so I installed a new distro from an iso image and on completion was able to acces the original HD and recover all necessary data..

Just swapped the HD's round really..:-))

I appreciate you taking the time to help.

Besty regards,

---

### Post by MrSteve on 2014-07-23
as an update to your last post 'pat4' i also did the same 
but this time i installed kubuntu 12.04.4

even with updates, everything is working better the ubuntu itself 
must admit the move from ubuntu to kubuntu has been eye opening ...

---

