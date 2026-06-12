---
title: "tail: cannot open `debian/changelog' for reading"
date: 2009-01-20
forum: Packaging and Compiling Programs
---

### Post by giuspen on 2009-01-20
I receive this error:
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1
but the file changelog is in the "debian folder" :(
Please help me.

---

### Post by giuspen on 2009-01-21
Ok I was just launching the command from inside the debian directory.
The "sudo dpkg-buildpackage" command must instead be launched from the upper lever (shame on me).
Cheers.

---

### Post by Ampersand. on 2009-04-05
could you please expand on this further? i think i understand what you mean, correct me if im wrong.

so say the folder i need to compile is called BootTheme and it was inside a folder called Themes
i was doing cd /home/user/Documents/Themes/BootTheme
then dpkg-buildpackage -rfakeroot


I just tried to cd /home/user/Themes then the buildpackage and that turns out not to help.

so what should i do instead?

---

### Post by giuspen on 2009-05-03
> **Ampersand. said:**
> could you please expand on this further? i think i understand what you mean, correct me if im wrong.

so say the folder i need to compile is called BootTheme and it was inside a folder called Themes
i was doing cd /home/user/Documents/Themes/BootTheme
then dpkg-buildpackage -rfakeroot


I just tried to cd /home/user/Themes then the buildpackage and that turns out not to help.

so what should i do instead?

basically that command expects to find in the current directory a folder named "debian", and inside the "debian" folder a file named "changelog".
in the beginning i was with the terminal current directory in the same directory where the file "changelog" is, that was not correct.
you have to be one level up, so see in the current directory the folder "debian", not the file "changelog".
if you have further problems, use instead this way to create debian packages: [http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/x169.html]("http://tldp.org/HOWTO/Debian-Binary-Package-Building-HOWTO/x169.html") it's simple and effective.
cheers,
giuseppe.

---

### Post by gnomeout on 2010-05-29
> **giuspen said:**
> Ok I was just launching the command from inside the debian directory.
The "sudo dpkg-buildpackage" command must instead be launched from the upper lever (shame on me).
Cheers.

ROFL, I just made the same mistake, but opposite. I was one level too high.

---

