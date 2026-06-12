---
title: "Problem while running a .c file using BlueZ libs. libbluetooth .so.2 not found"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Raju.88 on 2011-12-02
Hi,
I have installed Ubuntu 10.4. after that I installed only bluez-libs-3.36 typing './configure' and then 'make && make install'. Nothing else I have done. Bluez libs got installed in /usr/local/include. 
Now I have written some .c code(simplescan.c). Tried to compile it by 'gcc -o simplescan simplescan.c -lblietooth' and it got compiled. Now while I am trying to run the simplescan file by './simplescan' its giving some error like '[COLOR=Red]error while loading shared libraries: libbluetooth.so.2: cannot open shared object file: No such file or directory[/COLOR]'. I checked the folder /usr/local/lib. The file libbluetooth.so.2 is there. So what can I do now??
Note: I have not attached any dongle yet. So can that be the problem? Do I need to start any daemon (bluetoothd) before that?:confused:

---

### Post by Raju.88 on 2011-12-05
Hi,
I have installed Ubuntu 10.4. after that I installed only bluez-libs-3.36 typing './configure' and then 'make && make install'. Nothing else I have done. Bluez libs got installed in /usr/local/include. 
Now I have written some .c code(simplescan.c). Tried to compile it by 'gcc -o simplescan simplescan.c -lblietooth' and it got compiled. Now while I am trying to run the simplescan file by './simplescan' its giving some error like '[COLOR=red]error while loading shared libraries: libbluetooth.so.2: cannot open shared object file: No such file or directory[/COLOR]'. I checked the folder /usr/local/lib. The file libbluetooth.so.2 is there. So what can I do now??
Note: I have not attached any dongle yet. So can that be the problem? Do I need to start any daemon (bluetoothd) before that?:confused:

---

