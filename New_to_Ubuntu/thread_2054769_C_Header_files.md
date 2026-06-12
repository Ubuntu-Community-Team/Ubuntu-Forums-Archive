---
title: "C Header files"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by mpsingh0029 on 2012-09-08
I am not able to add new C header files (No write permission) in /usr/include. Any idea how to resolve this????

---

### Post by idoitprone on 2012-09-08
> **mpsingh0029 said:**
> I am not able to add new C header files (No write permission) in /usr/include. Any idea how to resolve this????

open the text editor with gksudo to gnome or kdesu for kde

or use sudo

/usr/include should be own by root, so you must be root or like it to add a new file

---

### Post by spjackson on 2012-09-08
> **mpsingh0029 said:**
> I am not able to add new C header files (No write permission) in /usr/include. Any idea how to resolve this????
Why are you wanting to do this? If these headers are for a library you are wanting to use, you should check whether it's in the repository, and if so, add it using one of the installation tools such as synaptic.

If the headers are for something else (such as your own programs), you probably don't need to put them in /usr/include.

---

