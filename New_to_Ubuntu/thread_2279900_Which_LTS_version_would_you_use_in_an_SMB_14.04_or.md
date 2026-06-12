---
title: "Which LTS version would you use in an SMB? 14.04 or 14.04.2?"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by 321linux on 2015-05-26
Before anyone goes into the details of the differences bewteen 14.04 and 14.04.2, we should all read this forum question and the answers so we are on the same page:
[http://ubuntuforums.org/showthread.php?t=2275409&highlight=difference+14.04+14.04.2%3F](http://ubuntuforums.org/showthread.php?t=2275409&highlight=difference+14.04+14.04.2%3F)

Now, with that as the background (assuming that the info presented there is correct & correctly understood)... which version would you recommend using in an SMB environment?

LTS is important if one wants the most stable release for the longest number of years/months without having to move to newer releases.

From what I read in that other thread, it appears that if one were to install 14.04.2 then the HWE (Hardware Enablement Stack?) sees end of life in August 2016 (as listed here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases))
...at which point, one would need to update to 14.04.3 (or higher) to remain fully "supported."

Should a production environment just use 14.04.1 (because it is supported fully to 14.04 EOL in April 2019)?
...or should a production environment use 14.04.2 and not worry about the differences from .2 to .3 or higher?

---

### Post by sandyd on 2015-05-26
There is no cut-and-dried answer.

The LTSEnablementStack primarily two purposes:
[LIST]
[*]Keep Xorg/Video drivers updated (this may not apply if you are using additional drivers such as the intel graphics installer or other PPAs that may be keeping this updated)
[*]Provide a newer kernel (in the case of 14.04, this would be the 14.10 kernel) that may support hardware previously not supported on the original 14.04 kernel
[/LIST]

If you are a SMB, and 14.04 works, then use the default kernel. There are times where a newer kernel may actually introduce additional issues/etc. If you have newer hardware that is supported in 14.10, but you want to use a LTS release, then this is the perfect time to use LTSEnablementStack

---

### Post by grahammechanical on 2015-05-26
It is your decision. You have all the information you need. I do not think that it makes any difference if it is one person on a computer at home, a small to medium business (SMB) or a large corporation. The options are the same. We are all equals in Ubuntu. We all get the same level of support. We get the same Ubuntu.

If a person was buying the latest hardware I would advise them to install Ubuntu 14.04.2. In six months time the advice would be to install 14.04.3 and so on. Otherwise they might find that their new hardware was not fully supported by Linux. And then they would have to pay the cost (in time) of upgrading.

If your company has machines that are more than a year old and 14.04 fully supports all the hardware, then install 14.04. If the company has more recent hardware and 14.04 fully supports all the hardware, then install 14.04. But what if you buy new machines in the next few years and 14.04 does not fully support the hardware but 14.04.2 or 14.04.3 does support it? What will you do then?

Will it actually make any difference to the employees if one machine is running 14.04 and another is running 14.04.2? No. Normal updates will update 14.04 to 14.04.1 and then to 14.04.2 and then to 14.04.3 but not the hardware enablement stack. We only get an upgraded hardware enablement stack if we specifically decide to do the upgrade or we put in a new installation of 14.04.2.

Through normal updates the operators will get updated versions of applications such as Libreoffice and they will all get these newer versions. So, I do not think that the employees will notice any difference or not much difference between using a machine with 14.04 on it and a machine with 14.04.2 on it.

Regards.

---

### Post by newb85 on 2015-05-26
I'm a little surprised and confused.  The machine I'm on had Trusty installed before 14.04.1 was released.  Since then, I've never been asked about upgrading to a newer point release.  Yet, when I hit
```
lsb_release -a
```
it tells me that I have 14.04.2.  Does this mean I have the 14.04.2 Hardware Enablement Stack, or not?
I am running unattended-upgrades.

Edit: Just answered my own question.  
```
uname -r
```
revealed that I still have the 3.13 kernel of 14.04.

---

### Post by craig10x on 2015-05-27
You automatically are on each new point release but if you want the newer kernel and drivers for that new point release you have to do the terminal commands that install those (hardware enablement stack)...
As explained in this wiki:
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack)

---

