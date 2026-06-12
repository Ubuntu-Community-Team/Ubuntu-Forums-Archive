---
title: "Static on laptop boot - before gdm"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by dwardingley on 2008-11-06
I had Hardy running fine on a Fujitsu-Siemens laptop (Amilo pa1510) but since I upgraded to Intrepid - when I enter the passphrase to decrypt the hard drive it accepts it and the Ubuntu splash screen bar finishes but there is then a slight delay and a flash of "static" across the top centimetre of the display before I get a little round "X" and then the gdm login screen.

When I say static, I mean the sort of blocky digital distortion you sometimes see on a scratched DVD.

I thought perhaps something had clashed between Hardy and Intrepid, so actually did a whole fresh install (I have all my data backed up ) but the same thing happened.

Has anyone else encountered this?

Any ideas on where to start looking for the problem?

Thanks,

d.

---

### Post by bscbrit on 2008-11-06
This sounds like the system reconfiguring the optimum screen resolution without blanking the screen.  As far as I know, it is not a serious problem (i.e. it is cosmetic rather than a sign of impending failure).  As for how to change it, I'm afraid that I cannot help.  It is possibly (and I am guessing here!) something to do with a changed driver or the introduction of xorg.conf 7.4.  If it causes you concern then you could raise it as a bug report but I suspect that it will be easier to learn to live with it. :-)

---

### Post by dwardingley on 2008-11-07
Thank you for your reply. I _hate_ it when something doesn't seem to work right and I haven't the skill to fix it.

As an addendum, when I have the middle level of visual effects enabled, so that menus fade in and out etc, I get a similar sort of distortion temporarily within the menu itself as it opens. I don't get that when I don't have any visual effects running (which I prefer anyway).

Thanks, again,

d.

---

### Post by bscbrit on 2008-11-07
Does the static disappear completely when you switch off visual effects?  I don't know enough about compiz etc, but I wouldn't of thought that it would be playing a role before you log in to gdm.

---

### Post by dwardingley on 2008-11-07
> **bscbrit said:**
> Does the static disappear completely when you switch off visual effects?  I don't know enough about compiz etc, but I wouldn't of thought that it would be playing a role before you log in to gdm.

The static on the menus disappears, but the static before gdm does not.

(and as I have said, it didn't appear under 8.04, only when I upgraded to and then fresh-installed 8.10)

d.

---

### Post by bscbrit on 2008-11-07
I would recommend that you raise a bug report (use apport which is already installed on your system).  Unless you tell somebody, it cannot be fixed.  But the fact that you do tell somebody doesn't mean that it will be fixed, or that it is even fixable.  I would rather be an optimist and hope that by reporting the bug an improvement might be available in the future.

Good Luck.

---

