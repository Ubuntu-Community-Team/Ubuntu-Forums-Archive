---
title: "compiling the kernel"
date: 2010-10-14
forum: Programming Talk
---

### Post by albert-mcfly on 2010-10-14
Hi everyone. I recentlly succeded to compile the kernel version 2.6 for a soft-core embedded CPU (MicroBlaze) in a development board designed by Xilinx (SP605). However, after reinstalling my OS and doing some other things I can no longer compile using the same procedure. ( I am using ubuntu 10.04 now)

 
Next I describe the steps that i have followed, some of them are pretty specific to my platform but don't worry if you don't totally understand them as I suspect that my problem is a more general and has to do with ubuntu itself.
I have uncompressed the initramfs.cpio file into a directory and pointed the CONFIG_INITRAMFS_SOURCE parameter in the .config file to it. I have applied the commands (both using sudo and without it) "sudo make ARCH=microblaze mmu_defconfig", "sudo make ARCH=microblaze menuconfig" (configured the platform). I have also generated the Device Tree Source file and placed it in  "../ARCH/microblaze/boot/dts". I also set the environment variable PATH with "  export PATH="/home/arquerc/mb-gnu-tools/microblaze-unknown-linux-gnu/bin":$PATH; " which is where I have the microblaze tools placed (the mb-linux-gcc executable is there).

 

If I am not forgetting anything I went ahead and ran "sudo make ARCH=microblaze CROSS_COMPILE=mb-linux- simpleImage.xilinx" and I got the following output:


[COLOR="DeepSkyBlue"]arquerc@arquerc-UBUNTU:~/linux-2.6-xlnx$ sudo make ARCH=microblaze CROSS_COMPILE=mb-linux- simpleImage.system
make: mb-linux-gcc: Command not found
make: mb-linux-gcc: Command not found
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s
/bin/sh: mb-linux-gcc: command not found
make[1]: *** [kernel/bounds.s] Error 127
make: *** [prepare0] Error 2[/COLOR]

 

If I am correct this means that the command mb-linux-gcc can not be found and that would mean that i have incorrectlly set the PATH variable . However if I type "echo $PATH" the value of the variable is correct.... I set the PATH variable by adding the following line to /home/arquerc/.bashrc : export PATH="/home/arquerc/mb-gnu-tools/microblaze-unknown-linux-gnu/bin":$PATH;

[COLOR="DeepSkyBlue"]arquerc@arquerc-UBUNTU:~$ echo $PATH
/home/arquerc/mb-gnu-tools/microblaze-unknown-linux-gnu/bin:/opt/Xilinx/12.2/ISE_DS/ISE/bin/lin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games[/COLOR]

The most alarming thing is that if i write "mb-linux-gcc" into the shell I don't get the "command not found" message... meaning that the file can actually be located....

[COLOR="DeepSkyBlue"]arquerc@arquerc-UBUNTU:~$ mb-linux-gcc
mb-linux-gcc: no input files
[/COLOR]
 
I really don't know what to do... I was able to compile using this same procedure without any problems just like a week ago.

---

### Post by spjackson on 2010-10-14
> **albert-mcfly said:**
> 
If I am not forgetting anything I went ahead and ran "sudo make ARCH=microblaze CROSS_COMPILE=mb-linux- simpleImage.xilinx" and I got the following output:

For security reasons, sudo resets PATH. You shouldn't normally need sudo simply to compile.

---

### Post by albert-mcfly on 2010-10-15
Thanks!!! I was only using sudo because the command "make ARCH=microblaze mrproper" had given me errors about some denied permisions. I did it without sudo and it is compiling right now!! 

Thanks again really!!

---

