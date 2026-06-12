---
title: "Unable to Boot Ubuntu 16.04.2 LTS on HP 15-AW009AX (AMD GPU)"
date: 2017-06-27
forum: New to Ubuntu
---

### Post by mroche1991 on 2017-06-27
Hi, [COLOR=#111111][FONT=Ubuntu]I want to install Ubuntu 16.04.2 LTS on my HP Pavilion 15-AW009AX
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]AMD 9600P Processor
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]AMD Radeon R7 M440 GPU

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I followed the installation guidelines to install Ubuntu via both a bootable USB flash drive and a disk. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I found the screen was freezing upon installation at the ubuntu load screen. After browsing through a few forums [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] I found that replacing "quiet splash" with "nomodeset" within the "Install Ubuntu" command was able to begin the installation process. Upon re-booting the login screen appears but I get stuck in a login loop and eventually a text console appears with lines such as "AMD-Vi: Completion-Wait loop timed out" repeated several times. I have also tried adding iommu=soft and amd_iommu=off to the line starting with "linux" within the grub terminal which still results in the same issue.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I have found another post on the ask ubuntu forums which lists a similar issue encountered when trying to boot ubuntu onto a HP laptop with similar specs: <[/FONT][/COLOR]https://askubuntu.com/questions/916348/hp-laptop-amd-apu-fail-to-boot-live-linux-cd>

[COLOR=#111111][FONT=Ubuntu]The post mentioned above conatins a link to a patch which I believe may solve the issue. I am unsure how to go about applying the patch, especially considering I am unable to login to Ubuntu and access the terminal. Will I be required to patch and compile the source code for the kernal?[/FONT][/COLOR]

---

