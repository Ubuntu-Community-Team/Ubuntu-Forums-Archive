---
title: "Rhythmbox hangs immediately after starting"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by /bee/ on 2012-10-27
12.10 Gnome Remix

Rhythmbox 2.97 and 2.98

Problem:
App freezes unless run as root.  Running with terminal gives no output as can be seen in the screenshot.

[IMG]http://i.imgur.com/ZbZmp.png[/IMG]

What I've tried:
Deleting the usr/lib/rhythmbox folder
Uninstalling/purging and then reinstalling

I can get it to work if I run 'gksu rhythmbox' from a terminal, but the library is empty and I cannot add any new tracks.

Relevant note:  I have a large music library (~500 GB) and it worked fine in 12.04.  I did a fresh install of 12.10, does it need an extended amount of time to analyze my music? I let it sit for 3 hours and there was no change.  I wish terminal would output something of use.

:confused:


Final edit:  Got tired of waiting.  I'd only been using the system for a couple hours, so I didn't feel really bad wiping it and doing a fresh install.  A little irritable, but at least Rhythmbox is working again.

PROBLEM UNRESOLVED.  CANNOT RECREATE.

---

### Post by kcode on 2012-12-13
Disabling plugins helped me solve the issue.

Try this command :

```
rhythmbox --disable-plugins
```

---

