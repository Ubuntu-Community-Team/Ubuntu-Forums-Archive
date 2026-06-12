---
title: "Changing Gnome 3 default file links"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by John_Rose1 on 2012-08-01
I have just updated from Ubuntu 10.10 (Meerkat) to 11.10 (Ocelot) and installed Gnome since I don't like Unity, but that unfortunately means going from Gnome 2 to Gnome 3. [Even in the Classic Gnome 3 interface, things seem much less flexible and friendly than in Gnome 2; I see that there is a broad user consensus that this change was for the programmers not the users, but now we have to accept it.]

My problem is how to change the default file links (Documents, Downloads, Images, etc.) which are proposed in the Places entry on the top toolbar in Classic Gnome 3 to the real addresses in my system (for example I have Documents at /media/Data/Documents and not at /home/[my account]/Documents). With 10.10 and default OpenOffice I could change the links by opening OpenOffice, asking to open a file, and right clicking on the default name to change (like Documents) but this does not work in the present situation either because of Gnome 3 and/or because OpenOffice has been replaced by LibreOffice.

So on the web I saw that the changes can be effected by editing the user-dirs.dirs file in the .config directory of my home directory. I have done this, and when I reboot the configuration file is as I want it, but I still get the default values for the default links (e.g.  /home/[my account]/Documents for "Documents"). What do do?

                                               Thanks, John

P.S. I note that the new values for the default file names are apparently taken into account by some programs like Shotwell, but not by LibreOffice and not reflected in the Places list.

---

