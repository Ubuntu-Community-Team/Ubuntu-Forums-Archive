---
title: "Whats Make error ERROR 1?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-09-08
I am trying to compile patched usbserial module.

I am getting the error 1.

What does it mean?

---

### Post by ModelM on 2008-09-08
On the man page for make, look under "Exit Status".

---

### Post by twistedumbrella on 2011-08-13
> **ModelM said:**
> On the man page for make, look under "Exit Status".

Exit Status

GNU make exits with a status of zero if all makefiles were successfully parsed and no targets that were built failed. A status of one will be returned if the -q flag was used and make determines that a target needs to be rebuilt. A status of two will be returned if any errors were encountered.

Always love those "go look it up" answers. Figured this might be a bit more helpful, since this comes up pretty high in the Google search results for make error 1. Having to open this just to go right back to Google is no fun.

---

