---
title: "Error compiling Wine 0.9 beta"
date: 2005-10-25
forum: Packaging and Compiling Programs
---

### Post by Sector on 2005-10-25
Hi, I was trying to compile the latest and greates Wine release which promises lots of good stuff, because the repositories are kind off outdated.

I resolved all the problems configure had with my install but it was during compilation that it errored:

```

...
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
...

```

I've searched the forums but I could only find one reference to someone adding -lXext via makedefs or something but didn't explain it. If I knew what those were I might be able to fix it, but now I'm stranded. (if you need anymore info just tell me).

Thank in advance!

---

### Post by beefsprocket on 2005-10-29
not sure, but try updating automake to a new version.

---

### Post by claydoh on 2005-10-29
[Look here]("http://www.winehq.org/site/download-deb") if you would like to use apt to get wine directly from winehq. It seems to work well for me so far.

---

