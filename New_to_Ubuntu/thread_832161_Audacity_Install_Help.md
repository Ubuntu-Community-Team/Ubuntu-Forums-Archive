---
title: "Audacity Install Help"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-06-17
I installed Audacity through Add/Remove Applications and this error popped up after it installed:
E: acetoneiso2: subprocess post-installation script returned error exit status 1
What is this? Is it a Problem? thanks.

---

### Post by Sarah L on 2008-06-17
Hi,
Try opening up a terminal window and typing:

```
sudo apt-get upgrade
```

and then

```
sudo apt-get update
```

and tell us what you see.

---

### Post by Fingers &amp; Thumbs on 2008-06-17
I've not encountered this problem myself, but what I would recommend trying is using terminal, type:  sudo apt-get update, then when this completes you can either type: sudo apt-get install audacity, or open synaptic and install audacity from there. Let us know the outcome.

---

### Post by redfox1160 on 2008-06-17
Right now, its at 9% after I typed in 
```
sudo apt-get upgrade
```

(80% 3:19)

---

### Post by redfox1160 on 2008-06-17
do you want me to copy everything that popped up when I typed it in? cause a lot popped up...

---

