---
title: "Keyboard shortcut to a file?"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-09-01
I am having no luck doing this I used as the command   to the file. ex  ```
 /home/me/file.txt
```   but no luck

---

### Post by whitesmith on 2013-09-01
Your post is confusing. If you want to bring up the file in an editor upon a keypress, then just write a short script:
```
#!/bin/bash
gedit /home/me/file.txt
```
Make the script executable and then assign a keyboard shortcut to it. This what you wanted?

---

### Post by cmcanulty on 2013-09-01
No I just want to open it in gedit with a keyboard shortcut. I refer to it a lot.

---

### Post by whitesmith on 2013-09-01
The method I described does what you want.

---

### Post by cmcanulty on 2013-09-02
OK thanks I didn't understand at first now it works

---

