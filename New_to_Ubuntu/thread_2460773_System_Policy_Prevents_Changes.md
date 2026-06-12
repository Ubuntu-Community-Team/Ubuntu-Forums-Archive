---
title: "System Policy Prevents Changes"
date: 2021-04-18
forum: New to Ubuntu
---

### Post by gadget069 on 2021-04-18
I'm completly new to Ubuntu. I had noticed that my timezone was incorrect. I went into settings/date & time. It has the wrong timezone and was greyed out. The un-lock button at the top of the menu is alos grey out so I could not make any changes. I've searched through the interwebs and could not find a definative answer. I was able however go into terminal and change to the correct time zone( foudn that command again on the interwebs).

Thanks

[ATTACH=CONFIG]288338[/ATTACH]

---

### Post by deadflowr on 2021-04-18
I believe the lock option means your user is not an admin user.
And being grayed out might mean you have no admin user.
I do not see this for any admin set user, but do see it for non-admin users.

---

### Post by ActionParsnip on 2021-04-18
Could use the terminal to set the time zone. Dead easy

---

### Post by gadget069 on 2021-04-18
> **ActionParsnip said:**
> Could use the terminal to set the time zone. Dead easy
Thanks, I was able to do it that way.

---

### Post by grahammechanical on 2021-04-18
If we have Automatic Date & Time set to on, then we do not get the option to manually change the Date & Time. If we have Automatic Time Zone set to on, then we do not have the option to change the Time Zone.

With Automatic Date & Time set to off we do not need to be Admin user. I believe to same would be true if Automatic Time Zone was set to off. Anyway it is Ubuntu policy to provide a password panel whenever a Standard user tries to make changes only an Admin user can make. In this way we transition fromSstandard user to Admin user and back again.

The date & time in Ubuntu without Automatic Date & Time being set to on will come from the time and date setting in UEFI/BIOS. Which may not take into account Daylight Saving Time that many countries use. Ubuntu regularly updates the Time Zone data so that the system time and date do not fall out of step with the time zone that has been set by the user.

Regards

---

