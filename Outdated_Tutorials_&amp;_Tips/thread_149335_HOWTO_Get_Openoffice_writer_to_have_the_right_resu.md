---
title: "HOWTO: Get Openoffice writer to have the right result of ctrl-shift-b"
date: 2006-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by kwaanens on 2006-03-23
**This is posted in the howto-section. Use that instead: <http://ubuntuforums.org/showthread.php?t=149335>**

In OpenOffice writer there is supposed to be an option to make characters "shrink" and "jump" up to the top of the line, like in math: an exponential function, like 2² or down, like the "2" in H20.

Ctrl-shift-p gives the right result (2²), but ctrl-shift-b does not. In order to fix this, do:

```
$ sudo gedit /usr/lib/openoffice/program/soffice
```

If you're using OpenOffice 2.0 with Breezy, that would be:

```
$ sudo gedit /usr/lib/openoffice2/program/soffice
```

Then insert 
```
export GTK_IM_MODULE=xim
```
on a new line in the file. I put it right beneath 
#
# STAR_PROFILE_LOCKING_DISABLED=1
# export STAR_PROFILE_LOCKING_DISABLED
#

Restart OOowriter (and the quickstart, if that's enabled), and ctrl-shift-b gives the right result.

This bug is present in Breezy and 
Dapper development, and probably Hoary as well.

See: [http://www.openoffice.org/issues/show_bug.cgi?id=57023](http://www.openoffice.org/issues/show_bug.cgi?id=57023) for more on this.

- Ketil

---

### Post by kwaanens on 2006-03-23
Sorry, can any administrator please move this to the howto-section?
Thanks!

- Ketil

Edit: Nevermind, posted it there myself at <http://ubuntuforums.org/showthread.php?t=149335>. Now that I know where howtos go, I'll never post another howto in this section.

---

### Post by robenroute on 2006-03-23
[QUOTE=kwaanens] In order to fix this, do:

```
$ sudo gedit /usr/lib/openoffice/program/soffice
```

[/QUOTE]

That could be **/usr/lib/openoffice2/program/soffice** for OOo-2.0 users.

Thanks for the tip, though.

---

### Post by kwaanens on 2006-03-23
[QUOTE=robenroute]That could be **/usr/lib/openoffice2/program/soffice** for OOo-2.0 users.

Thanks for the tip, though.[/QUOTE]

You're quite right! I'm using Dapper, and there it's "openoffice". In Breezy 2.0 it's what you're saying.

Editing in this in the original post.

- Ketil

---

### Post by kwaanens on 2006-03-23
In OpenOffice writer there is supposed to be an option to make characters "shrink" and "jump" up to the top of the line, like in math: an exponential function, like 2² or down, like the "2" in H20.

Ctrl-shift-p gives the right result (2²), but ctrl-shift-b does not. In order to fix this, do:

```
$ sudo gedit /usr/lib/openoffice/program/soffice
```

If you're using OpenOffice 2.0 with Breezy, that would be:

```
$ sudo gedit /usr/lib/openoffice2/program/soffice
```

Then insert 
```
export GTK_IM_MODULE=xim
```
on a new line in the file. I put it right beneath 
#
# STAR_PROFILE_LOCKING_DISABLED=1
# export STAR_PROFILE_LOCKING_DISABLED
#

Restart OOowriter (and the quickstart, if that's enabled), and ctrl-shift-b gives the right result.

This bug is present in Breezy and 
Dapper development, and probably Hoary as well.

NOTE: If you upgrade OOo version, you'll have to do this over again, as /usr/lib/openoffice(2)/program/soffice will be replaced with a new version on upgrade.

See: [http://www.openoffice.org/issues/show_bug.cgi?id=57023](http://www.openoffice.org/issues/show_bug.cgi?id=57023) for more on this.

- Ketil

---

### Post by wolli on 2006-04-24
While this solution would probably be helpful for **most** users, it is not perfect for everyone.

GNOME uses Ctrl+Shift+HEX notation to allow you enter arbitrary Unicode characters such as &#9824;&#9829;&#9827;&#9830;. So if your docs are full of Unicode, you might want to stick with the standard GTK+ input method instead of xim. If you need an easy way to do subscripts at the same time, you can reassign another shortcut key to <subscript> via Tools-Customise-Keyboard in OpenOffice.org.

---

### Post by kwaanens on 2006-04-27
Ctrl+Shift+b is already set up as being subscript, but if I write a letter and then select that letter, ctrl+shift+b makes it like this: _B_

Any other ideas?

- Ketil

---

### Post by Markus Valkeapaa on 2006-09-27
:-D Thank you very much kwaanens! Office applications in linux have been given me headaches. This was a major problem for me, since often need keyboard shortcut for subscript. 
 
 -Markus

---

### Post by kwaanens on 2006-12-08
Note: It does appear that this bug has been fixed in Edgy as I'm writing this. (Might have been since Edgy was released, but I didn't test it until today's edgy-proposed updates)

- Ketil

---

### Post by kwaanens on 2006-12-08
Note: It does appear that this bug has been fixed in Edgy as I'm writing this. (Might have been since Edgy was released, but I didn't test it until today's edgy-proposed updates)

- Ketil

---

### Post by raziv on 2007-01-27
> **kwaanens said:**
> Note: It does appear that this bug has been fixed in Edgy as I'm writing this. (Might have been since Edgy was released, but I didn't test it until today's edgy-proposed updates)

- Ketil

Bug persists on my PC Dapper, openeoffice.org 2.0.2-2ubuntu12.2.
The abovementioned fix solved it. thanks, Ketil! :KS 

- Raziv

---

### Post by EisenPM on 2007-04-22
the bug does exist in feisty with ooo 2.2. but the fix works, thanks!

---

### Post by kwaanens on 2007-04-22
It's not present on my Feisty. Weird.

- Ketil

---

### Post by EisenPM on 2007-08-28
it's still there in the german feisty.

---

