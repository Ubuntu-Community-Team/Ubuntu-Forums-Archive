---
title: "Gnutella Updater"
date: 2008-10-10
forum: Programming Talk
---

### Post by orethrius on 2008-10-10
Okay, so I'm working out the last little bits of a BASH script that should be able to handle an update to gtk-gnutella-0.96.5, which - if properly formatted - can serve as a leaping-off point for future RAD-language projects.

Here's the link: [http://lagreview.pastebin.com/fd5da9d1]("http://lagreview.pastebin.com/fd5da9d1")

The highlighted portion is my primary concern.  Right now, the script enforces a "best practices" update to GTk / glib 2.0, since [1.2 is being phased out]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-04/msg01474.html").  My primary concern is whether this should remain, or if an automatic switch should check glib-config and gtk-config --version results and acquire the appropriate development headers.  On my system, I have both, and built against 2.x, but the two config programs stubbornly identify the current version as 1.2.10.  Is this a problem that needs to be dealt with by enforcing latest versions?

---

### Post by starcannon on 2008-10-10
I'd offer a choice to the end user, you can always word the dialog to encourage an update if you think thats best. But it is always best to offer updates as a choice I think. Just my .02.

GL and have fun

---

### Post by orethrius on 2008-10-11
I think I may have misunderstood the structure of the glib libraries - it appears that you can have multiple versions on the same system simultaneously, and they'll be used as needed.  I'd still like to hear from someone whether my suspicions are correct on that before closing this thread.

---

