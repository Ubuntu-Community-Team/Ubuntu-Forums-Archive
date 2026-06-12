---
title: "Can`t install Lazarus &amp; free pascal compiler"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by ^^viktor^^ on 2008-05-17
I was trying to install free pascal compiler and  Lazarus. I sussesfully installed the compiler, but when I tried to build the source it says this..
> make: -iVSPTPSOTO: Command not found
make: -iSP: Command not found
make: -iTP: Command not found
make: -iSO: Command not found
make: -iTO: Command not found
make compiler_cycle RELEASE=1
make[1]: -iVSPTPSOTO: Command not found
make[1]: Entering directory `/home/viktor/Desktop/fpc'
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make -C compiler cycle
make[2]: -iVSPTPSOTO: Command not found
make[2]: Entering directory `/home/viktor/Desktop/fpc/compiler'
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make tempclean ppc3.exe
make[3]: -iVSPTPSOTO: Command not found
make[3]: Entering directory `/home/viktor/Desktop/fpc/compiler'
make[3]: -iSP: Command not found
make[3]: -iTP: Command not found
make[3]: -iSO: Command not found
make[3]: -iTO: Command not found
/bin/rm -f ppcross ppc ppc1.exe ppc2.exe ppc3.exe ./msg2inc.exe
make 'OLDFPC=' next
make[4]: -iVSPTPSOTO: Command not found
make[4]: Entering directory `/home/viktor/Desktop/fpc/compiler'
make[4]: -iSP: Command not found
make[4]: -iTP: Command not found
make[4]: -iSO: Command not found
make[4]: -iTO: Command not found
make rtlclean rtl
make[5]: -iVSPTPSOTO: Command not found
make[5]: Entering directory `/home/viktor/Desktop/fpc/compiler'
make[5]: -iSP: Command not found
make[5]: -iTP: Command not found
make[5]: -iSO: Command not found
make[5]: -iTO: Command not found
make -C  clean
make: Entering an unknown directory
make: *** clean: No such file or directory.  Stop.
make: Leaving an unknown directory
make[5]: *** [rtlclean] Error 2
make[5]: Leaving directory `/home/viktor/Desktop/fpc/compiler'
make[4]: *** [next] Error 2
make[4]: Leaving directory `/home/viktor/Desktop/fpc/compiler'
make[3]: *** [ppc1.exe] Error 2
make[3]: Leaving directory `/home/viktor/Desktop/fpc/compiler'
make[2]: *** [cycle] Error 2
make[2]: Leaving directory `/home/viktor/Desktop/fpc/compiler'
make[1]: *** [compiler_cycle] Error 2
make[1]: Leaving directory `/home/viktor/Desktop/fpc'
make: *** [build-stamp.-] Error 2

What`s happening wrong?:confused:

---

### Post by kellemes on 2008-05-17
The compiler is written in pascal, not in C. And so you need the binary version of the compiler to compile it. ;-)
Why not install through your package manager?
```
sudo apt-get install lazarus
```
(It'll grab the compiler because it's depending on it.)

---

