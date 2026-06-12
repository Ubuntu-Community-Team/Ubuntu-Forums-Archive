---
title: "Ubuntu Software Centre Problem"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-02-05
Up to 2  days ago, this problem did not exist!
Install/Remove button inactive! in all installed items
Can only Install/Uninstall through Synaptic
Examples of other weird happenings:
Installed Affiche.app - Does not appear in any main desktop menu
Installed Rhinote - Appeared in menus
I am the only user - something has changed, but am at a loss as to what.
Would appreciate help in solving this annoying problem.:confused:

---

### Post by lechien73 on 2012-02-05
Does the Software Center work if you press Alt+F2 and type:

```
gksu software-center
```

Have you changed your login password recently? If so, you might need to change it in seahorse as well. To do this:

[LIST]
[*]Press Alt+F2 and type *seahorse*.
[*]Click on the **Passwords** tab
[*]Right-click on **Passwords: login**
[*]Choose **Change password**, type in your old log-in password, then enter the new one twice.
[/LIST]

---

### Post by Bumpalot on 2012-02-05
Software Center now works

Changed my login & keyring passwords in seahorse.

Thanks for getting back so quickly!!

---

