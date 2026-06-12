---
title: "manpage cannot show description for system call"
date: 2008-05-25
forum: Programming Talk
---

### Post by namtien on 2008-05-25
Hi all,
i'm writing a socket program but when i tried to use manpage to show usage information for some api but it always returned the messages like these:

man select => No manual entry for select
man 2 select => No manual entry for select in section 2

would you please help me?

---

### Post by fyplinux on 2008-05-25
try
     sudo apt-get install manpages-dev
to install the manpages

---

### Post by namtien on 2008-05-25
thanks fyplinux a lot! it works fine now!!!

---

