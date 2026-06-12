---
title: "Install of 12.04 Requires PAE on CPU"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by aussieuntu on 2012-07-01
Hi, I am trying to install Ubuntu12.04. The install starts but comes to the message shown in the attachment. The message says that the PAE is required on the processor. My computer is relatively new and the processor is an Intel i5-2350. The manual for the processor says it has PAE. I used a utility that scans the computer hardware and its report said that PAE was present.
Does the Ubuntu 12.04 distro have a bug - does it fail to recognise the PAE?
Any help would be apprieciated.

---

### Post by synapsys on 2012-07-01
From your screenshot I can see you're installing in virtualbox. You need to enable pae in virtualbox. In the VM's settings, go to system -> processor -> enable pae.

---

### Post by aussieuntu on 2012-07-01
Thanks so much for the speedy reply - I made the change in Virtualbox settings and it worked immediately.  Thanks

---

