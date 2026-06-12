---
title: "sys/socket.h: No such file or directory when compile module program"
date: 2014-07-23
forum: Programming Talk
---

### Post by zerop2 on 2014-07-23
how to use sys/socket.h in module program

or

if can not use sys/socket.h
does it mean that have to use snull_tx and snull_rx? 
if snull_tx is layer 2, does it mean that i call the source code template in oreilly linux device drive first edition, 
then another side of computer can receive this in snull_rx in module?

wonder@wonder-VirtualBox:~/layer$ sudo make -C /usr/src/linux-headers-3.8.0-29-generic cli.c M=/home/wonder/layer modules
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
make: Nothing to be done for `/home/wonder/layer/cli.c'.
  CC [M]  /home/wonder/layer/cli.o
/home/wonder/layer/cli.c:2:0: warning: "MODULE" redefined [enabled by default]
<command-line>:0:0: note: this is the location of the previous definition
/home/wonder/layer/cli.c:5:24: fatal error: sys/socket.h: No such file or directory
compilation terminated.
make[1]: *** [/home/wonder/layer/cli.o] Error 1
make: *** [_module_/home/wonder/layer] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'

---

### Post by zerop2 on 2014-08-02
solved by not using this

---

