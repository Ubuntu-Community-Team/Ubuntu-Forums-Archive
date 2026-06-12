---
title: "What IDE (with debugging GUI) for assembler?"
date: 2010-03-11
forum: Programming Talk
---

### Post by vcppp_p on 2010-03-11
Hi,
I need to use assembler a lot in coming weeks (for my university classes).
Under windows I'm using MASM with Visual C++ for debugging (it handles breakpoints and registry preview).
Is there anything similar for Ubuntu? Please, don't tell me that every source editor highlights the code ... I know that, but I need a debugger frontend! 

thanks,
v.

---

### Post by azagaros on 2010-03-12
As far for the Open source world, I don't believe there is one.

NASM might be your best start for something similar.  They may suggest an IDE for assembly.  I have never done assembly with an IDE personally, except to edit the files.

Nasm might also support gdb(gnu debugger).

Open Watcom comes with a an assembler, and also runs on Linux.  I haven't done enough research to see if I could run assembly through its debugger yet.

---

### Post by MadCow108 on 2010-03-12
can't help with an IDE
but gdb is perfectly capable of debugging assembler
with ddd you also have a good frontend to it. Although it looks archaic it has lots of very powerful features.

---

### Post by mmix on 2010-03-12
[http://sourcenav.berlios.de/](http://sourcenav.berlios.de/)
[http://projects.gnome.org/nemiver/](http://projects.gnome.org/nemiver/)
[http://www.codef00.com/projects.php#debugger](http://www.codef00.com/projects.php#debugger)
[http://www.gnu.org/software/ddd/](http://www.gnu.org/software/ddd/)
[http://ald.sourceforge.net/](http://ald.sourceforge.net/)
[http://oss.sgi.com/projects/kdb/](http://oss.sgi.com/projects/kdb/)

---

### Post by NathanB on 2010-03-12
MMIX obviously provided you with your best options.  But don't forget that [http://asm.sourceforge.net/](http://asm.sourceforge.net/) is a fantastic starting-point for any *nix ASM resource search.

Nathan.

---

### Post by matthew.ball on 2010-03-12
Emacs has an ASM mode available, plus integration with gdb.

However, the ddd GUI front-end available for gdb isn't available from within Emacs as far as I know.

---

