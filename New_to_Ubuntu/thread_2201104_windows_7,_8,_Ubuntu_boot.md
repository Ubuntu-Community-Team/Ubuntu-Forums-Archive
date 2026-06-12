---
title: "windows 7, 8, Ubuntu boot"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by joshua14 on 2014-01-22
hello I have windows 7 and 8 installed on my computer and they both boot fine. I shrunk my drive and installed ubuntu 13.10 on the new partitions I created. one for boot one for root one for home and one for swap. the install ran fine but upon rebooting my computer I still only have the option to boot windows 7 and 8. how  can I easily fix this? I'm new to linux and I have little experience using the command prompt but I am willing to try.

---

### Post by oldfred on 2014-01-22
Best to see details. You may just need to install the grub2 boot loader to the MBR if a BIOS install. If a newer UEFI install you just have to choose ubuntu entry in UEFI menu.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

