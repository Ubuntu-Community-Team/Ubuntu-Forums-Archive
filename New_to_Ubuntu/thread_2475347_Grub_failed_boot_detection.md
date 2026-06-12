---
title: "Grub failed boot detection"
date: 2022-05-23
forum: New to Ubuntu
---

### Post by periyasamic on 2022-05-23
Hi fnds...

I am new to Ubuntu. And install latest version of Ubuntu 22.04. it was successfully installed. After that I install proton vpn, last step I mistakenly changed the desktop environment so that affect my laptop graphics driver . Screen shows bigger... After that I do many way to try my laptop normal but I am very tired. So I reinstall again Ubuntu. After successful installation, laptop stuck on black screen with underline blinking... I know this is boot failure. ... Grub not loading well..

I saw many videos and try that methods, but none of the methods was working.... Then I install previous version of Ubuntu 20.04 then it was fine... After I upgrading my Ubuntu to latest version. Again that issue came.. grub failed boot detection.... Then I walkover from Ubuntu..... Now I am using zorin os.... But I like Ubuntu very much... Please give any solution to solve this issue.....


&#128554;&#128554;&#128554;

---

### Post by yancek on 2022-05-24
Is Zorin now the only OS installed?  If that's the case, you will not be able to resolve the problem with 22.04 unless it is installed as there are a number of reasons for the blinking cursor but all of them are related to Grub not being correctly installed.  Are you using a UEFI system or Legacy/CSM?  You might try booting with the Ubuntu install USB and select the Try Ubuntu option.  Then use GParted on the Ubuntu USB and create some unallocated space (20-30GB) on which to install Ubuntu if you have no unallocated space now.  Then go back and install Ubuntu there.  If it doesn't boot, go back and use the Ubuntu install USB again and go to the boot repair site below and download and run boot repair.  The boot repair site has instructions, use the 2nd option on the page and select Create BootInfo  Summary and it will give you a link that you can post here and members will be able to view it.  It will have a lot of information and someone should be able to help.  Without this information, anyone trying to help now will simply be guessing. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

