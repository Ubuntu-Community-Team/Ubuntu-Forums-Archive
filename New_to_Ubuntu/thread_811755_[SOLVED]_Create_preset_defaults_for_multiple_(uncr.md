---
title: "[SOLVED] Create preset defaults for multiple (uncreated) user accounts?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2008-05-29
Is there a way to set the defaults for multiple users, even if those accounts haven't yet been created?  I mean things like setting the shortcuts on the panel, setting default fonts and themes,  setting gnome-mplayer as default video player and controlling the way shortcuts in the applications menu are displayed, things like that?  Can someone explain to me how to do this and have it inherited by every new account created?

Ideally there would be one account created, the 'Administrator' account which would have the ability to do updates and install software, and then any accounts created by that would inherit any customizations.

Can someone tell me how to do this?  Thanks!

--bornagainpenguin

PS: I'm in Gutsy Gibbon (with all updates) now, so it needs to be Gutsy specific and not Hardy specific due to lack of hardware support.

---

### Post by bornagainpenguin on 2008-05-29
Sorry for the bump, but this made it all the way to page eight with no replies in over five hours, so I wanted to make sure it gets seen.  Also, I have added tags to the post since then helping to identify what I'm looking for.  If there is a better area for this question to be in, please at least post and tell me that!

Thanks!

--bornagainpenguin

---

### Post by Oldsoldier2003 on 2008-05-29
> **bornagainpenguin said:**
> Is there a way to set the defaults for multiple users, even if those accounts haven't yet been created?  I mean things like setting the shortcuts on the panel, setting default fonts and themes,  setting gnome-mplayer as default video player and controlling the way shortcuts in the applications menu are displayed, things like that?  Can someone explain to me how to do this and have it inherited by every new account created?

Ideally there would be one account created, the 'Administrator' account which would have the ability to do updates and install software, and then any accounts created by that would inherit any customizations.

Can someone tell me how to do this?  Thanks!

--bornagainpenguin

PS: I'm in Gutsy Gibbon (with all updates) now, so it needs to be Gutsy specific and not Hardy specific due to lack of hardware support.

yes, just copy what you want to /etc/skel

example if you copy ~/Desktop to /etc/skel everything that is on your desktop (not the desktop background) will be added to new accounts. by copying the configuration files from a preoptimized account into /etc/skel you can set your users up with a predefined standard desktop of your own choosing.

---

### Post by bornagainpenguin on 2008-05-29
> **Oldsoldier2003 said:**
> yes, just copy what you want to /etc/skel

example if you copy ~/Desktop to /etc/skel everything that is on your desktop (not the desktop background) will be added to new accounts. by copying the configuration files from a preoptimized account into /etc/skel you can set your users up with a predefined standard desktop of your own choosing.

Thank you!  I think I can figure the rest out from here...  with a little help from Google and searching through the forums, that is.  Thanks for pointing me in the right direction though!  :)

--bornagainpenguin

---

