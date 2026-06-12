---
title: "Idiotic changes to filesystem layout."
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Eamonn65 on 2011-09-20
This change from the technical overview of beta 1 has got me mad enough to register and complain.

> Ubuntu 11.10 has migrated away from /var/run, /var/lock and /dev/shm and  now uses /run, /run/lock and /run/shm instead (respectively). While the  Ubuntu AppArmor packages and shipped policy have been adjusted for  this, custom policy may need to be updated. The following may be used to  aid in migration (it allows both the old an the new paths):

Really? this is an absolutely idiotic change that serves no purpose.

Why deviate from the LSB? 

New linux systems admins are going to buy books only to find out that Ubuntu does things differently. 

The more Ubuntu advances the more it seems to give the middle finger to the broader Linux community. 

Seriously can someone defend this change that makes it so important to break standards?

---

### Post by dino99 on 2011-09-20
everything is relative, even "standard" change along time :(

---

### Post by sumski on 2011-09-20
This is upstream , complain to them:
[http://lwn.net/Articles/436012/](http://lwn.net/Articles/436012/)

[http://wiki.debian.org/ReleaseGoals/RunDirectory](http://wiki.debian.org/ReleaseGoals/RunDirectory)

---

### Post by MacUntu on 2011-09-20
Definitely invented by Ubuntu. LOL

---

### Post by madjr on 2011-09-20
where you get this info from?

also where are the bug reports and/or blueprints for the change?

i dont see anything wrong as long as it's justified change.

Also people need to stop thinking that all linux need to be equal.

if i want to learn gentoo i look for (or purchase if necessary) a gentoo guide/book. If i want to learn ubuntu i look for ubuntu. If i want to learn the kernel i look for "linux".

i hope you **dont freak out**:
[http://www.gobolinux.org/](http://www.gobolinux.org/)

---

### Post by madjr on 2011-09-20
> **sumski said:**
> This is upstream , complain to them:
[http://lwn.net/Articles/436012/](http://lwn.net/Articles/436012/)

[http://wiki.debian.org/ReleaseGoals/RunDirectory](http://wiki.debian.org/ReleaseGoals/RunDirectory)

thanks for the articles!

if systemd needs it then its already justified.

i love systemd, cant wait to have it on ubuntu!

---

### Post by madjr on 2011-09-20
> .....The only reason why nobody dared to actually
implement such a directory was unwillingness to deal with the [B]political
backlash[/B], especially messy discussions on mailing lists like this one.

Understanding this, we came to the conclusion that we should rather
implement what everybody thinks is the right technical solution, instead
of evading the political backlash for it. And so we implemented this.

With this upload Fedora and Suse have already adopted /run now. Debian
folks will suggest this for their coming release. Ubuntu has agreed with
introducing /run as well.

Dracut, udev and systemd have already been updated upstream to make use
of /run. We expect mdadm and mount to follow suit quickly.

[B]A few years back Debian folks already suggested introduction of /run,
and even pinged LSB folks about this, and back then there even was a vaguely
positive response from them[/B].

[...]

sorry to say it, but if LSB doesnt like it, they can s*** it.

---

### Post by thatguruguy on 2011-09-20
> **Eamonn65 said:**
> 
Seriously can someone defend this change that makes it so important to break standards?

I think this quote from the LWN.net citation given earlier sums it up quite nicely: 
**"runtime data is not a device node"**

As an aside, I think it's really neat when some gets "mad enough to register and complain", and then logs off before a full explanation for the change is provided.

---

### Post by coffeecat on 2011-09-20
Thank you for participating, everyone.

Thread closed.

---

