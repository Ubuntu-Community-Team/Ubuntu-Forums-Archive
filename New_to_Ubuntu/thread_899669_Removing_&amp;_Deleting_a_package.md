---
title: "Removing &amp; Deleting a package"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-24
I have installed a package from the add/remove programs. Now suppose if i want to remove the program along with deleting all the packages that may have been installed in the /var/cache/apt/archives due to this program.

In other words i want to delete this program from my computer completely.

---

### Post by Kizlum on 2008-08-24
Hum, sudo apt-get remove --purge yourprogram ?

---

### Post by david sousa on 2008-08-24
Go to Synaptic packages manager at system -> preferences.

Then search for you program and mark it for complete removing.

;)

---

### Post by billgoldberg on 2008-08-24
sudo apt-get autoremove applicationname --purge

is what I usually use.

You could use synaptic and it's "completely remove package" option to do so, if you prefer an GUI instead of CLI.

---

### Post by wolfen69 on 2008-08-24
i always do (after uninstalling) ```
sudo apt-get clean
``` and ```
sudo apt-get autoremove
``` that's all you need.

---

