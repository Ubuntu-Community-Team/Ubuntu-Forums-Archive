---
title: "RapidSVN bookmarks not saving"
date: 2011-10-28
forum: Programming Talk
---

### Post by FrancisT on 2011-10-28
There's an old thread about this with no answer and I have now found the answer. I'm posting it here so that google etc. can index this so that others can find it.

The issue is that sometimes (e.g. just now after I installed xubuntu 11.10 and migrated stuff across) RapidSVN throws a wobbly loses its configuration. Then when you try and get it back it sort of works but bookmarks (and sometimes other settings) don't seem to be saved.

So here's the skinny on the fixes

1) the files you need in ubuntu are ~/.RapidSVN and the ~/.subversion/ tree, if you are restoring from a backup it's easy to forget the latter

2) the bookmarks are stored in ~/.RapidSVN in a section called [bookmarks] (doh) so if you need to you can hand edit the file once you've quit RapidSVN to add them. The format looks like this
```

[Bookmarks]
Count=2
Bookmark0=/srv/code/repo1
Bookmark0Flat=0
Bookmark0IndicateModifiedChildren=0
Bookmark1=/srv/code/repo2
Bookmark1Flat=0
Bookmark1IndicateModifiedChildren=0

```
you may also find it useful to add/remove history entries (which are in the [History] section)
```

[History]
[History/Repositories]
Count=2
Value0=http://gforge.domain.local/svn/repo1
Value1=http://gforge.domain.local/svn/repo2
[History/WorkingDirectories]
Count=2
Value0=/srv/code/repo1
Value1=/srv/code/repo2

```

It is possible that the corruption occurs when you logout/reboot/switch off a machine with RapidSVN still running so explicitly quitting RapidSVN before logging out sounds like a good thing to try and remember to do.

Share & Enjoy

Francis

---

