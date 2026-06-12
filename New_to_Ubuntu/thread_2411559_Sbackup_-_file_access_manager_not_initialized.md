---
title: "Sbackup - file access manager not initialized"
date: 2019-01-31
forum: New to Ubuntu
---

### Post by matuskm on 2019-01-31
Hi,

I have a problem with Simple backup suite.

```
DEBUG: pgrep x-session-manager = 
DEBUG: pgrep gnome-session = 3612
DEBUG: pgrep gnome-session = 3612
Desktop session gnome-session found
Updating SSH_AUTH_SOCK to: /run/user/1000/keyring-mFUtVs/ssh
DEBUG: pgrep x-session-manager = 
DEBUG: pgrep gnome-session = 3612
DEBUG: pgrep gnome-session = 3612
Desktop session gnome-session found
Updating GNOME_KEYRING_CONTROL to: /run/user/1000/keyring-mFUtVs
DEBUG: pgrep x-session-manager = 
DEBUG: pgrep gnome-session = 3612
DEBUG: pgrep gnome-session = 3612
Desktop session gnome-session found
Updating GNOME_KEYRING_PID to: 3412
DEBUG: pgrep x-session-manager = 
DEBUG: pgrep gnome-session = 3612
DEBUG: pgrep gnome-session = 3612
Desktop session gnome-session found
Updating GPG_AGENT_INFO to: /run/user/1000/keyring-mFUtVs/gpg:0:1
D-Bus session bus launched
    DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-kBiUtLIxYN,guid=522464cecbf6664ca29b2ed95c5330cd
    DBUS_SESSION_BUS_PID=7178
Attempt to launch indicator application (status icon).
DEBUG: pgrep x-session-manager = 
DEBUG: pgrep gnome-session = 3612
DEBUG: pgrep gnome-session = 3612
Desktop session gnome-session found
Indicator application started (PID: 7182)
Indicator application was started as superuser (EUID=0).
Now dropping privileges (to user 'serverkm').
drop privileges: running as serverkm/serverkm
Another `Simple Backup Indicator` is already running.
Group not changed to `admin`: unknown group
2019-01-31 18:30:56,097 - INFO: Log output for [Default Profile] is directed to file '/var/log/sbackup/sbackup.2019-01-31_18.30.56.096215.log'.
2019-01-31 18:30:56,097 - INFO: Profile settings are being read from file '/etc/sbackup.conf'.
2019-01-31 18:30:56,101 - INFO: Preparation of backup process
2019-01-31 18:30:56,101 - INFO: Initializing GIO File Access Manager.
2019-01-31 18:30:56,113 - ERROR: No such interface 'org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker
2019-01-31 18:30:56,114 - ERROR: Uncaught exception: Unable to mount: No such interface 'org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker
2019-01-31 18:30:56,114 - ERROR: Traceback (most recent call last):
  File "/usr/share/sbackup/sbackup/fs_backend/_gio_utils.py", line 371, in _mount_done_cb
    self.__mount_finish_callback(error)
  File "/usr/share/sbackup/sbackup/fs_backend/_gio_fam.py", line 157, in _mount_cb
    raise exceptions.FileAccessException("Unable to mount: %s" % error)
FileAccessException: Unable to mount: No such interface 'org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker

2019-01-31 18:30:56,114 - ERROR: An error occurred during the backup: File access manager not initialized
2019-01-31 18:30:56,118 - WARNING: Unable to copy log. File access is not initialized.
2019-01-31 18:30:56,119 - INFO: Terminating GIO File Access Manager.
2019-01-31 18:30:56,119 - WARNING: GIO File Access Manager is not initialized. Nothing to do.
2019-01-31 18:30:56,119 - INFO: Processing of profile failed with error: File access manager not initialized


```

This problem with use remote backup dhh (NAS).

---

