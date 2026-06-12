---
title: "[SOLVED] Trash can shows files while Trash file shows empty."
date: 2008-06-10
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-10
My trashcan shows that there are files to be deleted.  I tried deleting them and it did nothing.  I then went to ~/.local/share/Trash/files and did a ls -la and it showed no files.  I tried sudo rm -r * and it did nothing.
How do I get my trashcan to show empty?

---

### Post by bubba_169 on 2008-06-10
Are there any hidden files in there?

---

### Post by alienexplorers on 2008-06-10
Not that I know of.

---

### Post by goodfella on 2008-06-10
I had a similar problem.  I had files in my trash folder that should not be in there.  Like for example my entire home directory.  I was pointed to this bug report that solved the problem for me:
[https://bugs.launchpad.net/ubuntu/+bug/120884]("https://bugs.launchpad.net/ubuntu/+bug/120884")

The description in the bug report does not match yours exactly; however, I think it applies and is worth a shot.

---

