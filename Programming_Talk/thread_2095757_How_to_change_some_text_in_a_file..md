---
title: "How to change some text in a file."
date: 2012-12-17
forum: Programming Talk
---

### Post by ron999 on 2012-12-17
Hi
**SMPlayer** has a config file "smplayer.ini".
Located here:-
/home/user/.config/smplayer/smplayer.ini

A copy is attached below.

It stores the MPlayer version in the line:-
"mplayer_detected_version=35691"

This seems to be the MPlayer version that is detected when SMPlayer is first installed and the smplayer.ini file is created.

When I update MPlayer, I edit this file manually to insert the new version.
(So that the correct version appears in SMPlayer > Help > About SMPlayer screen).

Is there a command I could use that will find the line that starts "mplayer_detected_version=" and change it to "mplayer_detected_version=$version"?



PS
version can be obtained from MPlayer SVN with a command like this:-
```
version=$(LC_ALL=C svn info 2> /dev/null | grep Revision | cut -d' ' -f2)
```

And maybe it can be obtained modifying a command like this:-
```
mplayer -h | grep -i "MPlayer SVN-r"
```

---

### Post by Vaphell on 2012-12-17
```
sed -i "/mplayer_detected_version/ s/=.*$/=$version/" ~/.config/smplayer/smplayer.ini
```

---

### Post by ron999 on 2012-12-17
> **Vaphell said:**
> ```
sed -i "/mplayer_detected_version/ s/=.*$/=$version/" ~/.config/smplayer/smplayer.ini
```

That's done the job, thanks Vaphell. :cool:
:guitar:

---

