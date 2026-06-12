---
title: "Deja Dup - Restore failed with an unknown error"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by charliewarlie on 2014-03-03
I did a clean install of Ubuntu 13.10 (having backed up everything with Deja Dup), but when I try and restore from my backup, I get this error:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1414, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1407, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1341, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 635, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 526, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 499, in integrate_patch_iters
    final_ropath = patch_seq2ropath( normalize_ps( patch_seq ) )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 479, in patch_seq2ropath
    misc.copyfileobj( current_file, tempfp )
  File "/usr/lib/python2.7/dist-packages/duplicity/misc.py", line 166, in copyfileobj
    buf = infp.read(blocksize)
  File "/usr/lib/python2.7/dist-packages/duplicity/librsync.py", line 80, in read
    self._add_to_outbuf_once()
  File "/usr/lib/python2.7/dist-packages/duplicity/librsync.py", line 94, in _add_to_outbuf_once
    raise librsyncError(str(e))
librsyncError: librsync error 103 while in patch cycle


Does anyone have any idea what this means and how I can fix it? I have about 6 months worth of weekly backups with all my work and files which I really don't want to lose!

---

### Post by phidia on 2014-03-03
There's an [older thread here]("http://ubuntuforums.org/showthread.php?t=1975831") which refers to a patch for ignoring broken files.
Maybe that will help or lead you to more reading. There are a lot of hits when using that last line of output as search.
Good luck.

---

### Post by charliewarlie on 2014-03-04
Thank you, that did help - this was fixed in duplicity 0.6.23 release,  so I just installed that and now I have all my files back. :)

---

