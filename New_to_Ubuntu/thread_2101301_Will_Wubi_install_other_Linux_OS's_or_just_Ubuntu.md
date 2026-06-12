---
title: "Will Wubi install other Linux OS's or just Ubuntu?"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by HernanLinux93 on 2013-01-04
Hi everyone, well the titles says it all ...Will Wubi install other Linux OS's or just Ubuntu? since I want to triple boot my computer with another linux distro that being Fedora . :p

---

### Post by Mark Phelps on 2013-01-04
Wubi stands for Windows Ubuntu Installer -- so no, it doesn't work with other Linux distros.

---

### Post by audiomick on 2013-01-04
> **HernanLinux93 said:**
> ... since I want to triple boot my computer with another linux distro...

I think if you are up to that stage, then it is also time to move beyond WUBI and learn how to do a proper dual-boot, or in your case mult-boot install. WUBI was only ever intended for looking at Ubuntu long enough to decide if you want to use it for real or not.

Incidentally, I believe it is a good idea to install RH branch distros before Ubuntu. I can recall reading that somewhere, but I don't know where, and it was a while ago. You should check up on that, though.

---

### Post by offgridguy on 2013-01-04
> 

I think if you are up to that stage, then it is also time to move beyond  WUBI and learn how to do a proper dual-boot, or in your case mult-boot  install. WUBI was only ever intended for looking at Ubuntu long enough  to decide if you want to use it for real or not.  
Agreed

---

### Post by Frogs Hair on 2013-01-04
There is/was a Ubuntu only project  known as Lubi and it is most likely out dated and not usable.(2007) Jolicloud has a Windows installer but I think it is a cloud based operating system. The dual/ triple boot would be the only way to have a choice about what you install.

---

### Post by cmcanulty on 2013-01-04
I think you could do xubuntu or lubuntu by using wubi to install ubuntu then from within ubuntu just install lubuntu or xubuntu desktops from synaptic (or any other ubuntu supported desktop environment)

---

### Post by monkeybrain2012 on 2013-01-04
The answer is no. Wubi is for trying out Ubuntu in Windows. If you truly want to use Linux, give it its own partition instead of running it off a folder in Windows. Triple boot or multiple boot is not difficult once you know how to set up a real dual boot (with Linux's own partition), idea is the same.

---

### Post by monkeybrain2012 on 2013-01-04
> **audiomick said:**
> 

Incidentally, I believe it is a good idea to install RH branch distros before Ubuntu. I can recall reading that somewhere, but I don't know where, and it was a while ago. You should check up on that, though.

I am not sure what you mean by that. I have been dual booting between Ubuntu and Fedora (and have at one point a triple boot with another Fedora based distro) for a while and Ubuntu was set up first. You just need to be careful not to install the bootloader when installing Fedora.

---

### Post by audiomick on 2013-01-04
> **monkeybrain2012 said:**
> I am not sure what you mean by that. I have been dual booting between Ubuntu and Fedora (and have at one point a triple boot with another Fedora based distro) for a while and Ubuntu was set up first.[COLOR="Red"] You just need to be careful not to install the bootloader when installing Fedora.[/COLOR]

That last bit is probably the solution to the problem I had read about. As I said, it was a while ago, so I am a bit hazy. I can remember reading about people installing RH branch OS's to mult-boot setups, and having the grub obliterated in the previously working setup. Not installing the RH bootloader would, of course, avoid that.

---

### Post by newb85 on 2013-01-04
Genuine question (not an argument):
Wouldn't running grub-update from within Ubuntu put GRUB back?  I've never tried it, but I would expect one could run grub-update from a Live session, if it isn't possible to boot the Ubuntu partition.  (For that matter, I'd imagine that running Yann's boot-repair would fix the problem, as well.)

---

### Post by monkeybrain2012 on 2013-01-04
> **audiomick said:**
> That last bit is probably the solution to the problem I had read about. As I said, it was a while ago, so I am a bit hazy. I can remember reading about people installing RH branch OS's to mult-boot setups, and having the grub obliterated in the previously working setup. Not installing the RH bootloader would, of course, avoid that.


Oh almost forget, if you set up a multiple boot like this (with one Linux controlling grub) then whenever you have a kernel update in the others you always have to update grub in your first distro.

---

### Post by audiomick on 2013-01-04
> **newb85 said:**
> Genuine question (not an argument):
Wouldn't running grub-update from within Ubuntu put GRUB back?  I've never tried it, but I would expect one could run grub-update from a Live session, if it isn't possible to boot the Ubuntu partition.  (For that matter, I'd imagine that running Yann's boot-repair would fix the problem, as well.)

If I remember rightly, the existing boot loader was overwritten  and replaced by one that didn't see the other Linux install. I can't remember very well. Oh, and at the time, Yann's boot repair thingy was far in the future...

---

