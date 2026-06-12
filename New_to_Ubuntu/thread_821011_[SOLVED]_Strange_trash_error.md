---
title: "[SOLVED] Strange trash error"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-06-06
When I attempt to empty my trash..It refuses to empty the contents..Any ideas why?  There isnt an error message, just refuses to empty the contents

---

### Post by drs305 on 2008-06-06
Is this a recurring occurrence? You might try opening nautilus, even with gksudo nautilus, to try to empty the files. In hardy, user files are in ~/.local/share/Trash/files  Perhaps some trash owned by root ended up in your user's trash bin.

---

### Post by sports fan Matt on 2008-06-06
it just started earlier today, and I was away from the pc and now I cant empty the trash..(just restarted my pc before this occured on a patched system..

---

### Post by iaculallad on 2008-06-06
Using your (Hardy) terminal:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

would do the trick.

---

### Post by sports fan Matt on 2008-06-06
there wasnt anything in that folder..even with doing a ctrl H

---

### Post by sports fan Matt on 2008-06-06
that folder is empty, however the "trash" icon still shows 2 items in the trash...

---

### Post by drs305 on 2008-06-06
```
sudo find / -iname Trash
```
will find all the Trash entries on your system. I generally don't combine searches of this kind with rm and use nautilus to investigate (at least that's my forum advice).

---

### Post by sports fan Matt on 2008-06-06
Ah ha That did it!:)

---

