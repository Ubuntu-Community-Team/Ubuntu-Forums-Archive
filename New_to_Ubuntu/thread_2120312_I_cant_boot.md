---
title: "I cant boot"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by Brown256 on 2013-02-26
hi, i just finished installing my copy of ubuntu and i was asked to restart my computer. i did that and now my computer is giving me the following error message:"error: no such device: e8f32c5a-bc3d-4efb-ab3f-849b866ad575.
grub rescue>"
Now i cant even boot into my windows 7.
can anyone please help me out?

---

### Post by mapes12 on 2013-02-26
Google Boot Repair. Boot from your live media. Install Boot Repair in your live session and run it. Then boot from HDD to see if it's fixed the Grub problem.

---

### Post by oldfred on 2013-02-26
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

