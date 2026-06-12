---
title: "Changing terminal colors"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by danne33 on 2015-11-25
Trying to change the terminal colors by _only_ using commands and _no mouse_ clicks.

The following two commands:
```
gconftool-2 --set "/apps/gnome-terminal/profiles/<profile_name>/foreground_color" --type string "#FFFFFF"
gconftool-2 --set "/apps/gnome-terminal/profiles/<profile_name>/background_color" --type string "#000000"
```
Are only possible to use when "**Use colors from system theme" **is unchecked in "Edit -> Profile preferences -> colors".

Is it possible with a terminal command to uncheck "Use colors from system theme"?
It is checked by default...

---

### Post by Holger_Gehrke on 2015-11-25
> **danne33 said:**
> Trying to change the terminal colors by _only_ using commands and _no mouse_ clicks.
... snip ...
Is it possible with a terminal command to uncheck "Use colors from system theme"?
It is checked by default...

With
```

gconftool-2 -R "/apps/gnome-terminal/profiles"

```

you can get a dump of all the setting in all profiles for gnome-terminal. The boolean setting "use_theme_colors" should be the one you want:
```

gconftool-2 --set "/apps/gnome-terminal/profiles/<profile_name>/use_theme_colors" --type boolean false

```

If you're trying to use this to change colors in a script, the commands 
```

tput setf <number of color in palette>
tput setb <number of background color in palette>

```
might be more useful. They change the foreground and background color to use for subsequent output.

Holger

---

