---
title: "Error back up"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by dailammoc on 2013-03-24
Hi guys!
I'm using Ubuntu 12.04 LTS, when I back up my files I got the errors:
Failed with unknown error:
```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1411, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1404, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1284, in main
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 691, in set_values
    self.get_backup_chains(partials + backend_filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 814, in get_backup_chains
    map(add_to_sets, filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 804, in add_to_sets
    if set.add_filename(filename):
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 97, in add_filename
    (self.volume_name_dict, filename)
AssertionError:  ({1:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol1.difftar.gpg',  2:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol2.difftar.gpg',  3:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol3.difftar.gpg',  4:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol4.difftar.gpg',  5:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol5.difftar.gpg',  10:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol10.difftar.gpg',  11:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol11.difftar.gpg',  12:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol12.difftar.gpg',  13:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol13.difftar.gpg',  14:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol14.difftar.gpg',  15:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol15.difftar.gpg',  16:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol16.difftar.gpg',  17:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol17.difftar.gpg',  18:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol18.difftar.gpg',  19:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol19.difftar.gpg',  20:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol20.difftar.gpg',  21:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol21.difftar.gpg',  22:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol22.difftar.gpg',  23:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol23.difftar.gpg',  24:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol24.difftar.gpg',  25:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol25.difftar.gpg',  26:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol26.difftar.gpg',  27:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol27.difftar.gpg',  28:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol28.difftar.gpg',  29:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol29.difftar.gpg',  30:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol30.difftar.gpg',  31:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol31.difftar.gpg',  32:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol32.difftar.gpg',  33:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol33.difftar.gpg',  34:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol34.difftar.gpg',  35:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol35.difftar.gpg',  36:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol36.difftar.gpg',  37:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol37.difftar.gpg',  38:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol38.difftar.gpg',  39:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol39.difftar.gpg',  40:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol40.difftar.gpg',  41:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol41.difftar.gpg',  42:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol42.difftar.gpg',  43:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol43.difftar.gpg',  44:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol44.difftar.gpg',  45:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol45.difftar.gpg',  46:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol46.difftar.gpg',  47:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol47.difftar.gpg',  48:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol48.difftar.gpg',  49:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol49.difftar.gpg',  50:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol50.difftar.gpg',  51:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol51.difftar.gpg',  52:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol52.difftar.gpg',  53:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol53.difftar.gpg',  54:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol54.difftar.gpg',  55:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol55.difftar.gpg',  56:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol56.difftar.gpg',  57:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol57.difftar.gpg',  58:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol58.difftar.gpg',  59:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol59.difftar.gpg',  60:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol60.difftar.gpg',  61:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol61.difftar.gpg',  62:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol62.difftar.gpg',  63:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol63.difftar.gpg',  64:  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol64.difftar'},  u'duplicity-inc.20120512T034211Z.to.20120606T003514Z.vol64.difftar.gpg')
```

Could some one give me solution?

---

### Post by ssam on 2013-08-02
you are not the only one suffereing from this issue
[https://bugs.launchpad.net/deja-dup/+bug/1049002](https://bugs.launchpad.net/deja-dup/+bug/1049002)
you can subscribe to the bug to be notified of any updates

---

