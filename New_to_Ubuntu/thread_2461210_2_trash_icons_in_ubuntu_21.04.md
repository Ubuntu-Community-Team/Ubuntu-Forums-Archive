---
title: "2 trash icons in ubuntu 21.04"
date: 2021-04-26
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2021-04-26
In Ubuntu 210.04 I moved trash icon to dock which is where I prefer it. I upgraded to ubuntu 21.04 and discovered that I have trash icon still in dock and now on desktop. is it possible to remove the one on dock or desktop? Again thx for help.

---

### Post by ipv2 on 2021-04-26
> **tuesdaybarrett said:**
> is it possible to remove the one on dock or desktop?

to remove drives from desktop :

```
gsettings set org.gnome.shell.extensions.ding show-volumes false
```

to remove home from desktop :

```
gsettings set org.gnome.shell.extensions.ding show-home false
```

to remove trash from desktop :

```
gsettings set org.gnome.shell.extensions.ding show-trash false
```

to remove drives from dock :

```
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false
```

to remove trash from dock :

```
gsettings set org.gnome.shell.extensions.dash-to-dock show-trash false
```

to bring them back just replace false with true in the above commands.

---

### Post by tuesdaybarrett on 2021-04-26
thanks that is quite helpful

---

