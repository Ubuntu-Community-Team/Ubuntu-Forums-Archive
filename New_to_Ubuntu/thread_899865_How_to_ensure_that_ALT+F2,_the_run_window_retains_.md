---
title: "How to ensure that ALT+F2, the run window retains 100s of previous commands?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by legolas_w on 2008-08-24
Hi there,
Is there any way to configure the run window to retain 100s of previous commands that I execute? currently it does not store more than 10ish commands which is annoying.

thanks

---

### Post by Pro-reason on 2008-08-25
> **legolas_w said:**
> Hi there,
Is there any way to configure the run window to retain 100s of previous commands that I execute? currently it does not store more than 10ish commands which is annoying.

thanks

I no of no easy way to configure that.  You could simply use the Terminal instead.

---

### Post by kellemes on 2008-08-25
Better alternative..
[gmrun]("http://www.bazon.net/mishoo/gmrun.epl")

In ~/.gmrunrc, set your amount of lines to remember like so..
History = 500

---

### Post by legolas_w on 2008-08-25
Is there any way to assign ALT+F2 to this program?
for example when I press ALT+F2 it shows gmrun instead of usual run application.

Thanks

---

### Post by kellemes on 2008-08-25
> **legolas_w said:**
> Is there any way to assign ALT+F2 to this program?
for example when I press ALT+F2 it shows gmrun instead of usual run application.

Thanks

From terminal..
```
gconf-editor
```

Browse to Apps -> Metacity -> keybinding-commands
Now edit "command_1".. set it's value to gmrun

Browse to Apps -> Metacity -> global_keybindings
Now edit "run_command_1".. set it's value to <ALT>F2
And.. edit "panel_run_dialog".. and delete the value.

It should work.

---

