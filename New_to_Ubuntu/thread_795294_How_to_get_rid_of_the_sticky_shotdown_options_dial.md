---
title: "How to get rid of the sticky shotdown options dialog?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by netimen on 2008-05-15
I want my computer to shutdown when I press powerbutton without displaying any confirmation dialogs. Now if I press the button, I get the dialog with shutdown options. How can I get rid of it? May be it's possible via editing configuration files? (I failed to do it via systemsettings)

---

### Post by bluefrog on 2008-05-15
explain clearly what you want.

---

### Post by netimen on 2008-05-15
OK ) see the topic

---

### Post by nowshining on 2008-05-15
ah! I get what netimen is saying however I don't exactly know how or rem. how..

---

### Post by Ayuthia on 2008-05-15
> **netimen said:**
> I want my computer to shutdown when I press powerbutton without displaying any confirmation dialogs. Now if I press the button, I get the dialog with shutdown options. How can I get rid of it? May be it's possible via editing configuration files? (I failed to do it via systemsettings)
System Settings is the place for configuring this.  I am guessing that you found the section, but if you did not, go to the Advanced tab and select Session Manager.  As odd as it sounds, in the General section, the Offer shutdown options needs to be checked.  In the Default Shutdown Option, select Turn off computer.  I tried it out and everything turned off.

Hope that helps.

---

### Post by netimen on 2008-05-16
> **Ayuthia said:**
> System Settings is the place for configuring this.  I am guessing that you found the section, but if you did not, go to the Advanced tab and select Session Manager.  As odd as it sounds, in the General section, the Offer shutdown options needs to be checked.  In the Default Shutdown Option, select Turn off computer.  I tried it out and everything turned off.

Hope that helps.

Yeah, this worked, but only once ) When I boot up next time and press the powerbutton I see the dialog again. May be I should manually edit config files?

---

