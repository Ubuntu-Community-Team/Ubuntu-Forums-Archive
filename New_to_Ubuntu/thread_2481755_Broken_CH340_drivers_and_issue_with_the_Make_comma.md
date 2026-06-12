---
title: "Broken CH340 drivers and issue with the Make command"
date: 2022-12-08
forum: New to Ubuntu
---

### Post by carterk on 2022-12-08
Having a hell of a time trying to get my machine to talk to any device with a CH340 serial IC

Seems that any help thread I follow fails at some point, mostly when I attempt to run the make file/command/whatever.
I've just followed these steps, as describers here: [https://gist.github.com/dattasaurabh82/082d13fd61c0d06c7a358c5e605ce4fd](https://gist.github.com/dattasaurabh82/082d13fd61c0d06c7a358c5e605ce4fd)
[LIST=1]
[*]get the latest kernel 
[*]install build tools 
[*]git clone the CH340 drivers 
[/LIST]

but the "make" results in this -

```
~/CH341SER$ sudo make
make -C /lib/modules/6.0.9-060009-generic/build  M=/home/carterk/CH341SER 
make[1]: Entering directory '/usr/src/linux-headers-6.0.9-060009-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.2.0-9ubuntu1) 12.2.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0
  CC [M]  /home/carterk/CH341SER/ch34x.o
gcc: error: unrecognized command-line option ‘-ftrivial-auto-var-init=zero’
make[2]: *** [scripts/Makefile.build:249: /home/carterk/CH341SER/ch34x.o] Error 1
make[1]: *** [Makefile:1858: /home/carterk/CH341SER] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-6.0.9-060009-generic'
make: *** [Makefile:7: default] Error 2

```

And I'm at a loss as to where to go from here. I seem to be having this error across multiple machines with fresh installs - nothing works out of the box with this OS. 

Any help at all would be hugely appreciated, cheers!

---

