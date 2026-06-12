---
title: "Create a Debian Package"
date: 2008-11-28
forum: Packaging and Compiling Programs
---

### Post by flouran on 2008-11-28
Hi guys,
I wanted to create a debian package which would place my nautilus script in the directory ~/.gnome2/nautilus-scripts. Does anyone know from experience how to create a debian package and/or an easy-to-follow guide on the internet?

Any help is greatly appreciated

Happy Holidays!

---

### Post by x1a4 on 2008-11-28
Hi,
Try the [Ubuntu Packaging Guide]("https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html")

---

### Post by bapoumba on 2008-11-28
Moved to Packaging and Compiling Programs.

---

### Post by Flimm on 2008-12-05
Follow this guide: [http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717) , it's designed for files that aren't programs or for files that don't need to be compiled.

Unfortunately, there is no easy way to install files in a user's home directory, since .deb packages are meant for system-wide changes. Here's what I did:
1- I put all the scripts in /usr/share/nautilus-scripts
2- I symlinked /etc/skel/.gnome2/nautilus-scripts/shared to /usr/share/nautilus-scripts , that way all new users will automatically get the shared nautilus scripts.
The only thing that was left was adding the scripts for existing users, I had to make two bash scripts for that, postinst which runs at the end of the installation of the package, and postrm , which runs after uninstallation.

I've attached the tarball with the files I used before I typed ```
dpkg-deb --build nautilusstuff_1.0-1
```, as well as the .deb file. Enjoy!

---

