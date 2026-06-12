---
title: "&quot;dpkg --configure -a&quot; hangs!"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by cmSthlm on 2008-08-10
I tried to install a language pack, language-pack-sv-base, with Synaptic. This made Synaptic hang. Now when I open Synaptic, I get:

[PHP]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/PHP]

I run this command but it just never finishes. So I'm very stuck. I cannot uninstall anything and I cannot finish the installation...

Any ideas what could be the problem?

Thanks in advance

---

### Post by Ryadt on 2008-08-10
Type in terminal```
sudo dpkg --configure -a 
```

---

### Post by Martje_001 on 2008-08-10
> **cmSthlm said:**
> I run this command but it just never finishes. So I'm very stuck. I cannot uninstall anything and I cannot finish the installation..
What's the output?

---

### Post by cmSthlm on 2008-08-10
The output is:

```
Setting up language-pack-sv-base (1:7.10+20080205) ...
Generating locales...
  sv_FI.UTF-8... 
```

it seems to be getting nowhere...

---

### Post by Martje_001 on 2008-08-11
Just wait. It takes a long time..

---

### Post by cmSthlm on 2008-08-11
I have let it run for several hours now. It uses 99% of one of my CPU:s.

---

### Post by hyper_ch on 2008-08-11
> **cmSthlm said:**
> I have let it run for several hours now. It uses 99% of one of my CPU:s.

This doesn't sound good except if you have a really, really, really slow processor upon which the installation also took several hours.

---

### Post by cmSthlm on 2008-08-11
No, I have a Dell Inspiron 6400 and I have never had any of this before...

I could just skip this language pack but it's quite annoying. It was even a recommended update in the update manager.

---

### Post by emvy on 2008-08-30
hey, same problem here. plz help!!!

---

### Post by Nepherte on 2008-08-30
When the process of reconfiguring seems to hang, try pressing enter. Sometimes that helps.

---

