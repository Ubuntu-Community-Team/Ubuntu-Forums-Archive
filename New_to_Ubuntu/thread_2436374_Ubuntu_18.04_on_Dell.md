---
title: "Ubuntu 18.04 on Dell"
date: 2020-02-05
forum: New to Ubuntu
---

### Post by nick1971 on 2020-02-05
Hello everyone. Since yesterday, I have been an extremely satisfied owner of a Dell Vostro 3584 with Ubuntu 18.04 LTS preinstalled. I would like to ask two things:
1. There are no SATA data for my SSD, therefore I can't run any diagnostic tests or have access to important information about my drive.
2. The operating system has an OEM kernel. In two months' time, the new Ubuntu LTS will be released. How will I upgrade? Will there be a new OEM iso so as I can proceed with a clean install?
Thanks in advance.

---

### Post by mastablasta on 2020-02-05
is it the one with Intel CPU?

1. smartmon tools work: [https://www.smartmontools.org/wiki/NVMe_Support](https://www.smartmontools.org/wiki/NVMe_Support)
ubuntu and smartmontools: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
more: [https://www.percona.com/blog/2017/02/09/using-nvme-command-line-tools-to-check-nvme-flash-health/](https://www.percona.com/blog/2017/02/09/using-nvme-command-line-tools-to-check-nvme-flash-health/)

2. you current LTS is supported until spring 2023. i don't think there will be an OEM iso you could use. i would suggest trying 20.04 form live USB. if everything works there you can upgrade the system in the usual way.: [https://ubuntu.com/tutorials/tutorial-upgrading-ubuntu-desktop#1-before-you-start](https://ubuntu.com/tutorials/tutorial-upgrading-ubuntu-desktop#1-before-you-start)

---

### Post by nick1971 on 2020-02-05
Hello everyone. I have a Dell Vostro 3584 preinstalled with Ubuntu 18.04 which runs on an oem kernel. Will I be able to upgrade to the upcoming 20.04 version? Thank you in advance.

---

### Post by CelticWarrior on 2020-02-05
Yes, of course (and FYI it doesn't run a different kernel).

---

### Post by crip720 on 2020-02-05
Ubuntu usually only offers to upgrade after a couple of months of a new LTS coming out.  20.04 will come out in April or people who want to do clean installs, but system upgrades should be available in June.  Can set your software updater to let you know when it is available.

---

### Post by slickymaster on 2020-02-05
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by oldrocker99 on 2020-02-06
> **nick1971 said:**
> Hello everyone. I have a Dell Vostro 3584 preinstalled with Ubuntu 18.04 which runs on an oem kernel. Will I be able to upgrade to the upcoming 20.04 version? Thank you in advance.

There have been many posts, over the years, from people who have had trouble upgrading in place. I personally highly recommend that you just install 20.04. You **may** be successful, but you **might** have trouble.

Make sure you back up /home before doing *anything!*

---

