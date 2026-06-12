---
title: "Permission necessary to view the contents"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by Philosoweed on 2013-04-24
I am trying to view the content in various folders but keep getting "You do not have the permissions necessary to view the contents this folder.".

Any ideas....using Ubuntu 12.10.

Thanks in advance.

---

### Post by Bashing-om on 2013-04-24
Philosoweed; Hi ! Welcome to the forum.

Doing anything to the system requires administrative authority. Sometimes even looking at system files requires this authority.

Preseed your command with the term "sudo". /"sudo"== Super User DO/

See these docs for full disclosure:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm)[INDENT=3]
hope this helps

[/INDENT]

---

### Post by nerdtron on 2013-04-24
What folders are you trying to view? Some system folders are restricted and requires root access to view them.

---

### Post by fantab on 2013-04-24
To view your Folder with 'elevated privileges' open Nautilus from Terminal using:

```
gksudo nautilus
```

Be very careful. As long as you are ONLY viewing it should be okay. But if you make any changes it can be potentially hazardous to your system.

---

