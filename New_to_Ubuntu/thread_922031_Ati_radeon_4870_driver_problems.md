---
title: "Ati radeon 4870 driver problems"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Alfx on 2008-09-16
Hey everyone.

-I installed the ATI drivers.

-I enabled the drivers in system->administrator-> hardware drivers, but after I rebooted, I'm forced to run in low graphic mode.

-The catalyst control center doesn't work either!


Not being able to have a graphic card is a pretty big design flaw.

What I am supposed to do now?

---

### Post by Tatty on 2008-09-16
are you sure its definately a low graphic mode?  you may just need to adjust your screen resolution:

System->Preferences->Screen Resolution


And what happens when you try to use catalyst?

---

### Post by Alfx on 2008-09-16
> **Tatty said:**
> are you sure its definately a low graphic mode?  you may just need to adjust your screen resolution:



System->Preferences->Screen Resolution





And what happens when you try to use catalyst?


I am 100% sure its low graphic mode, unbuntu tells me its going to run in low graphic mode before it even lets me enter my login.



This is what happens when I try to open Catalyst control center:


[I]"There was a problem initializing Catalyst Control Center Linux Edition.
It could be caused by the following:
No ATI graphics driver is installed, or the ATI driver is not functionning properly.

Please install the ATI driver that is appropriate for your ATI hardware, or configure using aticonfig."[/I]

---

### Post by Tatty on 2008-09-16
Ok something clearly has gone wrong.

Go back to your hardware drivers manager and uninstall the drivers.

Next install envyng from the repos, and install the ATI drivers using that.

---

### Post by Alfx on 2008-09-16
> **Tatty said:**
> Ok something clearly has gone wrong.

Go back to your hardware drivers manager and uninstall the drivers.

Next install envyng from the repos, and install the ATI drivers using that.

I installed envy, uninstalled the old drivers and installed the new ones.

So far everything works.

Thanks alot.

---

