---
title: "How do I share folders on my desktop? I don't have permission?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by twoflatfish on 2008-09-06
This is I think a related question. I am trying to share some folders with other computers on my home network. On the desktop (nautilus, I believe), ..if I 'R' click the folder and click the 'share' option the process is refused because I (the user) do not have permission/privliges to create shares. I can't seem to find any information on this. Can you help?

Thanks 
twoflatfish


> **scorp123 said:**
> First of all, it's not very wise to change the permissions of *ANY* system file without exactly knowing what it does, why it is needed, and what the consequences are. If a file belongs to "root" (which would be the case here!) then you can assume that it is considered being a more or less essential "system file" and your normal user account is not supposed to touch it or mess with it.

Secondly, even if you used "sudo" (DONT DO IT!!) and changed the permissions of that file, you would not get much further. The installation would still fail because your account would still lack the appropriate write permissions into any of the folders where a program's binaries usually get installed into, e.g. /usr/bin ... That location is off limits for normal users as far as writing is concerned (only "root" can save, remove and overwrite programs there!). Same for the /etc folder where usually all config files are stored. Most programs need to store their system-wide configuration there and that too would fail, so the installation would most likely be aborted.

So the lesson here is: To use the desktop, use progams, surf the web ==> use your normal account.

For installing and removing stuff, reconfiguring the system --and *ONLY* for these type of activities!!-- use "root", e.g. via the "sudo" command.

---

### Post by lazyart on 2008-09-06
> **twoflatfish said:**
> This is I think a related question. I am trying to share some folders with other computers on my home network. On the desktop (nautilus, I believe), ..if I 'R' click the folder and click the 'share' option the process is refused because I (the user) do not have permission/privliges to create shares. I can't seem to find any information on this. Can you help?

Thanks 
twoflatfish

No, actually this is a thread hijack.  Create a new thread and you'll get your question answered.

---

### Post by aysiu on 2008-09-06
> **lazyart said:**
> No, actually this is a thread hijack.  Create a new thread and you'll get your question answered.
I've moved the question to its own thread.

---

### Post by BLTicklemonster on 2008-09-06
System>Administration>Users and Groups


Click on unlock, and enter your password.


manage groups, scroll to sambashare, click Properties, put a click mark next to "root".

No Samba installed? You can install it from the repositories.

---

### Post by twoflatfish on 2008-09-07
Sorry...new to the forum

---

### Post by wolfen69 on 2008-09-07
> **BLTicklemonster said:**
> System>Administration>Users and Groups


Click on unlock, and enter your password.


manage groups, scroll to sambashare, click Properties, put a click mark next to "root".

No Samba installed? You can install it from the repositories.

actually, he would probably want to add himself to sambashare and not root.

or just do ```
sudo adduser username sambashare
```

---

### Post by BLTicklemonster on 2008-09-07
The method I mentioned is the only thing that has worked for me.

Well, workED.

Since upgrades, I can't use shares any more, and the printer is inaccessible.

---

