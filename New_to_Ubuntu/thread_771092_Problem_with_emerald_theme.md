---
title: "Problem with emerald theme"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Saardox on 2008-04-27
Hello all. I have compiz fusion and can run perfectly the desktop effect but after importing and selecting themes in emerald theme manager nothing happens. What do I need for this application to work?

---

### Post by Alehbye on 2008-04-27
Once you have a theme selected in Emerald, press alt+f2 and type:

emerald --replace

your theme should update correctly now. You may need to add that same command to your startup configuration as well. That's what I had to do atleast. There is probably another fix, but I haven't found it yet.

---

### Post by omns on 2008-04-27
I usually run

emerald --replace &

I don't know if the '&' makes a difference

---

### Post by Alehbye on 2008-04-27
> **omns said:**
> I usually run

emerald --replace &

I don't know if the '&' makes a difference


From what I've read, the '&' just tells it to execute the command as a background process.

---

