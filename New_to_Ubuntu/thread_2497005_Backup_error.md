---
title: "Backup error"
date: 2024-04-19
forum: New to Ubuntu
---

### Post by apgp on 2024-04-19
When backup finises it gives this error message:
Fallo con un error desconocido
Traceback (innermost last):
  File "/usr/bin/duplicity", line 92, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 75, in with_tempdir
    fn()
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1568, in main
    do_backup(action)
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1651, in do_backup
    restore(col_stats)
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 736, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 788, in restore_get_patched_rop_iter
    file_names.append(backup_set.volume_name_dict[vol_num])
 KeyError: 2

Can it prevent restoring the copy? How I can solve that? Thank you

---

### Post by TheFu on 2024-04-20
I don't use duplicity. There are a number of reasons for that non-choice, but mainly because monthly "FULL" backups are still mandatory which most people seem to miss in their backup routine.

So, my first question is are you doing monthly full backups as required by all duplicity/deja dup/duplicati tools?

---

### Post by apgp on 2024-04-20
I make a full backup every week.

---

### Post by apgp on 2024-04-20
I am using the Ubuntu 22.04 backup app.

---

