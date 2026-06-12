---
title: "Ubuntu crashing when network drives are not present."
date: 2012-10-29
forum: New to Ubuntu
---

### Post by Tubbytee on 2012-10-29
Hi Guys,

I've been getting odd crashes happening when my network hard drives are not mounted. It happens at random intervals but always when I press the Enter key in whatever application I have open. Sometimes the error messages are from [mountall], sometimes they come from [cifs].
Most of the time, the computer hangs and I have to power off but sometimes it just dumps me out to the login screen.
As the computer in question is a laptop, I obviously use it away from the network drives a lot so this is quite a frustrating problem.
I'm on Ubuntu 12.04 and it's only been happening since I upgraded to this version.

Thanks in advance for any help and advice you can offer.

Tubbytee.

---

### Post by Bashing-om on 2012-10-29
I do not posses a great store of knowledge in respect to nas...However, the indications provided by you indicate a closer look at how /etc/fstab is mounting the nas drives is in order.
These links provide guidance  for configuring the file.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

See, and report back with any questions.
[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

