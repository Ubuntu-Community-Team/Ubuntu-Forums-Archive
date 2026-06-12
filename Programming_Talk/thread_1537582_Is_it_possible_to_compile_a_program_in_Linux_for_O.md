---
title: "Is it possible to compile a program in Linux for OS X?"
date: 2010-07-23
forum: Programming Talk
---

### Post by Ricky Velour on 2010-07-23
The reason that I ask is that I have been wanting to try out Ardour out for Mac OS X. I've been following their directions on what dependencies to install and what not however MacPorts is really troublesome to get to work. Needless to say I am interested in a doing this in Linux. I'm obviously a novice in all of this, but I have been enjoying the forty plus hours I have spent on doing this from OS X (Snow Leopard). Just thought I would ask the wise.

---

### Post by schauerlich on 2010-07-24
Sorry, I'm not entirely sure what you're asking. You want to install Ardour on Ubuntu, correct? According to [their site](http://ardour.org/download), it should be in the repos. A google search [confirms](http://packages.ubuntu.com/search?keywords=ardour&searchon=names&suite=lucid&section=all).

---

### Post by soltanis on 2010-07-24
No, he wants to cross-compile Ardour for OS X on Ubuntu. So he's trying to compile a Mac binary on Linux. I'm no expert on this, but previous experience with Appleware suggests that they don't take kindly to people cross-compiling for their platform, and so I'm not sure if you'll have any luck.

---

### Post by schauerlich on 2010-07-24
Why not just download the binary on the site, then? You can choose to pay $1 for the convenience of not dealing with compiling it yourself. And if you have a credit or debit card, it's easy enough to do via paypal. 

Re: cross compiling, it probably won't work. Apple's GUI stuff is all proprietary. Even with GNUstep you still need a Mach-O compiler. See: [http://stackoverflow.com/questions/693952/how-to-compile-for-os-x-in-linux-or-windows](http://stackoverflow.com/questions/693952/how-to-compile-for-os-x-in-linux-or-windows)

Even if you manage to pull it off (which would probably take much more effort than sorting out the MacPorts situation), it's not really worth saving $1 that could feed a programmer.

---

