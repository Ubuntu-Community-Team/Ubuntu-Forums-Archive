---
title: "[SOLVED] Launchpad &amp;quot;invalid .bzr directory&amp;quot;"
date: 2008-06-14
forum: Programming Talk
---

### Post by Andruk Tatum on 2008-06-14
For a school project, I started work on a small utility.  I have been trying to learn bazaar by following the [mini-tutorial]("http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html").

When I try to push my project to Launchpad using "bzr push bzr+ssh://..." I get the following error:

bzr: ERROR: Target directory bzr+ssh://... already exists, but does not have a valid .bzr directory. Supply --use-existing-dir to push there anyway."

Does anybody know what is wrong and how I can fix it?

Thanks in advance.
- Andruk

---

### Post by bobbocanfly on 2008-06-14
Notu sure why launchpad does this but when you try and push to a branch for the first time you have to add the --use-existing-dir flag to the end of your push command:

```
bzr push bzr+ssh://xxx.xxx.xxx --use-existing-dir
```

---

