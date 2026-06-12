---
title: "howto set rdesktop via ssh?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Ashrael on 2008-04-23
Hi,
 
MY QUESTION: how can i set rdesktop active from terminal?

Is it a setting in gconf? cannot find it.. 

I do have a ssh connection to the machine...


TIA..

---

### Post by sdennie on 2008-04-23
Have a look in /desktop/gnome/remote_access in gconf-editor.

---

### Post by bluefrog on 2008-04-23
in the xml file
.gconf/desktop/gnome/remote_access/%25gconf.xml

You could also enable it using the GUI over ssh by issuing ssh -Y user@machine vino-preferences

James Dupin

---

### Post by Ashrael on 2008-04-23
THANKS!

will give that a try...

---

