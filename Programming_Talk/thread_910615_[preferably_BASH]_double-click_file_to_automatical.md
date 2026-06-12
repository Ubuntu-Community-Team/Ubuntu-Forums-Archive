---
title: "[preferably BASH] double-click file to automatically &quot;open with&quot; my script?"
date: 2008-09-04
forum: Programming Talk
---

### Post by MaxIBoy on 2008-09-04
I'm writing a BASH script to parse the .lnk files that pass for shortcuts on Windows filesystems. Ideally, I'd double-click a .lnk file, and the target will be opened with the default application (so double-clicking a shortcut to a program in the "desktop" folder of my Windows installation opens the program in WINE.)

How do I associate the .lnk file format with my script, and what code should I write in my script to receive whatever file it is supposed to open?

If this is more conveniently done in another language, let me know.

---

### Post by ghostdog74 on 2008-09-04
don't know if its want you want. see [here](http://jesgue.homelinux.org/scripts/lnk2symlink)

---

### Post by mssever on 2008-09-04
In Linux (or Gnome; I don't know about other environments), you associate mimetypes, not extensions. Check out xdg-open for your best bet to auto-open a file in the right application. You might be best off "converting" .lnk files to .desktop files. There are a number of examples in /usr/share/applications, and there's a spec on freedesktop.org.

---

### Post by cb951303 on 2008-09-05
right click any *.lnk file.
click properties.
go to "open with" tab.
click "add".
click "use a custom command". 
voila!

---

### Post by mssever on 2008-09-05
> **cb951303 said:**
> right click any *.lnk file.
click properties.
go to "open with" tab.
click "add".
click "use a custom command". 
voila!
So How do you distinguish between a shortcut to an MP3 and a shortcut to an OOo document?

---

### Post by cb951303 on 2008-09-05
> **mssever said:**
> So How do you distinguish between a shortcut to an MP3 and a shortcut to an OOo document?

in this case that's the job of his/her shell script. there is no other way of doing it...

---

### Post by mssever on 2008-09-05
That's clearer now. You didn't specify earlier that a custom shell (or other) script was required.

---

### Post by cb951303 on 2008-09-05
> **mssever said:**
> That's clearer now. You didn't specify earlier that a custom shell (or other) script was required.

OP did. he/she is talking about relating his/her shell script to *.lnk files

---

### Post by MaxIBoy on 2008-09-06
> **mssever said:**
> So How do you distinguish between a shortcut to an MP3 and a shortcut to an OOo document?

/usr/bin/gnome-open.

---

