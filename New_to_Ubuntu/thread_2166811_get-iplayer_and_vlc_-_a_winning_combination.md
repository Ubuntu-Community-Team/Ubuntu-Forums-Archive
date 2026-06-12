---
title: "get-iplayer and vlc - a winning combination"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by KorkytheKat on 2013-08-11
You can watch a get-iplayer stream and simultaneously record it to v. good quality mp4-format file (at a location of your choice) with this command:

   get-iplayer --stream --get *** (or --pid b*******) --player="vlc - --sout '#duplicate{dst=display,dst=record{dst-prefix=/path/filename(no .mp4)}}'"

- works very well in Precise and Raring.

Just thought I'd mention it.

---

