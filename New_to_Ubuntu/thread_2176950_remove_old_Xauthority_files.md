---
title: "remove old Xauthority files"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-09-26
i have a lot of old .Xauthority files in my home folder. what would be the correct rm command to remove them all at once. tks

---

### Post by rburkartjo on 2013-09-26
here is the correct command just figured it out
sudo rm -rf .Xauthority*

---

### Post by DuckHook on 2013-09-26
...uhmmm... should not need *sudo* and best not to use it where not needed (I know, I'm being a nitpicker, but hey...).

---

### Post by philinux on 2013-09-26
Just delete them from nautilus.

---

