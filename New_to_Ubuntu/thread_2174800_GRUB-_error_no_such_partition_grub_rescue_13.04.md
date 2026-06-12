---
title: "GRUB- error: no such partition grub rescue 13.04"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by wal2-171 on 2013-09-16
I know there is a solved posts for the same problem and i followed the steps but it didn't work for me....

my laptop is dell inspairon 5521 windows 8 pro ...i had ubuntu 13.04 install and everything was working fine till i had a problem with ubuntu so i deleted the partition with ubuntu installed in it
and now all i got is this message error: no such partition grub rescue ..

what i tried so far, i tried to install ubuntu again and nothing happen

i tried to refresh windows with windows 8 cd and i get this message " the option is not supported on the operation system you've selected"
i tried to reinstall windows and same thing happen.

pls [SIZE=3]**help**[/SIZE] i'm frustrated ...now i'm using my laptop with the option of try ubuntu before install 
-----------------------------------------------------
update : after installing ubuntu again this message appears when i started my laptop :
"error: file '\boot/grub/i386-pc/normal.mod' not found. grub rescue>"

(english is not my native language . i'm sorry for spelling and grammar mistakes)

---

### Post by grahammechanical on 2013-09-16
Do you understand what happened? The Grub boot menu was looking to a certain partition for Ubuntu but you have deleted that partition and so the boot menu cannot find Ubuntu to boot and it puts you into Grub Rescue mode. What else could it do?

Please explain what you mean by "nothing happened" when you tried to re-install Ubuntu. You do not give us any clues as to what the problem could be. The only way to get Ubuntu back is to re-install it and then the boot menu would know where to find Ubuntu. It may also detect the Windows installation and load Windows for you.

As for Windows 8, I can give you no advice. You should not need to re-install Windows 8 or refresh it. 

Regards.

---

### Post by wal2-171 on 2013-09-16
thank u for reply..
i understand what happened but i dont know how to fix it..
i ment by nothing happened is im stuck at Grub Rescue mode because i deleted the partition and the message was showing is 
[h=2][SIZE=3]"error: no such partition grub rescue[/SIZE]"[/h]and now after i installed ubuntu 13.4 im still stuck at Grub Rescue mode and the message changed to 

**[SIZE=3]"error: file '\boot/grub/i386-pc/normal.mod' not found. grub rescue>"[/SIZE]**

---

### Post by oldfred on 2013-09-16
This may let you fix system, or post link.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

