---
title: "Beginner to Ubuntu"
date: 2021-12-06
forum: New to Ubuntu
---

### Post by sotonye on 2021-12-06
Hello guys, I'm new to Ubuntu Os. Before installing Ubuntu, I want to know what will happen previous Os. Because I want Ubuntu to be the primary operating system. My question is : 
1. will the previous operating system be removed for good?

---

### Post by GhX6GZMB on 2021-12-06
If you do a full install, all other previous OS' will be gone.
Some people do a dual install with both Win and (x)ubuntu, but I'm no expert here.

---

### Post by yancek on 2021-12-06
There are multiple options when installing Ubuntu.  There should always be at least two, ERase disk and install Ubuntu which will overwrite anything on the drive installed to and a Something Else opgion which is a manual option where the user makes the choices. See the link below.

[https://ubuntu.com/tutorials/install-ubuntu-desktop?gclid=CjwKCAiAhreNBhAYEiwAFGGKPHzOmrxvS4rdDzfMKjv0R9PwxmZjaFQ-cGmGXTo9HZsLSYKpSm8UmRoC_aMQAvD_BwE#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop?gclid=CjwKCAiAhreNBhAYEiwAFGGKPHzOmrxvS4rdDzfMKjv0R9PwxmZjaFQ-cGmGXTo9HZsLSYKpSm8UmRoC_aMQAvD_BwE#1-overview)

[https://ubuntu.com/server/docs/installation](https://ubuntu.com/server/docs/installation)

So the choice is up to the user instaling.

---

### Post by grahammechanical on 2021-12-06
Your question has been answered but I think that you need a bit more information to avoid a very common mistake. If you have a modern machine with Windows 8 or Windows 10 installed then this "previous" OS, as you call it, will be installed in UEFI mode. That means that Ubuntu must also be installed in UEFI mode. How you load the Ubuntu ISO image will determine the mode Ubuntu is installed in. You make the selection in the UEFI/BIOS settings.

If you install Ubuntu in BIOS/CSM/Legacy mode with Windows installed in UEFI mode then it will be difficult to chose which OS you want to load. If you install Ubuntu in the same mode as Windows then you will get the Ubuntu bootloader (GRUB) menu that should give you a choice to load Ubuntu or Windows. That will make life much simpler.

If you are running Windows 10 then you must deactivate Windows fast startup. It is a form of hibernation that will prevent the Ubuntu installer from recognizing that there is another OS on the drive.

Regards

---

### Post by sotonye on 2021-12-08
Thanks for help. 
I want Ubuntu to be my primary Operating System.

---

### Post by sotonye on 2021-12-08
Thanks for so much for help.
Am going to install Ubuntu next week when i get my USB drive.

---

