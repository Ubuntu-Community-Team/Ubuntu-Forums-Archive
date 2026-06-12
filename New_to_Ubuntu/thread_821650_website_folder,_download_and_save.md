---
title: "website folder, download and save"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by control_guy on 2008-06-07
Hello

I am interested in copying a certain folder from a website on regular basis. The name of folder changes (increments) daily. The website requires login. Is there a linux utility that can accomplish this task?

Thanks

---

### Post by rampageoberon on 2008-06-07
I guess wget could do this. And you could set up a cron job for this. Perhaps you could do something like this:

```
wget -r -l DEPTH --user=USER --password=PASSWORD <weblink>
```

Modify the code till it suits you. Check the man pages for more help.

---

### Post by nebu on 2008-06-07
use wget... that is if u know the exact name of the folder...

for more info try...

```
man wget
```

---

### Post by control_guy on 2008-06-08
Thank you everybody. I am now using wget to download the folder. It has even allowed me to handle cookie based sessions.

Thanks agian.

---

