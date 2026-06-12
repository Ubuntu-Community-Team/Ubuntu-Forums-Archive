---
title: "[SOLVED] Is this safe"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by natman on 2008-06-21
I am looking for a gui video converter for tranfer to creative zen player. I found this page from the guy who makes the liquid weather thing for super karamba.
[HTML]http://liquidweather.net/howto/index.php?id=59[/HTML]
is it safe to do what he says?

---

### Post by ad_267 on 2008-06-21
Doesn't sound too dangerous. But if you are having a problem with a particular script I would just change "#!/bin/sh" to "#!/bin/bash"

If you do want to do this and find it causes problems (although I don't think it will) then you can undo it with:
```
sudo rm -f /bin/sh
sudo ln -s /bin/dash /bin/sh
```

---

### Post by natman on 2008-06-21
Cool, all i did was this
> cd thinliquidfilm
or whereever you have it extracted to, then
> kate ./install.py
find the line
> print ''
cmd = 'ls -l /bin/sh'
output = commands.getoutput(cmd) and change to
> print ''
cmd = 'ls -l /bin/bash'
output = commands.getoutput(cmd)
then just run
> sudo ./install.py

---

