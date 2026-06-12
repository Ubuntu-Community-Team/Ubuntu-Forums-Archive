---
title: "[SOLVED] i installed openoffice 3, need advice"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-10-16
i installed the new openoffice 3.0 from here: [http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/]("http://www.quicktweaks.com/2008/10/11/install-openoffice-30-final-in-ubuntu/").

it works fine but how would i be able to do updates ? the update feature in openoffice won't connect, will ubuntu automatically do necessary updates ?

---

### Post by zzHanks on 2008-10-16
The updates are included in Ubuntu update manager, so you don't have to think about it.

[B]Edit: I see now that version 3 is not in the Package Manager yet, so it probably won't update until it is.

[/B]Personally I would just install it from the OpenOffice site or Package Manager (unless you really need version 3).

---

### Post by smooth3006 on 2008-10-16
> **zzHanks said:**
> The updates are included in Ubuntu update manager, so you don't have to think about it.

[B]Edit: I see now that version 3 is not in the Package Manager yet, so it probably won't update until it is.

[/B]Personally I would just install it from the OpenOffice site or Package Manager (unless you really need version 3).

doesn't matter if i download from the oo site or the one i went to, i don't think it will update until ubuntu releases it officially.

---

### Post by smooth3006 on 2008-10-16
i found the fix for it :


for people using ubuntu hardy
add this to your repos..
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

update it using sudo apt-get update

or follow this guide :[http://www.tectonic.co.za/?p=3363]("http://www.tectonic.co.za/?p=3363")

---

### Post by poet_imp on 2008-10-17
These ppa's appear to be for Intrepid only. The hardy package is empty.

---

