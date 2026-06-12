---
title: "run a list of commands from a file"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by svivian on 2008-10-03
I've been using linux for years but somehow this never came up before... how would I run a list of ordinary command-line commands from a file?

I've looked at shell scripts, but I first get a "permission denied" error when I ran it. So I ran as root, but now get "command not found" errors on the .sh file.

Surely there must be a direct equivalent of Windows .bat files? And one where I don't need to run as root?

---

### Post by Dr Small on 2008-10-03
Start your shell script with either:
```
#!/bin/bash
```
Or:
```
#!/bin/sh
```

And when you are finished, simply run:
```
chmod +x scriptname
```

Then to run it:
```
./scriptname
```

Or:
```
/path/to/scriptname
```

---

### Post by svivian on 2008-10-03
Excellent, it worked! Can't believe it was so simple.

---

