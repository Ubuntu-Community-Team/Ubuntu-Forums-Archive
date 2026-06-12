---
title: "How can I make an ssh session last forever?"
date: 2018-01-08
forum: New to Ubuntu
---

### Post by shayanthethief on 2018-01-08
I connect to my mining rig from my pc using putty but it (ssh session) terminates after I disconnect. how can I make it last forever?

---

### Post by TheFu on 2018-01-08
Welcome to the forums.

Use screen. Don't know if there is a Windows version, but people with Unix/Linux use it for months at a time.
There's another tool - tmux - if you prefer.

Of course, if the remote system reboots, then the session(s) will be closed.

---

### Post by HermanAB on 2018-01-08
Screen +1

---

### Post by SeijiSensei on 2018-01-09
I've had this issue with Putty.  You need to enable the keepalive functions in the "Connections" settings configuration for your Putty session. The OpenSSH client for *nix seems to handle this issue by default.

---

