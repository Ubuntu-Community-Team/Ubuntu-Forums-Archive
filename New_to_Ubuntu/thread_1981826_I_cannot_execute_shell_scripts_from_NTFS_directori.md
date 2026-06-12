---
title: "I cannot execute shell scripts from NTFS directories"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by haraldwong on 2012-05-17
I have recently upgraded from Ubuntu 10 to 12. I have lost the ability to run a bash script on my NTFS USB memory stick, from Thunar and Nautilus file managers. The Thunar "Help" link indicates that "application/x-desktop,         application/x-executable and application/x-shellscript" can be executed but does not tell me where to find more information on this.

I do not have this issue on a Unix filesystem.

Nautilus Note: Properties->Permissions has a "Allow executing file as program" check box that reverts to unchecked immediately.

Thanks,
Harald

PS. Unix I know. Desktop, not so much!

---

### Post by CharlesA on 2012-05-17
NTFS does not support linux permissions.

The permissions at set at mount and if I remember right, do not include the execute permission.

Put the shell script on a Linux partition and run it from there.

---

### Post by Vereinfachen on 2012-05-17
You can still execute bash scripts by going to the directory in a terminal and running
```
bash filename
```
to run *filename*. You don't need execute permissions for that and it will work on a NTFS file system.

---

