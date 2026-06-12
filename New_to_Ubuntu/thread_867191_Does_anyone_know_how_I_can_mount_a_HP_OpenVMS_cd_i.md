---
title: "Does anyone know how I can mount a HP OpenVMS cd in Ubuntu?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Ice Dragon on 2008-07-22
Does anyone know how I can mount a HP OpenVMS cd in Ubuntu?

Thanks

---

### Post by Ice Dragon on 2008-07-23
bump, anyone?

---

### Post by anewguy on 2008-07-23
If the Cd does not mount when loaded, try the following:

make a temporary directory:

cd ~ <enter>  get to your home directory

mkdir cdtemp <enter>

sudo mount /media/cdrom cdtemp

now see if you can navigate to cdtemp.

---

