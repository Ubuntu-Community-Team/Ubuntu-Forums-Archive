---
title: "Cannot boot"
date: 2016-10-30
forum: New to Ubuntu
---

### Post by jwn-2 on 2016-10-30
Ubuntu 14.04 LTS

I have a serious problem and urgently needs serious help.

I have Ubuntu 14.04 LTS on an encrypted disk, which worked perfectly fine for a long time now. This morning however when I switched on I suddenly am unable to boot my system. Instead of booting up normally, it asks for boot options. I selected "Ubuntu". Then instead of the normal "Enter passphrase . . . " or something similar, it displays "Please unlock disk sda5_crypt". I enter the correct passphrase. Then it first displays "cryptsetup: unknown fstype, bad password or options" and after a few seconds it does display "cryptsetup: sda5_crypt set up successfully". Then it just opens a terminal and ask for my login details.

Please HELP!!! What went wrong and what must I do to recover my system?

---

### Post by ajgreeny on 2016-10-30
Did you login at the command line when presented with that "terminal"?

That is probably the first step to take to ensure you can get into the OS even if it is without the GUI.  FRom there, assuming your files are not still encrypted, you should at least be able to back them up to another disk, and then try to figure out what is your problem.

I have never used encryption so will have to leave that to others to deal with.

---

