---
title: "update manager, add/remove &amp; synaptic package manager  problems"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Spinx on 2008-05-31
update manager, Synaptic package manager and ubuntu add/remove applications are no longer working. I am running Ubuntu 8.04, 64 bit with a dual boot to vista. Running on a HP Pavillion DV6645US

Update manager and Add/remove will load. If I take the install option it gets busy (???runs) but nothing really happens. I have had to use "force quit" to stop them. With synaptic package manager it starts loading then disappears.

Can anyone tell me whats wrong and how to fix it.

---

### Post by shifty_powers on 2008-05-31
what happens when you type

```
sudo apt-get update
```

into a terminal?

---

### Post by Spinx on 2008-05-31
read package lists and done. I still have the update icon on the panel and it still does not work

---

### Post by Sef on 2008-05-31
Run this code: ```
sudo apt-get update && sudo apt-get upgrade
```

Report any errors.

---

