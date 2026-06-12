---
title: "graphics.py"
date: 2008-12-18
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-12-18
I want graphics.py to be placed there in my file-system so that i can import it from anywhere on my system, rather than a copy of it always being placed along with my program,

---

### Post by unutbu on 2008-12-18
```
mkdir ~/pybin
mv graphics.py ~/pybin
```
Edit ~/.profile:
```

PYTHONPATH=$HOME/pybin
export PYTHONPATH
```
Log out, log back in to make ~/.profile changes active.

See [http://docs.python.org/tutorial/modules.html#the-module-search-path](http://docs.python.org/tutorial/modules.html#the-module-search-path)

---

### Post by 7raTEYdCql on 2008-12-18
Just to ask.
What does export PYTHONPATH actually do. Everything else makes complete sense to me.

---

### Post by unutbu on 2008-12-18
export is a bash command which makes the environment variable (PYTHONPATH) known to subsequently executed commands (outside of the ~/.profile file).

Type ```

help export
```
to learn more about export (help works for any bash command).

---

### Post by digitalvectorz on 2008-12-18
you can also programmatically set it up:

```

import sys
sys.path.append('/some/path/to/graphics.py')

```

*note that you're appending an absolute path (/home/user/graphics.py), not a relative path (~/graphics.py)

---

