---
title: "&quot;sudo nvidia-glx-config enable&quot; cmd not found"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by hoisinnlies on 2008-04-26
Newbie to Linux and Ubuntu.  

Have been trying to get my Nvidia FX550 PCI to work on the Hardy Heron version.

Been following instructions on [http://ubuntuforums.org/showthread.php?t=33142]("http://ubuntuforums.org/showthread.php?t=33142") but it does not seem that the enable command works.

Is there a different string to enter?

Thanks in advance for any assistance,

Richard.

EDIT: I have by the way discovered that this command is dropped in Hardy, so all I am asking is what to use instead.

---

### Post by overdrank on 2008-04-26
> **hoisinnlies said:**
> Newbie to Linux and Ubuntu.  

Have been trying to get my Nvidia FX550 PCI to work on the Hardy Heron version.

Been following instructions on [http://ubuntuforums.org/showthread.php?t=33142]("http://ubuntuforums.org/showthread.php?t=33142") but it does not seem that the enable command works.

Is there a different string to enter?

Thanks in advance for any assistance,

Richard.

EDIT: I have by the way discovered that this command is dropped in Hardy, so all I am asking is what to use instead.

Hi and welcome, that "how to" is way out of date. I am assuming you have a onboard graphics along with the nvidia graphics. Have you tried to install the restricted drivers located under system, administration, hardware drivers? Also post the output of the command ```
lspci
```

---

### Post by mcapozzi on 2008-05-02
I am having the same problem after upgrading from 7.10 to 8.04.

The package nvidia-glx-new for AMD64 is missing the nvidia-glx-config command.

Because of this, nothing as far as 3D works (GLX, compiz, etc.) with the new driver.

I have a 7600GT and all the 3D stuff was working prior to the upgrade, now it is all broken.

Any help would be appreciated.  I refuse to re-install the system because it is my work PC and I have commercial software that I do not wish to reinstall, and I don't have hours to spend in downtime.

Thanks,
Mike

---

