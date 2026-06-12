---
title: "assign define ctrl-alt keys lubuntu shortcut"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-03-22
Hi Guys

Hoping someone can help me assign my favourite shortcut keys via ctrl-alt or whatever works.

Before I ditched the expensive bloatware legacy operating system I could open my favourite documents or programs from anywhere on the system by going
ctrl-alt-[whatever letter I assign]

I could do it from the desktop under properties in the old unnamed legacy OS.

---

### Post by SteveDee on 2012-03-23
> **Kevin McCready said:**
> ...Hoping someone can help me assign my favourite shortcut keys via ctrl-alt or whatever works....

Take a look at: /home/{user}/.config/openbox/lubuntu-rc.xml

You can assign short-cuts to applications by adding sections in this format:-
```

<keybind key="C-A-T"><action name="Execute">
<command>lxterminal</command></action></keybind>

```

---

### Post by mikaere66 on 2012-04-19
> **SteveDee said:**
> Take a look at: /home/{user}/.config/openbox/lubuntu-rc.xml

You can assign short-cuts to applications by adding sections in this format:-
```

<keybind key="C-A-T"><action name="Execute">
<command>lxterminal</command></action></keybind>

```

Thank you so much ...
I've been trying to do this for ages!

---

### Post by decktrio on 2012-04-23
> **Kevin McCready said:**
> Hi Guys

Hoping someone can help me assign my favourite shortcut keys via ctrl-alt or whatever works.

Before I ditched the expensive bloatware legacy operating system I could open my favourite documents or programs from anywhere on the system by going
ctrl-alt-[whatever letter I assign]

I could do it from the desktop under properties in the old unnamed legacy OS.

In case you ever want to create some more complex shortcuts, and you can't figure out how to do it... you should check out [xbindkeys]("https://help.ubuntu.com/community/KeyboardShortcuts#Text_Entry_Shortcuts").

---

