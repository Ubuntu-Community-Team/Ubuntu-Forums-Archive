---
title: "No such file or directory error"
date: 2012-07-22
forum: Packaging and Compiling Programs
---

### Post by serhancan on 2012-07-22
I am cross-compiling a program on my PC (12.04) for my beaglebone (12.04 precise armhf). But when I try to execute the program on beaglebone:

root@omap:/home/ubuntu/helloworld# ./helloworldtest 
bash: ./helloworldtest: No such file or directory

Here are some properties:

root@omap:/home/ubuntu/helloworld# file helloworldtest 
helloworldtest: ELF 32-bit LSB executable, ARM, version 1 (SYSV), dynamically linked     (uses shared libs), for GNU/Linux 2.6.31,     BuildID[sha1]=0xca0159e70b99493764b601a0195ee18be5e29b31, not stripped


root@omap:/home/ubuntu/helloworld# ls -la
total 80
drwxrwxr-x 2 ubuntu ubuntu  4096 Jul 20 07:51 .
drwxr-xr-x 5 ubuntu ubuntu  4096 Jul 20 07:50 ..
-rwxrwxrwx 1 ubuntu ubuntu 72739 Jul 20 07:42 helloworldtest

I searched net and found out that most of the people who had this problem, had it because they were using 64 bits machine to compile the code but my PC's processor is 32 bits and my beaglebone's is 32bits too.

Also the strange thing is that, I am able to run this program on beaglebone if I use Angstrom Linux, rather than Ubuntu 12.04 Precise Armhf. Therefore I am sure that there is not anything wrong with my cross-compile process and my cross-compiled program.

Probably you are going to say install ia32-libs but I cannot install ia32-libs:

root@omap:~/helloworldtest# apt-get install ia32-libs Reading package lists... Done Building dependency tree
Reading state information... Done Package ia32-libs is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'ia32-libs' has no installation candidate

Here is the ldd output: (Problem seems like this?)

root@omap:/home/ubuntu/helloworld# ldd helloworldtest 
    not a dynamic executable

I compiled the same program on the target-machine (beaglebone) and checked its ldd output:

root@omap:~# ldd compiled_on_beaglebone 
    libgcc_s.so.1 => /lib/arm-linux-gnueabihf/libgcc_s.so.1 (0x400de000)
    libc.so.6 => /lib/arm-linux-gnueabihf/libc.so.6 (0x400ef000)
    /lib/ld-linux-armhf.so.3 (0x40086000)

Here is the readelf -hl output:

ubuntu@omap:~/helloworld$ readelf -hl helloworldtest 
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           ARM
  Version:                           0x1
  Entry point address:               0x85ad
  Start of program headers:          52 (bytes into file)
  Start of section headers:          68360 (bytes into file)
  Flags:                             0x5000002, has entry point, Version5 EABI
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         9
  Size of section headers:           40 (bytes)
  Number of section headers:         38
  Section header string table index: 35

Program Headers:
  Type           Offset   VirtAddr   PhysAddr   FileSiz MemSiz  Flg Align
  EXIDX          0x00071c 0x0000871c 0x0000871c 0x00018 0x00018 R   0x4
  PHDR           0x000034 0x00008034 0x00008034 0x00120 0x00120 R E 0x4
  INTERP         0x000154 0x00008154 0x00008154 0x00013 0x00013 R   0x1
      [Requesting program interpreter: /lib/ld-linux.so.3]
  LOAD           0x000000 0x00008000 0x00008000 0x00738 0x00738 R E 0x8000
  LOAD           0x000ef8 0x00010ef8 0x00010ef8 0x00144 0x001dc RW  0x8000
  DYNAMIC        0x000f08 0x00010f08 0x00010f08 0x000f8 0x000f8 RW  0x4
  NOTE           0x000168 0x00008168 0x00008168 0x00044 0x00044 R   0x4
  GNU_STACK      0x000000 0x00000000 0x00000000 0x00000 0x00000 RW  0x4
  GNU_RELRO      0x000ef8 0x00010ef8 0x00010ef8 0x00108 0x00108 R   0x1

 Section to Segment mapping:
  Segment Sections...
   00     .ARM.exidx 
   01     
   02     .interp 
   03     .interp .note.ABI-tag .note.gnu.build-id .gnu.hash .dynsym .dynstr   .gnu.version .gnu.version_r .rel.dyn .rel.plt .init .plt .text .fini .rodata .ARM.exidx  .eh_frame 
   04     .init_array .fini_array .jcr .dynamic .got .data .bss 
   05     .dynamic 
   06     .note.ABI-tag .note.gnu.build-id 
   07     
   08     .init_array .fini_array .jcr .dynamic 


