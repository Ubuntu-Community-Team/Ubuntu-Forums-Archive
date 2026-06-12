---
title: "windows activation in bios"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by david98 on 2014-03-12
I have a samsung laptop which I wiped completely after purchase and installed ubuntu had to disable uefi and fast boot etc. Problem now regrettably I need to install win 8 back as need some windows programs. I still want to keep ubuntu so used a live disk and minimised buntu partition to create a a new one. I purchased a oem copy of windows 8 for a small fee the problem I have is that I need to boot in uefi for my activation code in the bios to activate windows. I now need to boot in uefi so the question is can I make it so I can boot in uefi as to get my code and use uefi to boot buntu as it would be a bit of inconvenience to change the bios setting's. any help would be greatly appreciated.

I do hope the user oldfred can help clear this up as I enjoy reading his post's and has an extensive knowledge in this matter:)

---

### Post by newbie2244 on 2014-03-13
Which BIOS do you have? It sounds like you want a dual boot system now.  When I was   installing Ubuntu on my Windows 8 laptop, I changed BIOS settings also. I disabled secure boot in order to get Ubuntu to boot. I did not disable UEFI. I enabled Legacy mode and changed boot order in order to boot Ubuntu from USB flash drive.[ http://technet.microsoft.com/en-us/library/hh825112.aspx]( http://technet.microsoft.com/en-us/library/hh825112.aspx)

---

### Post by 3rdalbum on 2014-03-13
The same uEFI settings will boot both Windows and Ubuntu. I suspect you mean that you need Secure Boot turned on for Windows, well, Ubuntu works fine with that too.

---

### Post by david98 on 2014-03-15
Thanks for your advice buntu would not boot in secure boot so disabled it and booted with uefi enabled and everything works so thread marked as solved.

---

