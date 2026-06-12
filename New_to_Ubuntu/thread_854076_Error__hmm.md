---
title: "Error ? hmm"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by bjarnii on 2008-07-09
Hello :) I am new with linux (installed it yesterday) and I have got an error :/, something like "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." When I am going inside the synaptic package manager. Please help :) thanks

---

### Post by nikgare on 2008-07-09
You need to do what the error says and run this command in a terminal:

```
dpkg --configure -a
```

---

### Post by sayakb on 2008-07-09
At a terminal, do:
```
sudo dpkg --configure -a
```

---

### Post by bjarnii on 2008-07-09
Well like I say I just started yesterday .. how can i open this terminal ? :) thanks

---

### Post by sayakb on 2008-07-09
Application->Accessories->Terminal

---

### Post by bjarnii on 2008-07-09
um lol now there came something "You have 1 broken package on your system!

Use the "Broken" filter to locate it."

---

### Post by sayakb on 2008-07-09
```
sudo apt-get install -f
```

If it generates any error messages, copy them and post them here..

---

### Post by bjarnii on 2008-07-09
sweet

---

### Post by sayakb on 2008-07-09
Did it work?

---

### Post by bjarnii on 2008-07-09
Sure did :) thanks for the help mates

---

