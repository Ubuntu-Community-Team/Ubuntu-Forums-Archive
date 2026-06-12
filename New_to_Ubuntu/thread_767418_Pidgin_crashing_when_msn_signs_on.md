---
title: "Pidgin crashing when msn signs on"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ericxhall on 2008-04-25
I know this is a common problem there are threads all over the place and I know this was a problem in Dapper(?) or Edgy(?). I have been given the fix of

uset G_DEBUG
pidgin

but then I have to keep terminal open ALL the time...
there has to be a better way.
and do we know about any built in support for new ipods?

---

### Post by Mazza558 on 2008-04-25
-Right-click on the Ubuntu menu and click "edit menus".

-Click on the Internet option on the left and right-click on Pidgin

-Choose "Properties", and where it says "command", put this in instead:

> uset G_DEBUG && pidgin

Does this work? What is Uset anyway? If it's a program, this should work.

---

### Post by ericxhall on 2008-04-25
OOPS! I MEANT UNSET! hahaha

---

### Post by Mazza558 on 2008-04-25
> **ericxhall said:**
> OOPS! I MEANT UNSET! hahaha

Okay, then use unset then ;)

Oh, and if you only use MSN, you might want to try "emesene" - it has better support for the MSN protocol.

---

### Post by ericxhall on 2008-04-25
but i obviously know what you meant, and it worked, RAD!

---

