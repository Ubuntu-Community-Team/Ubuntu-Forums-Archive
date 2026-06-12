---
title: "Enable Rename"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by System Monitor on 2008-04-30
First off, I am the admin.

So I am trying to rename the firefox profile folder in "/etc/firefox-3.0/" but the rename button is button is grayed out, how could I rename the folder and also how can I make it so I can always rename, delete and ect.

Thanks :)

---

### Post by PeterJS on 2008-04-30
> **System Monitor said:**
> First off, I am the admin.

So I am trying to rename the firefox profile folder in "/etc/firefox-3.0/" but the rename button is button is grayed out, how could I rename the folder

You'll want to relaunch the file browser from the run dialog (alt+f2) with root priviliages using:
```

gksudo nautilus

```
You may be in the admin group, but you only have admin privileges when you explicitly request them with sudo.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> and also how can I make it so I can always rename, delete and ect.

Thanks :)
You don't, to do so would completely undermine the security system in place in Ubuntu. This is not supported, or encouraged, but possible, but the general understanding is that if you understand how to do so, you'll understand the serious implications of doing so.

---

