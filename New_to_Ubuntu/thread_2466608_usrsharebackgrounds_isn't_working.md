---
title: "/usr/share/backgrounds isn't working"
date: 2021-08-31
forum: New to Ubuntu
---

### Post by psychohermit on 2021-08-31
Hi Folks

Running ubuntu 20.04.2.0 LTS amd64 on a 7 year oldHP ENVY TouchScreen Notebook. 

I put a bunch of backgrounds in /usr/share/backgrounds and they aren't available in "Change Background". It don't make sense.

Any clues?

Thanks,
--glenn

---

### Post by monkeybrain20122 on 2021-09-01
You need to edit /usr/share/gnome-background-properties/focal-wallpapers.xml. It is kind of tedious. Better just leave the wallpapers in some subfolders of ~/Pictures ( click desktop change desktop background and click + to add the picture)

---

### Post by psychohermit on 2021-09-01
Thank you, I will live with it rather than editing an xml

--glenn

---

### Post by tea for one on 2021-09-01
> **psychohermit said:**
> Thank you, I will live with it rather than editing an xml 

You do not have to fiddle around with an xml.

[COLOR="#0000FF"]monkeybrain20122[/COLOR] mentioned the procedure above.

Right Click your Desktop > Change Background > Click Add Picture (top right of window) > Navigate to desired location > Select picture > Click Open

The picture will appear ready to be selected as a background.

---

