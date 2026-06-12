---
title: "[SOLVED] New Ubuntu install, but FF3.0 won't launch from launch on panel."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-06-24
Well, yesterday I wiped out my previous 8.04 and re-installed it. After all the updates I should have firefox 3.0 but for some weird reason firefox fails to start from the launcher in the panel, and from "firefox" in the terminal.
Right now only "sudo firefox" in the terminal launches FF3.0.
Does anyone know how to fix it?

Only mods to my system are:
mysql db for amarok
new opera browser (manual install)
medibuntu
pulse-audio fix (including Flash-player10)

---

### Post by ibuclaw on 2008-06-24
Could be a permissions issue in your own directory.

Try
```
sudo chown $USER:$USER ~/.mozilla -R
```

Regards
Iain

---

### Post by marcelo danico on 2008-06-24
That solved it. Thanks a million! :)

---

