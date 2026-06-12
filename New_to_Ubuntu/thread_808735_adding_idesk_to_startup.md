---
title: "adding idesk to startup"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by rockerphil on 2008-05-26
ok, i'm putting the finishing touches on the OS i built from the Ubuntu 7.10 minimal CD by installing a command line interface then adding the x windows server, IceWM, and ROX as my filter. well here's what i can't figure out. i've installed idesk to use for desktop icons and to set background images, i can start it by running it from the therminal but i can't figure out how to set it to run at startup, i've found how to add it to run at startup with Fluxbox, but like i said, i'm using IceWM as my windows manager. any help would be greatly appreciated. thanx guys

---

### Post by iaculallad on 2008-05-26
> **rockerphil said:**
> ok, i'm putting the finishing touches on the OS i built from the Ubuntu 7.10 minimal CD by installing a command line interface then adding the x windows server, IceWM, and ROX as my filter. well here's what i can't figure out. i've installed idesk to use for desktop icons and to set background images, i can start it by running it from the therminal but i can't figure out how to set it to run at startup, i've found how to add it to run at startup with Fluxbox, but like i said, i'm using IceWM as my windows manager. any help would be greatly appreciated. thanx guys

Did you try adding the command to:

**> ~/.icewm/startup**

---

### Post by rockerphil on 2008-05-26
there is no "~/.icewm/startup" file, so i created one and added idesk to it, but still no go

---

### Post by iaculallad on 2008-05-26
> **rockerphil said:**
> there is no "~/.icewm/startup" file, so i created one and added idesk to it, but still no go

Post the script you loaded onto startup.

---

### Post by iaculallad on 2008-05-26
And don't forget to make it executable:

Code:

> chmod a+x ~/.icewm/startup

---

