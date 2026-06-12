---
title: "Upgrade to Ubuntu 16.04 LTS?"
date: 2016-05-11
forum: New to Ubuntu
---

### Post by rdb3 on 2016-05-11
Hello, I  just did 

lsb_release -a

and see that I am running

Ubuntu 14.04.4 LTS trusty.

I then went here..

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

and do not see 14.04.4 LTS.

Is the end of life for 14.04.4 LTS also August 2016?  As a newbie to Ubuntu, is it time for me to start thinking about upgrading to Ubuntu 16.04?


I just found this..

Ubuntu 14.04 LTS is supported until mid-2019 on desktop, server and core.

[http://www.omgubuntu.co.uk/2016/02/14-04-4-lts-released-whats-new](http://www.omgubuntu.co.uk/2016/02/14-04-4-lts-released-whats-new)

So based on that, one does not need to upgrade right now ........ unless one just wants to..... agree?

---

### Post by philinux on 2016-05-11
Always best for stability etc to wait for the point release 16.04.1
You will then be automagically be offered the upgrade.
Usually 3 months after 16.04 was released.

---

### Post by howefield on 2016-05-11
> **rdb3 said:**
> So based on that, one does not need to upgrade right now ........ unless one just wants to..... agree?

Agreed.

Which kernel are you running ?

```
uname -r
```

---

### Post by rdb3 on 2016-05-11
3.19.0-59-generic

---

### Post by rdb3 on 2016-05-11
> **philinux said:**
> Always best for stability etc to wait for the point release 16.04.1
**You will then be automagically be offered the upgrade**.
Usually 3 months after 16.04 was released.

Thanks, I didn't know that!

The wiki ubuntu dates confused me on 14.04.  At this time I really have no reason to change.

---

### Post by howefield on 2016-05-11
Your kernel will go end of life in July 2016, and probably the graphics stack too.

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

---

### Post by philinux on 2016-05-11
> **rdb3 said:**
> Thanks, I didn't know that!

The wiki ubuntu dates confused me on 14.04.  At this time I really have no reason to change.

From the wiki.

> Upgrading from Ubuntu 14.04 LTS or 15.10

14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

To upgrade on a desktop system:

    Open the "Software & Updates" Setting in System Settings.
    Select the 3rd Tab called "Updates".
    Set the "Notify me of a new Ubuntu version" dropdown menu to "For any new version" if you are using 15.10, set it to "long-term support versions" if you are using 14.04 LTS.
    Press Alt+F2 and type in "update-manager" (without the quotes) into the command box.
    Software Updater should open up and tell you: New distribution release '16.04 LTS' is available.
    Click Upgrade and follow the on-screen instructions. 


---

### Post by grahammechanical on 2016-05-11
> Ubuntu 14.04 LTS is supported until mid-2019 on desktop, server and core.

It is not that simple. The Linux kernel that came with 14.04 & 14.04.1 (version 3.13) is supported with security fixes until April 2019. But the kernels that come with 14.04.2; 14.04.3 & 14.04.4 (versions 3.16; 3.19 & 4.2) are only supported with security fixes until August 2016.

You have the 3.19.kernel, So, your desktop has been upgraded to 14.04.4 but what is called the Hardware Enablement Stack (HWE) has not been upgraded to the HWE in Ubuntu 15.10. If all your hardware is being recognised by Linux there is no need to upgrade the HWE. So, it is not done automatically by the operating system. And as regards support it makes no difference. The 4.2 kernel is only supported to August 2016 as well.

You have a choice, a) to upgrade to 14.04.5 when it comes out in August 2016 and upgrade the HWE to get the Linux kernel 4.4 and get continued support for the kernel until April 2019. Or, b) Upgrade to 16.04.1 when it comes out in August 2016 and get kernel 4.4 which will be supported in 16.04.1 for 4 years & 9 months.

Here is where I get my information from.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards

---

### Post by rdb3 on 2016-05-11
> **grahammechanical said:**
> It is not that simple. The Linux kernel that came with 14.04 & 14.04.1 (version 3.13) is supported with security fixes until April 2019. But the kernels that come with 14.04.2; 14.04.3 & 14.04.4 (versions 3.16; 3.19 & 4.2) are only supported with security fixes until August 2016.

You have the 3.19.kernel, So, your desktop has been upgraded to 14.04.4 but what is called the Hardware Enablement Stack (HWE) has not been upgraded to the HWE in Ubuntu 15.10. If all your hardware is being recognised by Linux there is no need to upgrade the HWE. So, it is not done automatically by the operating system. And as regards support it makes no difference. The 4.2 kernel is only supported to August 2016 as well.

You have a choice, a) to upgrade to 14.04.5 when it comes out in August 2016 and upgrade the HWE to get the Linux kernel 4.4 and get continued support for the kernel until April 2019. Or, b) Upgrade to 16.04.1 when it comes out in August 2016 and get kernel 4.4 which will be supported in 16.04.1 for 4 years & 9 months.

Here is where I get my information from.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards

Thank you..... very helpful information.  I will wait until August to decide.  So far my hardware is being recognized.  In the meantime, I will try to familiarize myself with 16.04.

---

### Post by vasa1 on 2016-05-12
A post was moved from here to [http://ubuntuforums.org/showthread.php?t=2324331](http://ubuntuforums.org/showthread.php?t=2324331) because it was about installation of 16.04 rather than upgrading to 16.04.

---

