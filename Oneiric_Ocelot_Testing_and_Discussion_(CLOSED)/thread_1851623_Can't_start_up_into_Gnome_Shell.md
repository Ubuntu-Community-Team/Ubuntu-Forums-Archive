---
title: "Can't start up into Gnome Shell"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ZackC456 on 2011-09-28
I can't automatically start up into Gnome Shell session or any other shell besides Unity without logging out and back in. Help?

[SIZE="2"]P.S.
I have nothing ageist Unity.[/SIZE]

---

### Post by LinuxFan999 on 2011-09-28
I think the only way to switch shells is to log out, select the shell you want, then log back in. There is no way to do that without logging out.

---

### Post by jbicha on 2011-09-28
Go ahead and file a bug. With GDM, it's possible for the same user to be logged into multiple desktop sessions but it's not possible with LightDM. It might be too late for 11.10 but it's worth asking since this is a regression.

Otherwise, listing your own name in Unity's user menu which doesn't do anything useful is a bit pointless.

---

### Post by lucazade on 2011-09-28
the only way I've found is by enabling autologin from user capplet in control panel and then modify lightdm.conf by hand forcing a different session.

```
sudo sed -i 's/user-session=ubuntu/user-session=ubuntu-2d/g' /etc/lightdm/lightdm.conf
```

this will change the default session that will be auto loaded... don't know the exact name for gnome-shell session, probably it is simply 'gnome'.
you can check it by looking at .desktop files in  /usr/share/xsessions/

---

