---
title: "using gdebi as the default to open .deb files"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by beew on 2011-10-11
Hi,

I want to use gdebi instead of the USC as the default application to open .deb files, I would like to know how to do that.  When right clicking a file the drop down menu has an entry called open with gdebi (if you gave it installed) but if you just right click it would be open by the USC. I want to change this behaviour, however, the properties menu doesn't have an option to choose gdebi as the default and the additon list doesn't have gdebi either (and add custom command is no longer availiable)

Thanks.

---

### Post by mc4man on 2011-10-11
Open up ~/.local/share/applications/mimeapps.list

Either create or edit 2 lines, one under [Default Applications]
```
application/x-deb=gdebi.desktop
```

And you might as well do also - under [Added Associations]
```
application/x-deb=gdebi.desktop;
```

---

### Post by lucazade on 2011-10-12
> **mc4man said:**
> Open up ~/.local/share/applications/mimeapps.list

Either create or edit 2 lines, one under [Default Applications]
```
application/x-deb=gdebi.desktop
```

And you might as well do also - under [Added Associations]
```
application/x-deb=gdebi.desktop;
```

this is interesting also for me. thanks for the hint.

---

