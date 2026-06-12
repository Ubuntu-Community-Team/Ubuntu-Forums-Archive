---
title: "Cannot search on google - assertion fails????"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by the_fury on 2008-10-29
I'm getting a message that reads "assertion failed". Here is the accompanying error message:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:doSearch(proteins,current)
10:handleSearchCommand([object KeyboardEvent])
11:onTextEntered()
12:handleEnter(false)
13:onKeyPress([object KeyboardEvent])
14:onxblkeypress([object KeyboardEvent])

Can anyone decipher this and tell me what the problem is? Thanks.

---

### Post by jpeddicord on 2008-10-29
That's weird. What browser are you using, and would you be able to get a screenshot? I can't see that coming from Firefox.

And as always, restarting usually helps. :)

---

