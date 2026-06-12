---
title: "Where is a environment variable defined?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by caonima on 2008-10-24
I need to change the environment variable MATLAB_JAVA. But now I cannot remember in which file this variable is defined. Is there a way to locate the file defines a certain environment variable?

---

### Post by dash86no on 2008-10-24
> **caonima said:**
> I need to change the environment variable MATLAB_JAVA. But now I cannot remember in which file this variable is defined. Is there a way to locate the file defines a certain environment variable?

it's in /etc/environment i think....

---

### Post by dash86no on 2008-10-24
> **caonima said:**
> I need to change the environment variable MATLAB_JAVA. But now I cannot remember in which file this variable is defined. Is there a way to locate the file defines a certain environment variable?

how about sudo grep -r MATLAB_JAVA /*

?

---

### Post by caonima on 2008-10-24
Thanks for the lightening fast reply. I got it. I put it in the starting script of MATLAB.

---

