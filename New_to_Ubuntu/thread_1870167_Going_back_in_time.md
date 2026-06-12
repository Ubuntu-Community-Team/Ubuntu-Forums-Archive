---
title: "Going back in time"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by jsf_pp on 2011-10-26
let's say i did sth wrong and i want to move back in time in terminal. is there a way to do that?

i want to install this:

sudo add-apt-repository ppa:tiheum/equinox
sudo apt-get update
sudo apt-get install gtk2-engines-equinox faenza-icon-theme equinox-theme

but i'm not that sure i'll like afterwards so i want to know if i'll be able to discard it in case i dont dig it enough. 

thanks

---

### Post by wolfen69 on 2011-10-26
Sure, just do:
```
sudo apt-get remove --purge package_name
```

---

### Post by nick_goodfate on 2011-10-26
You can also remove the ppa:tiheum/equinox(if it isn't the source of any other package) from your "software sources" in order to keep your sources list clean from unused ppas.

---

