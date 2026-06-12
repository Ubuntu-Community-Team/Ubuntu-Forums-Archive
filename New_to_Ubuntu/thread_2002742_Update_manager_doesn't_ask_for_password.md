---
title: "Update manager doesn't ask for password"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by s1wood on 2012-06-13
I've just started using the XFCE desktop on 12.04 and am finding that the  update manager isn't asking me for a password for the updates. This seems like a security weakness - is there any way of correcting it?

Susan

---

### Post by MG&amp;TL on 2012-06-13
Update manager by default doesn't ask for sudo password unless you're installing/removing, rather than updating software. I think there's some dbus(?) cleverness going on there to make that happen. Something to do with Windows users and the updater being automatic?

Anyway, if you want to need to use the root password, you can either use synaptic, or the command-line bindings:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by afixane on 2012-06-13
Yeah, that happen to me, to :shock:

anyway, just write this on your terminal
```
sudo apt-get upgrade
```

---

### Post by MG&amp;TL on 2012-06-13
> **afixane said:**
> Yeah, that happen to me, to :shock:

anyway, just write this on your terminal
```
sudo apt-get upgrade
```

You'll want to prepend:

```
sudo apt-get update
```

to check for any updates available on the server first.

---

### Post by philinux on 2012-06-13
> **s1wood said:**
> I've just started using the XFCE desktop on 12.04 and am finding that the  update manager isn't asking me for a password for the updates. This seems like a security weakness - is there any way of correcting it?

Susan

This is perfectly normal. This change happened a couple of releases back. The argument being why ask for a password if it's updating software that is is already installed.

If however a new kernel is being installed, for example ,then it will prompt for a password.

---

### Post by steveferson on 2012-10-20
I'm having a similar but different problem.

Update Manager doesn't ask for a password but then doesn't update anything after I click Install Updates!

I have to open a terminal and run 
```
sudo update-manager
```

Then it works... have I done something wrong to cause this?

---

### Post by brabender on 2013-01-08
> **steveferson said:**
> I'm having a similar but different problem.

Update Manager doesn't ask for a password but then doesn't update anything after I click Install Updates!

I have to open a terminal and run 
```
sudo update-manager
```

Then it works... have I done something wrong to cause this?

Bump... Same problem here. Running update manager from GUI and then checking or installing updates makes the program freeze. Running from terminal with ```
sudo update-manager
``` and it works without problem. Running from GUI in Cinnamon, Unity and Gnome Classic in the same computer it works too (I'm still trying desktops to replace Gnome 2, so far XFCE seems to be the best choice)

---

