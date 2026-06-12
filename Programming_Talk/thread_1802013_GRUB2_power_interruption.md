---
title: "GRUB2 power interruption"
date: 2011-07-11
forum: Programming Talk
---

### Post by Clive McCarthy on 2011-07-11
I'm using Ubuntu 10.10 in an 'appliance' application. There is no keyboard or mouse, just a power button. This works fine since I have a script that launches my application when Ubuntu starts.

There is a problem I have encountered if power is interrupted during the small window when GRUB is operating but when Ubuntu is not yet running. In this case, when the system is restarted, GRUB will have noted that a prior boot failed and then it offers a menu of boot options which requires user input. This causes my 'appliance' to simply sit and wait since there is no keyboard...

To work around this I have edited /etc/grub.d/00_header and modified the **[COLOR="Blue"]recordfail[/COLOR]** function so that it _always_ returns false. I, of course, run update-grub too.

Apart from the problem that would occur should the OS not actually boot, what other downside might this change have?

---

