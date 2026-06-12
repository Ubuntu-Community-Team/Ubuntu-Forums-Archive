---
title: "How to change theme?"
date: 2011-08-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-08-04
I cant seem to find it ,typed 'appearance' and 'themes' in search but dont see any results.

---

### Post by madjr on 2011-08-04
> **rajeev1204 said:**
> I cant seem to find it ,typed 'appearance' and 'themes' in search but dont see any results.

ah 11.10 alphas and gnome 3...

try system settings

or look in the log out button

hopefully they will add some easier ways and shortcuts to access this

---

### Post by lucazade on 2011-08-04
@rajeev1204
 
you can change theme in three ways:
- using dconf-editor and navigate in gnome > desktop > interface and change theme preference (install dconf-tools)
- change gsettings directly via cli without using dconf-editor (don't remember now the command)
- install gnome-tweak-tool and tune settings via this tool (this will carry some extra deps like gnome-shell)

---

### Post by rajeev1204 on 2011-08-04
> **lucazade said:**
> @rajeev1204
 
you can change theme in three ways:
- using dconf-editor and navigate in gnome > desktop > interface and change theme preference (install dconf-tools)
- change gsettings directly via cli without using dconf-editor (don't remember now the command)
- install gnome-tweak-tool and tune settings via this tool (this will carry some extra deps like gnome-shell)


Hm things are different now it seems.I just installed the alpha .

Thanks ill try this out.Thanks majdr too.

---

### Post by madjr on 2011-08-04
ah forgot you need the gnome-tweak-tool (easiest way)

things are kinda a mess right now.

ubuntu will need to re-adapt or even rewrite some of these tools.

---

### Post by scradock on 2011-08-04
> **madjr said:**
> ah forgot you need the gnome-tweak-tool (easiest way)

things are kinda a mess right now.

ubuntu will need to re-adapt or even rewrite some of these tools.
I just tried installing gnome-tweak-tool, and altering some settings. I've previously tried altering theme settings with dconf-editor, and even in gconf.

None of the changes makes the slightest difference, as far as I can see.

Looks like the theme settings are locked to defaults - and one of the theme setting defaults is Adwaita, which doesn't appear in Synaptic.

I'm using GNOME with Gnome Shell, btw.

---

### Post by rajeev1204 on 2011-08-04
> **scradock said:**
> I just tried installing gnome-tweak-tool, and altering some settings. I've previously tried altering theme settings with dconf-editor, and even in gconf.

None of the changes makes the slightest difference, as far as I can see.

Looks like the theme settings are locked to defaults - and one of the theme setting defaults is Adwaita, which doesn't appear in Synaptic.

I'm using GNOME with Gnome Shell, btw.

Ok here is what i did.
Tried dconf editor and couldnt (=could not) manage to do it.
Installed gnome tweak tool and changed to ambiance.Have to wait a few seconds for it to change theme.Then if you log out and select gnome during login you will get a proper gnome-shell working.

---

