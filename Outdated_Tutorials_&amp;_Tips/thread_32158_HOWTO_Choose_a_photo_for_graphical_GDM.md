---
title: "HOWTO: Choose a photo for graphical GDM"
date: 2005-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by McQuaid on 2005-05-06
First off, Ubuntu is using whats called a graphical greeter, but there is no reserved space for pictures of users with that theme.  So to change that run System/administration/login screen setup.

Then go to the graphical greeter tab and cycle through them until you find one that uses pictures for logins.  You can have more themes if you install gdm-themes which is in universe.  

Once you have choosen one then next time you log in you will see a space for a picture for the users you have.  To select one you run gdmphotosetup.  Or create this menu short cut.

sudo gedit /usr/share/applications/LoginPhoto.desktop

copy this into gedit:

[Desktop Entry]
Name=Login Photo
Comment=Choose Login Photo
Exec=gdmphotosetup
Icon=gdm
Terminal=false
Type=Application
Categories=Application;System;

save, and you will now have a program under applications/system tools called Login Photo.  Pick a picture and you will see it on your next login.  Caution, I don't think gdm has any picture size constraints so choose something of reasonable size.  

Also, I haven't mucked with themes but it would be nice if someone could change the ubuntu theme to support photos.

---

### Post by BAshworth on 2005-05-06
Good to know.  I just typically put a jpg file named .face into the home folder of the user I want it to apply to, but this looks good too.

Thank you.

---

### Post by mtron on 2005-05-12
an other way for gnome:

open terminal 

$ gdmphotosetup

 ;-)

---

