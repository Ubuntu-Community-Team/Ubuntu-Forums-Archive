---
title: "Update Errors and exits"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-06-24
Trying to upgrade an old laptop - tried with a flash drive but that failed so I thought I'd try an update - got this. Any thoughts?

```
apport start/running
    sys.exit(main())
  File "/tmp/update-manager-DMmiDy/DistUpgradeMain.py", line 202, in main
    if app.run():
  File "/tmp/update-manager-DMmiDy/DistUpgradeController.py", line 1642, in run
    return self.fullUpgrade()
  File "/tmp/update-manager-DMmiDy/DistUpgradeController.py", line 1612, in fullUpgrade
    if not self.doDistUpgrade():
  File "/tmp/update-manager-DMmiDy/DistUpgradeController.py", line 1006, in doDistUpgrade
    self._maybe_create_apt_btrfs_snapshot()
  File "/tmp/update-manager-DMmiDy/DistUpgradeController.py", line 990, in _maybe_create_apt_btrfs_snapshot
    res = apt_btrfs.create_btrfs_root_snapshot(prefix)
  File "/tmp/update-manager-DMmiDy/apt_btrfs_snapshot.py", line 122, in create_btrfs_root_snapshot
    os.path.join(mp, self.SNAP_PREFIX+additional_prefix+snap_id))
  File "/tmp/update-manager-DMmiDy/apt_btrfs_snapshot.py", line 69, in btrfs_subvolume_snapshot
    source, dest])
  File "/usr/lib/python2.7/subprocess.py", line 486, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.7/subprocess.py", line 672, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1213, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

---

### Post by cariboo on 2011-06-24
What command did you use to update?

---

### Post by Peter09 on 2011-06-24
> What command did you use to update?

```
update-manager -d
```

---

### Post by icek on 2011-06-24
I just got the same error...
edit: Ok, I'm on oneiric :-). Solved it by upgrading with synaptic...

---

