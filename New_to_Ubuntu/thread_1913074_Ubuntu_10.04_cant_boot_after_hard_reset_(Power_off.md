---
title: "Ubuntu 10.04 cant boot after hard reset (Power off)"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by ACORQ on 2012-01-21
Hi all, can someone help me to understand what is happening and how can i fix it. This is the message that appears on the screen:

> [    7.842285] Code: 00 55 89 e5 57 89 c7 56 53 e8 b3 f7 22 00 8b 5f 04 b8 ff ff
 ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 40 1e 7a c0 8b 57 14 <8b> 14 0a
89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 cc af 59 c0 ba
[    7.843079] EIP: [<c035daea>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f6a7
9d6c
[    7.843079] CR2: 00000000017bd000
[    7.844918] ---[ end trace e9c6c0694ef25562 ]---
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootrag


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1unbuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   35.082209] atkbd.c: Unknown key pressed (translated set 2, code
0xd9 on isa0060/serio0).
[   35.082275] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[00035.082867] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa
0060/serio0).
[   35.082935] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Thank you

---

### Post by SuaSwe on 2012-01-21
Hello there!

Do/could you have a LiveCD to hand? If you boot into it, can you still see, mount and access your old partition(s)?

---

### Post by sandyd on 2012-01-21
> **ACORQ said:**
> Hi all, can someone help me to understand what is happening and how can i fix it. This is the message that appears on the screen:


Thank you
Sounds like a corrupted /boot or /root or initrd.

Boot into a livecd, and see if FSCKing the partitions help.

---

### Post by ACORQ on 2012-01-22
> **SuaSwe said:**
> Hello there!

Do/could you have a LiveCD to hand? If you boot into it, can you still see, mount and access your old partition(s)?
How do i do it, i can create a live cd, but i have no idea what to do after that. 
Before i posted the original question i tried to reboot from wubi, but it didn't give any options to do other than "try" or "install" .Can you help me?. Thank you.

---

### Post by SuaSwe on 2012-01-22
When you say you tried to reboot from Wubi, do you mean this is a Wubi install? I thought it looked like an independent partition. If it's a Wubi install, I'm afraid I've no clue how to progress! I must say though I thought the symptoms looked typical of a regular install. Anyone else able to assist?

You can read more on the uses of the brilliant LiveCD here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) . Maybe have a go of booting from the LiveCD, opening Terminal and typing 'sudo fdisk -l' and posting the output here; the output should clarify whether you have a separate Ubuntu partition at any rate! You can read more about SD's suggestion in various places on the forum and outside, for example [[COLOR=BLUE]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1518426"). :)

---

### Post by ACORQ on 2012-01-23
> **SuaSwe said:**
> When you say you tried to reboot from Wubi, do you mean this is a Wubi install? I thought it looked like an independent partition. If it's a Wubi install, I'm afraid I've no clue how to progress! I must say though I thought the symptoms looked typical of a regular install. Anyone else able to assist?

You can read more on the uses of the brilliant LiveCD here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) . Maybe have a go of booting from the LiveCD, opening Terminal and typing 'sudo fdisk -l' and posting the output here; the output should clarify whether you have a separate Ubuntu partition at any rate! You can read more about SD's suggestion in various places on the forum and outside, for example [[COLOR=BLUE]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1518426"). :)
You are right this is the only OS in that computer, but instead of using a live CD the first time i just tried with a usb stick thinking it would produced the same effect. 
Now, i tried using the Live CD and pressing CTRL+ALT+F1 as stayed in [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but it didn't work, i still ended up on the screen that gives you the option to try or to install.
If this can not be fixed, do you know if there is another way to access or recover the data inside the HD to later reinstall Ubuntu again, because i just notice i should have use the AMD 64 version of LTS. This Laptop came with Vista 32, but i never checked that the processor is an AMD Turion 64. 
Sorry for diverting from the main point. If i enter the trial version of LTS and enter the terminal can i fix, reinstall or update the existing install without deleting the info inside?

---

### Post by ACORQ on 2012-01-23
> **sandyd said:**
> Sounds like a corrupted /boot or /root or initrd.

Boot into a livecd, and see if FSCKing the partitions help.
How? when you say booting into the Live CD do you mean getting in the desktop of  the Live CD and entering the terminal? and what instructions should i type?

---

### Post by |{urse on 2012-01-23
> You are right this is the only OS in that computer, but instead of using a live CD the first time i just tried with a usb stick thinking it would produced the same effect. 
Now, i tried using the Live CD and pressing CTRL+ALT+F1 as stayed in [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but it didn't work, i still ended up on the screen that gives you the option to try or to install.

actually, when you get to that menu that says try or install, select try

press ctrl alt f1 when you are on the desktop then follow the rest of the directions

---

