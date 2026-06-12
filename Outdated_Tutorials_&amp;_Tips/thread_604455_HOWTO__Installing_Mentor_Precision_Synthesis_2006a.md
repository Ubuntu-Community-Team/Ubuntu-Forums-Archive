---
title: "HOWTO : Installing Mentor Precision Synthesis 2006a update 1"
date: 2007-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Euripide on 2007-11-06
The following HOWTO is aimed at installing mentor precision synthesis on Ubuntu 7.10

Step 1 : Download install_linux.bin

Step 2 : Allow install_linux.bin to be started

```
chmod 755 install_linux.bin
```

Step 3 : If you start install_linux.bin now, you should get the following error message :
[...] error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
We have to remove LD_ASSUME_KERNEL from the script :
```
cp install_linux.bin install_linux.bin.bak
cat install_linux.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" >  install_linux.bin
rm  install_linux.bin.bak
```

Step 4 : Run  install_linux.bin as root :
```
sudo install_linux.bin
```

Step 5: Now we should remove also all these LD_ASSUME_KERNEL from the precision executable :
```
cp [Precision Install Directory]/Mgc_home/bin/precision /tmp/precision.bak
cat /tmp/precision.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > /tmp/precision
sudo cp /tmp/precision   [Precision Install Directory]/Mgc_home/bin/precision 
rm /tmp/precision*
cp [Precision Install Directory]/Mgc_home/bin/ucf2mgc /tmp/ucf2mgc.bak
cat /tmp/ucf2mgc.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > /tmp/ucf2mgc
sudo cp /tmp/ucf2mgc  [Precision Install Directory]/Mgc_home/bin/ucf2mgc 
rm /tmp/ucf2mgc*
  
```                                           

It should now work fine !

---

