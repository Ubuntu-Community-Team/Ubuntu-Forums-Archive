---
title: "How can I completely purge and reinstall grub using boot-repair's advanced options"
date: 2015-07-22
forum: New to Ubuntu
---

### Post by loren3 on 2015-07-22
So I've been having a problem for several days now, where my computer continually boots into memtest86+. After the check is 100% complete with no errors, it simply starts the test again, with no signs of stopping. I tried to holding down the shift key while booting to get into the grub menu and boot manually, but the only options listed in the grub menu were two having to do with memtest. Some other threads said the best thing to do was to completely purge and reinstall grub. To completely purge grub with boot-repair from a Live CD seems like the easiest option, but it's not clear to me how to use boot-repair's advanced options to do this, and it was recommended that I post a thread here before trying to use any of the advanced at all. 

Any advice would be much appreciated!

---

### Post by Bashing-om on 2015-07-22
loren3; Hi ! Welcome to the forum.

Ist up is :
Is this a UEFI system ?

2nd up :
Boot the install medium you used to install ubuntu in "try ubuntu" mode;
Activate a terminal and post back the outputs - between code tags - of terminal command :
```

sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

These will tell us what you are working with to allow us to give accurate advise.

[INDENT][INDENT]yeah, 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

