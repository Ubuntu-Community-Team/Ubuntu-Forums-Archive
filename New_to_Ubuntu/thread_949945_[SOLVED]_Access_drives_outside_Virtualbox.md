---
title: "[SOLVED] Access drives outside Virtualbox"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-10-16
How do I set Virtualbox for a windows XP installation to access drives outside of the virtual OS.

---

### Post by ChildOfMana on 2008-10-16
You first need to install the Virtualbox Guest Additions image. You can then set up a shared folder between you host and your guest OS.

Unfortunately I can't remember how to install the Guest Additions... but I remember it being very easy!!

Once you've installed your Guest Additions though then check out [this](http://liquidweather.net/howto/index.php?id=103) tutorial for how to set up a share between a Linux host and Windows guest.

Edit: I seem to remember you need to use Virtualbox to mount the Guest Additions .iso image to your virtual CD/DVD-ROM (in Windows) and then browse it and find the install executable. Think its fairly straight forward after that. You can obtain the Guest Additions image from [here](http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso).

2nd Edit: made the link for the image work... I'm really not with it tonight! Sorry.

---

### Post by celticbhoy on 2008-10-16
Managed to work it out, once I had set the shared folders I just didn't realise that I had to install them in XP

---

### Post by Average Joe on 2008-10-16
In the Virtualbox settings of your Virtual machine (Windows XP) you can configure Shared folders. These can point to any location outside the Virtual OS, but is within the host OS (Ubuntu).

---

