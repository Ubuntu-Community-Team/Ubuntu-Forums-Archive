---
title: "Upgrade server version 12.04.1"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by mikeybinec on 2014-08-03
Tried yum, tried apt-get.. tried do-release-upgrade, tried sudo  do-release-upgrade

Anything else?

Thanks

---

### Post by sudodus on 2014-08-03
There are reports that

```
sudo   do-release-upgrade
```

for 12.04 to 14.04.1 is delayed because it still needs debugging.

But there is no hurry. Ubuntu Server version 12.04 will be supported for a long time (until April 2017). Is there a reason why you are still running 12.04.1? Doesn't your computer work with the later point releases?

In that case there may also be problems with 14.04 (and 14.04.1) for your computer.

Please [URL="http://ubuntuforums.org/showthread.php?t=2230389"]try the new version of Ubuntu Server before installing it
[/URL]
It is also recommended to ***update/dist-upgrade*** to the latest point  release (now 12.04.4) actually all the way to the current daily program  packages before running ***do-release-upgrade***.

You can install it into a USB drive and do some tests before decide to upgrade. Things happen during installations and upgrades, so a recent ***backup*** will give you peace of mind.

---

### Post by Bashing-om on 2014-08-03
mikeybinec;

ninja'd sudodus ! +1 .

IF there exist  a pressing need to release upgrade, there are means to " force " the issue, but expect breakage.

The current expectation for a fix is this coming weekend. Testers are hard at work, we shall see.

[INDENT][INDENT]patience, is a virtue
[/INDENT][/INDENT]

---

### Post by mikeybinec on 2014-08-10
Thanks for response.. Machine nags me with a "new release 12.10 available"  Run "do-release-upgrade"

No reason for me to upgrade is fine with me

Thanks again

---

### Post by Bashing-om on 2014-08-10
mikeybinec; OK,

Seems all is in the clear now from the developers.
BUT set your settings correctly in "Software Sources" to look at "LTS"
YOU DO NOT WANT:
> 
 Machine nags me with a "new release 12.10 available" Run "do-release-upgrade"

as release 12.10 is End_Of_Life and has no support .. select LTS and you should now have the option to upgrade to 14.04.1.
Keep in mind there is now "phased updates" and your turn may not be up to this time.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by nerdtron on 2014-08-10
And before you upgrade to 14.04, be sure to apply all updates from your current system.

sudo apt-get update && sudo apt-get upgrade

---

