---
title: "Dual boot with 12.04 and Win 7 not loading ubuntu"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by Wolffee on 2012-09-28
Hey guys,
I have moderate amounts of computer savvy-ness but a couple of my friends that are better at computers than I helped me dual partition my hard drive with ubuntu and windows 7. The computer came with win 7 and the ubuntu boot went fine. I know it's still partitioned right because my hard drive space is still split but when I start up my computer I'm given no option to boot unbuntu. Pressing F12 just gives me win 7 booting options. I've been reading online and it seems like some people have trouble with GRUB2 but I don't know how to tell if that's my issue or how to fix it. Any advice would be greatly appreciated. 
Thanks

---

### Post by oldfred on 2012-09-28
Welcome to the forums.

Download into your liveCD/USB and post the link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Wolffee on 2012-09-28
[http://paste.ubuntu.com/1248552/](http://paste.ubuntu.com/1248552/)
Here is the Url, thank you for your help!

---

### Post by oldfred on 2012-09-28
Your MBR only has grub in it now. What happens when you boot?

Do you get grub menu and does both Ubuntu & Windows boot?

If not booting:
The issues could be related to either a BIOS setting or grub bug where large root partitions or one's far from start of drive with these newer large drives have issues. 

Also some have video issues after grub menu until video drivers are installed. What video card/chip do you have?

---

### Post by Wolffee on 2012-09-28
It fixed it! Thank you so much

---

