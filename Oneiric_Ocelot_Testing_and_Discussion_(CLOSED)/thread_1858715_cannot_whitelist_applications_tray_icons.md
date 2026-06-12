---
title: "cannot whitelist applications tray icons"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by beew on 2011-10-12
I try to change the system-whitelist in dconf-editor to ['all'] but it always reverts to the default when I close dconf-editor. 

Help!

---

### Post by mc4man on 2011-10-12
Not a big fan of 'all' vs. naming individually  here but - 
when using dconf-editor to make changes you need to keep the cursor in the edit area & press enter on the keyboard to set
If you try to 'click set' nothing will change as you've seen

Or just run this - (& then with either method log out/in

```
gsettings set com.canonical.Unity.Panel  systray-whitelist "['all']"
```

---

### Post by beew on 2011-10-12
Thanks! It works. Though I don't remember having to do that in Natty.  Maybe I am just confused. :)

---

