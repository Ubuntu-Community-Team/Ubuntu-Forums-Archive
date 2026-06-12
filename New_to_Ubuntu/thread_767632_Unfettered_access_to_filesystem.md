---
title: "Unfettered access to filesystem?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Xylar Wasterend on 2008-04-25
(/is new to Ubuntu...)

I spend a lot of time in the filesystem explorers (on Windows 2000 it was Windows Explorer) and here it's Nautilus. I browse around with it running as user and root where applicable, but even in root get hit with barriers, like this one: "Error making symbolic link" when trying to copy "flashplugin-alternative.so" to the '/plugins' folder of an [uninstalled / on USB Flash Drive] SeaMonkey 2.0a1pre nightly Linux build. Since it's not installed I just copy over files where needed... Any way around this barrier? :(

---

### Post by nhandler on 2008-04-26
A symbolic link in Ubuntu is similar to a shortcut in Windows. So when you were trying to copy the file to the flash drive, you want to copy the actual file, you don't want to make a short cut. I'm not sure how you went about copying the file, but try right clicking it and selecting "Copy". Then paste it onto your flash drive. Another option is to use the terminal and do:

```
cp /path/to/flashplugin-alternative.so /path/to/folder/on/flash/drive
```

Add sudo to the beginning of the command if it gives a permissions error. Both of those methods should allow you to copy the file.

---

### Post by Xylar Wasterend on 2008-04-26
I see what you mean now. The real file / plugin that it pointed to is "libflashplayer.so", which did copy over. Thank you. :)

---

