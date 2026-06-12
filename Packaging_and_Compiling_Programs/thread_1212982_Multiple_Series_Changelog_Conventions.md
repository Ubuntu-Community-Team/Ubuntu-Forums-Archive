---
title: "Multiple Series Changelog Conventions"
date: 2009-07-14
forum: Packaging and Compiling Programs
---

### Post by ace214 on 2009-07-14
I am maintaining a package for Jaunty and planning to publish it for Karmic as well. I am wondering what the conventions are for the changelog, especially since more versions will probably be released before Jaunty packaging stops.

So for example, should I make a Jaunty package of version 1, then a Karmic package of version 1, and then when version 2 comes out, so back to the changelog of the Jaunty package?
Also, the only difference between the two is that there is one less build-dep in the Karmic package.

---

### Post by laney on 2009-07-16
> **ace214 said:**
> I am maintaining a package for Jaunty and planning to publish it for Karmic as well. I am wondering what the conventions are for the changelog, especially since more versions will probably be released before Jaunty packaging stops.

So for example, should I make a Jaunty package of version 1, then a Karmic package of version 1, and then when version 2 comes out, so back to the changelog of the Jaunty package?
Also, the only difference between the two is that there is one less build-dep in the Karmic package.

A usual way is to append ~release~ppaX (assuming you're uploading to a ppa), for example foo_0.1-0ubuntu1~jaunty~ppa0 is less than ~karmic~ppa0, but you can still issue new revisions for each release separately. The monotonically increasing release names that we have help here.

---

