---
title: "Remove the leftover icons"
date: 2020-05-06
forum: New to Ubuntu
---

### Post by arvindprasad on 2020-05-06
I have recently upgraded from 19.10 to 20.04. After upgrade I found that I found that the 19.10 Ubuntu Software manager icons has not been removed. How can I do this. Clicking this does not open the software center.

---

### Post by deadflowr on 2020-05-06
Is that on the desktop?
Or somewhere like the Show Applications overview?

---

### Post by Dennis N on 2020-05-06
How do you know it's a leftover? Did you have the snap-store snap package installed? It would now be named "Ubuntu Software" instead of "Snap Store". What does the icon open?

---

### Post by arvindprasad on 2020-05-06
It is a leftover icon as clicking it does nothing. For installing software in Ubuntu 20.04 I have another icon with same picture and Software written below. It opens up the software center. This icon is not in the desktop but in the softwares page, which opens when you click show applications in the left bottom corner of the Unity launcher.

---

### Post by Dennis N on 2020-05-06
> **arvindprasad said:**
> It is a leftover icon as clicking it does nothing. For installing software in Ubuntu 20.04 I have another icon with same picture and Software written below. It opens up the software center. This icon is not in the desktop but in the softwares page, which opens when you click show applications in the left bottom corner of the Unity launcher.
In your terminal, give the command:
```
snap remove snap-store
```
That should make the "Ubuntu Software" go away.

---

### Post by arvindprasad on 2020-05-06
Thanks buddy, its done. How do we declare this thread as solved?

---

### Post by Dennis N on 2020-05-06
> **arvindprasad said:**
> Thanks buddy, its done. How do we declare this thread as solved?
Use the "Thread Tools" just above your post #1.

---

