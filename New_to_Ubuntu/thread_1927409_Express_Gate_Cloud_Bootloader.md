---
title: "Express Gate Cloud Bootloader??"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by davidc60 on 2012-02-17
Hi,
I have recently reinstalled Windows 7 Starter on Partition 1 of my Asus 1015PEM. Then I installed 3 Linux distributions on Partitions 2, 3 and 4 (Ubuntu; EasyPeasy and Peppermint). They operate using Grub2 and as the Windows MBR has been overwritten by Grub2, Windows 7 Starter was then chainloaded via the most recent Linux install. On pressing the main power-on button the Grub 2 bootloader menu appeared in the normal way allowing a choice of which operating system to boot into.
 
I then reinstalled the latest version of Express Gate Cloud within Windows (where it is supposed to be) and Express Gate Cloud itself boots-up as it normally should via its own separate, dedicated power-on button on the netbook. For readers unfamiliar with Express Gate Cloud, it is a Splashtop/Linux based 'Instant-On' OS shipped by ASUS with their netbooks
 
However, when I now press the main power-on button it boots straight into Windows 7 Starter and no longer shows the usual Grub2 menu.
 
Clearly, the re-installation of Express Gate Cloud seems to have overwritten the Grub2 MBR which itself had overwritten the Windows MBR. (I know how to restore both the Grub2 MBR and the original Windows MBR if I ever want to do so, so that is not the issue).
 
My enquiry is simply whether Express Gate Cloud has actually already restored the original Windows MBR by doing this? If so, exactly what files has it used to do so and where can I find them? If not, and most crucially what bootloader has EGC overwritten the Grub2 MBR with? (The response I had from ASUS is that their engineers 'cannot answer this' !!).
 
Many thanks,
davidc60

---

