---
title: "Problem with install Win10 and Ubuntu"
date: 2018-10-01
forum: New to Ubuntu
---

### Post by menido on 2018-10-01
Hello

After installing Antegros on my tablet (inter cherry trail z8300 64 bit) i can install again Windows 10 form my usb and i cant install/start even ubuntu live 
Booting in both cases starts but unfortunately hangs when the system logo is displayed ;/ 

[Antegros and Antegros Live worki but i wont back to my Os...]

---

### Post by oldrocker99 on 2018-10-01
The rule for dual-booting is to install Windows **first**. Installing Windows after installing Linux will rewrite the boot sector, and only Windows will boot.

---

### Post by menido on 2018-10-02
Thank you for your info


But something does not agree with this reasoning.


I managed to install linuxmint . 
I still can't load Ubuntu or Windows installation?


Is it the fault of the lack of boot sectors?
If so, how can I fix it from the linux level?

---

### Post by oldfred on 2018-10-02
Is system UEFI or BIOS?
If UEFI, you can install as many systems as you want and they share the /EFI folder for boot files.
One issue may be that all flavors of Ubuntu and many based on Ubuntu use /EFI/ubuntu. So last install is the one that boots to grub.
If BIOS, Windows only installs to primary partitions and you only have one MBR for boot loader. 

For both Ubuntu & Windows how you boot install media, UEFI or BIOS, is then how it installs. And system then must be set to boot in that mode.

But Windows only installs in UEFI boot mode to gpt partitioned drives. And only installs in BIOS boot mode to MBR drive. If you force install in other mode it converts drive, in effect erasing it.

---

### Post by menido on 2018-10-04
Im not sure is it UEFI or BIOS.
I know that i was convering 3 days ago my disk from GPT to MBR and then i install windows 10 . Now i Install second OS = ubuntu.

But i cant now boot elementeryOS / Manjaro etc (live cant run)

---

### Post by yancek on 2018-10-04
You need to clarify your situation when you make changes.  In your initial post you indicate you installed Antegros and then mention windows 10 and Ubuntu.  It isn't clear from that post if you then installed windows 10 or were trying and failed?  Your next post mentions you installed Linux Mint.  Was that before or after you installed Antegros and did you have both systems installed?

> I still can't load Ubuntu or Windows installation?

Being unable to boot from a usb/DVD has really nothing to do with whatever OS is installed on the computer.  Have you been booting and installing Antegros/Mint from a usb or DVD?  If so, do you have the same BIOS settings to boot from USB/HDD or DVD?  Have you verified the download of the other systems with md5 checksum?  What software did you use to create the bootable usb or DVD?

---

### Post by menido on 2018-10-06
I have booting from usb
Same bios setting ? What do you mean ?
Iso verified
I have made iso using Rufus 3.2

---

### Post by menido on 2018-10-16
> **oldrocker99 said:**
> The rule for dual-booting is to install Windows **first**. Installing Windows after installing Linux will rewrite the boot sector, and only Windows will boot.

What if i can run linux (lubuntu and mint) but i cant run windows 10 and even i can run new instalation from usb ? (every time botting logo screen is hanging off)
I trying many setting in bios but it is horrible;/

---

### Post by mrgnome on 2018-10-17
You say the install gets stuck on the boot screen? To troubleshoot this error, you should press Escape during the part of the boot sequence when the 'ubuntu' screen is there. This will deactivate the Plymouth boot screen and show you what the computer is doing that's making it stick. Then, you can try and diagnose it.

---

