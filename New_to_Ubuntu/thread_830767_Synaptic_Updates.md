---
title: "Synaptic Updates"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by bern1939 on 2008-06-16
As my Synaptic GUI does not work what is the line command to do a package update please?


Thanks


Bern

---

### Post by EmperorMoo on 2008-06-16
```


sudo apt-get update


```

---

### Post by philinux on 2008-06-16
sudo apt-get update && sudo apt-get upgrade

This will do the job like the update manager.

Why is your gui not working, any error messages.

---

### Post by Bradtek on 2008-06-16
```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by kpkeerthi on 2008-06-16
**Edit: Beaten! I was slow.**

You need to run these one after the other to get the updates.
```

sudo apt-get update
sudo apt-get upgrade

```
Or, in one line
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bern1939 on 2008-06-16
Thanks indeed..... the GUI and the Update Mgr. refuse to load up....why? I have no idea but will do with the commands for now thanks


Bern

---

### Post by Nepherte on 2008-06-16
Does it say anything if you type this in a terminal?
```
gksudo synaptic
```

---

