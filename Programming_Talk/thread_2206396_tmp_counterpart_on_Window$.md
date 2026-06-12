---
title: "/tmp counterpart on Window$?"
date: 2014-02-18
forum: Programming Talk
---

### Post by kangaba on 2014-02-18
Hi,
On Linux the files in /tmp are usually cleaned up between reboots, and from /var/tmp aren't.
On Windows %T(E)MP% points to a folder which acts like /var/tmp, but I need one which acts like /tmp (cleaned up after reboot), is there such one?

[After googling, this]("http://stackoverflow.com/questions/15111103/tmp-folder-in-windows-like-tmp-in-linux") seems to indicate there's no such folder in Windows.

---

### Post by CharlesA on 2014-02-18
No such folder exists on Windows, but you could probably write a script to empty the temp folder if you really wanted to.

---

### Post by kangaba on 2014-02-18
Thanks, I won't do a script because by using a /tmp style folder I'm trying to work around a bug in Qt5, and I don't wanna work around a workaround.
I guess I'll have to look for another solution.

---

