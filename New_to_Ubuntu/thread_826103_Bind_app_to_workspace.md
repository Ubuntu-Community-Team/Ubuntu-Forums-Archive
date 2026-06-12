---
title: "Bind app to workspace?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Halsnalle on 2008-06-11
I guess this is so simple nobody has bothered writing it down, because I haven't been able to find any helpful information. Anyway, I'd like to bind certain applications to a specific workspace, so that, say, Skype and Pidgin always open in the second workspace. VirtueDesktops, which I use in Mac OS X, has this functionality, so how to do it on Ubuntu?

---

### Post by Cypher on 2008-06-11
in Kubuntu..click on the icon next the app's name on the Titlebar (with the _ [] X) go Advanced->Special Application Settings->Desktop, Remember, Desktop #.

I wonder if this holds true on Ubuntu as well, don't have access to a machine to try it out..

---

### Post by sdennie on 2008-06-11
If you are using compiz you can do this as well.  First:

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Effects Settings and scroll to the bottom where you will see "Place Windows".  On the second tab you can add rules to force windows to a particular desktop.  For instance, to force Pidgin to the second desktop, I think you could make a rule that looks like this:

```

class=Pidgin 1 0

```

---

### Post by MrBucket101 on 2008-11-13
> **vor said:**
> If you are using compiz you can do this as well.  First:

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Effects Settings and scroll to the bottom where you will see "Place Windows".  On the second tab you can add rules to force windows to a particular desktop.  For instance, to force Pidgin to the second desktop, I think you could make a rule that looks like this:

```

class=Pidgin 1 0

```
this method works perfectly, the only thing that irks me, is when i open an app i set to a different workspace than I'm on, the workspace does not automatically change

---

### Post by aneganov on 2010-10-12
I don't have such a configuration. 
Is there something similar in ccsm?

---

