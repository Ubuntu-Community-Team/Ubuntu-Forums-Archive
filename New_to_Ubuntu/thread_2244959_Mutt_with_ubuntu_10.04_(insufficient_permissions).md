---
title: "Mutt with ubuntu 10.04 (insufficient permissions)"
date: 2014-09-20
forum: New to Ubuntu
---

### Post by rakesh10 on 2014-09-20
Hi,

I am using Ubuntu 10.04. I know this is not supported now. But I have very old hardware so newer versions causing some or the other issue. 

The problem now is, 

mutt is not working.I followed these instructions [https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail). 

I checked the permission those are also fine.
I also checked everything from here [http://ubuntuforums.org/showthread.php?t=1428565](http://ubuntuforums.org/showthread.php?t=1428565), and from here [http://ubuntuforums.org/showthread.php?t=1016884](http://ubuntuforums.org/showthread.php?t=1016884).

I am getting this : ```
Error sending message, child exited 77 (Insufficient permission.).

msmtp: authentication failed (method PLAIN)
msmtp: server message: 534-5.7.14 <[https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbsbB](https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbsbB)
msmtp: server message: 534-5.7.14 GqpU6cdf1uHHgoOuueyre363TZOmrzFggopE8DmQ-qMMsSnIdev-Vv5tZhPZ6IwO0qEYE2
msmtp: server message: 534-5.7.14 bqR0sGaexjWMuxEHyMl1OM31_IHPu65pbgz801MqJLDiZUBfE6nQUOG5LtVx4pCLu8nHXV
msmtp: server message: 534-5.7.14 xERIw2BG2CmaNPYw4RHb-9poFj2TRLHf2VuahoROHXIb2ze2yx5We_VvxfIVxgez0B5TBM
msmtp: server message: 534-5.7.14 0MbfPpw> Please log in via your web browser and then try again.
msmtp: server message: 534-5.7.14 Learn more at
msmtp: server message: 534 5.7.14 [https://support.google.com/mail/bin/answer.py?answer=78754](https://support.google.com/mail/bin/answer.py?answer=78754) iu1sm3241931pbc.53 - gsmtp
msmtp: could not send mail (account default from /home/computername/.msmtprc

```
I can't figure it out, where is the problem.


It would be great if someone can help me to resolve this issue.

Thank you so much.

---

### Post by lisati on 2014-09-20
10.04 reached its end of life quite some time back. The usual recommendation is to upgrade to a newer version if possible. For more information, see [this]("http://ubuntuforums.org/showthread.php?t=2229730") thread, we are unlikely to offer support that is specific to 10.04.

Having said that, there might be someone more familiar with using Mutt might be able to help you.

---

### Post by andrew.46 on 2014-09-26
Certainly one thing to try is the 'UnlockCaptcha' page from Google:

[https://www.google.com/accounts/DisplayUnlockCaptcha](https://www.google.com/accounts/DisplayUnlockCaptcha)

which is suggested in the error message, and if this gives no joy could you post the contents of your ~/.msmtprc file? Good news is that I have been using mutt via gmail exactly as described in that guide, well, I guess I also wrote that guide :), and when it is all set correctly it will work reliably for ever!

---

### Post by kira-yamato-2008 on 2014-09-26
rakesh10 if you have insufficient hardware for newer versions of Ubuntu, why not migrate to a less demanding official distrobution?

Xubuntu and Lubuntu spring to mind, as official spins they're both pretty good for older systems. That being said it depends on how outdated your hardware is. Lubuntu is with out a doubt the fastest of the official spins due to it's use of the Lightweight X11 Desktop Environment (LXDE) and a slew of other optimizations. This applies generally if you have a single core CPU, less than 2 GB of ram, and a significantly older, or no graphics accelerator (Nvidia GeForce, ATi/AMD Radeon, or Intel Graphics for example.) Since your current Ubuntu 10.04 is unsupported it's missing a lot of current compatibility features, and is considered no longer secure.

---

### Post by kurt18947 on 2014-09-26
> **kira-yamato-2008 said:**
> rakesh10 if you have insufficient hardware for newer versions of Ubuntu, why not migrate to a less demanding official distrobution?

Xubuntu and Lubuntu spring to mind, as official spins they're both pretty good for older systems. That being said it depends on how outdated your hardware is. Lubuntu is with out a doubt the fastest of the official spins due to it's use of the Lightweight X11 Desktop Environment (LXDE) and a slew of other optimizations. This applies generally if you have a single core CPU, less than 2 GB of ram, and a significantly older, or no graphics accelerator (Nvidia GeForce, ATi/AMD Radeon, or Intel Graphics for example.) Since your current Ubuntu 10.04 is unsupported it's missing a lot of current compatibility features, and is considered no longer secure.

I agree about looking for a less demanding distro.  I've found that even Lubuntu or Xubuntu won't run on 10+ yr. old machines. I've been using MX14, an antiX offshoot based on Debian testing (I believe).  It uses a customized XFCE desktop and runs as well as can be expected on a 1999 vintage machine with a Celeron 667Mhz. processor & 512 MB. RAM that came with WinME.  The limiter I've found is Xorg support for old graphics systems.

---

