---
title: "How to change admin password?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by RachelFaith on 2008-05-28
I have a new server from OVH. It came with a default admin name and some random password.

I am slightly a novice, but I do know some linux stuff.

I have tried to change this default password 5 times 5 different ways.

I reboot and everytime, I can still only log in with the default.

I can sudo reboot or ssh only with the OLD random password, not the one I have tried to change it to 5 times.

I cannot get into it directly, only remotely as it is located in France many miles from me.

What do I need to do to change this generic user admin's password?

Thanks so much.

---

### Post by quelx on 2008-05-28
Are you talking about [http://www.ovh.co.uk/](http://www.ovh.co.uk/) hosting?

if ```
passwd
``` after you ssh into the box is not changing the password you should probably contact their support group.

[http://www.ovh.co.uk/customerspace/support/technical.xml](http://www.ovh.co.uk/customerspace/support/technical.xml)

---

### Post by RachelFaith on 2008-05-28
That's normally a good idea, but, since that took 3 weeks to set up a 72 hour server... I thought Id try my chances here.

Yes I have done sudo passwd root and it still does not change.

Is it just a bug and I have to wait for them?

Ugh !

---

### Post by sayakb on 2008-05-28
Try:
```
sudo bash
passwd
```

---

### Post by The Cog on 2008-05-28
I thought you were trying to change your own password. 
**passwd**
will change your login password, while
**sudo passwd**
will change root's password.

---

