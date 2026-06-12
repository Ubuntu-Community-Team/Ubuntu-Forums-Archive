---
title: "How do I change the &quot;Sorry, try again.&quot; phrase when I enter a password wrong."
date: 2014-07-17
forum: New to Ubuntu
---

### Post by TheInfamousAlk on 2014-07-17
Sorry, I forgot a question mark in the title.

While in the terminal, I enter my password wrong far too often and I want to shame myself into typing it right by insulting myself whenever I get it wrong. How do I change the message that pops up when I enter the wrong password? I have searched the forums, but found nothing.

---

### Post by Mark Phelps on 2014-07-17
> How do I change the message that pops up when I enter the wrong password?

You probably can't -- without access to the source code for that message generating activity, changing the code, recompiling and regenerating the message executable (if that's how it's made).

---

### Post by steeldriver on 2014-07-17
You could enable the **built-in insults **- it won't allow you to customize the message catalog AFAIK (at least, not without recompiling sudo from source), but at least it will change the messages up

```

sudo visudo

```

and add 'insults' to the list of Defaults e.g.

```

Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
**Defaults        insults**

```

Then

```

$ sudo -K
$ 
$ sudo ls /root
[sudo] password for steeldriver:
**Have you considered trying to match wits with a rutabaga?**
[sudo] password for steeldriver:
**This mission is too important for me to allow you to jeopardize it.**

```

See [http://ubuntu-tutorials.com/2007/02/18/let-sudo-insult-you-when-you-screw-up/](http://ubuntu-tutorials.com/2007/02/18/let-sudo-insult-you-when-you-screw-up/)

---

### Post by slickymaster on 2014-07-17
> **steeldriver said:**
> You could enable the **built-in insults **- it won't allow you to customize the message catalog AFAIK (at least, not without recompiling sudo from source), but at least it will change the messages up

```

sudo visudo

```

and add 'insults' to the list of Defaults e.g.

```

Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
**Defaults        insults**

```

Then

```

$ sudo -K
$ 
$ sudo ls /root
[sudo] password for steeldriver:
**Have you considered trying to match wits with a rutabaga?**
[sudo] password for steeldriver:
**This mission is too important for me to allow you to jeopardize it.**

```

See [http://ubuntu-tutorials.com/2007/02/18/let-sudo-insult-you-when-you-screw-up/](http://ubuntu-tutorials.com/2007/02/18/let-sudo-insult-you-when-you-screw-up/)

:lolflag:

Thanks for that steeldriver. I must confess that I was completely unaware that **sudo** had that feature available within it.

---

### Post by oldos2er on 2014-07-17
> **steeldriver said:**
> You could enable the **built-in insults ** 

One of the first things I do on a new install!

---

### Post by ajgreeny on 2014-07-17
> **oldos2er said:**
> One of the first things I do on a new install!

And me!
Anyone watching me type my password wrongly is VERY impressed and highly amused.

Stupid I know, but little things please little minds

---

### Post by coldcritter64 on 2014-07-17
> **oldos2er said:**
> One of the first things I do on a new install!

And here. They've been on every linux install I've done in about the last 4 years or so. Love 'em. :D

> ...little things please little minds          Yep. :lol:

---

### Post by sp40140 on 2014-07-17
@ Slickymaster
Ma Man..!!
Good to know.

---

### Post by redbikemaster on 2014-07-18
Oh, this is golden! I just enabled this.

---

