---
title: "Compiling GemRB from source, getting undefined reference to `__stack_chk_fail' error."
date: 2014-05-19
forum: Programming Talk
---

### Post by Roman_Z on 2014-05-19
Greetings,

I'm trying to compile the popular BioWare engine simulator, GemRB from source. I have all the dependencies, following the INSTALL instructions. Using g++ and cmake + make.

Everything went fine until I issued the make command and got to 81% of compilation. I get the following error:

```
[ 79%] Built target DirectoryImporter
Linking CXX shared module ../EFFImporter.so
/usr/lib/i386-linux-gnu/libc_nonshared.a(stack_chk_fail_local.oS): In function `__stack_chk_fail_local':
(.text+0x10): undefined reference to `__stack_chk_fail'
collect2: error: ld returned 1 exit status
make[2]: *** [gemrb/plugins/EFFImporter.so] Error 1
make[1]: *** [gemrb/plugins/EFFImporter/CMakeFiles/EFFImporter.dir/all] Error 2
make: *** [all] Error 2
```

I found that this is a new feature built into the newer kernels to avoid stack collision. I also found directions to issue -CFLAGS="-fno-stack-protector -fno-stack-protector-all", but this is for C. How do I issue a similar command for the g++ compiler?! Thanks!

---

### Post by rodriguez-juanmanuel on 2014-09-28
Hello. I've found a workaround to this problem. First, you have to install clang:
Code:
> sudo apt-get install clang-3.5
I don't know why clang works, while gcc doesn't. But, it works.
Then, you have to add some environment variables and start the compilation process from the scratch.:
> 
$ mkdir build
$ cd build
$ export CC=/usr/bin/clang
$ export CXX=/usr/bin/clang++
$ cmake ..
...
$ make
...
$ make install


---

