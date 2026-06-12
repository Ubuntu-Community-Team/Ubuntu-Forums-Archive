---
title: "Will installing &amp; removing applications make Ubuntu unstable?"
date: 2018-08-30
forum: New to Ubuntu
---

### Post by mark19602 on 2018-08-30
I am new to Linux and Ubuntu. I am impressed with the amount and ease of installing and removing programs for trial use. On windows this eventually result in your system becoming unstable, a situation call "Windows Rot" requiring a re installation of the operating system to clean things up.

Does this occur with Linux as well or is the program removal extremely clean.

Thank 
Mark

---

### Post by DuckHook on 2018-08-30
No OS is immune to rot and cruft, although Linux-based systems are more resistant due to better design (for example: the old practice of building config files in plain text, although even Linux has recently moved to the obscurity of a "registry"). Depending on the app, service or utility, various configuration files or system settings get changed or left behind and the system is modified, sometimes in subtle ways that don't manifest until much later, often only after another conflicting app is installed. Some of the problems on these forums are the result of such cruft. They are very hard to diagnose.

If you are an app junkie, a good practice is to keep your base OS as close to default as possible and do your experimentation in a series of VMs. That way, by rolling back to a more pristine snapshot, you can easily undo any damage. VMs have the additional advantage of being easily cloneable, so one original can be cloned to as many separate ones as you like. VMs are not as popular in the Windows-sphere because each requires a separate licence, whereas with Linux, it's all free (and already part of the kernel if you use KVM or XEN).

---

### Post by oldos2er on 2018-08-30
> **mark19602 said:**
>   "Windows Rot" requiring a re installation of the operating system to clean things up.

Does this occur with Linux as well or is the program removal extremely clean.

As long as you stick with the package manager, you should be fine. Just be aware that any package manager will NOT remove any files from your /home/user folder, where most programs store their settings and configuration files.

---

### Post by HermanAB on 2018-08-30
You cannot unscramble an egg, so YMMV and your machine may very well end up broken when some part of Gnome is removed.

I learned years ago, never to uninstall anything.

---

