---
title: "Help applying a patch"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by Kexolino on 2011-12-19
Gnome Shell's animations are somewhat choppy with the propriety nvidia driver, but I found a patch that solved the issue for a few other people, here's the [link]("https://bugzilla.gnome.org/show_bug.cgi?id=613936"). [This page]("http://live.gnome.org/GnomeShell/SwatList") says that it can be applied with these commands:
```

$ cd ~/gnome-shell/source/gnome-shell
$ curl http://bugzilla-attachments.gnome.org/attachment.cgi?id=157326 > shell-animations-nvidia.patch
$ git am shell-animations-nvidia.patch
```but after entering the last command I get:

```
fatal: Not a git repository (or any of the parent directories): .git
```

---

### Post by hhh on 2011-12-19
Hey Kexolino,

I'm not getting the flashing error with my Nvidia GeForce 6150LE, but I looked around and found this thread, which may help, specifically these posts (from pgs. 52 & 53)...
[http://ubuntuforums.org/showpost.php?p=10398285&postcount=516](http://ubuntuforums.org/showpost.php?p=10398285&postcount=516)
[http://ubuntuforums.org/showpost.php?p=10409924&postcount=527](http://ubuntuforums.org/showpost.php?p=10409924&postcount=527)

If not, try posting in that thread. Best of luck, 

hhh

---

### Post by Kexolino on 2011-12-25
Sorry for the very, very late reply. No luck. It doesn't work on Fedora either. I get the same error message. I have a guess why it doesn't work, but since I don't understand exactly what this does, it doesn't matter. Hopefullty the issue will diesappear with Gnome 3 maturing more. :-k

---

