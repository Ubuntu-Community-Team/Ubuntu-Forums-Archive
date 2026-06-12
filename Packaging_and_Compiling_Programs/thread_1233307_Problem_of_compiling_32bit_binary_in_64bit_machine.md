---
title: "Problem of compiling 32bit binary in 64bit machine"
date: 2009-08-06
forum: Packaging and Compiling Programs
---

### Post by carfield on 2009-08-06
I following this guide, [https://developer.mozilla.org/en/Compiling_32-bit_Firefox_on_a_Linux_64-bit_OS](https://developer.mozilla.org/en/Compiling_32-bit_Firefox_on_a_Linux_64-bit_OS) , I get the following error, I guess I missing some package for gcc to compile 32bit binary, anyone know what is it? I am using ubuntu 9

configure: error: Library requirements (gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 glib-2.0 gobject-2.0 gdk-x11-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

But all *.pc are exist at /usr/lib/pkgconfig .... any idea? I've asked at [http://forums.mozillazine.org/viewtopic.php?f=42&t=1395275&p=7159455&sid=24d225d7d17ab68cd71c383d72a2b776#p7159455](http://forums.mozillazine.org/viewtopic.php?f=42&t=1395275&p=7159455&sid=24d225d7d17ab68cd71c383d72a2b776#p7159455) , some suggest I should install *.i386 package, but those are not able to find in synaptic

---

### Post by Grishka on 2009-08-06
do you have [ia32-libs](apt://ia32-libs) installed? also, you'll need the [gcc-multilib](apt://gcc-multilib) package.

---

### Post by carfield on 2009-08-06
thx, have all installed... but still have problem....

---

### Post by Grishka on 2009-08-06
maybe try changing 'ac_add_options --x-libraries=/usr/lib' to 'ac_add_options --x-libraries=/usr/lib32'.

---

### Post by carfield on 2009-08-08
Yes,that help

---

