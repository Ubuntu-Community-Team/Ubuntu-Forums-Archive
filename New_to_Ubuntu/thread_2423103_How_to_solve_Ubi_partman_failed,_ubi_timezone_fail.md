---
title: "How to solve Ubi partman failed, ubi timezone failed error?"
date: 2019-07-17
forum: New to Ubuntu
---

### Post by x202 on 2019-07-17
Currently no OS is installed on my laptop. I am trying to install ubuntu 16.04 but i am getting issues like ubi partman failed, ubi timezone failed  installer crashed. If  i choose continue anyway installation freezes when scanning disk stage running. I want to install ubuntu anyhow .   My laptop model is asus X441UA.

---

### Post by oldfred on 2019-07-17
Have you updated UEFI and if SSD updated SSD firmware?

Did you verify downloaded ISO is correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
       Asus Zenbook UX433FN with nVidia
[https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn](https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn)
Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)
Asus X541UV [SOLVED] How to partition my ssd in order to install ubuntu 17.10 / 16.04.4
[https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)

Many models of Asus need this boot parameter in addition to nomodeset (if nVidia).
       How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221)

---

### Post by Impavidus on 2019-07-17
Good comments by oldfred (as always).

The Asus X441UA comes in multiple versions or some components may have been replaced. More specific specs may help.

Ubuntu 16.04 LTS is over 3 years old, although 16.04.5 has a hardware enablement stack only 1 year old. Still, Ubuntu 18.04 LTS may give better results and certainly has a longer support period left.

---

