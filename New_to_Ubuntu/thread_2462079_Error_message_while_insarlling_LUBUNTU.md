---
title: "Error message while insarlling LUBUNTU"
date: 2021-05-13
forum: New to Ubuntu
---

### Post by eli-beths-elza on 2021-05-13
As i manual partitioned, i set 1gb fot boot, 4gb as swap, 100gb as root and 100gb as home. But after clicking next it shiwed a message "A GPT partition table is the best option for all systems. This installer suports such a setup for BIOS system. To configure a GPT partition table, go back  and set the oartition table to GPT, next, create a 8MB unformattted partition with the bios_grub flag enabled." Please someone tell me what should i do!  IM NEW TO LINUX COMMUNITY

---

### Post by guiverc on 2021-05-13
Welcome to Ubuntu Forums :)

It's a warning more than an error message.

You've selected MBR/DOS/*legacy* partition table instead of the normal GPT.  (*don't worry, the box I'm using to reply here is MBR too*)

If your box uses uEFI or Secure-uEFI, it maybe a problem, but if your box is BIOS/*legacy* your system will boot anyway (*the warning applies to uEFI setups; and you didn't provide specifics as to your release, and/or your hardware or firmware settings*).

I'll provide the manual page most appropriate - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)   (*scroll down to Manual partitioning*).

A question I answered on a question somewhat similar can be found at [https://askubuntu.com/questions/1273421/lubuntu-installer-giving-error-after-partition-creation-your-system-may-or-may](https://askubuntu.com/questions/1273421/lubuntu-installer-giving-error-after-partition-creation-your-system-may-or-may) which may also be helpful (if your box is uEFI)


Note:  You didn't provide any release details; so the manual I've linked is the latest *stable* release, meaning Lubuntu 21.04 (2021-April release).  If you're on Lubuntu 20.04 LTS for example, you'll just swap out "*stable*" with "*lts*" in the URL to read that manual.

---

### Post by ActionParsnip on 2021-05-13
100Gb for root is quite a lot. Could easily get away with 60Gb. More space for user data. Lubuntu is lean and doesn't use a lot of space

---

### Post by GhX6GZMB on 2021-05-13
> **ActionParsnip said:**
> 100Gb for root is quite a lot. Could easily get away with 60Gb. More space for user data. Lubuntu is lean and doesn't use a lot of space

30 GB is plenty, unless you need a lot of software with big libraries (eg, CAD), and they can be relocated to /home.

The Lubuntu installer is quite friendly, but partitioning can be challenging for a beginner.
Do a manual partition with the first partition (/sda1) as 30 GB, ext4, mount point / and boot flag set. Select format.
A second partition (/sda2) with size RAM + 25%, type SWAP.
The rest of the space (/sda3) as ext4, mount point /home. Select format.

That should get you up and running.

---

