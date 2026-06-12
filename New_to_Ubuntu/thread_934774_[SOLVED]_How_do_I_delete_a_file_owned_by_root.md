---
title: "[SOLVED] How do I delete a file owned by root?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-30
If I want to delete some files owned by root, how do I do that? Thanks.

---

### Post by cobra741 on 2008-09-30
sudo rm <filename> 

the sudo command executes the command following it as a super user (root)

be careful with it though ... with great power comes great responsibility :)

---

### Post by iaculallad on 2008-09-30
Or you could use:

```
gksudo nautilus
```

and browse the file/folder from that Nautilus window.

---

### Post by bobsmith2 on 2008-10-01
Thanks cobra741 and iaculallad.

---

### Post by rybaxs on 2008-10-01
gksudo nautilus

it really helps me a lot. now i know.. i need to know more about Ubuntu.
it reminds me about my pet nautilus, she dies after 5days when i put her at my aquarium tank. sorry about this nonsense reply. thanks iaculallad!

---

### Post by iaculallad on 2008-10-01
> **rybaxs said:**
> gksudo nautilus

it really helps me a lot. now i know.. i need to know more about Ubuntu.
it reminds me about my pet nautilus, she dies after 5days when i put her at my aquarium tank. sorry about this nonsense reply. thanks iaculallad!

But just be very extra careful when initiating nautilus with gksudo. Remember that you're on 'root-mode' so you have the ability to delete/cut any file/folder you wanted from any Filesystem folder.

---

