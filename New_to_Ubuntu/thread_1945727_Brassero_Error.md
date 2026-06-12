---
title: "Brassero Error"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by johnaaronrose on 2012-03-23
I'm trying to burn a CD from the iso for Ubuntu 10.04.4.

I've tried cdrecord -fix -dev=/dev/dvdrw, cdrecord -fix -dev=/dev/cdrw & cdrecord -fix -dev=/dev/cdrom afterwards. They all give 'Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.' (or similar) repeatedly. Any ideas?

I looked on Launchpad bugs & there's a 2010 bug about brasero & wodim: if I understand it correctly, the problem is with wodim.
Any other solution?

---

### Post by d4m1r on 2012-03-23
> **johnaaronrose said:**
> I'm trying to burn a CD from the iso for Ubuntu 10.04.4.

I've tried cdrecord -fix -dev=/dev/dvdrw, cdrecord -fix -dev=/dev/cdrw & cdrecord -fix -dev=/dev/cdrom afterwards. They all give 'Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.' (or similar) repeatedly. Any ideas?

I looked on Launchpad bugs & there's a 2010 bug about brasero & wodim: if I understand it correctly, the problem is with wodim.
Any other solution?

Brasero causes numerous weird issues....K3B is the better free alternative, but Nero (linux version) is actually the best of the best as I've used all 3. But the full version isn't free.

---

### Post by flemur13013 on 2012-03-23
I replaced brasero with gnomebaker from the repositories.

---

### Post by Cheesemill on 2012-03-23
Xfburn is another alternative.

---

### Post by nothingspecial on 2012-03-23
Question moved out of old thread.

---

