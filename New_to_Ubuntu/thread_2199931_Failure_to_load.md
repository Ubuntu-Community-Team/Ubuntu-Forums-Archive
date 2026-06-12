---
title: "Failure to load"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by Rebecca_D on 2014-01-16
I have a MESH x64 PC with Ubuntu 12.10 installed. A while ago the machine stopped working completely. I have only just got it fixed (needed a new PSU) and when I tried to get it to run Ubuntu fails to load correctly.

I tried repairing the boot using the [Boot Repair]("http://sourceforge.net/p/boot-repair-cd/home/Home/") disk, but this has made no difference.

When started, at first it appears that the OS is loading, but eventually shows a screen entitled** GNU GRUB version 2.00-7ubuntu11** with various options. I have tried the first **Ubuntu** and **Advanced options for Ubuntu** but I end up with the following screen.

[INDENT][OK][/INDENT]
[INDENT]speech-dispatcher disabled : edit /etc/default/speech-dispatcher[/INDENT]
[INDENT]* Starting file alteration monitor FAM[/INDENT]
[INDENT]...done[/INDENT]
[INDENT]]saned disabled : edit /etc/default/saned[/INDENT]
[INDENT]* Starting web server apache2[/INDENT]
[INDENT]apache2 : Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName [OK][/INDENT]
[INDENT][OK][/INDENT]
[INDENT]* Checking battery state...[/INDENT]

Since the failure of the PSU I have done nothing else to the machine and I am confused why an OS that was working perfectly before now fails to load correctly. I have run the machine using a Live CD and the file system seems to be in place.

Is there any way I can avoid having to do a complete re-install with the loss of other software?

Many thanks for any help you can give.

---

### Post by steeldriver on 2014-01-16
It looks like the machine is basically booting (starting the apache2 service comes quite late in the boot sequence) but is just failing to bring up the GUI. This is often due to proprietary graphics drivers becoming incompatible when the kernel gets updated.

Some things you can try:

1. select the 'Advanced options' grub menu again, but look for an earlier kernel and try booting that

2. also from the 'Advanced options', select recovery mode --> [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

3. without rebooting, just try switching to one of the virtual terminals using the Ctrl-Alt-F1 / Ctrl-Alt-F2 etc key combinations - if you can log in there, we can begin troubleshooting

---

### Post by Bashing-om on 2014-01-16
Rebecca_D;

Too slow on my part, +1 ^ !

[INDENT][INDENT]"we can begin troubleshooting"
[/INDENT][/INDENT]

---

### Post by Rebecca_D on 2014-01-16
Many thanks steeldriver. I have managed to login using the recovery mode and I have updated all software (541 updates!!! Phew). On reboot I still have to go through the recovery mode options to login. I will try your point 3 but what info do you need from this?

5 minutes later... I restarted after all the updates and although I still get the **GNU GRUB version 2.00-7ubuntu11** with various options, I can now login just using the first option without recovery. Is there any way of by-passing this screen??

---

### Post by Bashing-om on 2014-01-16
Rebecca_D; Hey:

Your machine, is it a desk top or a server installation ?
> 
* Starting web server apache2


Can you boot to anything beyond the grub menu if you select a "normal" kernel to boot to (at the grub menu) ?

[INDENT]getting there is half the fun
[/INDENT]

---

### Post by Rebecca_D on 2014-01-17
Thanks for all the help guys. Problem fixed itself after all the updates were installed. Have now upgraded to 13.10

---

### Post by Bashing-om on 2014-01-17
Rebecca_D; Great !

Is not ubuntu wonderful ? 
Given the opportunity it will heal it's self.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

