---
title: "Control Chars Display in Xemacs Shell"
date: 2007-04-06
forum: Programming Talk
---

### Post by radioflyer on 2007-04-06
Ubuntu Version:  Desktop 6.06 LTS
Xemacs Version: 21.4.18-1ubuntu1 (xemacs21-gnome-nomule)

Installed Xemacs and everything works okay except when I go to the shell mode 
(M-x shell).  When I do a listing I see what looks like control characters mixed in with the listing.

I can run Emacs in shell mode with no problems.

Thanks in advance for any help.

Andy ...

---

### Post by radioflyer on 2007-04-06
After further research discovered the following:

The alias: ls='ls --color=auto' is apparently causing control characters for color to be sent to the shell display in Xemacs when the ls command is executed.  If the alias is removed at the shell prompt then ls works fine in Xemacs.  

The root cause appears to be the LS_COLORS environment variable which isn't set when Xemacs spawns its shell.  If I execute the Xemacs shell and set the LS_COLORS value to something reasonable (something I copied from the shell that emacs spawns-note emacs doesn't have this ls problem) I can then run the ls command without deleting the alias mentioned above.  

There is probably some way to set the LS_COLORS variable when Xemacs is started up-don't really know that much about Xemacs startup.

---

