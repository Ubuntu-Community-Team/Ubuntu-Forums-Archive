---
title: "New to Linux, does Ubuntu need a completely clean partition for install inside window"
date: 2015-10-05
forum: New to Ubuntu
---

### Post by david_richards2 on 2015-10-05
Sorry guys, I am new to all of this and just looking to see how I can best dual boot my old xp machine without losing data etc...

I have one disk on my pc, partitioned into two: C drive has windows and some files, d drive is purely for documents.

If I was to install Ubuntu using Wubi, I guess I need to select a 'clean' partition to install to?

Sorry if this is a simple question, but just want to be sure before I do anything silly!!

Thanks in advance

David

---

### Post by howefield on 2015-10-05
Wubi installs to a file on your existing Windows partition so no need for a separate dedicated partition for Ubuntu.

Wubi is intended for a fairly short term look at Ubuntu and has a few significant [disadvantages]("http://ubuntuforums.org/showthread.php?t=481219"), mainly in performance and reliability. It is currently unsupported for newer versions of Windows.

Your mileage may vary.

---

### Post by flocculant on 2015-10-05
> **howefield said:**
> ... It is currently unsupported for newer versions of Windows.
...

There are (once again) moves to remove it completely - I don't think that's far off happening.

[http://irclogs.ubuntu.com/2015/09/24/%23ubuntu-release.html#t19:06](http://irclogs.ubuntu.com/2015/09/24/%23ubuntu-release.html#t19:06)

comment from Adam Conrad @ [http://irclogs.ubuntu.com/2015/09/24/%23ubuntu-release.html#t19:45](http://irclogs.ubuntu.com/2015/09/24/%23ubuntu-release.html#t19:45)

> Right, let's pick this conversation up after beta, then, but I think removing it is probably the right thing.

---

### Post by SeijiSensei on 2015-10-05
Rather than using WUBI, might I suggest installing [VirtualBox]("http://www.virtualbox.org/") on Windows, then creating a "virtual machine" and installing Ubuntu into that?

---

### Post by ajgreeny on 2015-10-05
As it is an XP machine you may find that it is not powerful enough to run Ubuntu OS with unity desktop; that requires a good 3D graphics card which yours may not have.  One of the alternatives such as Xubuntu or Lubuntu may be better if your specification is too limited for Ubuntu.  Virtualbox may also need more resources than you have but you can also try that if you wish.
See [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389) for more info.

Try it as a live system first and if that works well you can install it properly, but as others have said, I suggest you forget about wubi, it is no longer supported, and it was never intended as a long term dual boot system but merely as a way to test if Ubuntu worked on your hardware.

---

