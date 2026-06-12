---
title: "unable to rum matlab exe in ubuntu"
date: 2010-06-22
forum: Programming Talk
---

### Post by bilol on 2010-06-22
Dear all,
I have created a function file 'urfun.m' in Matlab.Then I have mada its exe. When I run the exe within Matlab by issuing the command *system('/urfun') * it is running well , but when I tried to run it from command line it gives the following error

```
dhiman@dhiman-desktop:~$ ./urfun
./urfun: error while loading shared libraries: libmwmclmcrrt.so: cannot open shared object file: No such file or directory

```

Then I find libmwmclmcrrt.so by using :
```
dhiman@dhiman-desktop:~$ find /opt/Matlab/ -name "libmwmcl*"
/opt/Matlab/bin/glnx86/libmwmclmcr.so
/opt/Matlab/runtime/glnx86/libmwmclmcrrt.so
/opt/Matlab/runtime/glnx86/libmwmclmcrrt.so.7.13
/opt/Matlab/runtime/glnx86/libmwmclmcrrt.so.7.13.csf
```

and add the path to LD_LIBRARY_PATH by :
```
export LD_LIBRARY_PATH=/opt/Matlab/runtime/glnx86/libmwmclmcrrt.so
```

But still I am getting the following error as above :

```
dhiman@dhiman-desktop:~$ ./urfun
./urfun: error while loading shared libraries: libmwmclmcrrt.so: cannot open shared object file: No such file or directory

```

Any help will be highly appreciated....

---

### Post by Zugzwang on 2010-06-22
> **bilol said:**
> 
and add the path to LD_LIBRARY_PATH by :
```
export LD_LIBRARY_PATH=/opt/Matlab/runtime/glnx86/libmwmclmcrrt.so
```


You should export the path and not the file. So try instead:
```
export LD_LIBRARY_PATH=/opt/Matlab/runtime/glnx86
```
Probably you need a trailing "/".

---

