---
title: "deja-dup, fail with decoding error"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-11-29
Tried to use deja-dup for backup, but it give the following error. Is there a way to find the filenames that is causing this error?
```

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1404, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1397, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1277, in main
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 691, in set_values
    self.get_backup_chains(partials + backend_filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 814, in get_backup_chains
    map(add_to_sets, filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 808, in add_to_sets
    log.Debug(_("File %s is not part of a known set; creating new set") % (filename,))
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 3: ordinal not in range(128)

```

---

