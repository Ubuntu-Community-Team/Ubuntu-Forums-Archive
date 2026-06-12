---
title: "How do i install fonts?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by josh_melvin on 2008-05-20
Does anyone know how to install fonts? Because i am puzlled!

---

### Post by shifty_powers on 2008-05-20
msttcorefonts?

or just random fonts?

---

### Post by josh_melvin on 2008-05-20
> **shifty_powers said:**
> msttcorefonts?

or just random fonts?

just random fonts, like ones from fontriver.com

---

### Post by stchman on 2008-05-20
> **josh_melvin said:**
> Does anyone know how to install fonts? Because i am puzlled!

I have a tutorial on font installation.

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

Hope this helps.

---

### Post by HotShotDJ on 2008-05-20
> **josh_melvin said:**
> Does anyone know how to install fonts? Because i am puzlled!It depends.  Some fonts are in the repositories.  However, if you've got some random true-type fonts that you want to use, you can simply copy them to your /home/USER/.font directory (replace USER, with your user name, of course).  Then run from a terminal:```
sudo fc-cache -vf
``` to make them available to applications.

---

### Post by HotShotDJ on 2008-05-20
> **stchman said:**
> I have a tutorial on font installation.Hi, stchman!  I looked at your tutorial and it is nicely done.  May I humbly suggest an edit?  You suggest that the preferred location is /usr/share/fonts, which is exactly correct for system-wide deployment.  I would approach it from the other direction with a statement such as this:
> I recommend you install them in the #2 location. However, if you want other users on your system to also have access to your new, shiny, fonts, you'll need to use the #1 location to make them available system wide.Changes at the system-level should always be presented as the scary, last-resort, method for configuring a system.

---

### Post by robertchahine on 2008-05-20
i think this script may help you

[http://www.gnome-look.org/content/show.php/Font+Installer?content=80905](http://www.gnome-look.org/content/show.php/Font+Installer?content=80905)

---

