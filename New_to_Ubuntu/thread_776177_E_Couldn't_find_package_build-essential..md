---
title: "E: Couldn't find package build-essential."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by iforgot123456 on 2008-04-30
Hi all,

I've just put Hardy Heron on my old laptop and I'm trying to install drivers for my wireless card (Acer travelmate 2300 (IPN2220 wireless card.))

When I run the command
```

sudo apt-get install build-essential
```

I get the message

```
E: Couldn't find package build-essential.
```

Any help with where to find the build essentials package much appreciated (PS the installation disc is in the drive.)

---

### Post by Shazaam on 2008-04-30
Does the laptop have internet access? Do you have the cdrom enabled in Software Sources (repositories)?

---

### Post by decius6i5 on 2008-12-21
You have to run "apt-get update" first.

---

