---
title: "First Ubuntu related bash script"
date: 2007-04-10
forum: Programming Talk
---

### Post by dv5237 on 2007-04-10
Hello,

Is there a more nicer or better way to do this? Just curious.

```
#!/bin/bash
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get autoremove -y && sudo apt-get clean
```

Thanks

---

### Post by slavik on 2007-04-10
you can skip upgrade and simply do dist-upgrade ...

dist-upgrade will upgrade the package even if the upgrade breaks dependancies, upgrade will only upgrade a package when the upgrade does not break dependencies.

I am not aware of any built-in options to apt-get that provides similar functionality. You also sometimes don't want to upgrade blindly. :)

---

### Post by dv5237 on 2007-04-11
Ok thanks ill do that

---

