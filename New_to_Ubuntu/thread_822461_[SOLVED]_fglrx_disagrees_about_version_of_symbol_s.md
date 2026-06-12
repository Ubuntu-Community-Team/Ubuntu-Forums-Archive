---
title: "[SOLVED] fglrx: disagrees about version of symbol struct_module"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by dynamethod on 2008-06-08
why why why why why why why


dmesg | tail:

Jun  9 01:24:49 darksun kernel: [  101.789235] fglrx: disagrees about version of symbol struct_module


This happend after i upgraded to the .18 kernel, now i get a white screen everytime i log in, wtf? just having a hell of a lot of problems with ubuntu today, now this.


using latest driver from ATi, and dont tell me to use official repo driver, ive used the latest ones all the time no problems, but now i get the white screen of death for what? upgrading my kernel? ffs

---

### Post by dynamethod on 2008-06-08
bah, all i had to do was:

sudo ./ati-driver-installer-8-5-x86.x86_64.run

and it sorted itself out, phew thats one down on the burn list

---

