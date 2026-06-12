---
title: "Compiz Fusion Icon"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-13
meh....I DLed the icon, but I need the command to start the app to put in the icon config. Could someone please tell me the command I need to put in there?

thanks! .

---

### Post by ubuntu-freak on 2008-05-13
> **chadwit said:**
> meh....I DLed the icon, but I need the command to start the app to put in the icon config. Could someone please tell me the command I need to put in there?

thanks! .

 
The icon that sits in the system tray? I think the command is "fusion-icon" and you can make it start each time you login, by adding the command to System > Preferences > Sessions. 
 
Nathan

---

### Post by chadwit on 2008-05-13
ok that worked, but I'm trying to start the actual Compiz config GUI with all of the checkboxes.  "fusion-icon" starts the Compiz app. How do I start the Compiz config GUI?

---

### Post by ubuntu-freak on 2008-05-13
> **chadwit said:**
> ok that worked, but I'm trying to start the actual Compiz config GUI with all of the checkboxes.  "fusion-icon" starts the Compiz app. How do I start the Compiz config GUI?

 
In the Terminal:
 
**sudo apt-get install compizconfig-settings-manager**
 
Then open it in System > Preferences > Advanced Desktop Settings.
 
Nathan

---

