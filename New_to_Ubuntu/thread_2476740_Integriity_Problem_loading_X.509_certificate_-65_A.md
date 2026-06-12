---
title: "Integriity: Problem loading X.509 certificate -65 After installing Ubuntu"
date: 2022-07-05
forum: New to Ubuntu
---

### Post by caox22 on 2022-07-05
Hi, i'm new with Linux!
I bought a notebook that came with Satux installed on it and i changed to Ubuntu.
After the installation of Ubuntu, i get "[B][      0.16033] integrity: Problem loading X.509 certificate -65
/dev/nvme0n1p2: clean, 231092/15597568 files, 4183345/62383360 blocks[/B]" every time i turn on my pc.
I tried to check my disk using shell command and it looks fine, i also tried to enable secure boot, but didn't work either.
Can some one help me with that?

---

### Post by grahammechanical on 2022-07-05
I suggest you explain how you changed from Satux to Ubuntu. Have you encrypted the partition that Ubuntu is on?

[https://www.howtouselinux.com/post/understanding-x509-certificate-with-openssl-command](https://www.howtouselinux.com/post/understanding-x509-certificate-with-openssl-command)

Regards

---

### Post by ActionParsnip on 2022-07-05
Looks like a secure boot thing. Is this a dual boot system?

---

### Post by caox22 on 2022-07-05
I followed a tutorial on yt, making a bootable pendrive. I just made the bootable pendrive, ran it and chose the option to install ubuntu.
In this tutorial i needed to change my bios to legagy in order to change my boot device but i returned it to the original state, after the installation.
Its not a dual boot system.

---

