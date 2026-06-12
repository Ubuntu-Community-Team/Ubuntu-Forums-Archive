---
title: "compiling arrayfire examples: undefined reference to cungtsqr_row_"
date: 2022-05-11
forum: Packaging and Compiling Programs
---

### Post by 3togo on 2022-05-11
```
lsb_release -a
```
[INDENT]No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 22.04 LTS
Release: 22.04
Codename: jammy
[/INDENT]


```
uname -a
```
[INDENT]Linux jc-acer 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux[/INDENT]


```
sudo apt install libarrayfire-*-dev libarrayfire-doc
cp /usr/share/doc/libarrayfire-doc/examples/ . -Rf
cd examples
mkdir build
cd build
cmake ..
make
```
[INDENT]Consolidate compiler generated dependencies of target example_blas_cpu
[ 0%] Linking CXX executable benchmarks/blas_cpu
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `cungtsqr_row_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `zungtsqr_row_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `dgetsqrhrt_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `sgetsqrhrt_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `dorgtsqr_row_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `sorgtsqr_row_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `zgetsqrhrt_'
/usr/bin/ld: /lib/x86_64-linux-gnu/liblapacke.so.3: undefined reference to `cgetsqrhrt_'
collect2: error: ld returned 1 exit status
make[2]: *** [CMakeFiles/example_blas_cpu.dir/build.make:98: benchmarks/blas_cpu] Error 1
make[1]: *** [CMakeFiles/Makefile2:375: CMakeFiles/example_blas_cpu.dir/all] Error 2
make: *** [Makefile:91: all] Error 2[/INDENT]

---

