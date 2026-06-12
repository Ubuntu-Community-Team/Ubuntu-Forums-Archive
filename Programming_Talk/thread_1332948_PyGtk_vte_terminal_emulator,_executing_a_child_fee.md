---
title: "PyGtk vte terminal emulator, executing a child_feed"
date: 2009-11-20
forum: Programming Talk
---

### Post by exutable on 2009-11-20
So I an app that uses python-vte, Virtual Terminal Emulator.  Everything works fine until I want to telnet and execute a command.  I can easily telnet, and I can easily feed the telnet a command.  For example "help".  I just can't execute it.  I read through all the documentation and there is no function for executing the child feed.


Do I need to somehow start a new fork?

Here is a simple example:
```

terminal = vte.Terminal()
terminal.fork_command("telnet localhost 4444")
terminal.feed_child("help")

```

I get telnet with "help" entered, if I press enter with the keyboard it comes up but I can't get it to happen automatically.



Thanks,

Dane

---

### Post by exutable on 2009-11-21
bump?

---

### Post by exutable on 2009-11-21
Turns out that all commands MUST have a \n after them if they are to be executed.  Very important.  Everything works as planned now without forking anything :)

---

### Post by 10101011 on 2010-09-22
Thanks for posting the solution. It helped me with my problem.

---

