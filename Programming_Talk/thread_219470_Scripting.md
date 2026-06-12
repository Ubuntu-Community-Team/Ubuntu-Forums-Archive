---
title: "Scripting"
date: 2006-07-20
forum: Programming Talk
---

### Post by munwin on 2006-07-20
Have a few questions, all involving how to find out various things, using Bash.... Can I find out:
When the OS was initially installed ?
The version of X being used ?
The driver version numbers of ATi & Nvidia ?
The services that run at boot ?
List the Users and their Groups ?

TIA.
Mark.

---

### Post by Daverz on 2006-07-20
None of these are programming questions; they are basic Linux admin questions.  Well I guess the last one is a programming question as it's something that would be covered in Stevens's Unix Programming book.

I don't think there's any real way to know when the OS was installed, as opposed to the kernel, which you can check with uname.  I see there's an /etc/debian_version.  You could do a stat on that.  But that could be somewhat fluid...I'll leave that question for the more experienced debian people.

For X, you can use xdpyinfo.

For driver versions, modprobe.

Services are configured in the /etc/rc directories.

Users and Groups: /etc/passwd and /etc/groups (come on now, that's a basic unix question).

---

