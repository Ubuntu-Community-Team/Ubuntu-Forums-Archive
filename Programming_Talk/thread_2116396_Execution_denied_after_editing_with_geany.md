---
title: "Execution denied after editing with geany"
date: 2013-02-15
forum: Programming Talk
---

### Post by ppparadox on 2013-02-15
Hello,
i recently switched from gedit to geany to edit my bash scripts but an odd thing started to happen: sometimes (not always, i can't seem to reproduce this behaviour consistently) after saving my changes the script file loses its execution bit and i cannot run it until i enable it again.

I looked into the preferences but there's nothing related to this, or so it seems.

Please note that "use_gio_unsafe_file_saving" and "use_atomic_file_saving" are enabled.

---

### Post by kajoky on 2013-12-22
Both of these, use_gio_unsafe_file_saving and use_atomic_file_saving, try to first save a temporary copy of the file and if that is successful, the original file is deleted and the temporary file is renamed.  The permissions on the temporary file may not be the same as the original and that is why you can not execute the script.  Disable both of these and it should fix the execution problem.

---

