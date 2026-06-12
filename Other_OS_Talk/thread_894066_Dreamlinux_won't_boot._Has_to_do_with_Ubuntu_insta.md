---
title: "Dreamlinux won't boot. Has to do with Ubuntu instalation..."
date: 2008-08-18
forum: Other OS Talk
---

### Post by Animeniac on 2008-08-18
I have made different partitions for each of the Linux distros I want installed on my computer. Each one also has its own /home partition. I also want to use just one boot loader. I also gave each partition mount points for my installations. For example, hda5 is my Ubuntu root partition and when installing openSUSE, I mounted it as /ubuntu. I also mounted the Ubuntu home partition (hda6) as /ubuntu/home. Here is what I have done:

1. I have installed openSUSE with a GRUB boot loader saved in the /root partition.
2. I have installed Dreamlinux without any boot loader.
3. I have installed Ubuntu with a GRUB boot loader saved in "hd0".

The boot loader installed by the Ubuntu installer reads Dreamlinux as "Debian GNU/Linux...". Then I select it and then the screen with the Dreamlinux logo and the loading bar pops up with a text box under it. When the text box says "waiting for root file system", Dreamlinux won't keep loading. After a few minutes, I get a black text screen with "/bin/sh: can't access tty; job control turned off". Then the loading stopped.

What did I do wrong??? What was I supposed to do before I installed Ubuntu?

Installing Dreamlinux and adding it as a boot option in Ubuntu's GRUB boot loader also doesn't work for me, because when I load Ubuntu, I get a text screen ending with "Press control-D to resume booting". I don't like it.

Please, help me get my computer able to boot both Dreamlinux and Ubuntu right.

---

### Post by kiwiadam2 on 2008-08-18
Partitioning is a pain. Use virtualization, its easier.

---

