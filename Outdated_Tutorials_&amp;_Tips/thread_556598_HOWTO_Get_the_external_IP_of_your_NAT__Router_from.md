---
title: "HOWTO: Get the external IP of your NAT / Router from Shell"
date: 2007-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by djupp on 2007-09-21
Hi everyone!

I hope this is on the correct board :)

I searched the whole web for a simple solution to a not so simple problem: mostly I'm connected via NAT / Router to the WWW, so if I want to tell someone my ip, I always had to visit sites like "whatsmyip.org" and stuff..
As I grew weary of it, I wrote a simple line with curl and awk which will give you only your IP-Address:

```
curl www.wieistmeineip.de | awk '(/[0-9]?[0-9]?[0-9]\.[0-9]?[0-9]?[0-9]\.[0-9]?[0-9]?[0-9]\.[0-9]?[0-9]?[0-9]/) {print}' | awk 'gsub(/[>||<]/," ")' | awk '{print $3}'
```

This is not yet very dynamic, but I'm on it.. If I make any advantages I'll post them here, and if you have any suggestions you're welcome :)

---

### Post by tlinsenm on 2008-05-02
thanks! just upgraded to hardy, and the firefox 3 beta disabled the extension that normally told me my IP, so this saved my life :)

---

### Post by SjRaptor on 2008-05-02
Or you can just do

```
$ GET http://www.whatismyip.org/
```

---

### Post by kyle205 on 2008-11-22
If you add an -s to curl, it keeps the download info from being shown.

---

### Post by kevdog on 2008-11-22
This is a duplicate thread -- a solution for this has already been posted with many other solutions offered.

---

