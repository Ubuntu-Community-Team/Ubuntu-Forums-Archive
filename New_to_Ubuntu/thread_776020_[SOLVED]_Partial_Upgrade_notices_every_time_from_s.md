---
title: "[SOLVED] Partial Upgrade notices every time from synaptic"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-04-30
Hey all,

I am running Gutsy 64 with Ubuntuzilla's install of firefox and thunderbird ([http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")). For those unfamiliar, Ubuntuzilla installs the official mozilla releases and not simply the distro releases. It also is suppose to install the 32 bit versions even on 64 bit installs since that is all that is available from mozilla. Install went fine, Sun java and flash work great without any wrapper. There are only two little quirks I'm hoping someone knows how to fix.

First, every time I get a update notice, the update manager gives me a partial upgrade notice. Clicking the partial upgrade button gives me some error messages about things ending unexpectedly (i.e. stacks.py ended unexpectedly). If I simply close and ignore the partial upgrade button things seem to progress fine. What's up?

Second, any URL links in Thunderbird no longer automatically open a firefox window when clicked. I have to open firefox and drag the link into the window. Same thing with other software's "about" boxes that have a url to the software's homepage. Clicking those doesn't launch firefox and most of them don't let you highlight and copy the link.

EDIT: Forgot one other quirk. When doing a save as or file open in Firefox or Tbird, the icons of all the files are little papers with 'x' on them. I suppose the firefox and tbird have a borked link to the custom icons I have installed (glass icons). The icons work everywhere else and worked before using Ubuntuzilla. 

Any clues!
Thanks,
Eric

---

### Post by Adramelech on 2008-04-30
I got something similar with avant window manager from bazaar, I uninstalled it, reinstalled, and the update manager do not display any "partial upgrade" message anymore

---

### Post by nowhere@cox.net on 2008-04-30
I looking into it and it appears that I had stuff installed from non-bazaar and bazaar. I removed everything awn/avant window navigator and reinstalled only bazaar.  We will see what's going on.

Thanks!

As for my other problems. Anyone have any ideas? I am also have flakey behaviors from other things now that I start looking. The system claims dmesg is no longer installed. If I try to install util-linux then it wants to remove linux32 before installing.

My system is so borked. I don't know how to fix half of the goofy stuff happening. Let me know if you can help.

Thanks,
Eric

---

