---
title: "[SOLVED] Could not resolve ‘HTP0893782.32’ when updating"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by kincora on 2008-05-30
When running update manager in ubuntu it hangs and freezes. So I tried running sudo aptitude update which resulted in :

Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not resolve ‘HTP0893782.32’

This message is repeated for every address it attempts to find. Anyone have any ideas? The sources.list file looks fine as far as I can tell.

---

### Post by kincora on 2008-05-30
Ok figured it out, for some reason HTP0893782.32 was set up as a proxy.

Deleted that and it's working again.

---

