---
title: "HOWTO: kprinter style printing dialogs for GNOME"
date: 2004-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2004-10-27
Q: How do I get a nice printing dialog for non-GNOME applications?

A: Yeah, it is annoying figuring out a good way to print from like Firefox or xpdf. They have super-primitive printing systems, no way to configure printer properties, etc. KDE has a program called kprinter, which you can tell other apps to print with. Programs like firefox are configured to send kprinter its  print jobs, and kprinter presents you with a cool dialog that you can configure # copies, printer settings, etc. GNOME currently has no such feature, but they're working on such a system for the next GNOME release.

Though GNOME has no built-in printing managers (unlike KDE with kprinter), you have a few choices:


1. **install kprinter from KDE.**
   Simply install **kdeprint** with apt or synaptic. Instruct your program to issue the command **kprinter** to print. I do not recommend this solution because you need to initialize KDE libs every time you print, which could be time-consuming on older systems.

2. **Use the X Printing Panel**.
   Use apt or synaptic to install **xpp**. This is non-desktop-environment specific, and therefore looks plain and ugly inside GNOME. Nevertheless, it's a great printing program. Use in the same fashion as kprinter: set it as the printing command.

3. **Use gtklp**.
   Use apt or synaptic to install **gtklp**. This is a GTK program, so it'll "fit in" with the rest of your GNOME. **I recommend this program.** Use in same fashion as others.

---

### Post by drunken-wallaby on 2004-10-29
hello jdong. thanks for this perfect howto. everything now works fine. i found a little typo though. one has to install the package **kdeprint**, not kde-print :)

---

### Post by mr_ed on 2004-11-09
If this works (it looks promising) I'll buy you a beer or something, jdong!  Do you have a PayPal account? ;)

I've caused myself much grief last night looking for something to print 4x6 colour photos with my HP PSC 1210.
Gimp-print does nothing at all (turns out the PSC 1210 isn't supported -- the bar goes across the screen, status changes to "sending 24125435 bytes..." and then switches to 0 jobs), and everything else leaves huge borders, when I want NO border (or very little, at most)!

It's frustrating to the point where we're going to re-install Windows if it doesn't work -- as a dual-boot, of course.

---

### Post by jdong on 2004-11-09
[QUOTE=drunken-wallaby]hello jdong. thanks for this perfect howto. everything now works fine. i found a little typo though. one has to install the package **kdeprint**, not kde-print :)[/QUOTE]
Oops! Sorry! Gentoo, Fedora, and SuSE (the distros I "grew up" with) have a lot of memories still burned into me. It'll take me a while to get over that!

---

### Post by mr_ed on 2004-11-11
gtklp worked for me!  Thanks very much!

Now all I have to do is change the source code so that it has the GNOME 2.6+ file dialog.  Oh, and drag and drop.  And GnomeVFS.

All the previous file selectors are butt-ugly.

---

### Post by jdong on 2004-11-12
Please let us know if you do get those patches working!

---

### Post by mr_ed on 2004-11-18
Well... it's a bit slow going.

I've never coded before with GTK+, or used Anjuta, or ever done development on Free software before for that matter, so there's a bit of learning taking place.  :)
Now that I've discovered DevHelp, I'm a lot happier.

Also, it looks like they've simpified the interface a LOT with GTK+ 2.4.0.
For the block of code that I'm currently working on, 11 gtk_blah_blah_blah commands have been reduced to 3, while providing the same functionality.

---

### Post by mr_ed on 2004-11-24
Ok, I have a patch that uses the new file selector.  I've emailed the maintainer, so hopefully it'll show up in Debian Sid some time in the future.

Onto VFS, and drag and drop!  (I have a feeling that those will be a lot harder)  :)

Oh, also the bugs I discovered.  I'll post them here so I don't forget.
If you start gtklp not from a terminal, the File tab doesn't show up.
If you click the "reset all" button, and you have files listed in the selection box above, then "remove all" gets ghosted out.

---

### Post by herror on 2007-04-23
I have problems installing a HP Z11 printer and a Creative Audigy 2 soundcard. Do you knot where to look for answers? Thanks!

---

### Post by xurizaemon on 2007-05-21
thanks for this howto. I was delighted to get a nice print dialog out of Xemacs with this:

```

(custom-set-variables
 '(lpr-command "gtklp")
 '(ps-lpr-command "gtklp")
)

```

krpinter was very slow compared - it would keep xemacs tied up until the print job was finished.

@herror: that's not the delicate odour of linkspam i detect, is it?

---

