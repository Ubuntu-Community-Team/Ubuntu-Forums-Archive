---
title: "Remove .sh"
date: 2015-11-21
forum: Packaging and Compiling Programs
---

### Post by rocco6 on 2015-11-21
Is there a trick to run a custom command without ./command.sh?

---

### Post by ian-weisser on 2015-11-21
You mean like 'sh command' instead ? Yes, easily.
Or you mean without the '.sh' suffix? Yes, easily - you can change the name to anything you wish. The suffix is for *you*, not the system. 
Or you mean without any shell command at all? Yes, but you need to learn either sockets or dbus.

---

### Post by Lars Noodén on 2015-11-21
Or if you mean run by just typing the name and not the whole path, then you can put it in ~/bin/ or /usr/local/bin/   If you put it in the former, it will be available your account after next login.  If you  put it in the latter, it will be available to everybody immediately.

---

