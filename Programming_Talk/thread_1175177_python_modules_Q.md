---
title: "python modules Q"
date: 2009-05-31
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-05-31
I know that modules need to end in a .py extension. 
i want to know where they need to be located so that the running program can find them. so far ive only put them in the same directory as my running program.

---

### Post by unutbu on 2009-05-31
Here are two options:
[list]
[*] Edit ~/.profile. Add lines like these:
```

PYTHONPATH=$HOME/pybin
export PYTHONPATH
```

This would allow you to put modules in ~/pybin. 

[*] Edit the script that imports the module. Put something like this at the top:

```
import sys
sys.path.append('/home/user/pybin')
```

This would also allow you to put modules in ~/pybin.
This method is not recommend; the first method is generally preferrable.
[/list]

One difference between these two methods is that the directories listed in the PYTHONPATH are prepended to the front of the sys.path, so modules in the PYTHONPATH trump modules of the same name in the standard installation path.

If you uses "sys.path.append" then your path is appended to the end of the sys.path, and are used only if there is no module of the same name in the standard installation path.

Of course, usually it is not a good idea to name your modules the same as standard modules.

PS. You can check the order of the paths that Python will search for modules with this little script:
```
#!/usr/bin/env python
import sys
print(sys.path)
```
The directory that contains the calling script is always first. Then the directories in the PYTHONPATH, and then directories in the standard installation path.

---

