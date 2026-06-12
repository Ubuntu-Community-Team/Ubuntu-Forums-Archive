---
title: "undefined reference to `gpg_strerror'"
date: 2007-06-16
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-16
I am trying to compile 'libgcrypt', but I get this error: 

Can you please tell  tell me how to fix it? I have download, make, install libgpg-error-1.5, but it does not help.

```

i486-linux-gnu-gcc -I/home/scheung/src/vlc-trunk/extras/contrib/include -I/home/scheung/src/vlc-trunk/extras/contrib/include -isystem /home/scheung/src/vlc-trunk/extras/contrib/include -Wall -o .libs/basic basic.o  -L/home/scheung/src/vlc-trunk/extras/contrib/lib ../src/.libs/libgcrypt.so -lnsl -Wl,--rpath -Wl,/home/scheung/src/vlc-trunk/extras/contrib/lib
basic.o: In function `check_cbc_mac_cipher':
basic.c:(.text+0x3b3): undefined reference to `gpg_strerror'
basic.c:(.text+0x4ed): undefined reference to `gpg_strerror'
basic.c:(.text+0x568): undefined reference to `gpg_strerror'
basic.c:(.text+0x67f): undefined reference to `gpg_strerror'
basic.o: In function `check_aes128_cbc_cts_cipher':
basic.c:(.text+0xb59): undefined reference to `gpg_strerror'
basic.o:basic.c:(.text+0xbb0): more undefined references to `gpg_strerror' follow
collect2: ld returned 1 exit status
make[5]: *** [basic] Error 1
make[5]: Leaving directory `/home/scheung/src/vlc-trunk/extras/contrib/src/libgcrypt/tests'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/scheung/src/vlc-trunk/extras/contrib/src/libgcrypt'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/scheung/src/vlc-trunk/extras/contrib/src/libgcrypt'
make[2]: *** [.gcrypt] Error 2
make[2]: Leaving directory `/home/scheung/src/vlc-trunk/extras/contrib/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/home/scheung/src/vlc-trunk/extras/contrib'
make: *** [all] Error 2


```

---

### Post by nitro_n2o on 2007-06-17
Try 

```
 sudo apt-get install libgpg-error-dev
```

---

### Post by yinglcs2 on 2007-06-17
It said it is already installed :

```
$  sudo apt-get install libgpg-error-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgpg-error-dev is already the newest version.
libgpg-error-dev set to manual installed.
The following packages were automatically installed and are no longer required:
  xaw3dg liblockfile1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
```

---

### Post by nitro_n2o on 2007-06-18
Make sure that libgcrypt and configured...
```
  libgcrypt-config --libs
```
But, you don't really have to compile it... i know you'll miss the fun, but get from the repos... 

```
sudo apt-get install libgcrypt
```

---

