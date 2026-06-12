---
title: "^M character in file when checked out into Windows"
date: 2010-07-30
forum: Programming Talk
---

### Post by qmqmqm on 2010-07-30
When checking out files into Windows using a revision control system (e.g. cvs), make changes to the file, then check it back into cvs, every line will have a trailing “^M” generated from  Windows.

So when the file is checked out into a unix system afterwards, it will show the “^M” characters at the end of each line.

Is there a way to avoid the “^M” characters after working on the file in Windows; or remove these characters before checking it out into a unix system?

Is there a configuration that can be set in the IDE, or in CVS, that automatically handles this?

Thanks a lot.

---

### Post by worseisworser on 2010-07-30
The editor you use on Windows needs to be configured to use "Unix style newlines".

---

### Post by soltanis on 2010-07-30
If you can't get Windows to cooperate or just need to batch convert the newlines back, you can use the **[dos2unix]("http://gd.tuwien.ac.at/linuxcommand.org/man_pages/dos2unix1.html")**(1) program.

---

### Post by lisati on 2010-07-30
Unashamed plug for a similar utility to the better known "dos2unix" and "unix2dos" utilities: [http://lisati.homelinux.com/fixlinebreak.html](http://lisati.homelinux.com/fixlinebreak.html)
It's not particularly well written but it does the job and is portable.

---

### Post by dribeas on 2010-07-31
Depending on the revision control system you use, you might be able to configure [pre-]commit hooks to perform operations on the files before they are stored in the revision control system. You can then use dos2unix or similar scripts to remove the '\r' at the end of the lines.

---

