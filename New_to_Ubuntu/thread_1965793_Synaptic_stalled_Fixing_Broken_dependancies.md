---
title: "Synaptic stalled Fixing Broken dependancies"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-04-26
Synaptic - Fixing Broken dependancies 
process stalled at libc6-dev.

Message: "An error occurred. Could not perform immediate configuration on already unpacked 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details"

Unable to understand the man 5 apt.conf info.

Need specific details on how to remedy this asap.

---

### Post by matt_symes on 2012-04-26
Hi

Try switching off immediate configure and fixing the install.

```
sudo apt-get -o APT::Immediate-Configure=0 -f install
```

and then type

```
sudo apt-get update
```

Finally 

```
^date^grade
```

You can copy and paste the commands into the terminal one after another to save typing errors.

Kind regards

---

### Post by Bumpalot on 2012-04-26
Magnificent!! Thanks so much for your help - mucho appreciated!!

---

