---
title: "Issues on Boot Up"
date: 2019-11-07
forum: New to Ubuntu
---

### Post by kayrish52 on 2019-11-07
Hello,

I am relatively new to Ubuntu. I am trying to troubleshoot where my boot up process is going wrong. I built a new PC with some powerful components and I want it to be a powerful data processing Lubuntu box. Installed everything and the OS worked well for a day. Then I ran into issues on bootup. I see the following things happen:
1. Motherboard BIOS/UEFI appears to work fine.
2. Grub 2.02 OS Selector pops up. Shows 4 versions of Ubuntu. Ubuntu 18.04.0.0.32-generic, Ubuntu 18.04.0.0.23-generic, and a recovery version for both.
3. When I select Ubuntu 18.04.0.0.32, I see a list of boot up items flash by the screen, then it gets hung up and never enters the Graphical Interface phase where I can log in.
4. Errors I have seen include:
[COLOR=#000000]Couldn't get size: ...[/COLOR]
[COLOR=#000000]MODSIGN: Couldn't get UEFI db list[/COLOR]
[COLOR=#000000]Couldn't get size: ...
5. I implement the changes in this post, and I get a set of new errors that scroll to fast to read. [/COLOR][https://ubuntuforums.org/showthread.php?t=2407705](https://ubuntuforums.org/showthread.php?t=2407705)
6. Everything ultimately gets hung up with 'AHCI unavailable' or something to that extent.

Let me know what else you need.

Thanks,

---

### Post by oldrocker99 on 2019-11-07
Basically, the advice says to reinstall with Legacy mode. I have, personally, never had a working install using UEFI; Grub fails to install every time.

It's never failed in Legacy mode, FWIW.

---

