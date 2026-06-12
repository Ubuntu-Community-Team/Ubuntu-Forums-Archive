---
title: "Switch between unity and gnome-shell"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by RikoW on 2011-09-22
Dear all,

I'd like to test both unity and gnome shell to see which one I like better. So I installed gnome-shell as well, but when I selected it at login, I didn't get a desktop. I only got what looked like a full screen, transparent gnome-shell window. Couldn't do anything not even log-out.

But worse, when I wanted to login to unity again, the set-up was bombed, I guess the compiz profile could messed up. Again I eneded up with a blank desktop. While fixing it, I noticed that the unity plugin was disabled.

How do you run both "in parallel" without one messing up the other?

Thanks and cheers,
                 Riko

---

### Post by dino99 on 2011-09-22
unity borked
compiz borked

so you need to refresh settings:

gnome-shell --replace &
unity --reset

and maybe the others too (compiz, metacity, gnome-session, ...)

---

### Post by RikoW on 2011-09-22
Thanks! Yeah, I know that 

However I don't really like to do that every time I switch environment. Plus, I'd loose my personal settings in compiz.

Cheers,
         Riko

---

### Post by dino99 on 2011-09-22
i fully agree, its why i dont care about unity on my end, its useless to my needs. So *unity* packages are not installed (ubuntu-desktop removed) and only use gnome-session-fallback.

---

