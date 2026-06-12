---
title: "Changing keymaps in Xfce, X, GDM, the console, GRUB"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by jrothwell97 on 2008-08-23
Hi all,

I've been trying to get Ubuntu to use the British Dvorak Simplified Keyboard system-wide. I've found that it's possible to switch in Xfce using 

```
setxkbmap gb dvorak
```

but as soon as the session ends, this setting is lost.

As I see it, there are four things that need reconfiguring:

[LIST]
[*]The X keymap (for the desktop environments - I have GNOME and Xfce installed)
[*]The console keymap
[*]The GRUB keymap
[*]GDM's configuration - it needs to inherit the X settings
[/LIST]

These all need to be configured on booting the system - can anyone make any suggestions for these? I'm probably overlooking something blindingly obvious...

---