ldd and readelf -hl outputs of the cross-compiled executable on Angstrom Linux:

root@beaglebone:~# ldd hello
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x401c3000)
        libc.so.6 => /lib/libc.so.6 (0x401d4000)
        /lib/ld-linux.so.3 (0x40098000)


root@beaglebone:~# readelf -hl hello
ELF Header:
  Magic:   7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF32
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           ARM
  Version:                           0x1
  Entry point address:               0x8380
  Start of program headers:          52 (bytes into file)
  Start of section headers:          2696 (bytes into file)
  Flags:                             0x5000002, has entry point, Version5 EABI
  Size of this header:               52 (bytes)
  Size of program headers:           32 (bytes)
  Number of program headers:         8
  Size of section headers:           40 (bytes)
  Number of section headers:         38
  Section header string table index: 35

Program Headers:
  Type           Offset   VirtAddr   PhysAddr   FileSiz MemSiz  Flg Align
  EXIDX          0x0004e0 0x000084e0 0x000084e0 0x00050 0x00050 R   0x4
  PHDR           0x000034 0x00008034 0x00008034 0x00100 0x00100 R E 0x4
  INTERP         0x000134 0x00008134 0x00008134 0x00013 0x00013 R   0x1
      [Requesting program interpreter: /lib/ld-linux.so.3]
  LOAD           0x000000 0x00008000 0x00008000 0x00534 0x00534 R E 0x8000
  LOAD           0x000534 0x00010534 0x00010534 0x00124 0x00128 RW  0x8000
  DYNAMIC        0x000540 0x00010540 0x00010540 0x000f0 0x000f0 RW  0x4
  NOTE           0x000148 0x00008148 0x00008148 0x00020 0x00020 R   0x4
  GNU_STACK      0x000000 0x00000000 0x00000000 0x00000 0x00000 RW  0x4

 Section to Segment mapping:
  Segment Sections...
   00     .ARM.exidx
   01
   02     .interp
   03     .interp .note.ABI-tag .hash .dynsym .dynstr .gnu.version .gnu.version_r     .rel.dyn .rel.plt .init .plt .text .fini .rodata .ARM.extab .ARM.exidx .eh_frame
   04     .init_array .fini_array .jcr .dynamic .got .data .bss
   05     .dynamic
   06     .note.ABI-tag
   07


What can be my problem? Any suggestions or ideas?
Regards

---

### Post by oldos2er on 2012-07-22
Moved to Packaging and Compiling Programs.

---

### Post by jonnyboysmithy on 2012-07-22
> I am cross-compiling a program on my PC (12.04) for my beaglebone (12.04  precise armhf). But when I try to execute the program on beaglebone:

root@omap:/home/ubuntu/helloworld# ./helloworldtest 
bash: ./helloworldtest: No such file or directory
Perhaps you left out the cd?
Isn't is supposed to be cd /home/ubuntu/helloworld 
Its the only thing I can think of. 
Greetings

---

### Post by serhancan on 2012-07-22
> **jonnyboysmithy said:**
> Perhaps you left out the cd?
Isn't is supposed to be cd /home/ubuntu/helloworld 
Its the only thing I can think of. 
Greetings

No, it is not. I am already in the right directory and trying to run my executable C program.

---

### Post by serhancan on 2012-07-23
I solved my problem by copying ld-linux.so.3 which is located under /lib/arm-linux-gnueabihf/ to the upper directory /lib/.

But is not it strange that I do not have a ld-linux.so.3 directly under /lib/ ?

---

### Post by SevenMachines on 2012-07-23
I think this is a problem to do with 
[https://wiki.linaro.org/OfficeofCTO/HardFloat/LinkerPathCallApr2012](https://wiki.linaro.org/OfficeofCTO/HardFloat/LinkerPathCallApr2012)
which is 'in progress' to be fixed I imagine
You could compile -static I suppose for the moment, maybe theres a more elegant temporary solution I can't say

---

### Post by serhancan on 2012-07-24
> **SevenMachines said:**
> I think this is a problem to do with 
[https://wiki.linaro.org/OfficeofCTO/HardFloat/LinkerPathCallApr2012](https://wiki.linaro.org/OfficeofCTO/HardFloat/LinkerPathCallApr2012)
which is 'in progress' to be fixed I imagine
You could compile -static I suppose for the moment, maybe theres a more elegant temporary solution I can't say

Thank you so much. This is exactly what I was looking for.

---

