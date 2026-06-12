---
title: "[SOLVED] Flash Regression when update manager was checked"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by crjackson on 2008-07-12
A couple of days ago the v10 flashplugin-nonfree installed with synaptic.  Today I checked for updates and it reinstalled v9.  What gives?

---

### Post by crjackson on 2008-07-13
Wow! I must be the only one this has happened to.

---

### Post by drs305 on 2008-07-13
> **crjackson said:**
> A couple of days ago the v10 flashplugin-nonfree installed with synaptic.  Today I checked for updates and it reinstalled v9.  What gives?

Maybe you had the hardy-proposed repository enabled? The normal repos still show v9 but when I enable the hardy-proposed it shows v10 available. I didn't/don't know that unticking a proposed repo would downgrade a package -  maybe there was a problem with it...

---

### Post by crjackson on 2008-07-13
> **drs305 said:**
> Maybe you had the hardy-proposed repository enabled? The normal repos still show v9 but when I enable the hardy-proposed it shows v10 available. I didn't/don't know that unticking a proposed repo would downgrade a package -  maybe there was a problem with it...

I do have proposed enabled, but the strange thing is that I didn't change the repos.  It was still enabled when it got overwrote with v9.  Is it possible that it was temporarily removed from the proposed repo for a bit?

---

### Post by philinux on 2008-07-13
Version 10 beta 2 has come from the backports. Check your sources.

Nothing wrong with backports by the way.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I think the devs have backed out 10 beta 2. It's too buggy.

---

### Post by kaibob on 2008-07-13
> **philinux said:**
> ...I think the devs have backed out 10 beta 2. It's too buggy.

Yeah, that's what happened. With Flash 10, I couldn't access any page with Flash--Firefox just crashed. Now, with Flash 9, I have no problems. I'm sure we will see Flash 10 again before long.

BTW, I have backports but not proposed enabled. Also, there is another thread that discusses this issue in greater detail.

---

### Post by crjackson on 2008-07-13
Yeah you are right.  It is the backports repo.  I just installed updates on another system that already had v10.  It said it was updating TO v10 through the back ports.  When it was done, I had v9 installed again.  Funny that it says it's installing v10 when it's actually installing v9.

Anyway, mystery solved...

---

