---
title: "Sleep Type in Hardy Heron"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by nospamprl on 2008-06-28
My laptop isn't going to sleep when left alone on battery power for more than the 10 minute defined parameter in the power management dialog.

In Gutsy there was a "Sleep Type" field in the General tab, but in Hardy it's not there anymore.

Does anyone knows how to set the "Sleep Type" to Suspend in Hardy?

Thanks

---

### Post by sdennie on 2008-06-28
Try hitting Alt-F2 and typing gconf-editor.  Then navigate to /apps/gnome-power-manager/actions and set sleep_type_battery to suspend.

---

### Post by nospamprl on 2008-06-28
Thank you. Problem solved. Only comment to add is that a reboot was needed for the change to take effect.

---

