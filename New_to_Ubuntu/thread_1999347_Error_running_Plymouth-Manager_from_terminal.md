---
title: "Error running Plymouth-Manager from terminal"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-07
Hi all

I installed plymouth manager and ran the program. I changed a bunch of things, and restarted the machine. Nothing changed.
So I thought "Thats Odd" and decided to try running plymouth-manager from terminal. I did so and on the first screen, changed the screen res  to 1920*1080, which is my current screen res.
The terminal output of this is:
```

glenn@design:~$ sudo plymouth-manager
[sudo] password for glenn: 
Traceback (most recent call last):
  File "/usr/share/plymouth-manager/src/main.py", line 35, in on_btnChangeRes_clicked
    funcmain.ChangeRes(self.cmbResolution.get_active_text())
  File "/usr/share/plymouth-manager/src/funcmain.py", line 45, in ChangeRes
    shutil.copyfile("/etc/default/" + bl, "/home/" + getpass.getuser() + "/." + bl + ".backup")
  File "/usr/lib/python2.7/shutil.py", line 83, in copyfile
    with open(dst, 'wb') as fdst:
IOError: [Errno 2] No such file or directory: '/home/root/.grub.backup'

```
And when I Control+C to exit, I get:
```

^Cg_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
/usr/bin/plymouth-manager: line 3:  9034 Terminated              python plymouth-manager.py
glenn@design:~$ 

```
Can anyone make sense of this?

---

### Post by Senior_Buckethead on 2012-06-11
Bump

---

### Post by Senior_Buckethead on 2012-06-13
Bump again

---

### Post by Senior_Buckethead on 2012-06-15
Bump Yet Again

---

