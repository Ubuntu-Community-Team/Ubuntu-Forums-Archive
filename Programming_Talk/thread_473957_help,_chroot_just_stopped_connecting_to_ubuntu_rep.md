---
title: "help, chroot just stopped connecting to ubuntu repos"
date: 2007-06-14
forum: Programming Talk
---

### Post by Hendrixski on 2007-06-14
OK, f**ing TWICE now!  I had dchroot working and it was all nice, I was doing some development and packaging and then apt just STOPPED WORKING on the chroot.

No particular reason why... so I tinkered with it for a while then just reinstalled a new chroot and it worked for a week or so and again, apt just died.

what the hell.?

anyone else have this problem? ever? or am I the only one who'se ever had it?  there's nothing on google about it and nobody on #ubuntu has a clue.  how can I get it to work again?

I am just SO angry, someome please help.  please

---

### Post by Hendrixski on 2007-07-02
After poking at it enough I found that it's the resolv.conf on the chroot

I thought I'd post that here in case anyone else came across the same problem.. it's very frustrating.  made me really angry that I couldn't find anything... hopefully this helps someone else avoid that.  just copy the resolv.conf from the base system into the chroot.  :-)

---

