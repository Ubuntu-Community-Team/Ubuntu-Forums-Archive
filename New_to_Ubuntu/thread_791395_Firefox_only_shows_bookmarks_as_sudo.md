---
title: "Firefox only shows bookmarks as sudo"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by lolwhites on 2008-05-12
I started Firefox-3 in sudo and checked for upgrades. Nothing new, but when I restarted, all the bookmarks were gone and FF won't restore them. I only get my full profile in FF-3 when I start is as sudo, which I obviously don't want to do while browsing the net. How can I restore it?

---

### Post by subzero316 on 2008-05-12
> **lolwhites said:**
> I started Firefox-3 in sudo and checked for upgrades. Nothing new, but when I restarted, all the bookmarks were gone and FF won't restore them. I only get my full profile in FF-3 when I start is as sudo, which I obviously don't want to do while browsing the net. How can I restore it?




Try this,
Get in with sudo
Import the bookmarks 
exit
get in WITHOUT sudo
export that bookmars file:)

---

### Post by Trail on 2008-05-12
Maybe a permission issue, that the firefox settings are owned by root and non-root users cannot write to them. If that's the case, try:

```

sudo chmod -R 777 ~/.mozilla

```

---

### Post by lolwhites on 2008-05-12
Thanks Trail!

---

