---
title: "Login Window Doesn't Show - &quot;input not supported&quot;"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-22
Thankfully i "auto-login", but if i need to log-out etc for any reason all i get is an "input not supported" dialog on a black screen.

I still whack my login info in anyway and hit return, but it'd be nice to be able to see the login screen.

is there any obvious reason why this is?

---

### Post by Xiong Chiamiov on 2008-10-26
X is trying to use a screen resolution / refresh rates / vertical sync / etc. that your monitor doesn't accept.  Fortunately, something in your GUI changes the settings when you login, apparently.  If you decide to go whacking about with your Xorg.conf, make sure to keep a backup of what you have to go back to if need be.

---

