---
title: "Change permission in root and save file?"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-11
Trying figure out a problem, got idea of changing a code in [B]etc/conky/conky.conf
[/B]But I cannot make it work.

I been trying commands in terminal such as: sudo chmod 667 /etc/conky/*

And it seems that it has worked, but still, I cannot save the file.
It looks like this: [http://screencloud.net/v/erAq](http://screencloud.net/v/erAq)

I keep on pressing "save anyway", but it just wont save!

---

### Post by th.sigit on 2013-11-11
Instead of chmod-ing /etc/conky/* you could have just edit etc/conky/conky.conf with sudo permission, thus:

> sudo gedit etc/conky/conky.conf

---

### Post by Niemil on 2013-11-11
> **th.sigit said:**
> Instead of chmod-ing /etc/conky/* you could have just edit etc/conky/conky.conf with sudo permission, thus:
> [COLOR=#000000]*sudo gedit etc/conky/conky.conf*[/COLOR]
Hm, but that doesn't go under root.
It popped up an gedit with the following path: /home/sozu/etc/conky/conky.conf

---

### Post by deadflowr on 2013-11-11
> **Niemil said:**
> Hm, but that doesn't go under root.
It popped up an gedit with the following path: /home/sozu/etc/conky/conky.conf

?

Do you mean the file is in /home?
And not /etc.

---

### Post by th.sigit on 2013-11-11
Pardon me! Forgot the "/" (root) before "etc"

Should go with 

> [COLOR=#000000]*sudo gedit /etc/conky/conky.conf*[/COLOR]

---

### Post by Niemil on 2013-11-12
> **deadflowr said:**
> ?

Do you mean the file is in /home?
And not /etc.
What I mean is that the file is in the **/etc**

> **th.sigit said:**
> Pardon me! Forgot the "/" (root) before "etc"

Should go with
> *sudo gedit /etc/conky/conky.conf*

Oh thank you! now it works :o
Quite mindblowing. Because yesterday I were on an IRC channel where I use to talk with friends, and I've a dude using Linux there and he tried help me, and I am quite sure he also wrote similar to this code, but that it didn't work to save it. We been trying change the owner to me and all kind of stuffs.

Now however, it works! thanks

---

