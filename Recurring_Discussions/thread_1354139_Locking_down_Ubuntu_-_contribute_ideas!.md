---
title: "Locking down Ubuntu - contribute ideas!"
date: 2009-12-13
forum: Recurring Discussions
---

### Post by ram2500 on 2009-12-13
Hi all, 

Linux is a really secure system, however, I've noticed a big security problem with the Ubuntu start-up: you can drop to root shell prompt. If a theft or someone who merely had access to the machine, would occur, the thief or hacker could delete, modify or read/retrieve files. Very scary. I am thinking that the "root shell prompt" isn't the only security problem. Can others on the Ubuntu Forums talk about other security holes they've discovered and post them? We should all discuss potential problems and give solutions. I'm sure many are interested and concerned about the security holes throughout the system (every system has them;)) - any and all information is useful!

If you are posting about a potential security problem prior to 9.10, please designate that.

Thanks!

---

### Post by tubbygweilo on 2009-12-13
The use of full disk encryption may well keep your data safe but then the thief has your kit and will no doubt just reformat the hard disk and sell your machine on to others. If someone has physical access to your kit then you should no longer view it as yours but as something owned by others. Not much else to say other than don't let it out of your sight if at all possible.

---

### Post by BkkBonanza on 2009-12-13
Getting root access at boot is no surprise, and it's not something to fix. It's a well established fact that physical access means full, root access.

Short of using encryption you have no protection against accessing drive data. Any user who steals your laptop can just pop the drive and plug it into any other system (where they do have root) and access the data. So unless you use encryption there is no way to lock down the drive. This is the same for any data on any OS.

---

### Post by bodhi.zazen on 2009-12-13
> **ram2500 said:**
> Hi all, 

Linux is a really secure system, however, I've noticed a big security problem with the Ubuntu start-up: you can drop to root shell prompt. If a theft or someone who merely had access to the machine, would occur, the thief or hacker could delete, modify or read/retrieve files. Very scary. I am thinking that the "root shell prompt" isn't the only security problem. Can others on the Ubuntu Forums talk about other security holes they've discovered and post them? We should all discuss potential problems and give solutions. I'm sure many are interested and concerned about the security holes throughout the system (every system has them;)) - any and all information is useful!

If you are posting about a potential security problem prior to 9.10, please designate that.

Thanks!

Moved to recurring discussions. Physical access == root access is true of any OS and has been discussed many many times.

In terms of security tips, please see the stickies in the security section.

If you want to see what locked down Ubuntu might look like, try Zenix :

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

In addition to the security enhancements, the guest account is confined by apparmor.

---

