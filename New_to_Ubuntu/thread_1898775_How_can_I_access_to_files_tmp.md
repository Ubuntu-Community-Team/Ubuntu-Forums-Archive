---
title: "How can I access to files tmp"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2011-12-22
Hi, I'd like to copy a video from files tmp while executing it from Internet, but I don't know how  I can have access to tmp. Can anyone tell me how I can do it?
thanks

---

### Post by MG&amp;TL on 2011-12-22
First...why is the vid in /tmp? Second:


1. Press Alt-F2

2. Enter into the box, very carefully, 

```
gksu nautilus
```

3. Press the "up one directory" button until you can't go any further, or press the "filesystem" button at the side. You should end up in a directory with things like /var, /usr, /home, and (!) /tmp

4. Double click on "tmp"

5. Now to find your vid.

Screenshots attached (although I'm using a different file manager)

Warning, while using nautilus (file browser) as root (the 'gksu' bit), you can destroy, change, and corrupt stuff you wouldn't normally have access to. Therefore, be very careful. /tmp should be OK though.

---

