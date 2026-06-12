---
title: "Native Eclipse for Ubuntu?"
date: 2005-06-21
forum: Programming Talk
---

### Post by benguin on 2005-06-21
Hi there,
I had a few question about Eclipse's future in Ubuntu, if there's any. Fedora Core 4 has shipped with Eclipse 3.x natively compiled RPMS, and I believe that's the basic development environment Fedora is pushing. I use Eclipse for C++ work, and I've been quite impressed so far. I won't go too much into the details about Eclipse and the C/C++ Development Tools, but I was wondering if there is any plans of packaging a gcj-compiled version of Eclipse with Ubuntu Breezy. I know there KDevelop for KDE users but I feel comfortable with GNOME. Anjuta 2.0 looks very promising but still very unstable and buggy. It's just a curiousity, and I thought I'd ask the forums about it. The natively-compiled version of Eclipse supposedly is quicker, and not as memory hungry as the VM-executed version; I haven't had the chance to test that claim, but that's the word these days.

If anyone knows where I could find (unsupported) deb packages for a natively-compiled Eclipse version, that'd be great. I can always use alien on Fedora packages but that's my last option.

Thanks a ton in advance, everyone. To the Ubuntu team, keep up all the magnificent work!

-J-

---

### Post by LordHunter317 on 2005-06-21
The last time I used a natively-compiled version of eclipse, it was significantly less stable than one run via vm.  I've yet to have reliable results with gcj compiled code.

I'd just as soon not see a natively compiled one.  For Java development, you have to have a VM anyway, so the value quickly diminishes.

---

### Post by crapufish on 2006-05-26
Any news about a native pre-compilled Eclipse?

---

### Post by daneel_olivaw on 2006-05-26
Did you try this?
```
sudo apt-get update
sudo apt-get install eclipse
```

I did like that, successfully.

---

### Post by orlox on 2006-05-27
I recently been giving a try to Fedora Core 4, that comes with a native eclipse. It's really faster that any other eclipse I had tested on any OS. But it suddenly started to get some weird bugs I couldnt solve...

---

### Post by cabezon on 2006-08-09
I got eclipse gcj from the repos (ubuntu breazy x86_64)and eclipse is not working with the gcj virtual machine. Is it supposed to work with gcj vm, right?

Anyways, it sums up to this on some log:

!ENTRY org.eclipse.osgi 2006-08-10 00:08:24.349
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar[/email] [23] was not resolved.

thanks
cabezon #2

---

