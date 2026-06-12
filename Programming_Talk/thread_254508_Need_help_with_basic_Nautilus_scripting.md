---
title: "Need help with basic Nautilus scripting"
date: 2006-09-10
forum: Programming Talk
---

### Post by bluntu on 2006-09-10
I would like to UNRAR a selected rar file.

```

unrar e $@

```

Problem is that some files have password so I would like a dialog to appear before doing the unrar thing. The dialog would asks for a password and then pass it onto the unrar command.

```

unrar e $@ p$THE_PASS

```

Not sure if I got that last part correct (the p[password]). I need help with the dialog and password variable.

---

### Post by lukew on 2006-09-10
Collecting information from the user at the terminal is always called standard input:

< as aposed to >, which is standard output.

[http://www.ibiblio.org/gferg/ldp/practical_linux_guide/x80.html](http://www.ibiblio.org/gferg/ldp/practical_linux_guide/x80.html)

Bash does not have "dialog" though I think I have read about a program called whiptail, which can convert bash into some form of gui.

I hope this helps.

Luke

I hope this helps.

---

### Post by Tomosaur on 2006-09-10
password=$( zenity --entry --text="Enter password:" --title="Password")
unrar e $@ $password

---

### Post by cwaldbieser on 2006-09-11
> **Tomosaur said:**
> password=$( zenity --entry --text="Enter password:" --title="Password")
unrar e $@ $password

You would probably want to add the "--hide-text" option to the zenity command so the password shows up as asterisks.

---

