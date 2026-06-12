---
title: "how to detect from ubuntu if my pc support virtualization technology?"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by edsh on 2012-08-08
HI!
I am beginner in Ubuntu, I want how to detect from ubuntu if my pc support virtualization technology?
I am waiting for your respose,
Regards Edsh

---

### Post by Cheesemill on 2012-08-09
Look at the output of:
```
cat /proc/cpuinfo
```

You are looking for either the **vmx** or **svm** flag being present (depending on whether your CPU is Intel or AMD).
You also have to make sure that the appropriate feature is turned on in your computers BIOS.

Another way is to just Google the make and model of your processor, the full specs will be in the first couple of results.

---

