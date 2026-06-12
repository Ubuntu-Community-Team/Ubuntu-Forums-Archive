---
title: "What touches /etc/sudoers"
date: 2010-02-02
forum: Programming Talk
---

### Post by kev000 on 2010-02-02
I have my own package that installs a /etc/sudoers however, something in the ubuntu install is touching it and adding an entry right after i install.  Anyone know what app/package/process is doing that?

thanks.

---

### Post by nvteighen on 2010-02-03
> **kev000 said:**
> I have my own package that installs a /etc/sudoers however, something in the ubuntu install is touching it and adding an entry right after i install.  Anyone know what app/package/process is doing that?

thanks.

Your package shouldn't be installing /etc/sudoers... What the hell are you trying to do?

---

### Post by Reiger on 2010-02-03
Well to be fair you might have a &#8216;service pack&#8217; you want to apply, like a collection of administrative settings + additional software.

Anyway there is a mechanism in place to detect /etc/sudoers change and/or corruption. I noticed when I messed up once with visudo.

---

### Post by kev000 on 2010-02-03
> **nvteighen said:**
> Your package shouldn't be installing /etc/sudoers... What the hell are you trying to do?

Yes, it's more of a "service pack" for a custom build of ubuntu (see my sig).

I know this is a hack, but since i own the login manager, I suppose I could have it check if the sudoers file has changed (compare md5's or something) and fix it.  I wish I could figure out whose changing it and have them change it to the way I want it.

---

### Post by Hellkeepa on 2010-02-03
HELLo!

Well... You could write a small app that puts an inotify watch on the file, and logs all the processes that modify it. Probably the fastest and most reliable way to do this.

Happy codin'!

---

### Post by nvteighen on 2010-02-03
There has to be an API or less brutal way to do this... I just can't believe the only way to do this is to replace /etc/sudoers.

---

