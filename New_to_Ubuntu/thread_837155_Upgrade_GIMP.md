---
title: "Upgrade GIMP?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by dalezjc on 2008-06-22
If I upgrade my version of GIMP using apt-get install gimp, will this overwrite/delete my custom scripts?  If so, is there a better way to upgrade?

Thanks,
Dale

---

### Post by MasterSander on 2008-06-22
I don't think it'll overwrite but you never know of course, back them up first and then upgrade.

---

### Post by billgoldberg on 2008-06-22
> **dalezjc said:**
> If I upgrade my version of GIMP using apt-get install gimp, will this overwrite/delete my custom scripts?  If so, is there a better way to upgrade?

Thanks,
Dale

I doubt it.

But to be sure, back up your folder where the scripts are located.

It could be  /home/username/.gimp

(.gimp, is a hidden folder, press "ctrl + h" to view them)

or

/usr/share/gimp/2.0/scripts

(for the second one, it might be necessary to use "gksudo nautilus" in a terminal)

---

### Post by dalezjc on 2008-06-22
I went to install using sudo apt-get install gimp, but I get this error:

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What does this mean?

thanks
Dale

---

### Post by dalezjc on 2008-06-22
Bump

---

### Post by Nepherte on 2008-06-22
Restart and try again, or close synaptic if it is still open.

---

