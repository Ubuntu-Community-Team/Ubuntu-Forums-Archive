---
title: "Confirm before emptying trash bin Ubuntu 14.04 LTS"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by mdavis1231 on 2015-02-28
Do you guys know how to make Ubuntu 14.04 LTS confirm before emptying the trash bin like you used to be able to in 12.04 LTS?  Used to be all you had to do was open Nautilus[SUP] [SIZE=2]> Preferences > Behavior[/SIZE][/SUP][SIZE=2] [/SIZE]> Trash, then simply uncheck the box "Ask before emptying the Trash or deleting files", then re-check it.  After that, whenever you would right click on "Empty Trash", it would ask you "Are you sure you want to empty the trash bin?".  This no longer works.  It doesn't make any difference.  Is there a new way of doing this in Ubuntu 14.04 LTS, or has this feathre completely been done away with? :confused:

---

### Post by mc4man on 2015-02-28
Not sure why it doesn't for you but works as expected here, are you using an ubuntu session (unity) or something else?

---

### Post by mdavis1231 on 2015-03-01
> **mc4man said:**
> Not sure why it doesn't for you but works as expected here, are you using an ubuntu session (unity) or something else?

I'm actually using gnome-session-fallback.

---

### Post by whitesmith on 2015-03-01
I'm also using Gnome fallback and permission is required before emptying the trash.

---

### Post by CantankRus on 2015-03-01
Trash deletion confirmation is a nautilus preferences setting.
You can do a quick check by running this terminal command....
```
dconf read /org/gnome/nautilus/preferences/confirm-trash
```

---

### Post by mdavis1231 on 2015-03-07
> **CantankRus said:**
> Trash deletion confirmation is a nautilus preferences setting.
You can do a quick check by running this terminal command....
```
dconf read /org/gnome/nautilus/preferences/confirm-trash
```

I've done that.  In 12.04 LTS whenever you wanted Ubuntu to ask you to confirm that you actually wanted to delete the trash that was in your bin, all you had to do was go in, uncheck that box, close out, reopen, check the box again, and there you'd have it.  Nothing whatsoever seems to work with my Ubuntu 14.04 LTS.  All I get when I right click and choose "Empty Trash" is what appears to be a flash of a box, then the trash is gone.  I would like for the box to pop up to actually confirm that I am indeed wanting to empty everything in my trash bin, and I can't figure out how to make that happen on Ubuntu 14.04 LTS Trusty Tahr.

---

### Post by CantankRus on 2015-03-07
I don't know then.
Do you get the confirmation in the guest session?

---

