---
title: "No Windows 8.1 on grub menu - Dual boot with Ubuntu 13.10"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by muhlisahhh on 2013-11-29
Hi! I have an HP laptop with Win 8.1 on it and I decided a few days ago to dual boot with Ubuntu 13.10.  Everything with the installation went fine and I was able to switch between the two at will until last night.  I did my Ubuntu updates and after that I had no option for Windows 8.1 on my grub menu. All that was left was Ubuntu and then Other options for Ubuntu with my old kernels. I ran boot repair to see if I could get it back and that was without luck.  Any advice guys? Thanks!

---

### Post by grahammechanical on 2013-11-29
If you run this command, please look at the output to see if Windows 8 (loader) is listed.

```
sudo update-grub
```

Boot repair provides a printout and a URL that you can post so that we can look at the printout for ourselves. Seeing that printout would be helpful to us. It may gives us clues. Boot repair also offers to fix what is wrong. More inofrmation about what happened when you ran boot repair and what boot repair did and what happened next would also be useful otherwise the information that you provide is too little to offering useful suggestions.

Regards.

---

### Post by muhlisahhh on 2013-11-29
Thank you for the response.  I was in a rush earlier when posting so I apologize for not posting everything that I needed to.  When I run update grub I do not see anything for Windows, only "Adding boot menu entry for EFI firmware configuration" underneath my Ubuntu kernels. [http://paste.ubuntu.com/6495617/](http://paste.ubuntu.com/6495617/) is what boot repair gave me when I ran the bootinfo summary.  I'll apologize in advance as I've never used Win8/8.1 so I'm not well versed in UEFI/EFI/SecureBoot in regards to Windows.  I know to install Ubuntu I had to disabled Secure Boot, but as I had no problems switching between the two OS until last night, I don't know if that would have anything to do with it.  This isn't my computer, its my brothers so I'm unsure if he "did anything" to cause these issues, but he says he did nothing.

---

### Post by muhlisahhh on 2013-11-29
Ok so I see the windows partition is no longer on the computer.  I have no idea what my brother did as it was there last night but I seem to have solved my own problem. Thanks anyways!

---

