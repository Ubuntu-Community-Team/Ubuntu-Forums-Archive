---
title: "find command"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Cthulu2156 on 2013-02-14
Hello,

  Just a quick question as I have not been able to find the answer anywhere else.   I would like to use the find command to find files starting from root directory.  This has to be executed as root, my question is, what would I do to execute this as root?  Sudo does not do that right?  What command can I use to execute it as root?  If it is sudo, why is it not finding the file?  I know it is in the downloads directory in my home directory, which should be found with sudo find / 'filename' right?

---

### Post by CharlesA on 2013-02-14
```
sudo find / -name "filename" -print
```

Should work...

---

### Post by Frogs Hair on 2013-02-14
See the manual page for more details . ```
man find
```

---

### Post by Cthulu2156 on 2013-02-14
Great thanks guys, just wasn't sure it was the sudo command that was keeping it from working...thanks!  I read the man pages, good idea!

---

### Post by andrew.46 on 2013-02-16
> **Cthulu2156 said:**
> Great thanks guys, just wasn't sure it was the sudo command that was keeping it from working...thanks!  I read the man pages, good idea!

A bit more friendly than the man pages:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

:)

---

