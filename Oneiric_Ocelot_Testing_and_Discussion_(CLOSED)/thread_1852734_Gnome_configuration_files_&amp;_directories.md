---
title: "Gnome configuration files &amp; directories"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zerubbabel on 2011-09-30
I did a fresh install of Oneriric Beta 2, then installed gnome-shell (which I prefer to Unity), and am trying to carefully restore my files and folders from my backed-up home directory (from 11.04 classic) so as not to corrupt or conflict with the new environment. 

On a previous attempt, I just restored my entire old home directory into the new environment, merging and overwriting whatever was preexisting in my new home directory, but then after logging out and in again, the desktop environment was gone.

So now that I have nice clean Oneiric/Gnome3 install, what directories and/or configuration files does the new gnome 3.2 environment depend on, which I should avoid overwriting when I restore the contents of my old home directory?

---

### Post by cariboo on 2011-09-30
To make things easier, just transfer your data files, and the specific configuration files for the programs you use. ~/.config is where the individual configuration files/directories exist.

I also transfer ~/.thunderbird to my home directory, as that's where all my mail since 2000 is stored.

---

### Post by zerubbabel on 2011-09-30
> **cariboo907 said:**
> To make things easier, just transfer your data files, and the specific configuration files for the programs you use. ~/.config is where the individual configuration files/directories exist.

I also transfer ~/.thunderbird to my home directory, as that's where all my mail since 2000 is stored.

Right, I know the application-specific configuration files and folders are safe, but what about restoring my old "keyring", wireless network passwords, etc.?

Also, what does Gnome 3 use to maintain a search index? I like recoll, but I don't want two indexers running.

---

