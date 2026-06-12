---
title: "Awaking from suspend results in a flash of desktop before login"
date: 2011-08-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by meborc on 2011-08-15
I don't know if this is up to the slowness of my netbook processor or if it is a true bug, so I am asking confirmation on the following anomaly:

When awaking my netbook from suspend, the desktop is displayed for a few seconds. Long enough to read what documents are being edited or what websites have been left open. In a sense, whatever the desktop looked like when going into sleep.

The preferred way would be displaying nothing before user is authorised via password on login screen.

Is anyone else seeing this?

---

### Post by travishume on 2011-08-15
I've seen this. Not only that but after resume I was allowed to interact with the desktop or a good 20 seconds before it was locked and the password dialog was presented.

I often see the lag you mention, but not always.

---

### Post by danniel on 2011-08-15
> **meborc said:**
> Is anyone else seeing this?

Just tested and I get this too. Make a bug report and I will confirm that it also affects me.

---

### Post by tekstr1der on 2011-08-16
I've seen this for a couple of releases at least now. Did a bug get filed by the OP?

Please post the launchpad bug # here or ask that someone else files it.

---

### Post by meborc on 2011-08-17
I will post a bug as soon as I get back home to my netbook.

Thanks for the feedback guys :) at least I am not alone on this

---

### Post by meborc on 2011-08-17
OK, this is interesting :)

When going to suspend from the top-right menu, the screen is locked first and the desktop is NOT shown when waking up. In other words, it is working properly.

When going to suspend by closing the lid of the netbook, the problem is still there. The desktop (and my text files) can be seen by anyone for a few seconds.

So any ideas against which package I should file the bug? gnome-power-manager perhaps?

it might be connected to this also, but not sure - [https://bugs.launchpad.net/unity/+bug/802112](https://bugs.launchpad.net/unity/+bug/802112)

PS this I have been able to reproduce ten times already, so I know it is not just lucky random event. Menu suspend works, closing the lid has a security flaw.

EDIT: submitted bug #827883 but marked it security related, so it might not be visible

---

### Post by meborc on 2011-08-23
Just received an email that the fix is committed to the git :) so I will try to mark this thread as solved

the fix should now be just a few days away from your upgrade path

---

