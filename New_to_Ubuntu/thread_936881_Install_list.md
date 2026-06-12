---
title: "Install list"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-03
How can I see (in console mode) what is installed on my system?

---

### Post by Orange_and_Green on 2008-10-03
Hello Konstabel,

```
dpkg --get-selections | grep -v deinstall > installedpackages
gedit installedpackages
```

you can use "less" instead of "gedit" if you want to keep this 100% command-line.

If you are interested, I am currently developing a tool that automatically generates backups of installed packages, you can find more about it here:

[http://ubuntuforums.org/showthread.php?t=915712](http://ubuntuforums.org/showthread.php?t=915712)

Hope this helps, good luck:KS

---

### Post by hyper_ch on 2008-10-03
someone in IRC posted this a while back:

```

dpkg -l | awk '/ii/ { print $2 }' > packages.txt

```

That will create a file "packages.txt" that contains a list of all installed packages.

You can also put them all onto one line:

```

dpkg -l | awk '/ii/ { print $2 }' | tr '\n' ' ' > packages.txt

```

---

