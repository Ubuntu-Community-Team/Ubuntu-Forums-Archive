---
title: "[SOLVED] strange message when terminal is opened"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-09-01
Hi,

For some reason when I opened up my terminal today it came up with the following message:

> 
bash: shells.: command not found

I have no idea what this means or how to get rid of it!

Help please.

---

### Post by schauerlich on 2008-09-01
Can you post your ~/.bashrc?

---

### Post by unutbu on 2008-09-01
The first line of the default bashrc is
```

# ~/.bashrc: executed by bash(1) for non-login shells.
```

Check that a return has not inadvertently made it
```

# ~/.bashrc: executed by bash(1) for non-login 
shells.
```
This would make bash look for a command called "shells.", which it will not find.

---

### Post by Lorelei- on 2008-09-01
opened up .bashrc and it was the fact that an extra return had mananged to appear that had done it.

thanks for the help :)

---

