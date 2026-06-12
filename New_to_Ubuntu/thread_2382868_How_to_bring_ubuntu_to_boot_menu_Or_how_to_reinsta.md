---
title: "How to bring ubuntu to boot menu? Or how to reinstall it"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by fatemeh1998 on 2018-01-18
I first installed ubuntu by choosing "erase the disk and install ubuntu" option. I had windows 10 on my laptop. This erased my windows and successfully installed ubuntu. After restarting, the windows boot manager showed a message that it can't find windows. I went to the bios to change the order of ubuntu and bring it to top! There was no ubuntu there!!! I repaired the Grub by repair-boot but no result. Now can you tell me what should I do?<br>
<br>
<br>
If i want to reinstall the ubuntu and choose "something else" option this time, how should i erase the installed ubuntu?<br>
<br>
Thanks

---

### Post by oldfred on 2018-01-18
Re-install probably will not resolve issue.
In Something Else you choose (change button) your existing / (root) as new root.

What brand/model system.
UEFI or BIOS install?

Some brands require work arounds as they violate UEFI standards.
See link in my signature and:
 Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789) 

If only booting Ubuntu you can use the option that creates a new UEFI entry that says "Windows Boot Manager" but actually boots using Ubuntu/grub's shimx64.efi file. Remove other Windows entries in UEFI menu to avoid confusion.

---

