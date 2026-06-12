---
title: "Live CD installing VMware viewer"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by RichardC73 on 2008-09-01
Hi!

I've got a few windows pc's here, which should remain untouched. However, I will need to run a VMware image. Since these pc's only have 1 Gb of RAM I figured I could simply run an ubuntu live CD, use the liveCDpersistence and be done with it.

So, I figured out the liveCDPersistence-part, by using 512 MB of harddisk space nobody is going to miss. I'm running 6.06 LTS "Dapper Drake", since it won't work with the latest version.

I downloaded the VMware viewer and happily started installing. Then I got to the part of a C compiler. I searched this forum, and found the "sudo apt-get install build-essential" command to install a general c compiler.
However, next question VMWare viewer asks is: "What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]". It won't accept the default answer, since there's nothing after /usr/src. How do I solve this problem?

{edit} If I miss the 'h' in some words I would like to appologize in advance... this isn't the best keyboard I ever worked on{/edit}

---

### Post by cwsnyder on 2008-09-01
The header file which matches your installed Kernel you can get with 'sudo apt-get install linux-headers-2.6.24-16-generic' or whatever your kernel version is, which will install the header files in the /usr/src/linux/include folder.  Go to the /boot directory and do an 'ls' command: whatever follows the 'vmlinuz-' in the file name should be what would be put following the 'linux-headers-' in the 'sudo apt-get' command above.

---

