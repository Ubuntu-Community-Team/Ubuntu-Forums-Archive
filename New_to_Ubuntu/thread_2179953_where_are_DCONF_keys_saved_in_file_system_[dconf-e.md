---
title: "where are DCONF keys saved in file system? [dconf-editor &amp; gsettings]"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by kevin_do2 on 2013-10-10
I currently come across [COLOR=#ff0000]dconf-editor[/COLOR] and wonder where [COLOR=#ff0000]dconf[/COLOR] keys are saved in Linux systems. I also know that [COLOR=#ff0000]gsettings[/COLOR] command can change [COLOR=#ff0000]dconf[/COLOR] keys in terminal. For Example: 

# gsettings set org.gnome.shell.clock show-date true
# gsettings set com.canonical.indicator.session show-real-name-on-panel false
# gsettings set org.gnome.desktop.interface clock-show-date true

Where are [COLOR=#ff0000]org.gnome[/COLOR] in file system? Where can I get a list of all [COLOR=#ff0000]dconf[/COLOR] keys in file system?
Thanks.

---

### Post by steeldriver on 2013-10-10
You can do 

```
dconf dump /
```

although I *think* that only lists non-default key-value pairs; or

```
gsettings list-recursively
```

which seems to list everything.

---

### Post by heir4c on 2013-10-10
And with this command you safe the output direct in a file:
```
gsettings list-recursively > filename
```
You can change "filename" in anything you want.

---

### Post by Dennis N on 2013-10-11
> **kevin_do2 said:**
> I currently come across [COLOR=#ff0000]dconf-editor[/COLOR] and wonder where [COLOR=#ff0000]dconf[/COLOR] keys are saved in Linux systems. 
Thanks.

I assume the settings are stored in:

**~/.config/dconf/user**

The file command thinks **user** is data meaning it is binary stuff.

```
dn@Roxanne:~/.config/dconf$ file user
user: data

```

It is not human readable.

---

