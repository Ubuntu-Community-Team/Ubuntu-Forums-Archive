---
title: "1 not fully installed or removed"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by markbusu on 2008-06-02
Hi guys,

My Apt-get is screwed :(...  Every time I perform an installation, i get the following error message:

1 not fully installed or removed

Is there any way to clean apt get and ask for it to re install the application at start.. (AKA Config Files etc)

Thanks!

---

### Post by shifty_powers on 2008-06-02
so what is the exact output from something like

```
sudo apt-get update
```?

---

### Post by anjilslaire on 2008-06-02
also try
```

sudo apt-get autoremove
sudo apt-get -f update 

```

---

### Post by markbusu on 2008-06-03
Thank you for your comments... will try and get back later.

Mark

---

