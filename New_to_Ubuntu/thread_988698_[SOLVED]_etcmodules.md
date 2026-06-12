---
title: "[SOLVED] /etc/modules"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Father Shaggy on 2008-11-20
I've had a problem with my wireless adapter driver, but it's been fixed.  however, I'd rather not load the driver every time I want to use the modem.  I've been told to add "ndiswrapper" to the modules file, but when I try to, I'm told I don't have the authority to make changes to the file.

How do I change it?  Why doesn't it know I'm the administrator?

---

### Post by santy_kushwaha on 2008-11-20
the reason why it doesnt allow u to modify the files sytem bcoz by defult u wont have the root acess to make changes in the system files so log in as root and do so

Lets us know if u know about how to again Root acess...if not i will post a reply again how to do so

---

### Post by adult swim on 2008-11-20
to change it hit alt+f2 and type in ```
gksudo gedit /etc/modules
``` then put ```
ndiswrapper
``` at the end of the file and save it

---

### Post by Father Shaggy on 2008-11-20
This got it.  Thanks.

---

