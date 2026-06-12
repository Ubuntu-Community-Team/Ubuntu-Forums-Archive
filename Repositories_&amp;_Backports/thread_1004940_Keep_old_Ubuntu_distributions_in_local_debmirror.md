---
title: "Keep old Ubuntu distributions in local debmirror"
date: 2008-12-07
forum: Repositories &amp; Backports
---

### Post by nmb3000 on 2008-12-07
Hello,

I have a local Ubuntu mirror that I keep up-to-date with debmirror and a cron job.  My problem is that I would like to keep old versions of Ubuntu that are no longer supported in the same mirror as the new and current versions are.  This is primarily due to people using the mirror who cannot or will not upgrade to a newer version of Ubuntu.

For example, Feisty has just recently been removed from the official mirror at [http://archive.ubuntu.com](http://archive.ubuntu.com). If I don't modify my debmirror command, I get 404 errors and failed updates.  If I remove 'feisty' from the list of distributions then all the feisty files in the mirror are deleted.

I know I can add the --nocleanup option to debmirror, but this means that the mirror will never get pruned of files that aren't needed any longer. Does anyone know of a better way to keep old distributions which are no longer present in the upstream mirror in the same local mirror as the current and active ones?

If it matters, here's the debmirror command I'm currently using:

```
/usr/bin/debmirror --verbose --host=us.archive.ubuntu.com --method=http --root=ubuntu/ --dist=dapper,dapper-updates,dapper-security,feisty,feisty-updates,feisty-security,gutsy,gutsy-updates,gutsy-security,hardy,hardy-updates,hardy-security,intrepid,intrepid-updates,intrepid-security --section=main,universe,multiverse,restricted --arch=i386,amd64 --ignore-release-gpg --nosource /mirrors/ubuntu/
```

Thanks!

---

