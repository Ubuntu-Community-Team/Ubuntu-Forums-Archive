---
title: "Any way to re-build Unity application cache from 'make install'?"
date: 2011-12-26
forum: Packaging and Compiling Programs
---

### Post by MicahCarrick on 2011-12-26
After my application installs it's .desktop file, Unity does not find the application without logging out and logging back in (thus, my user's would have to be told to log out as part of the installation process). Is there a command to rebuild the application cache?

---

### Post by MicahCarrick on 2011-12-26
I haven't tested it yet, but, I'm assuming a call to 'update-desktop-database' in the install data hook ought to do the trick.

---

### Post by MicahCarrick on 2011-12-26
Well now, update-desktop-database does not seem to work. That's strange. Anybody know?

---

