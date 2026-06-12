---
title: "How to uninstall Lamp"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by Tjkhan on 2013-06-14
I installed Lamp 
```

sudo apt-get install lamp-server^
```

Now I want to uninstall that. What I have to do? 

Thank you.

---

### Post by coldraven on 2013-06-14
Try this
```
sudo apt-get purge lamp-server^
```

You can see all the options with
```
man apt-get
```

Or install Synaptic and search for "lamp-server". I like using Synaptic because it shows me lots of information. Like right click on an installed program select properties and then click on the "Installed files" tab sometimes shows that an interesting document is also installed somewhere obscure.

---

### Post by Tjkhan on 2013-06-14
Thanks dude :)

---

### Post by Mopar1973Man on 2013-06-14
Then to clean up the extra modules check out the "sudo apt-get autoremove" function in the man pages.

[http://ss64.com/bash/apt-get.html](http://ss64.com/bash/apt-get.html)
**autoremove**
autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.

---

