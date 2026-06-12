---
title: "empathy accounts disappear between logins"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by travishume on 2011-09-28
I haven't been able to find a bug around this so I'm reaching out to you happy people ...

Runny a fully updated Oneiric system and gnome shell. Every time I login I have to re-setup my empathy accounts. Grrrr.

If I check the keyring I see see the empathy IM accounts there, they just aren't being used.

Ideas?

---

### Post by Seq on 2011-09-28
Have you moved the ~.mission-control folder? Or done any other creative file changes?

I had an issue where I kept my .mission-control in another place (a git repo on the same filesystem) and symlinked it where it was expected. Apparmour didn't like this and would refuse to let empathy access the file until configured to.

---

### Post by travishume on 2011-09-28
I haven't. Thanks for the avenues of investigation though. I wiped out the .mission-control directory as well as .cache/mc_connections.

No luck.

I then disabled the usr.lib.telepathy apparmour profile.

No luck.

Grrrr ... I'm not even sure how to debug this problem.

---

