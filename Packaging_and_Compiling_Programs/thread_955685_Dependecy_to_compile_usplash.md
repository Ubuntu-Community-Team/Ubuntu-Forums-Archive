---
title: "Dependecy to compile usplash"
date: 2008-10-22
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2008-10-22
I think I've managed to create a usplash theme, and I'm trying to compile it. make works, but when I do make install I get
```

/usr/bin/install -c -d /usr/lib/usplash
/usr/bin/install -c -m 755 common-usplash-theme.so /usr/lib/usplash/common-usplash-theme.so
update-alternatives --remove usplash-artwork.so /usr/lib/usplash/common-usplash-theme.so 
update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/common-usplash-theme.so 55
update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
find: /lib/modules/2.6.24-21-generic/kernel/drivers/ide: Nessun file o directory
find: /lib/modules/2.6.24-21-generic/kernel/drivers/ata: Nessun file o directory
find: /lib/modules/2.6.24-21-generic/kernel/drivers/block: Nessun file o directory
find: /boot/initrd.img-2.6.24-21-generic.bak: Nessun file o directory
make: *** [install] Error 1

****  Installazione fallita. Creazione del paccheto annullata.

Pulitura in corso.../usr/bin/checkinstall: line 302: [: /home/andrea/Extra/Dropbox/Ready: binary operator expected
OK

Ciao.

```

I think I'm missing something needed to compile, but I don't know what to install. Any ideas?

---

### Post by Steveway on 2008-10-22
You can use the build-dep option of apt-get to get dependecies for compilation.
The syntax should be: sudo apt-get build-dep <appname>

---

### Post by Nonno Bassotto on 2008-10-22
Ok, I'm trying with usplash dependecies, although this is my own theme, so there is no official package. Hope it works :)

---

### Post by Nonno Bassotto on 2008-10-22
Nope... I get the same error. It complains about the files
```

/lib/modules/2.6.24-21-generic/kernel/drivers/ide
/lib/modules/2.6.24-21-generic/kernel/drivers/ata
/lib/modules/2.6.24-21-generic/kernel/drivers/block
/boot/initrd.img-2.6.24-21-generic.bak

```
which are missing. Especially the last one seems what is causing it to stop. Can anyone check for me on packages.ubuntu.com where this files or dir should be available? For some reason I'm not able to connect to the site, I don't know if it is a problem of mine.

---

