---
title: "How to install Ubuntu on Asus X200CA?"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by j.hajahmad on 2013-12-06
I have never installed or used Ubuntu or any other linux distribution before and would like to try it out on my laptop. Ubuntu certified says the Asus X200CA fully supports Ubuntu [http://www.ubuntu.com/certification/hardware/201306-13793/](http://www.ubuntu.com/certification/hardware/201306-13793/) but Asus only has "BIOS" available under the "others" OS drivers section. [http://www.asus.com/Notebooks_Ultrabooks/X200CA/#support](http://www.asus.com/Notebooks_Ultrabooks/X200CA/#support)

---

### Post by oldfred on 2013-12-06
If it is Windows 8 then it is UEFI with secure boot. But you can turn secure boot off.

You should try Ubuntu in live mode from the install flash drive.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Similar model?

 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by thatredbird on 2013-12-06
Try a live disk first. It recommends buying that model with a preinstall option. However my guess is that yours didn't come with.  A live disk is a great way to see how thing ms will run without an install.  Then if you like it.  The install option comes with the live disk.

http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install

sorry oldfred, was too slow on my post didn't mean to double.

---

### Post by j.hajahmad on 2013-12-08
I've downloaded the ISO to a USB flash drive and I am planning on following these install instructions [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support) and replacing windows but I am still not sure how I am supposed to install the drivers since they are not available on the Asus website?

---

### Post by j.hajahmad on 2013-12-08
> **oldfred said:**
> If it is Windows 8 then it is UEFI with secure boot. But you can turn secure boot off.

You should try Ubuntu in live mode from the install flash drive.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Similar model?

 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

Yes its Windows 8 but why would I want to turn off secure boot? Is it necessary to install the BIOS firmware from the "Other OS" section if I want to install Ubuntu? [COLOR=#000000]I've downloaded the ISO to a USB flash drive and I am planning on following these install instructions [/COLOR][http://www.ubuntu.com/download/deskt...g-term-support]("http://www.ubuntu.com/download/desktop/install-desktop-long-term-support")[COLOR=#000000] and replacing windows but I am still not sure how I am supposed to install the drivers since they are not available on the Asus website?[/COLOR]

---

### Post by oldfred on 2013-12-08
With the new Windows 8 computers you may have better success with 13.10 and then upgrade to 14.04LTS when it comes out. Also 12.04.4 in Jan will have more updates also. If very new Haswell processor or 4th gen 13.10 is required as Intel updated drivers, kernel updates & other updates were added. Some of those updates also helped older versions and they now are adding fixes and updates for the next Intel chips coming next year. I believe AMD also has some updates but have not followed them as much.

With Linux you do not download drivers from vendors normally. All drivers are included. But best to dual boot until you know system works correctly.

Lots more info on UEFI that you need to review from the link in my signature.
First three links are most important.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)



       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

