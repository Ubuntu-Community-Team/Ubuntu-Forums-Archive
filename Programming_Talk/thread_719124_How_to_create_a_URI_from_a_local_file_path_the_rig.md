---
title: "How to create a URI from a local file path the right way?"
date: 2008-03-08
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2008-03-08
I am playing with drag & drop right now in Python, and have hit an odd little snag: Attaching URIs!

I of course know the *URL* of the file I am attaching, and the easy / arbitrary way of turning that into a URI would be to suffix it with "file://". That works, but also seems like bad practice and likely to screw up somewhere.

I have found two other things:
-gnomevfs.get_uri_from_local_path(self.dndavatar_svg)
-g_filename_to_uri

The former works fine but adds a dependency on Gnome VFS. The latter does not seem to have any obvious Python bindings. I suppose I am looking for the Python alternative to g_filename_to_uri.

---

