---
title: "404 Error When Trying to Update"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by Nick56x on 2014-06-04
I am not exactly new to Ubuntu, but I am at the same time. I have never really had an issue with this before, but whenever I try to update my Ubuntu setup with sudo apt-get update, I get the:
```
W: failed to fetch

[LIST=1]
[*][COLOR=#000000]W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found[/COLOR]
[*]
[*][COLOR=#000000]W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found[/COLOR]
[*]
[*][COLOR=#000000]E: Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]
[/LIST]

```

I've looked and looked, and I can't figure out how to remove those. Can I get any suggestions? I would prefer to remove it from the command line if possible.

---

### Post by QIII on 2014-06-04
Raring Ringtail reached End Of Life on January 27, 2014 and its repos have been moved.  I suggest a fresh installation of a currently supported version 12.04.4 or 14.04.

---

### Post by deadflowr on 2014-06-04
Raring is End of Life.
Update to a supported release
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Hope that helps.

**Edit**: To add, what is the whole output for apt-get update.
Is it all for raring, or is the raring reference only for the extras repos?

---

### Post by Nick56x on 2014-06-04
Hm.. I guess I will have to do a complete reinstall. I didn't want to, but it seems like the only way to fix everything.

Thanks for pointing that out. :)

---

