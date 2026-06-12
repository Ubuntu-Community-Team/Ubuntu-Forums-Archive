---
title: "Upgrade to Heron"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by hAvAAck on 2008-07-17
Hey all, sorry if I missed it in a search, I'm not quite sure what terms to use.

I recently had to do a clean install, and unintentionally installed 7.10
I want to upgrade to 8.04 without losing all of my customizations, and without it changing me to FF3.  I'm not sure if this is possible, but is there a way to do this via the terminal; it doesn't seem that using the update manager will allow me to choose what gets upgraded and what doesn't.

Thanks, and sorry if this is a ridiculous question.

---

### Post by NullHead on 2008-07-17
Run:> gksudo update-manager -dIn a terminal window, Accessories>Terminal. 

This should update you to 8.04 with no problems. There is also a package for firefox 2 if you wish to keep ff2.

---

### Post by hAvAAck on 2008-07-17
All that's available in my upgrade manager is an update to a new distro release
If running it, will I be able to choose what parts of the system it upgrades?

---

### Post by NullHead on 2008-07-17
No, it'll upgrade you to a standard install of 8.04, upgrading all the packages you have installed and installing new ones along the way. Don't worry, I upgraded my laptop and the settings and everything, for the most part, were intact. 

After the upgrade, you'll have to restart and then you'll need to open up Synaptic Package Manager and uninstall firefox 3 and revert back to ff2 if that's what you want to do.

---

### Post by hAvAAck on 2008-07-17
All right, I'll get on that.
On a side note - is there a most appropriate way to downgrade FF? I tried it once before and it borked my entire install, hence the new one. It wouldn't allow any add-ons or anything.

I appreciate your responses

---

### Post by NullHead on 2008-07-17
I guess the way I'd do it, is from Synaptic. Uninstall FF3 and install FF2 .. if that's possible. FF3 should suit you better than ff2 though. I see no reason to downgrade, but you can if you want to. I really can't change your mind. ;)

---

### Post by drs305 on 2008-07-17
I know you were asking for a command line method of keeping FF2. If you want to use synaptic instead, you could highlight the firefox2 entry in synaptic, then select Package > Lock Version.  It may prevent FF from dumping FF2 when you do the upgrade. 

If you try it please let us know the results.

---

### Post by hAvAAck on 2008-07-17
> **NullHead said:**
> I guess the way I'd do it, is from Synaptic. Uninstall FF3 and install FF2 .. if that's possible. FF3 should suit you better than ff2 though. I see no reason to downgrade, but you can if you want to. I really can't change your mind. ;)
My experience with FF3 is that it is much slower than FF2, but I might give it another try.

> **drs305 said:**
> I know you were asking for a command line method of keeping FF2. If you want to use synaptic instead, you could highlight the firefox2 entry in synaptic, then select Package > Lock Version.  It may prevent FF from dumping FF2 when you do the upgrade. 

If you try it please let us know the results.

Ack, a bit too late for that, but interesting. I wish I had seen this post before taking the plunge, for at least the testing side of things ;)

---

### Post by hAvAAck on 2008-07-17
Ack, the update actually failed (hung and now fails to startup) and borked the entire install
Starting from scratch again.. but with an 8.04 CD
Thanks for the help anyway

---

### Post by NullHead on 2008-07-17
Sorry to hear about the upgraded failure, but I must stress that FF3 is superior, for me at least. 

Best of luck to you, 
NullHead

---

