---
title: "A humble request / noble challenge / chance to write a little code"
date: 2011-10-03
forum: Programming Talk
---

### Post by ResultantRag on 2011-10-03
I have an issue that's not urgent, but would be nice to have solved.
Therefore, only solve if it looks like it might be fun.

Here is how internet works at my apartment: If there is no activity for 30 minutes, your apartment becomes logged out. When you need the internet again, you have to enter a username and password. This is inconvenient, although not terribly.

I have a netbook running ubuntu that is always on. If I had a program/script that were to open firefox/chromium every, say, 20 minutes, wait for the homepage to load, and then close the browser, I don't think anyone on our router would need to login anymore.

My programming skills are very limited, but I post this request because it seems like someone with skill could probably solve this in under a minute.

---

### Post by Smart Viking on 2011-10-03
Maybe this'll do it

```
#!/bin/bash
while [ 1 ]
do
ping -c 4 www.google.com
sleep 1200
done




```

---

### Post by karlson on 2011-10-03
> **ResultantRag said:**
> I have an issue that's not urgent, but would be nice to have solved.
Therefore, only solve if it looks like it might be fun.

Here is how internet works at my apartment: If there is no activity for 30 minutes, your apartment becomes logged out. When you need the internet again, you have to enter a username and password. This is inconvenient, although not terribly.

I have a netbook running ubuntu that is always on. If I had a program/script that were to open firefox/chromium every, say, 20 minutes, wait for the homepage to load, and then close the browser, I don't think anyone on our router would need to login anymore.

My programming skills are very limited, but I post this request because it seems like someone with skill could probably solve this in under a minute.

I would suggest reading up on crontab.

You can schedule a program to run with frequency of up to once a minute.  And run the following
```

ping -c 20 www.google.com

```

---

### Post by ResultantRag on 2011-10-03
I'll try it out, thank you very much!

---

