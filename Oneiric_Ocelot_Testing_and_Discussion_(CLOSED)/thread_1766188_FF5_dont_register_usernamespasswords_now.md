---
title: "FF5 dont register usernames/passwords now"
date: 2011-05-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-05-24
when i register on a new site then login, FF5 dont ask if i want to save the username/password

---

### Post by dext on 2011-05-24
> **dino99 said:**
> when i register on a new site then login, FF5 dont ask if i want to save the username/password

if i recall its still Beta, expect Bugs. report them.

---

### Post by Sworddragon on 2011-05-24
My firefox 5 installation is working fine (so it's maybe not a bug). You can check if the input elements of the site got the attribute autocomplete="off". This attribute suppresses the saving of passwords.

If the attribute exists you can temporary remove it with the addon Firebug. If this isn't the problem try temporary using a clean profile by renaming your ~/.mozilla directory.

---

