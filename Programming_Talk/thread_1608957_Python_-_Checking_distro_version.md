---
title: "Python - Checking distro version"
date: 2010-10-29
forum: Programming Talk
---

### Post by Drakx on 2010-10-29
Hi
I'm trying to get python to check a version of ubuntu using the platform module how ever not 100% sure how to find if the script is running on any thing version of ubuntu less then 10.10
How can I check that the script is running on 10.10 or not?
I'm trying to make is so that the script wont try to exec a command on any version of ubuntu less then 10.10

Thanks.

---

### Post by Drakx on 2010-10-29
OK so after a little thought and plenty of swearing I've kinda figured it out

```

This is just an example

import platform
osInfo = ('Ubuntu', 10.10', 'maverick')
sysInfo = platform.linux_distribution()

if osInfo == sysInfo:
    print("Working")
else:
    print("Not working")

```

By running this it seems the if is true and fires so just to make sure its working as i wanted i ran it again but this time with:

```

import platform
osInfo = ('Ubuntu', 9.04', 'janty')
sysInfo = platform.linux_distribution()

if osInfo == sysInfo:
    print("Working")
else:
    print("Not working")

```

---

