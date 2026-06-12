---
title: "readelf -d gives different output for the same c++ shared folder"
date: 2017-12-05
forum: Packaging and Compiling Programs
---

### Post by dk1979 on 2017-12-05
[COLOR=#242729][FONT=Arial]Hi
I have created a c++ app that needs avro c++ shared library. Also one need to install also boost specific libraries for the avro to be built
. In a Ubuntu 16.04 VM I have built the library boost 1.63 and then I created the libavro 1.8.1. I have two ubuntu 16.04 VMs where in the one
I have built the libraries and in the other I want to test my c++ app with the needed shared libraries wihtout having to install anything.
The strange thing is on the Ubuntu where the libraries are built when I give:
[/FONT][/COLOR]```
readelf -d libavrocpp.so.1.8.1.0  
```
in /usr/local/lib I get the following :
```
Dynamic section at offset 0xf9100 contains 28 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libboost_iostreams.so.1.63.0]

```

while when I transfer the c++ app with the shared libraries (libboost_iostreams.so.1.63.0 and libavrocpp.so.1.8.1.0)  on the new VM and give the same command on libavrocpp.so.1.8.1.0 I get the following:
```
Dynamic section at offset 0xf9100 contains 28 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libboost_iostreams.so.1.62.0]
```

Even though the libboost_iostreams.so.1.62.0 exist neither in the system nor in the additional shared libraries.

On the second VM [COLOR=#242729][FONT=Arial]I install the c++ on /usr/bin and the libraries  on a folder lib in /usr/share and then update the /etc/ld.so.conf so that it can find the new libraries.
I also tried to [/FONT][/COLOR]export LD_LIBRARY_PATH=/usr/share/lib but every time I try to run my c++ app I get the following error:
```

[COLOR=#242729][FONT=Arial]"while loading shared libraries: libboost_iostreams.so.1.62.0: cannot open shared object file: No such file or directory"[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

What am I doing wrong?[/FONT][/COLOR]

---

