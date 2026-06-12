---
title: "Ubuntu on samsung with UEFI bug"
date: 2018-07-27
forum: New to Ubuntu
---

### Post by tetricoaullante on 2018-07-27
So I've been thinking on installing Ubuntu OS for two days now, the major problem is that my laptop has windows 8.1 x64 installed, quad core (Language: Spanish), the system model is 300E4C/300E5C/300E7C Samsung, so it means it is affected by the UEFI bug that would turn my pc in an useless brick. The question is the following: if I enable Legacy boot mode in my bios instead of UEFI, would I be able to install Ubuntu on it? Are there any other ways to install Ubuntu on my old laptop (aka the problem was solved years ago and I didn't know)?
Sorry if the question was asked before, just couldn't find it on google nor in the forums.

---

### Post by oldfred on 2018-07-27
Issue was primarily Lenovo.
       Fixed ISO for UEFI/BIOS issues in 17.10.1, but does not have any KPTI/Retpoline for Meltdown/Spectre mitigation or other changes. 
Ubuntu 17.10 "corrupting" BIOS - many LENOVO laptops models Intel SPI & kernel issue Also some Acer, mostly  Insyde UEFI
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147/comments/458](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147/comments/458) 
    
You need to update UEFI from Samsung.
And since issue was fixed back with 17.10.1 (which has now reached End of Life), you should be able to use 18.04.
Both UEFI & kernels need to be updated for KPTI/Retpoline for Meltdown/Spectre mitigation. Both Windows and Ubuntu have updated kernels, but new variants are found and you need to keep system current, both UEFI & system updates.

---

### Post by tetricoaullante on 2018-07-27
The bug I was talking about happened in 2013 with these Samsung laptops (yes, my laptop is quite old), that would transform them in an useless thing. So I don't know if the problem was solved and can install Ubuntu without any further issue or may I change the BIOS to Legacy instead of UEFI before trying to do so.
Sorry if you answered my question but I want to be sure before taking any risks.

---

### Post by oldfred on 2018-07-27
If I remember correctly they originally blamed Linux as it was first found with Linux installs. 
Then a Windows user/developer was able to recreate problem with Windows.
Issue was really Samsung UEFI and it did not houseclean old UEFI internal data and when 50% full caused system to totally brick. I think Linux was updated to minimize issue, but really Samsung's issue.

Or have you updated UEFI from Samsung. That is first thing you need to do. Also for many other reasons now.

---

### Post by oldrocker99 on 2018-07-27
My experience has been that if you boot in UEFI mode, grub will not install, and the computer will not boot.  Use Legacy mode for no headaches. It will work just fine.

---

