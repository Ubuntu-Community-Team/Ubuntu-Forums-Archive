---
title: "VBox won't load"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by almabeck on 2008-07-09
When I try to start Virtual Box, I get this error message:

Could not load the settings file '/home/alma/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'

Before I did a clean install of Hardy Heron, it worked fine. Any ideas on what I can try?

---

### Post by sdennie on 2008-07-09
It sounds like before you were using a newer version of VirtualBox.  Did you previously use VirtualBox downloaded directly from Sun and are you now using virtualbox-ose?  If so, you may need to uninstall virtualbox-ose and download the version from [www.virtualbox.org](www.virtualbox.org) again.

---

