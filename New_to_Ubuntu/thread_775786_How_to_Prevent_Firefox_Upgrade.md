---
title: "How to Prevent Firefox Upgrade"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by krinderlin on 2008-04-30
Okay, I want to upgrade to 8.04 LTS, however, the one thing I don't want is Firefox 3.  I have several plugins that I use that haven't caught up to Firefox 3 yet.  I recall reading somewhere a way to prevent upgrading a package from say 2.x to 3.x, but I can't seem to find it again.

Essentially, I want to tell aptitude to accept any minor updates to Firefox 2, but not to actually update all the way to Firefox 3.

Thanks ahead of time!

---

### Post by aheckler on 2008-04-30
I would suggest just upgrading straight to Hardy then uninstalling FF3 and installing FF2. It's perfectly possible, see the link in my sig.

---

### Post by wadelewis4 on 2008-04-30
> I would suggest just upgrading straight to Hardy then uninstalling FF3 and installing FF2. It's perfectly possible, see the link in my sig.
__________

I agree with aheckler. Simply remove beta3 and install Firefox2. It's what I did, and it's working great.

---

### Post by muteXe on 2008-04-30
+1 to mr aheckler.

---

### Post by FuturePilot on 2008-04-30
If you upgrade from Gutsy to Hardy, Firefox 2 will still be installed. It's also still in the repos so if you do a fresh install you can always install it from the repos.

---

### Post by krinderlin on 2008-04-30
Doh.  I somehow had it in my head that Firefox 3 was the same package as 2, so once you upgraded and started using the Hardy repositories, it'd end up getting replaced.

One would think I'd have figured this out after having to install GCC 3 when attempting to compile Doomsday Engine from source.

((Which was fun, because I figured it out completely on my own.  Even down to swapping over the symbolic link /usr/bin/gcc to temporarily point to gcc-3.4.  In fact, the idea first struck me when I was screaming at gcc, realized it was gcc 4, and recalled some general freakout in the Linux community back when gcc 4 came out and stuff was purportedly broken everywhere.))

---

