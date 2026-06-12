---
title: "About Linux Terminal"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by Aiyer99 on 2012-11-21
In a linux terminal, why it shows different coloured files or directories ?

---

### Post by Lars Noodén on 2012-11-21
It is because [ls](http://manpages.ubuntu.com/manpages/precise/en/man1/ls.1.html) is aliased to 'ls --color=auto'  It's in the file .bashrc and you can comment it out by starting the line with a pound sign (#) if it gets in your way.  If you just want to temporarily avoid the colors, you can run ls with the full path

```

/bin/ls

```

'ls' has a lot of options, the manual page is worth looking at, even if you don't end up using them.

---

### Post by CWZ on 2012-11-21
You can also try typing
ls --help
Also --help will work on almost all commands just remember to use both -'s

---

### Post by lykwydchykyn on 2012-11-21
The colors indicate various aspects about file system contents, such as whether something is a file, folder, device, etc.; also indicates permissions or other attributes.

---

