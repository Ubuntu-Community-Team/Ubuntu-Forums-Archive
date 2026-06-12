---
title: "error while loading shared libraries: libstdc++.so.5:"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by kuzumadam on 2016-09-09
```
ThinkPad-S3-S440:~/SymmRef1.2$ perl addHydrogens.pl 3mge_monomer.pdb
```

And receive the following error:
```

/home/toni/SymmRef1.2/reduce.2.21.030604: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ThinkPad-S3-S440:~/SymmRef1.2$ 
```

I have tried updating as follows:

```
ThinkPad-S3-S440:~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree      
Reading state information... Done
libstdc++5 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-85 linux-headers-3.13.0-85-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-85-generic
  linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-85-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.
ThinkPad-S3-S440:~$ 
```

But I get the same error. I am a newbie but I think the problem is the binary I am calling is 32 bit and I have 64 bit installed? However I cannot seem to download the correct version as I receive the following message:

```
ThinkPad-S3-S440:~/SymmRef1.2$ sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package libstdc++.so.5
E: Couldn't find any package by regex 'libstdc++.so.5'
ThinkPad-S3-S440:~/SymmRef1.2$ 
```

I have obviously looked around different forums and on google but have not been able to find a solution, some of the threads on this seem out of date - can anybody help?

Thanks

---

### Post by howefield on 2016-09-09
Duplicate thread closed.

---

