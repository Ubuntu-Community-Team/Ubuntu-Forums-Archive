---
title: "No sound on new hardy upgrade i need help"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by burgerbeanhomfry on 2008-05-22
I'm a total noob that just upgraded from gutsy to hardy and my sound completely stopped working. I'm not sure if it is not recognizing my sound card anymore or what its doing, i've done some of the basic remedies but to no avail,  I'm on a dell inspiron 1525, new this spring so i'm nearly positive i meet the system requirements.

Any suggestions?

---

### Post by garyedwardjohnston on 2008-05-22
What are the results from testing your hardware?

System > Administration > Hardware Testing

---

### Post by billgoldberg on 2008-05-22
Try this:

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

---

### Post by burgerbeanhomfry on 2008-06-05
Neither of those really attacked the problem, my system doesn't even seem to recognize that i have a sound card. I get error messages anytime I try to modify sound settings and silence when i play something with sound.

any other sugestions?

---

### Post by persev on 2008-06-06
> **burgerbeanhomfry said:**
> Neither of those really attacked the problem, my system doesn't even seem to recognize that i have a sound card. I get error messages anytime I try to modify sound settings and silence when i play something with sound.

any other sugestions? 

I have the same laptop that came with Gusty preinstalled and no sound card was detected after upgrde to Hardy Heron. The quick fix is to boot into your old kernel. Try this until a fix is found open a terminal and copy and paste this "sudo gedit /boot/grub/menu.lst" without quotes and you should get a text file with this at the end:

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro single
initrd		/boot/initrd.img-2.6.22-14-generic


title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1

make it look like this:

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=81387f8c-74a9-4d6a-9828-bf852a962979 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1


This will change the boot order of your kernels booting you into your older kernel. This worked for me.

---

### Post by ukripper on 2008-06-06
Here is the solution on Hardy - [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

---

### Post by persev on 2008-06-06
> **ukripper said:**
> Here is the solution on Hardy - [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

Does not work, I tried it. I also tried it Hardy's kernel Ubuntu 8.04, kernel 2.6.24-18-generic. **Doesn't work**.

---

### Post by ukripper on 2008-06-07
there was kernel update yesterday 24-19 try that.

run update manager

---

### Post by Dumpy Dumpster on 2008-06-07
I am experiencing the same problem, but none of the commands given in [http://linux.dell.com/wiki/index.php...bution_Upgrade](http://linux.dell.com/wiki/index.php...bution_Upgrade) work.  They all report command not found.  Getting very fed up!!!

---

### Post by Zarckon on 2008-06-08
Hey Guys:

I'm running Hardy Kubuntu, so don't know that the solution I found will work for any of you (for instance I don't have the System> Administration > Hardware testing that was suggested early on.

I upgraded to Hardy from Gutsy about a week ago. I had to add a sound card because I blew the input jack from the onboard card. Sound was working, though there were (and maybe still are) games that seem to take it over, so I was loosing sound after playing. Then for some reason sound stopped working altogether. I hadn't made any changes to anything, but started looking at system settings, etc. Nothing made any difference. Came here and found that Hardy and sound problems seem to go together. ow!

I got to fooling with the sound mixer for no real reason other than it was something I hadn't tried (before I went and did all the kernal destruction advised earlier). I started fooling with the switches on the switches tab and found that unchecking the Analog/Digital jack gave me back sound. No idea how it got checked in the first place, but maybe something to try if Ubuntu Hardy has something similar to that.

Anyway my $.00000002.

---

