---
title: "Anyone else who upgraded and is having issues with Thunderbird notifications?"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dsfitzpat on 2011-09-01
Before I go ahead and report this as a bug, I thought I'd see if anyone else has had this problem, and if there's a resolution.

Situation: upgraded to 11.10 Alpha 3 from 11.04 on my netbook.  I had Thunderbird already installed in 11.04, with the libnotify extension installed to give me new mail notifications.  Since there was no native support in 11.04 for Thunderbird, this was installed as an add-on, and probably required some tinkering under the hood.

Problem: after upgrading to 11.10, notifications no longer work.  The new version of the notifications extension is installed (it's there by default) but nothing happens when new mail comes in, and the Thunderbird entry in the mail indicator applet isn't quite right.  I suspect this is because I probably had to manually edit the items that appear in the mail indicator applet.

Is there someone with a clean install who can point me towards the right settings?

---

### Post by dameat on 2011-09-02
I just banged my head on this for a bit as well. It seems the solution is:
```
apt-get install libunity4
```

My clue was this bug:
[https://bugs.launchpad.net/messagingmenu-extension/+bug/817598](https://bugs.launchpad.net/messagingmenu-extension/+bug/817598)

seems like thunderbird ought to depend on this lib?

---

### Post by dsfitzpat on 2011-10-04
OK, thanks!  Sorry for the slow reply - I forgot to subscribe to the thread when I created it!

---

### Post by dsfitzpat on 2011-10-06
Hmm, the bug you linked to is marked as fixed - Thunderbird is built against libunity5 now, and libunity4 is not even in the repositories.  Well in any case, it's working properly on a clean install on another machine, so I'll just do a clean install once the official release comes out.
But thanks for the reply in any case.

---

