---
title: "[SOLVED] If I install a driver how do I remove it?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-06-09
I installed 

vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb

from [here]("https://forge.vodafonebetavine.net/frs/?group_id=12").

but it messes up my present dial-up connection through Gnome-PPP.

I was looking in Synaptic to remove it but can't see it - so how do I get rid of it or undo what it's done?



.

---

### Post by billgoldberg on 2008-06-09
> **Sealbhach said:**
> I installed 

vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb

from [here]("https://forge.vodafonebetavine.net/frs/?group_id=12").

but it messes up my present dial-up connection through Gnome-PPP.

I was looking in Synaptic to remove it but can't see it - so how do I get rid of it or undo what it's done?



.

If it's installed, it should be in synaptic.

Or try this command (but you'll need to know the name of the app, I guess that's not the case)

```
sudo apt-get autoremove --purge NameOfProgram
```

---

### Post by brian_p on 2008-06-09
> **Sealbhach said:**
> I installed 

vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb

from [here]("https://forge.vodafonebetavine.net/frs/?group_id=12").

but it messes up my present dial-up connection through Gnome-PPP.

I was looking in Synaptic to remove it but can't see it - so how do I get rid of it or undo what it's done?



.

```
sudo apt-get remove --purge vodafone-mobile-connect-card-driver-for-linux

```
or

```
sudo dpkg -r vodafone-mobile-connect-card-driver-for-linux

```
Either should do it.

---

### Post by Sealbhach on 2008-06-09
Thanks, I'm at work at the moment so can't try it until this evening.

I was wondering, can I give these commands from any folder? Because I don't know where the driver was installed.


.

---

### Post by Robux the great on 2008-06-09
Hi

You should be able to use that command from anywhere in the system.

I am new to Ubuntu though so don't hold me to that

Regards

Rob:guitar:

---

### Post by Sealbhach on 2008-06-09
> **brian_p said:**
> 

```
sudo dpkg -r vodafone-mobile-connect-card-driver-for-linux

```
Either should do it.


Thanks Brian,

this one worked, the other one couldn't find any files.

You've saved me a lot of heartache so you've been officially thanked.

Thanks to everybody else too for responding.

Sealbhach.



.

---

