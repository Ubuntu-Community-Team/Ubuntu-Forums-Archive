---
title: "Crazy Firefox Errors!!!"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by stropyboy11 on 2008-06-14
My Firefox Beta 3 is not working. It just suddenly died. First off, whenever I try to type anything in the address bar, I get confronted with this:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([www.myspace.com](www.myspace.com))
7:getEngineByAlias([www.myspace.com](www.myspace.com))
8:getShortcutOrURI([www.myspace.com](www.myspace.com),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])

Also, my bookmarks, history, and settings are not working. Any ideas?

---

### Post by Bubba64 on 2008-06-14
There was a thread on this just yesterday I believe, hopefully you can find it or somebody will post the answer I will look for the thread.

---

### Post by Tomatz on 2008-06-14
Try reinstalling it via synaptic first. You won't loose your bookmarks, extensions etc.

---

### Post by alienexplorers on 2008-06-14
Haven't you updated to firefox RC2.  It is the current version in synaptic repositories.

---

### Post by stropyboy11 on 2008-06-14
Wait RC2? What is that? I searched for Firefox RC2 in synaptic, nothing came up...

Oh, and I'm completely fine with losing my bookmarks, etc...I pretty much got Ubuntu about a week ago (hard drive failure and had to get a new one, now THAT was a pain), so everything is easily replacable

---

