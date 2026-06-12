---
title: "FileZilla"
date: 2012-05-15
forum: Programming Talk
---

### Post by emoguitarist06 on 2012-05-15
Hey Ubuntu Community,

I have a little pet-peeve with using FileZilla under Ubuntu 12.04 64-Bit that I don't experience under Windows 7 64-Bit

Under my local host (my computer) FileZilla shows duplicates of a lot of my files, not all of them just some of them.
FileZilla adds a "tilde" ~ to the end of the title

Example:
index.php <--- original, my file as seen in Nautilus
index.php~ <---FileZilla shows this and the one above

I have attached a screenshot

Thank You,
Phillip

---

### Post by The Cog on 2012-05-15
They are probably real files. Have a look in that directory with your normal Ubuntu file browser and turn on the option to show hidden files (probably control-H). 

Several editors, including gedit, leave a backup copy of the original file contents (same name with a tilde on the end) when you edit and save a modified copy.

---

### Post by emoguitarist06 on 2012-05-15
> **The Cog said:**
> They are probably real files. Have a look in that directory with your normal Ubuntu file browser and turn on the option to show hidden files (probably control-H). 

Several editors, including gedit, leave a backup copy of the original file contents (same name with a tilde on the end) when you edit and save a modified copy.

Okay yes they are hidden files which seem to be backups

However is there a way to hide the hidden files from showing in FileZilla? I just looked through the interface settings and I didn't see such an option

---

### Post by codemaniac on 2012-05-15
In order to prevent Gedit from creating these backups in the future, open up Gedit, open the Preferences dialog (Edit > Preferences), select the Editor tab, remove the check in the &#8220;Create a backup copy of files before saving&#8221; option, and click Close. After doing this, Gedit will no longer make the backups with tildes all over the place.

---

### Post by emoguitarist06 on 2012-05-15
> **codemaniac said:**
> In order to prevent Gedit from creating these backups in the future, open up Gedit, open the Preferences dialog (Edit > Preferences), select the Editor tab, remove the check in the “Create a backup copy of files before saving” option, and click Close. After doing this, Gedit will no longer make the backups with tildes all over the place.

Nice! Although that's an awesome feature of gedit I have never found myself using it in the years I've been using gedit ;)

---

