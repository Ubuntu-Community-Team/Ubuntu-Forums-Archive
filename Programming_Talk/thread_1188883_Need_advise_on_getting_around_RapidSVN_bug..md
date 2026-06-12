---
title: "Need advise on getting around RapidSVN bug."
date: 2009-06-16
forum: Programming Talk
---

### Post by Jonas thomas on 2009-06-16
Hi... I'm running Hardy and RapidSVN 9.4 which appears to have a nasty [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/rapidsvn/+bug/264969").

I don't want to upgrade from Hardy and I want to minimize my unintended consequences from trying to fix this. (I basically know enough to be exceedingly dangersoure;) )

From the bug thread it appears I have two options to fix this:

> A temporary fix is just to downgrade the client side to an older version.

> aptitude remove subversion
> Press no until aptitude proposes to downgrade to version 1.4.x

Repositories that have been edited with version 1.5.x will be unaccessible, but new (or old) repositories work perfectly.

or
> I resolved this simply by switch apt sources to intrepid and downloading 0.9.6 from there. There were only 2 or 3 dependencies that installed without a hitch. No more segfaults.

I think switching apt sources to intrepid will end up doing something weird..  So I guess I should do the down grade trick..

In the thread someone suggested backporting a fix. Does anyone know if this was ever done.  If so, what to I need to edit in sources.list to get it?

---

