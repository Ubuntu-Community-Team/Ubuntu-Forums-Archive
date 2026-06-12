---
title: "openhackware"
date: 2007-09-13
forum: Programming Talk
---

### Post by pdunning on 2007-09-13
Hi, I've recently been trying to run debian ppc in qemu on my amd64 kubuntu using qemu.
To run a ppc guest on qemu one must run the qemu-system-ppc program included in the package from synaptic. The package installs fine and the normal setups for x86 and amd64 guests work fine. The version for ppc guests though is missing /usr/share/qemu/ppc_rom.bin. This is a link to ../openhackware/ppc_rom.bin. Open hackware, however is not included in qemu or depended on by it, nor does openhackware exist in the repositories. This problem will not be fixed in gutsy (it seems). Openhackware does however exist as an ubuntu source package, so I decided to make a .deb out of it to solve the problem once and for all and keep my system tidy.

I ran into a few problems though. The tutorial in the ubuntu documentation applies only to edgy and dapper and cannot be used with feisty as dh_make is no longer included in the debhelper package, or any other for that matter.

Can anyone help?

---

### Post by Afishionado on 2007-09-13
```
sudo aptitude install dh-make
```

It seems okay to me. 8-[

---

### Post by pdunning on 2007-09-17
silly me!
What a difference an underscore is compared to a dash!

---

