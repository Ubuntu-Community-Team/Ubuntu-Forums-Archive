---
title: "New User menu"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Curnel_D on 2011-08-26
I have 4 computers that I use daily, 2 more that I regularly use a few times a week, and not a single one of them has more than one User Account.  

So why then, would I need an always visible user menu that clutters things up, that doesn't even show the right User Name in the first place? [Invalid UTF-8]

Does anyone have any idea how to remove this from the panel?

Thanks

---

### Post by Ichtyandr on 2011-08-26
> **Curnel_D said:**
>  doesn't even show the right User Name in the first place? [Invalid UTF-8]
its a bug, it will go with the new "indicator-session" update

---

### Post by Curnel_D on 2011-08-26
Lol, I don't mind the bug.  It's an alpha release, afterall.  But the entire user menu itself is useless to me and just mucking up my workspace.

---

### Post by jbicha on 2011-08-26
This is why the user menu is there: [http://pad.lv/831758](http://pad.lv/831758)

---

### Post by lucazade on 2011-08-26
> **jbicha said:**
> This is why the user menu is there: [http://pad.lv/831758](http://pad.lv/831758)

"This makes it more difficult for users of single-user computers to set up Online Accounts or more importantly change their password or add a second user via the "User Accounts" button that was added today to indicator-session."

These things are already available in the control-panel.
The indicator seems useless with only one user configured on the computer.

---

### Post by terry_gardener on 2011-08-26
> **lucazade said:**
> "This makes it more difficult for users of single-user computers to set up Online Accounts or more importantly change their password or add a second user via the "User Accounts" button that was added today to indicator-session."

These things are already available in the control-panel.
The indicator seems useless with only one user configured on the computer.

i also use single user machine and this menu is useless as lucazade says. the setting it provides are in system settings uder the power button. 

i see the point of having it there.

---

### Post by lucazade on 2011-08-26
> **terry_gardener said:**
> i also use single user machine and this menu is useless as lucazade says. the setting it provides are in system settings uder the power button. 

i see the point of having it there.

I (try to) understand that this will help Jeremy writing documentation:
"As a member of the Ubuntu Documentation Team, this makes our job more complicated to explain how to do these tasks."
Although Alt+F2 + "gnome-control-center user-accounts" is consistent, if 1 or more users are present on the system, and easy for a documentation.
It is also possible to reach user capplet via indicator-session > System Settings.

I wonder how many times a user should change his password and if it is necessary to put this option in an indicator that should indicate something in action/status.
Also with only one user how it could be useful to switch users? from my account to my account?!

---

### Post by mc4man on 2011-08-26
If you wish to build you could return the old behavior - 1 user not shown, 2 or more shows
ck. /src/user-menu-mgr.c around line 176

---

### Post by lucazade on 2011-08-26
> **mc4man said:**
> If you wish to build you could return the old behavior - 1 user not shown, 2 or more shows
ck. /src/user-menu-mgr.c around line 176

thanks mc4man for the suggestion, really kindly!
I was looking at that file this morning, I hoped to solve by disabling guest account  because if i'm not wrong there was a check also on this.
Anyway i'll look at that line and rebuild my own indicator-session... too bad, i hoped this time in oneiric i hadn't to rebuild stuff, in natty did for a lot of stuff.

---

### Post by lucazade on 2011-08-27
to remove user menu from indicator session, really useless when using only one user, I've rebuilt a new patched package without the half-baked user-menu.

```
wget https://launchpad.net/~lucazade/+archive/ppa/+build/2749237/+files/indicator-session_0.3.3.2-0ubuntu1a_i386.deb
sudo dpkg -i indicator-session_0.3.3.2-0ubuntu1a_i386.deb
```

or add my ppa... anyway the package will be likely updated before OO release because of the new bug introduced with the new user-menu, so I'll have to update my package again.

many thanks to mac4man and his suggestions.

---

### Post by madjr on 2011-08-27
> **lucazade said:**
> to remove user menu from indicator session, really useless when using only one user, I've rebuilt a new patched package without the half-baked user-menu.

```
wget https://launchpad.net/~lucazade/+archive/ppa/+build/2749237/+files/indicator-session_0.3.3.2-0ubuntu1a_i386.deb
sudo dpkg -i indicator-session_0.3.3.2-0ubuntu1a_i386.deb
```

or add my ppa... anyway the package will be likely updated before OO release because of the new bug introduced with the new user-menu, so I'll have to update my package again.

many thanks to mac4man and his suggestions.

so they plan to show it by default even with just 1 user?

---

### Post by lucazade on 2011-08-27
> **madjr said:**
> so they plan to show it by default even with just 1 user?

at the moment this seems the final solution, unfortunately.
anyway Jbicha is better informed than us, so he can confirm or not.

---

### Post by jbicha on 2011-08-27
> **lucazade said:**
> Although Alt+F2 + "gnome-control-center user-accounts" is consistent, if 1 or more users are present on the system, and easy for a documentation.
It is also possible to reach user capplet via indicator-session > System Settings.

I wonder how many times a user should change his password and if it is necessary to put this option in an indicator that should indicate something in action/status.
Also with only one user how it could be useful to switch users? from my account to my account?!

While your command isn't that complicated, I believe new Linux users would rather point and click than type all of that. It is inconsistent for a menu to only show up if a second user is added to the system. If that behavior had remained, the user help would have had to do the more complicated "Click the indescribable button in the top right corner of your screen. Select System Settings. Now find User Accounts way at the bottom. You might need to scroll down to see it" every time we mentioned changing account settings.

The "Switch From" button has one bonus use: allowing a user to log in to say Unity & GNOME Shell at the same time. While definitely not a normal use case, without that button, that use case might be impossible. So it's a design versus functionality problem.

---

### Post by lucazade on 2011-08-27
> **jbicha said:**
> While your command isn't that complicated, I believe new Linux users would rather point and click than type all of that. It is inconsistent for a menu to only show up if a second user is added to the system. If that behavior had remained, the user help would have had to do the more complicated "Click the indescribable button in the top right corner of your screen. Select System Settings. Now find User Accounts way at the bottom. You might need to scroll down to see it" every time we mentioned changing account settings.

The "Switch From" button has one bonus use: allowing a user to log in to say Unity & GNOME Shell at the same time. While definitely not a normal use case, without that button, that use case might be impossible. So it's a design versus functionality problem.

Looks like this time you won (and I'll patch my indicator!).
I was so happy to not see user menu again in Oneiric that this new one, inside an overloaded indicator-session, make me "sad".. i'll survive! :)

---

### Post by jbicha on 2011-08-27
It wasn't a fight. :-) It would be nice if individual indicator status menus could be hidden without requiring recompiling. Some support this (like the clock!).

You could try submitting a patch/merge proposal for a hidden gsettings to hide the user menu regardless of how many users are setup on the computer.

---

### Post by nrundy on 2011-08-27
> **Curnel_D said:**
> Lol, I don't mind the bug.  It's an alpha release, afterall.  But the entire user menu itself is useless to me and just mucking up my workspace.

+1

I've always uninstalled the "Me-Indicator"

Hopefully I'll be able to uninstall the new Me-indicator as well.

---

### Post by lucazade on 2011-08-27
> **nrundy said:**
> +1

I've always uninstalled the "Me-Indicator"

Hopefully I'll be able to uninstall the new Me-indicator as well.

no, you can't.
it is part of indicator-session now.

---

### Post by mc4man on 2011-09-06
It seems to be working right now in dconf so another option (vs. rebuild) to remove would be 
```
gsettings set org.gnome.desktop.lockdown disable-user-switching true


```

---

### Post by lucazade on 2011-09-06
> **mc4man said:**
> It seems to be working right now in dconf so another option (vs. rebuild) to remove would be 
```
gsettings set org.gnome.desktop.lockdown disable-user-switching true


```

great.. you made my day :)
it works, bye me-menu

---

### Post by jbicha on 2011-09-06
This was fixed in [https://launchpad.net/ubuntu/+source/indicator-session/0.3.4.3-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-session/0.3.4.3-0ubuntu1) .

---

### Post by alexvy13 on 2011-09-16
would it be safe to just remove inidicator-session in synaptic?

---

### Post by jbicha on 2011-09-17
No, you likely don't want to do that as that will remove the system menu as well.

Instead set **/apps/indicator-session/user-show-menu** to false in dconf-editor. (That gsettings may move in the future since it's rather inconsistent that we have 4 different indicators using gsettings and all 4 chose a different schema location!). Alternatively, you might like setting **show-real-name-on-panel** to false to just use an icon without text for the user menu.

It looks like you'll need to restart Unity for the user menu to pick up on your change.

---

