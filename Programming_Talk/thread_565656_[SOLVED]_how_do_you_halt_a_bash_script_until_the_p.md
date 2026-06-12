---
title: "[SOLVED] how do you halt a bash script until the previous command is done"
date: 2007-10-02
forum: Programming Talk
---

### Post by HokeyFry on 2007-10-02
i am trying to make a script to download a multipart RAR archive while i am gone at work. there are 50 or so parts to it, and this is what essentially my script consists of:

```
wget rarfile.partX.rar
```

50 or so times. How do I tell the script to wait until the previous wget command is finished running?

---

### Post by aks44 on 2007-10-02
> **HokeyFry said:**
> How do I tell the script to wait until the previous wget command is finished running?

You don't. This is the default behaviour. Did you even try it before posting?

---

### Post by HokeyFry on 2007-10-02
yeah i did, it just flew through each file and didnt download any of them

---

### Post by aks44 on 2007-10-02
> **HokeyFry said:**
> yeah i did, it just flew through each file and didnt download any of them

Hmm better post your whole script then.

```
wget http://server.com/file
``` downloads a file, and doesn't return until it is downloaded, so I guess your problem is elsewhere...

---

### Post by HokeyFry on 2007-10-02
i found the problem, the site that was hosting the file wanted me to click a bunch of buttons first, so i think that was the issue. ill just have to do it manually


thanks though i know the default behavior now

---

### Post by aks44 on 2007-10-02
Unless the server uses session-based tickets, there has to be a direct download link...

When you find it you can automate the download. :)

---

