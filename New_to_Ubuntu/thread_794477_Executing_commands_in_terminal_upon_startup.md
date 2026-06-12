---
title: "Executing commands in terminal upon startup?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Muffinabus on 2008-05-14
Basically, I despise mouse acceleration and the only way I have found that completely disables it is 'xset m 0 0'.  Now this is only for your current session and it resets when I reboot.  It isn't THAT big of a deal to type it into terminal each time I logon, but I figured why not ask anyway, I'll probably want to know how to do it sooner or later, or if it's even possible.  

On top of that, how can I get programs to automatically start up on boot as well?  Specifically I'd like pidgin to be up and running when my machine boots up.

AND one last, slightly unrelated, question.  Any way to turn off system beeps?  Linux seems to randomly enjoy making use of my computer speaker (the one inside my case/on my motherboard).  IE: in pidgin, hitting backspace on an empty text box causes my system speaker to beep.  It seems like an odd thing for an OS to make use of.  Not used to hearing that sound after POST.

---

### Post by shifty_powers on 2008-05-14
to start a program on boot, system>preferences>sessions ;)

---

### Post by Mr A Mouse on 2008-05-14
> **Muffinabus said:**
> Basically, I despise mouse acceleration and the only way I have found that completely disables it is 'xset m 0 0'.  Now this is only for your current session and it resets when I reboot.  It isn't THAT big of a deal to type it into terminal each time I logon, but I figured why not ask anyway, I'll probably want to know how to do it sooner or later, or if it's even possible.  

On top of that, how can I get programs to automatically start up on boot as well?  Specifically I'd like pidgin to be up and running when my machine boots up.

For both of these, you can create a script that takes care of any tasks you want done during startup, and include it in your "Sessions" preference under the Startup Programs tab.

> AND one last, slightly unrelated, question.  Any way to turn off system beeps?  Linux seems to randomly enjoy making use of my computer speaker (the one inside my case/on my motherboard).  IE: in pidgin, hitting backspace on an empty text box causes my system speaker to beep.  It seems like an odd thing for an OS to make use of.  Not used to hearing that sound after POST.

Check Preferences > Sound > System beep. If it's checked, deselect it.

HTH. :)

---

### Post by Muffinabus on 2008-05-14
> **Mr A Mouse said:**
> For both of these, you can create a script that takes care of any tasks you want done during startup, and include it in your "Sessions" preference under the Startup Programs tab.



Check Preferences > Sound > System beep. If it's checked, deselect it.

HTH. :)

So simple, yet I have no clue why it is even enabled in the first place!

Thanks guys!

---

