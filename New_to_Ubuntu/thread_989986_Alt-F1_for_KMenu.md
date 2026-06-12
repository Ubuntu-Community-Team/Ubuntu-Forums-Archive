---
title: "Alt-F1 for KMenu"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by jimreynold2nd on 2008-11-22
Although this is marked Kubuntu, it should applies to all KDE 4.1 installation
I noticed that some people doesn't have Alt-F1 mapped to the Kmenu.
Here's what I did: (note: all "{" and "}" are actually square brackets. I can't seem to escape BBcode....)
1. find ~ -type f -iname plasma-appletsrc
2. Backup the plasma-appletsrc file, then open it with your favorite editor.
3. Look for "plugin=launcher". Note the number after {Containments} and {Applets}
4. Add one section that looks like this: ("#"'s are numbers from step 3)
```
{Containments}{#}{Applets}{#}{Shortcuts}
Global=Alt+F1
```
4. Relog

For example, my plasma-appletsrc's launcher section looks like this
```
[Containments][2][Applets][41]
geometry=0,4,32,32
immutability=1
*plugin=launcher*
zvalue=293

[B][Containments][2][Applets][41][Shortcuts]
global=Alt+F1[/B]

```

---

