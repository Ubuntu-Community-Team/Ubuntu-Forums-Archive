---
title: "Accessing Program Files x86 with Terminal"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by frank85 on 2014-12-18
I tried these

[http://ubuntuforums.org/showthread.php?t=1609536](http://ubuntuforums.org/showthread.php?t=1609536)

And no luck. Program\ Files\ (x86\) doesn't work

"Program\ Files\ (x86)" doesn't work

Using Tab to find the directory and typing it as it appears doesn't work.

I'm trying remove XnView which was installed through wine, and I can't figure out how. I may just delete the folders if I can't find any solution.

---

### Post by steeldriver on 2014-12-18
If you want to use backslash escapes, you would need to escape both the space AND the parenthesis:

```

$ ls ~/.wine/drive_c/Program\ Files[COLOR=#0000ff]**\ \(**[/COLOR]x86\)/
Common Files  Internet Explorer

```

OTOH if you want to use quotes, you don't need the backslashes as well:

```

$ ls ~/.wine/drive_c/"Program Files (x86)"
Common Files  Internet Explorer

```

---

