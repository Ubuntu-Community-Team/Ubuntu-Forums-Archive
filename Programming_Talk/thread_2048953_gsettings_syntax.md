---
title: "gsettings syntax"
date: 2012-08-27
forum: Programming Talk
---

### Post by heyup on 2012-08-27
What is the correct syntax to use where a key has multiple values?

For example:-
```
gsettings list-recursively org.gnome.nautilus.list-view
```
This lists the default keys and values:-
> org.gnome.nautilus.list-view default-visible-columns ['name', 'size', 'type', 'date_modified']
To add the values 'owner' and 'permissions' to the key, I tried this:
```
gsettings set org.gnome.nautilus.list-view default-visible-columns ['name', 'size', 'type', 'date_modified', 'owner', 'permissions']
```
But that doesn't work. It gives error. What is the correct syntax?

---

### Post by spjackson on 2012-08-27
You just need to quote the value
```

gsettings set org.gnome.nautilus.list-view default-visible-columns "['name', 'size', 'type', 'date_modified', 'owner', 'permissions']"

```

---

### Post by heyup on 2012-08-28
> **spjackson said:**
> You just need to quote the value
```

gsettings set org.gnome.nautilus.list-view default-visible-columns "['name', 'size', 'type', 'date_modified', 'owner', 'permissions']"

```
Thank you. That worked. Problem solved!

---

