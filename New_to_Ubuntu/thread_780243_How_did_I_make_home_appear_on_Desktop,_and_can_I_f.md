---
title: "How did I make /home appear on Desktop, and can I fix it?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by nintennuendo on 2008-05-03
I don't know how I did it but I made the contents of my /home folder appear on my desktop, but the stuff on my desktop is now only visible through a file manager. 

someone please help?

---

### Post by SunnyRabbiera on 2008-05-03
well what precisely did you do before this?

---

### Post by llamakc on 2008-05-03
You can fix this by opening the program gconf-editor (type ALT-F2) and enter gconf-editor.

Now navigate to:

/apps/nautilus/preferences

and look for the entry on the right named "desktop_is_home_dir" and UNCHECK it.

You should be good to go.

This assumes you are using GNOME.

---

### Post by nintennuendo on 2008-05-03
Yes!  That is what I did the first time.  Thanks so much.

---

### Post by llamakc on 2008-05-03
Please mark the thread as [SOLVED].

---

