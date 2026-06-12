---
title: "Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by miguelmalheiro17 on 2014-03-20
Hi, ubuntu doesn't seem to have my Asus F5VL webcam drivers out of the box. In skype (installed from ubuntu software center) it detects no device, and on flash content in firefox the same.
How can I install my webcam?
I've seen this thread [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam), and the website [www.rastageeks.org](www.rastageeks.org) doesn't seem to open...
Any easy method to make this work?

The webcam's name is D-Max GD-6A31 (at least it's the name of the windows' drivers provided by Asus).

Thanks in advance

---

### Post by Arup_Ghosh on 2014-03-21
Hi, Please install cheese from the store or using command line and check if your webcam working or not. If your webcam is not showing up then its may be a permission issue. Use the following command to solve this issue:
> sudo usermod -a -G root <your username>

I was also facing the same trouble with my HP laptop, now the camera is working fine with any software.

Regards,
[Arup Ghosh]("http://www.wptron.com")

---

### Post by miguelmalheiro17 on 2014-03-21
Thanks for the reply.
I installed cheese and nothing happens.
Used the command you provided, still the same.
Any suggestions?

---

### Post by miguelmalheiro17 on 2014-03-21
Used lsusb and got this:
Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S

Does this mean the webcam is already installed? Or Ubuntu just detects it?
Please help
Thanks in advance

---

### Post by miguelmalheiro17 on 2014-03-24
Nobody answered, and I went looking for a solution.
Followed a french tutorial [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek) and got this error:



miguel@miguel-F5VL:~/webcam/stk11xx-2.1.0$ sudo make -f Makefile.standalone
make -C /lib/modules/3.11.0-18-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
make[2]: *** No rule to process target `/usr/src/linux-headers-3.11.0-18-generic/arch/x86/syscalls/syscall_32.tbl', necessary for `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make[1]: ** [archheaders] Error 2
make[1]: Exiting directory `/usr/src/linux-headers-3.11.0-18-generic'
make: ** [driver] Error 2

---

### Post by miguelmalheiro17 on 2014-03-24
The above error is from the file provided by sourceforge.
The file provided by the 1º option in the tutorial gives me this error:

miguel@miguel-F5VL:~/webcam/syntek/driver$ sudo make -f Makefile-syntekdriver
make -C /lib/modules/3.11.0-18-generic/build SUBDIRS=/home/miguel/webcam/syntek/driver modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.11.0-18-generic'
  CC [M]  /home/miguel/webcam/syntek/driver/stk11xx-v4l.o
/home/miguel/webcam/syntek/driver/stk11xx-v4l.c: In function &#8216;v4l_stk11xx_register_video_device&#8217;:
/home/miguel/webcam/syntek/driver/stk11xx-v4l.c:1773:11: error: &#8216;struct video_device&#8217; has no member named &#8216;parent&#8217;
  dev->vdev->parent = &dev->interface->dev;
           ^
make[2]: ** [/home/miguel/webcam/syntek/driver/stk11xx-v4l.o] Erro 1
make[1]: ** [_module_/home/miguel/webcam/syntek/driver] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.11.0-18-generic'
make: ** [all] Erro 2

---

### Post by miguelmalheiro17 on 2014-03-24
My webcam isn't detected in skype or cheese. Please help

miguel@miguel-F5VL:~$ lsusb
Bus 001 Device 004: ID 0bda:0116 Realtek Semiconductor Corp. RTS5116 Card Reader Controller
Bus 001 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0458:012f KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Vladlenin5000 on 2014-03-24
[http://ubuntuforums.org/showthread.php?t=1840889](http://ubuntuforums.org/showthread.php?t=1840889)

---

### Post by miguelmalheiro17 on 2014-03-25
Thanks for the reply, followed the instructions in the link you provided and got the following error in the attempt:

miguel@miguel-F5VL:~/webcam/stk11xx-1.4.0$ sudo make -f Makefile.standalone
make -C /lib/modules/3.11.0-18-generic/build SUBDIRS= modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.11.0-18-generic'
make[2]: *** Sem regra para processar o alvo `/usr/src/linux-headers-3.11.0-18-generic/arch/x86/syscalls/syscall_32.tbl', necessário por `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Pare.
make[1]: ** [archheaders] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.11.0-18-generic'
make: ** [driver] Erro 2

---

### Post by mörgæs on 2014-03-25
Please stop double-posting.
Merged.

---

