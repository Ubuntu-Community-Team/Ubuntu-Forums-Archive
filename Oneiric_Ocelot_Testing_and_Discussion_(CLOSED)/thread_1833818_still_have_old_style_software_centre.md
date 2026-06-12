---
title: "still have old style software centre"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by berthiggins on 2011-08-26
Hi Everyone seems to be talking about the new software centre and how it is now default .
My system is still using the old one.
Please forgive me if the answer has been posted but I cannot find it.
Any ideas what went wrong?

---

### Post by cariboo on 2011-08-26
If you are using anything but the Main mirror for updates, you may have to wait for it to catch up.

---

### Post by coffeecat on 2011-08-26
> **cariboo907 said:**
> If you are using anything but the Main mirror for updates, you may have to wait for it to catch up.

+1.

The GB Ubuntu mirror simply stopped getting updates for over 24 hours. I haven't checked (the GB mirror) since yesterday, but when I switched to the main mirror (yesterday), over 100MB of updates tumbled into my system. :)

---

### Post by Sennaista on 2011-08-26
> **coffeecat said:**
> +1.

The GB Ubuntu mirror simply stopped getting updates for over 24 hours. I haven't checked (the GB mirror) since yesterday, but when I switched to the main mirror (yesterday), over 100MB of updates tumbled into my system. :)

I'm in the UK and didn't change mirrors but there was a large update today, including software-centre, but it is still the old style.

---

### Post by coffeecat on 2011-08-26
> **Sennaista said:**
> I'm in the UK and didn't change mirrors but there was a large update today, including software-centre, but it is still the old style.

The GB mirror must be well behind because I got the new-style software centre from the main mirror either this morning or last evening (can't remember exactly when).

Yesterday, I experimented with some of the "other" UK servers such as virginmedia and mirrorservice and I was getting different results with each. After doing a reload from one of those, Synaptic informed me that I had a broken package but that it couldn't find it, and then changed its mind when I reverted to the main mirror. :| The subsidiary mirrors must be in an inconsistent state at the moment.

---

### Post by fjgaude on 2011-08-26
The changes are coming so fast in step with the first Beta release this coming Thursday that links are too slow with syncing.

From the main mirror thinks look to be coming in shape for the release.

---

### Post by klim8 on 2011-08-26
```
$ software-center-gtk3
```

---

### Post by berthiggins on 2011-08-27
Hi Guys thanks for the replies but I have been on the main mirror since alpha 1.
I can see the new software center by running software-center-gtk3
but, my understanding is that it should now be the system default?

---

### Post by mc4man on 2011-08-27
If you're using it from a  launcher icon then remove it. Start the new S-C and then pin
Alt+f2 > software-center-gtk3 should suffice

Atm on a fresh install the /usr/share/applications/ubuntu-software-center.desktop Exec='s to the new S-C script but both the old & new scripts are still being installed along w/ 2 /usr/bin links

Edit:
or you could open & ck. /usr.share/applications/ubuntu-software-center.desktop & make sure the Exec= is 
software-center-gtk3

---

### Post by berthiggins on 2011-08-27
Thanks mac4man
I have edited the desktop entry.
I think this install is "limping" it has lasted since alpha 1 with some dist-upgrades to get it updated at times .
Think a reinstall may be the way forward.

---

