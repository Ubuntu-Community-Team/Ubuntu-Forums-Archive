---
title: "[SOLVED] Can't install AVLD"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by shoot2kill on 2008-11-20
i have tried downloading to desktop
extracting the files.

CDing to the dir

sudo make && make install

then i get the following

```

gav@gav-desktop:~$ cd Desktop/avld_0.1.4/
gav@gav-desktop:~/Desktop/avld_0.1.4$ sudo make && make install
[sudo] password for gav: 
make -C /lib/modules/2.6.27-8-generic/build M=/home/gav/Desktop/avld_0.1.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-8-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-8-generic'
make -C /lib/modules/2.6.27-8-generic/build M=/home/gav/Desktop/avld_0.1.4 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-8-generic'
mkdir: cannot create directory `/lib/modules/2.6.27-8-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-8-generic'
make: *** [install] Error 2
gav@gav-desktop:~/Desktop/avld_0.1.4$ 

```

any help apreciated..

link to instructions.. [http://allonlinux.free.fr/Projets/AVLD/](http://allonlinux.free.fr/Projets/AVLD/)

---

### Post by taurus on 2008-11-20
```
sudo make && **sudo** make install
```

---

### Post by shoot2kill on 2008-11-20
d'oh.. thanks mate (Y)

---

