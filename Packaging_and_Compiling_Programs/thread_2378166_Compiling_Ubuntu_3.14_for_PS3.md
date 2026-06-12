---
title: "Compiling Ubuntu 3.14 for PS3"
date: 2017-11-20
forum: Packaging and Compiling Programs
---

### Post by kabone on 2017-11-20
Hello all,

Let me first start by saying if I posted this in the wrong section I'm sorry and please move it. I have been working on trying to get a newer kernel and Ubuntu version running on the PS3 within otherOS on a PS3 slim. I managed to find a git repository made by Geoff that is still being updated as of a few days ago. That can be found here - [https://kernel.googlesource.com/pub/scm/linux/kernel/git/geoff/ps3-linux](https://kernel.googlesource.com/pub/scm/linux/kernel/git/geoff/ps3-linux). I was able to compile it, but when I try to boot from within petitboot using this command:
```
kexec -l vmlinux --initrd=initrd.gz
```
I am greeted with - 
```
[COLOR=#333333][FONT=arial]Warning: append= option is not passed. Using the first kernel root partition [/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Modified cmdline: [/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Unable to find /proc/device-tree//chosen/linux,stdout-path, printing from [/FONT][/COLOR]
[COLOR=#333333][FONT=arial]purgatory is diabled 
[/FONT][/COLOR]
```[COLOR=#333333][FONT=arial]
I am using the following commands 
I am a noob when it comes to kernel development and have no idea what I need to do get fix this. If anyone can help me that would be greatly appreciated! 

I have tried so many things, and am lost as to what I need to do. Some additional things I have tried:
[/FONT][/COLOR]```
http://www.psdevwiki.com/ps3/Booting_Linux_2.6_kernel_on_running_PS3_Linux_with_kexec
https://www.kernel.org/pub/linux/kernel/people/geoff/petitboot/lpc-2012/petitboot-lpc-2012.pdf
https://www.vivaolinux.com.br/topico/Comandos/Kernel-for-Newbies-Compilacao-facil-do-Kernel
http://psx-scene.com/forums/f119/help-wanted-how-install-xubuntu-ydl-proper-hdd-partition-ps3-namely-ps3dd-please-help-me-try-xubuntu-ps3-108488/#post1020141
http://www.psdevwiki.com/ps3/OtherOS%2B%2B
https://kernel.googlesource.com/pub/scm/linux/kernel/git/geoff/ps3-linux/+/base/Documentation/process/changes.rst
http://psx-scene.com/forums/f119/detailed-guide-install-ubuntu-9-04-jaunty-jackalope-internet-accoring-ps3devwiki-glevand-skynet-108907/
https://www.youtube.com/watch?v=Upu6X3m8rV0
https://www.youtube.com/watch?v=4jGG51riijo
https://www.youtube.com/watch?v=0hyZJgNt4to
```
This is just a small amount of what I have used to get to where I am now..


any help would be much appreciated.

*UPDATE 1*
Played a bit with the sources.list on ubuntu 10.04 and have it pulling repos now. So I think my issue is solved!

Thanks!

---

