---
title: "Where to save nvidia xsettings file?"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by ELD on 2014-04-05
So, where after changing my primary monitors around can I save my x config from within the nvidia control panel to have it save across reboots?

---

### Post by steeldriver on 2014-04-05
Are you talking about an xorg.conf file created from the nvidia-settings GUI? if so it would need to go in the /etc/X11 directory - if there's a pre-existing xorg.conf file, back it up in case things don't work out and you need to revert.

OTOH if you are referring to a monitors.xml file that would go in your home ~/.config (hidden) dir I think

---

### Post by SeijiSensei on 2014-04-06
When you save the altered configuration, tell the NVIDIA control panel app to write the new version of xorg.conf to your home directory.  Then use sudo to copy that file to /etc/X11/.

---

