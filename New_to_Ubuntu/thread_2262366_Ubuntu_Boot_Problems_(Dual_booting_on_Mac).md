---
title: "Ubuntu Boot Problems (Dual booting on Mac)"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by marc48 on 2015-01-24
Hi everyone,

I am completely new to Ubuntu and was hoping for a little help. I want to dual boot Ubuntu on my Mac. I installed rEFIt and managed to install Ubuntu from a live CD. However, every time I try to boot into it, I get the flashing underscore. I know that this issue has been addressed before but I can only seem to find solutions for Windows machines. I tried running Boot Repair on the live cd and I got an error message about being in Legacy Mode and not EFI mode. I know this has something to do with configuring the BIOS and stuff but I'm at a loss to see how to do that on a Mac! Also, I have no idea how to work GRUB and the like.

Here is the link to the pastebin: [http://paste.ubuntu.com/9852663/](http://paste.ubuntu.com/9852663/)

Any help on the matter would be greatly appreciated! Thanks.

---

### Post by yancek on 2015-01-24
You need to install Ubuntu in EFI mode.  You have an efi vfat partition but I don't see any ubuntu files there.  You do show a BIOS boot partition which would indicate you did not use EFI for your Ubuntu install.  Either do some research on that or wait for someone else to post.  I don't use EFI so don't have any specific suggestions.  Apple has always made serious efforts to prevent people from doing what you are trying to do but it is possible.

---

