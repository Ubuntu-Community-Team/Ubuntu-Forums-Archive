---
title: "mounting with terminal"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by nikhil3 on 2013-09-03
hey everone


after getting ubuntu on a pen drive, i entered the OS without installation and unmounted the main hard disk using disk utility. now i am not able to "try edubuntu without installation".

this is the screen i am seeing once i hit "try edubuntu without installation". 



BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' fpr a list of built-in commands.

(initramfs) BusyBox 1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) multi-call binary.

Usage: mount [options]  [-o OPS] DEVICE NODE

Mount a filesystem. Filesystem autodetection requires /proc.

(list of "options" followed by "-o OPT")

There are filesystem-specific -o flags.

Can not mount /dev/loop1 on /cow 


(initramfs)





now whatever i enter here,it says the command is "not found". 

Please help.

---

### Post by cariboo on 2013-09-03
It looks like you may have removed something mistakenly, I'd suggest you recreate your usb drive, and try again. When unmounting drives in a gui atmosphere, it may be better to use the file manger to eject or safely remove a drive or partition.

---

