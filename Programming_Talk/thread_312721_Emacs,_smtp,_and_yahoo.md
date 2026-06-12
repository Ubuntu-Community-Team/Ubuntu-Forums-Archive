---
title: "Emacs, smtp, and yahoo"
date: 2006-12-04
forum: Programming Talk
---

### Post by thomasaaron on 2006-12-04
I wish I would have posted this thread in the programming section, but I can't figure out how to move it.

Could someone familiar with emacs and smtp settings please have a look?

[http://www.ubuntuforums.org/showthread.php?t=311952](http://www.ubuntuforums.org/showthread.php?t=311952)

Thank you.
Tom

---

### Post by ArtechnikA on 2006-12-05
Just something to look at - if you already know the answer, nevermind...

But are you sure you can access Port 25 through your ISP?  'cause lots of ISP's won't let you send via 'foreign' (non-ISP) smtp.  E.g. - I have to use smtp.comcast.net even though my incoming mailserver is on my own domain.  So it might just be as easy as making sure you're accesing the correct smtp server.  If you know the Yahoo smtp works for you in other contexts, this isn't your problem.

---

### Post by thomasaaron on 2006-12-05
I've written applications in Python that access my yahoo smtp server with no problem.

I just can't figure out how to write to configure my .emacs file to do the same thing.

Best,
Tom

---

### Post by pchachte on 2007-02-19
You might try the solution presented here (it worked for me):

[http://wiki.debian.org/Manual-Howto#head-bf008f4d5019a18b892d243e2ad5f407a30c41a4]("http://wiki.debian.org/Manual-Howto#head-bf008f4d5019a18b892d243e2ad5f407a30c41a4")

---

