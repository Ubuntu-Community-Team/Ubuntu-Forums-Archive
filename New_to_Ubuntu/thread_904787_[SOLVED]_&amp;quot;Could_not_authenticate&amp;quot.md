---
title: "[SOLVED] &amp;quot;Could not authenticate&amp;quot; in Users Settings"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Frogbarf on 2008-08-29
I've just installed Hardy Heron in a brand new PC, then updated it. During installation, it asked me to create a userid & pwd, but alas! didn't say "this will be your administrative user" so I entered my normal userid thinking that I would be asked to create an admin user later.

No such luck.

Going into System->Administration->Users & Groups, I created a second user "Administrator" and set its properties to include "administrative".

My intended next step was to go into Users Settings again and remove admin privileges from the user id I set up in the first place, but when I click the unlock button, nothing happens. After a l-o-n-g wait, I get an error message "Could not authenticate, An unexpected error has occurred".

Google and search of the Ubuntu forums both reveal an enormous number of instances of this kind of issue and I'm in the situation that I have no idea which of the many instances leads to a resolution.

AFAICT, I have two user ids with admin privileges, but I can't unlock the users settings function with either one.

There's unquestionably something anti-intuitive about the way Hardy Heron handles users with admin privileges.

Short of a complete reinstall, how can I sort this mess out?

---

### Post by cmnorton on 2008-08-29
All my application user IDs have the ability to use sudo. I added them to the admin group by running usermod. If you want to use web-based CUPS [http://locahost:631](http://locahost:631), add any user to lpadmin.

---

### Post by Frogbarf on 2008-08-29
> **cmnorton said:**
> All my application user IDs have the ability to use sudo. I added them to the admin group by running usermod.

I don't understand how this would correct my problem. For that matter, I haven't a clue how to run usermod, and I'm looking at "info usermod" as I write.

Please don't forget, this is *absolute* *beginner* talk; things have to be spelled out in words of one syllable, so to speak.

:confused:

---

### Post by Frogbarf on 2008-08-29
More info:

I was able to go into Users Settings while logged in under each of these  user ids, and discovered that neither one has "administer the system" checked even though one was created during system install and the other specifically created with administrative privileges.

Moreover, both of them show the full list of system admin menu items, which non-admin users don't see. Yet neither has the add/delete apps menu item under Applications and I can't edit the menu to add it.

It's as though Ubuntu is keeping info on admin users in two separate places and somehow those are no longer in agreement, so in some places in the system Ubuntu thinks these ids are admin-capable, but in other places thinks they aren't.

Ooooopsie!

To restate the issues in view of this:

1. How did that happen? I'm not that stupid and I'm not a complete newbie at this stuff. Somehow both user ids have had their administrative privileges yanked.

2. What do I do to restore admin privileges to at least one of them? Or to create a new, third user id with admin privileges? Root is locked in its usual Ubuntu way.

---

### Post by Cheesehead on 2008-08-29
Test it.

Open Add/Remove and try to install a small game or something frivolous.
The system will prompt for your password.

If the system *does* install it, then obviously you do have admin permission.

My accounts show the same thing in that silly control panel (empty boxes), and I can screw up my system with sudo just fine.

---

### Post by Frogbarf on 2008-08-29
> **Cheesehead said:**
> Open Add/Remove and try to install a small game or something frivolous. The system will prompt for your password.

Add/remove isn't present in the menus. Whatever decides to display that, or not, thinks my two user ids are not admin-enabled.

I think I'm going to have to re-install from scratch unless someone can tell me what to do when you don't have an admin id.

---

### Post by drs305 on 2008-08-29
If I understand the situation, you can boot to the recovery mode and then:

```
adduser *username* admin
```

That user will then be granted administrative (sudo) powers.

---

### Post by Frogbarf on 2008-09-05
And I learned a lesson: that first user id you create when you install Ubuntu is going to be your admin ID, so be careful not to create an ordinary user id at that stage.

Fortunately, I'd hardly used the machine, so reinstallation caused no issues.

Thank everyone for their replies.

---

### Post by kiwi-pete on 2008-09-27
> **drs305 said:**
> If I understand the situation, you can boot to the recovery mode and then:

```
adduser *username* admin
```

That user will then be granted administrative (sudo) powers.

How does one boot to the recovery mode.
I'm in the same boat here, no add menu in applications and I cannot run update manager.

---

### Post by drs305 on 2008-09-27
> **kiwi-pete said:**
> How does one boot to the recovery mode.
I'm in the same boat here, no add menu in applications and I cannot run update manager.

If grub pauses at the menu.lst to allow you to select the kernel or OS, there should be an option to choose the recovery mode. It's usually the second option. If you select the recovery mode, the boot will continue to another menu giving you four choices. At that point, you would select the one to take you to the root prompt.

If grub automatically starts without giving you a menu, as the computer is booting press the ESC key and you should be presented with the grub menu.

---

### Post by kiwi-pete on 2008-09-28
> **drs305 said:**
> If grub pauses at the menu.lst to allow you to select the kernel or OS, there should be an option to choose the recovery mode. It's usually the second option. If you select the recovery mode, the boot will continue to another menu giving you four choices. At that point, you would select the one to take you to the root prompt.

If grub automatically starts without giving you a menu, as the computer is booting press the ESC key and you should be presented with the grub menu.

Thanks, all sorted now.

---

