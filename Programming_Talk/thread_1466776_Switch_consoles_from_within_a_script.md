---
title: "Switch consoles from within a script"
date: 2010-04-30
forum: Programming Talk
---

### Post by DBQ on 2010-04-30
Hi, does anybody know how to switch consoles from within a script?

---

### Post by tookyourtime on 2010-04-30
What are you trying to accomplish?

Are you talking about bash scripting?

You can run other scripts from within a script...

Your can also pop open another terminal with
```

gnome-terminal -e /home/testscript

```

where -e is to start it executing a program

---

### Post by nvteighen on 2010-05-01
Are you trying to make a script be able to switch consoles as when you use Alt+F(1...8) (Ctrl+Alt+Fkey while in X Window System)? I think that's hardly accomplishable from a script as consoles are managed by the kernel... and maybe even designed only to work from a certain user input; letting any program be able to switch consoles doesn't sound a sane decision to me. Anyway, if there's any facility in the Linux kernel API for this, you'll have to use C (C++ too?).

---

