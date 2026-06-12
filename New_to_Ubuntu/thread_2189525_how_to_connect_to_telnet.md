---
title: "how to connect to telnet"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by volden11 on 2013-11-22
i'n new to ubuntu and i'm trying to use older dell 3100's to connet to a telnet server that is already in place. we have connected to it on windows but are gonna be switching to ubuntu. telnet is installed on ubuntu. how do i get it opened up and connet to the server like i would if i was in window's?   

was using telnet in windows xp

---

### Post by drmrgd on 2013-11-22
You can pretty much run it the same way you're used to, depending on whether you launched it from a command prompt or had an icon on the desktop to a telnet client.  If the former, the simple method would be to open a terminal window by going to Menu -> Accessories -> LXTerminal (I think you might be able to launch it with Ctrl+T or Ctrl+Alt+T...not positive on that), and then typing the following:

```

telnet <ip.address.of.server>

```

You should then be asked for a username and password and you're all set.

Hope that helps.

---

### Post by DuckHook on 2013-11-23
Completely unrelated to your question on any technical front, but is this telnet server exposed to the whole wide world? Telnet is far and away the most insecure and easily-cracked service in existence. Why not ssh (and even that has to be configured very carefully with keys and without passwords)?

---

