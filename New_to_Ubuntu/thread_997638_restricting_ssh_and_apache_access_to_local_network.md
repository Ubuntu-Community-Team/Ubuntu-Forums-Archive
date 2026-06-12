---
title: "restricting ssh and apache access to local network?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Karpah on 2008-11-30
hi all, 

this is a pretty simple question that hopefully has a simple answer.

I've just set up openssh-server on my desktop PC running Intrepid, for the purpose of using unison to sync files with my laptop. That part works all good, and I can ssh from my laptop to the desktop PC.

I'm a bit paranoid about security, so I don't want my desktop to be accessible externally. How can I check/test whether or not ssh-ing from outside my local network would be possible?

Also, I have Apache installed on both my laptop and my desktop, so I can do some web development. I'd also like to retrict access to that to only local sites (ie. I'm not hosting any internet-accessible sites). Is that possible/simple, does it happen by default, or is this a really silly question?

cheers,
Rebecca

---

### Post by Xiong Chiamiov on 2008-11-30
If you are behind a router, then you have nothing to do, as it will block all of those ports automatically.

---

### Post by Karpah on 2008-11-30
Thanks for the quick reply!

I do have a router on the network, but I'm not sure how many router-y things it's actually doing.

The internet on the network comes from a USB wireless broadband modem attached to another desktop PC, so I guess the other desktop PC is looking after that sort of thing? Should I be checking it to see if the ports are blocked? (It's running Windows XP.)

---

