---
title: "Gnome Shell 3"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alexvy13 on 2011-09-06
How safe is it to install it as of this very moment? I had it before but i messed up my install (not related to gnome shell im pretty sure it wasnt) and i liked it! but i dont want to break my system, especially since i have it set up so awesomely right now :D

i did deja dup back up that time that time I messed up my system but when i tried to restore from that after re-installing 11.10 it got stuck on the screen that says staring kernel 00ps before yo log in and i had to reinstall. So idk if i accidently did something or if it was deja dup. I don't want to install unless i know how safe and stable it is (i don't care if i get a lot of error reports as long its still usable) and also only if deja dup really can save my butt.

---

### Post by SavageWolf on 2011-09-06
I use 11.10 with Gnome 3 on my Notebook (For U1). It's quite stable, but occasionally gnome-shell crashes/fails to load. If you have nautulus set to show icons on the Desktop, I'd suggest copying /usr/bin/gnome-shell to there, so you can start it up if it dies.

---

### Post by alexvy13 on 2011-09-06
Cool! or i might just make a keyboard shortcut for it ;) and what is the most recent version of it and is it available in the repos?
and if i wish to uninstall it how may i completely remove it (including its many dependencies) without having to write them all down somewhere to hunt for later in synaptic?

---

### Post by pressureman on 2011-09-06
> **SavageWolf said:**
> I use 11.10 with Gnome 3 on my Notebook (For U1). It's quite stable, but occasionally gnome-shell crashes/fails to load. If you have nautulus set to show icons on the Desktop, I'd suggest copying /usr/bin/gnome-shell to there, so you can start it up if it dies.

If you're going to do that, you should symlink it, not copy it.

```

ln -s /usr/bin/gnome-shell ~/Desktop/gnome-shell

```

---