### Post by Impavidus on 2022-12-08
Apparently, the option -ftrivial-auto-var-init=zero was [added to gcc](https://gcc.gnu.org/pipermail/gcc-patches/2021-February/565514.html) with version 12, but on Ubuntu 22.04 you only get gcc 11. Ubuntu 22.10 has gcc 12.

Maybe the -ftrivial-auto-var-init=zero option was only used for extra security and all variables in your program are properly initialised before use. In that case, removing that option from the Makefile should work. On the other hand, maybe the programmer was lazy and skipped initialisation, assuming the compiler would do it automatically with this option. In that case, the program will not work if you remove that option.

Have you read [this question](https://askubuntu.com/questions/1403705/dev-ttyusb0-not-present-in-ubuntu-22-04), linked from that github page? Sounds like an easier solution, without manual compilation or non-standard kernels. Those aren't things most people new to Ubuntu should want to try

---

### Post by #&amp;thj^% on 2022-12-08
Ok on Lunar it works just fine, but Think hard about using it as stable;
```
cd CH341SER


me on Thu Dec 08 at 01:30 PM in ~/CH341SER nothing to commit:   
>> sudo make clean 
rm -rf .tmp_versions Module.symvers *.mod.c *.o *.ko .*.cmd Module.markers modules.order
##############
sudo cp /sys/kernel/btf/vmlinux /usr/lib/modules/`uname -r`/build/
[sudo] password for me: 


me on Thu Dec 08 at 01:47 PM in ~/CH341SER nothing to commit:   
>> sudo make
make -C /lib/modules/5.19.0-23-generic/build  M=/home/me/CH341SER 
make[1]: Entering directory '/usr/src/linux-headers-5.19.0-23-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.2.0-3ubuntu1) 12.2.0
  You are using:           gcc (Ubuntu 12.2.0-9ubuntu1) 12.2.0
  CC [M]  /home/me/CH341SER/ch34x.o
  MODPOST /home/me/CH341SER/Module.symvers
  CC [M]  /home/me/CH341SER/ch34x.mod.o
  LD [M]  /home/me/CH341SER/ch34x.ko
  BTF [M] /home/me/CH341SER/ch34x.ko
make[1]: Leaving directory '/usr/src/linux-headers-5.19.0-23-generic'


me on Thu Dec 08 at 01:47 PM in ~/CH341SER untracked:   
>> sudo make load
modprobe usbserial
insmod ch34x.ko


me on Thu Dec 08 at 01:48 PM in ~/CH341SER untracked:   
>> lsmod | grep ch34*
grep: ch34x.ko: binary file matches
grep: ch34x.o: binary file matches

```
This is a normal warning:
```
sudo dmesg | grep ch34x
[16022.694838] ch34x: module verification failed: signature and/or required key missing - tainting kernel
[16022.696514] usbcore: registered new interface driver ch34x
[16022.696531] usbserial: USB Serial support registered for ch34x

```
Examples on taint
```
sudo dmesg | grep taint
[    3.575995] spl: loading out-of-tree module taints kernel.
[    3.579061] znvpair: module license 'CDDL' taints kernel.
[    3.579063] Disabling lock debugging due to kernel taint
[    9.605110] nvidia_uvm: module uses symbols nvUvmInterfaceDisableAccessCntr from proprietary module nvidia, inheriting taint.
[16022.694838] ch34x: module verification failed: signature and/or required key missing - tainting kernel

```

---

### Post by carterk on 2022-12-09
Yep, I've followed through with the brllty issue previously - lost a week of my life trying to isolate that issue on my Raspberry Pi machine. Doesn't help here though unfortunately. 

Removing the -ftrivial-auto-var-init=zero option from the make file, how would I go about that? Here's the contents of that file but I can't see it referened anywhere:

```
ifeq ($(KERNELRELEASE), )

KERNELDIR := /lib/modules/$(shell uname -r)/build

PWD :=$(shell pwd)
default:
    $(MAKE) -C $(KERNELDIR)  M=$(PWD) 
clean:
    rm -rf .tmp_versions Module.symvers *.mod.c *.o *.ko .*.cmd Module.markers modules.order
load:
    modprobe usbserial
    insmod ch34x.ko
unload:
    rmmod ch34x
else
    obj-m := ch34x.o
endif
```

Thanks for your response

---

### Post by carterk on 2022-12-09
| grep ch34x and taint result in nothing for me, which I guess would be the expected result if the make file hadn't been executed?

sudo make seems to follow the same steps as yours for me until it gets to:
```

CC [M]  /home/carterk/CH341SER/ch34x.o
```

for it to fail after that, would it indicate a missing library or driver, or an incorrect folder pointer, didn't hold my breath long enough or sacrifice to the right god? 

This is the line that follows, but it means nothing to me.
```

gcc: error: unrecognized command-line option &#8216;-ftrivial-auto-var-init=zero&#8217;
```


Is there a version of linux that just works stably and consistently out of the box? Not having a go at Ubuntu specifically here, I just need something that I can plug an Arduino into without doing a months fault finding first

Thanks for your response

---

### Post by Impavidus on 2022-12-09
gcc is called with an option it doesn't know. make puts that option there. make must get it from somewhere, but it's not entirely clear from where it comes in this case. Maybe use grep on every text file in that source code package?

The easiest solution may be using Ubuntu 22.10, which comes with a more recent version of gcc.

Ubuntu is stable and works out of the box for most people, but it may be more difficult if you have peculiar hardware demands, or if you want to use something the makers of which insist on not having it work with Linux. In that case you'll have difficulty in any Linux distro. They all use the same kernel.

---

### Post by #&amp;thj^% on 2022-12-09
> **Impavidus said:**
> They all use the same kernel.

Well yes And no, All Linux distributions use the same binary format ELF, but there is still some differences:
[list]
    [*]different cpu arch use different instruction set.
    [*]the same cpu arch may use different ABI, ABI defines how to use the register file, how to call/return a routine. Different ABI can not work together.[/list]
EDIT: Yes, several distros might use "Linux version X.Y.Z.," but No, they might not use the same configuration options when building it.
I do agree though that 22.10 with kernel 5.19.0-23-generic will work, and provide a more stable experience.
Just a heads up working with 6.0.9-060009-generic/build is causing issues here with your compile.

---

