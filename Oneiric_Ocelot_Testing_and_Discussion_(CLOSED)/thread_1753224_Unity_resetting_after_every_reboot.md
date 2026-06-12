---
title: "Unity resetting after every reboot"
date: 2011-05-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2011-05-08
Is this happening to anyone else, every time I restart my computer the default icons are back in the launcher. It's annoying having to re-configure every time :(

---

### Post by cecilpierce on 2011-05-08
> **lee.jarratt said:**
> Is this happening to anyone else, every time I restart my computer the default icons are back in the launcher. It's annoying having to re-configure every time :(

There is a thread on this 'Panel Icons'

Your not alone.

---

### Post by go7Ul1ai on 2011-05-08
> **cecilpierce said:**
> There is a thread on this 'Panel Icons'

Your not alone.

Ah I saw it but got mislead by the title, I thought it was an issue with the panel and not the launcher. Thanks for the heads up

---

### Post by mc4man on 2011-05-08
Don't think this is terribly unexpected, you're no longer using natty and nothing resembling O at all

I guess if I was doing so i'd ck. a few things. - 
As soon as you add or remove a shortcut from the launcher (icon), it should be immediately seen in either dconf-editor or gsettings

```
gsettings get com.canonical.Unity.Launcher favorites
```
So I'd ck. that
If it is then maybe boot to text login, login and re-run the above command and see what it shows

Worst case just create a gsettings set command to run just after login (could be added to startup apps

---

### Post by pferraro on 2011-05-09
Downgrade libdconf0 to the version from natty.  There's something wrong with the oneiric package - gsettings is not recognizing the dconf backend and so defaults to a read-only in-memory backend.

---

### Post by bedbug on 2011-05-09
sudo apt-get install dconf-gsettings-backend

---

### Post by pferraro on 2011-05-09
> **bedbug said:**
> sudo apt-get install dconf-gsettings-backend

Ah - so this logic was refactored into a separate package, and the appropriate package dependency is missing.  Thanks.

---

