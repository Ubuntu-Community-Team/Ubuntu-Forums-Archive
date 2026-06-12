---
title: "Where is the correct place to talk about Ubuntu on the Raspberry PI ?"
date: 2020-09-02
forum: New to Ubuntu
---

### Post by vasco65 on 2020-09-02
The Subject says it all, I installed ubuntu on my raspberry pi 4 with 8 Gb ram and I'm using it as my desktop. And I have a few questions that may be specific to this platform, is there a correct place to discuss it ?

tks

```
~$ cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS"
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

```

---

### Post by CelticWarrior on 2020-09-02
Welcome.

This forum is for all things Ubunt**u**. We don't do "Ubunto" though.

---

### Post by vasco65 on 2020-09-02
ups.... sorry.... can't correct the subject. :-(

---

### Post by TheFu on 2020-09-02
How did you get a pi v5 before the rest of the world?
[https://www.raspberrypi.org/forums/viewtopic.php?t=269832](https://www.raspberrypi.org/forums/viewtopic.php?t=269832)

---

### Post by vasco65 on 2020-09-02
typo :-( fixed...

---

### Post by trpted on 2020-09-02
Just ask the question and let the mods/admin handle where it goes.

---

### Post by CelticWarrior on 2020-09-02
> **trpted said:**
> Just ask the question and let the mods/admin handle where it goes.

Yeah, pretty much.

RPis aren't that different as to need a special section. However, as with any ARM architecture make sure to mention the hardware in the posts.

Ubuntu for ARM has a few specific issues. Most issues are common and have the same solutions, others will need a different solution.

So, if it's about drivers or something not working the Hardware section should be a good fit.
If it's about the Desktop Environment then, of course, Desktop Environments.
Any problem with networks goes to Networking & Wireless.
(...)

---

### Post by TheFu on 2020-09-02
Many things are the same with raspberry pis as they are with normal amd64/intel64 settings, but when it comes to specific hardware support, then it can be extremely different.  I think of Raspberry Pi questions similar to the way I think about running Ubuntu on Apple hardware. If it doesn't seem hardware connected, then I'll try to help.

FYI: [https://www.phoronix.com/scan.php?page=news_item&px=Raspberry](https://www.phoronix.com/scan.php?page=news_item&px=Raspberry)
For example, performance of v4 Pis doesn't compare favorably to low-end Celerons. 
[https://openbenchmarking.org/embed.php?i=2007316-NE-RPINTEL8536&sha=13c594602804&p=2](https://openbenchmarking.org/embed.php?i=2007316-NE-RPINTEL8536&sha=13c594602804&p=2)

Whenever posting a question related to HW, please be certain to mention early in the title, "r-pi v4."
If it isn't obviously related to HW, best to mention it in the question text somewhere so people aren't blindsided.

---

