---
title: "Errors installing gcc-4.5.0 on lucid  lynx"
date: 2010-06-24
forum: Packaging and Compiling Programs
---

### Post by sirishy2k on 2010-06-24
I was able to configure gcc-4.5.0 and had no problems with it but when i execute make, this is what happens

make[5]: Entering directory `/home/bullhound/Desktop/gcc-4.5.0/host-i686-pc-linux-gnu/64/zlib'
make[5]: *** No rule to make target `all'.  Stop.
make[5]: Leaving directory `/home/bullhound/Desktop/gcc-4.5.0/host-i686-pc-linux-gnu/64/zlib'
make[4]: *** [multi-do] Error 1
make[4]: Leaving directory `/home/bullhound/Desktop/gcc-4.5.0/host-i686-pc-linux-gnu/zlib'
make[3]: *** [all-multi] Error 2
make[3]: Leaving directory `/home/bullhound/Desktop/gcc-4.5.0/host-i686-pc-linux-gnu/zlib'
make[2]: *** [all-stage1-zlib] Error 2
make[2]: Leaving directory `/home/bullhound/Desktop/gcc-4.5.0'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/bullhound/Desktop/gcc-4.5.0'
make: *** [all] Error 2

and I am attaching the config.log file

---

### Post by sirishy2k on 2010-06-24
I used the following command for make.
```

 sudo make -j 2 all-gcc
```

no errors where encountered for make 

and used this command for install
```
sudo make install-gcc
```
I got this error for install

make[1]: *** No rule to make target `../libcpp/libcpp.a', needed by `cc1-dummy'.  Stop.
make[1]: Leaving directory `/home/bullhound/Desktop/gcc-4.5.0/host-i686-pc-linux-gnu/gcc'
make: *** [install-gcc] Error 2

---

