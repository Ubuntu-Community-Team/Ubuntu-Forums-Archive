---
title: "Wine"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-12
I'm trying to open Dreamweaver in Wine, and it's not doing anything. I tried going to Configure Wine, but that doesn't open either. I did:

```

sudo apt-get purge wine

```

then

```

sudo apt-get install wine

```

and tried to open configure again, but nothing happened. Any ideas?

---

### Post by Darkade on 2008-06-12
What happens when you run
```

wine ~/.wine/routetodreamwever

```

??

---

### Post by Joeb454 on 2008-06-12
What happens when you run ```
winecfg
``` Do you get any errors?

---

### Post by adobrakic on 2008-06-12
Nevermind, sorry guys, i got this installed. But now I have no clue where it's installed to. :x
any idea where it would go? Also, it didn't ask me where it should be installed to, it just did it.

---

### Post by llama320 on 2008-06-12
after you run winecfg without problems (i.e. wine is working just fine by itself), take a look at this HOWTO run Dreamweaver 8..it does require a windows box though, but it worked flawlessly after I installed on vista.

[http://luiscosio.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps](http://luiscosio.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps)

As an aside, the bullet that talks about Documents and Settings..if you're running vista I don't think that folder exists any longer...in any event, I did without it and Dreamweaver still ran fine :)

Good Luck

EDIT: Sorry, adobrakic responded while I was writing this...but yeah, if anyone's having trouble this is still a great little wiki :D

---

### Post by adobrakic on 2008-06-12
With a "Windows Box," I guess that means a windows version on my computer? Cause I don't have that, I only got ubuntu on here.

---

