---
title: "[SOLVED] Update Manager Hangs - Heron"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Piddell on 2008-07-19
There are a few threads on this sort of subject, but I still can't get this sorted.

I have 18 updates, so I click the update manager (or select it from the menu) it shows all the updates available.
When I click "install updates" the update manager starts, but never loads.  I do not get the enter password part.  after a few seconds it vanishes from the  list at the bottom.

I can't close the first update manager window - multi clicks on the close button are ignored.
The rest of the machine is still working ok - I can type this, open other apps. etc.

Ideas?

Thanks
Phill

---

### Post by pavel989 on 2008-07-19
force it to quit and do "sudo apt-get update"

---

### Post by Piddell on 2008-07-19
Wow that was amazing
I ran xkill and zapped the update manager (cool app!)
Re-loaded and all looking good (well it's doing something)

THANKS:)

---

### Post by pavel989 on 2008-07-19
glad it works!

---

### Post by Piddell on 2008-07-30
> **pavel989 said:**
> glad it works!

But why do I have to keep doing this in Heron?

It's just failed again today, xkill and sudo apt-get update have me working, but it's not very slick!:confused:

---

