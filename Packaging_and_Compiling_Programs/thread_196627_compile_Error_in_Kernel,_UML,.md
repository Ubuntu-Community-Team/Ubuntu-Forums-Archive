---
title: "compile Error in Kernel, UML,"
date: 2006-06-14
forum: Packaging and Compiling Programs
---

### Post by marcopolo on 2006-06-14
Hi,  I'm new in this forum and using ubuntu,  and I hope you can help me with my problem.

I'm using kubuntu 6.06 in an Inspiron 5160 (wich video card XGI Volari I can't configure , but that's other problem.
My problem is that I get this error when I try to run Linux in UML (user mode linux)
./linux udb0=/home/polox/uml/fs/root_fs.md-8.2-full.pristine.20020324

[42949373.520000] VFS: Cannot open root device "98:0" or unknown-block(98,0)
[42949373.520000] Please append a correct "root=" boot option
[42949373.520000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(98,0)
[42949373.520000]

where /home/polox/uml/fs/root_fs.md-8.2-full.pristine.20020324 is the path of a FileSystem y downloaded*1 and I tried with more FS getting same error.

I compiled the linux Kernel (downloaded*2)  with the following commands:
make config ARCH=um
make menuconfig ARCH=um
make linux ARCH=um
(ext3 is  set to supported)
I dont really know how to know if I need to set other parameters to compile.

Please let me know if you had any similar problem or a possible solution.  
Any question or comment please let me know.

Any help will be appreciated.  Thanks

*1: [http://user-mode-linux.sourceforge.net/dl-sf.html](http://user-mode-linux.sourceforge.net/dl-sf.html)
*2: [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)


Regards // Marcopolo

---

