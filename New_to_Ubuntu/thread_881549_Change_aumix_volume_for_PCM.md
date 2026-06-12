---
title: "Change aumix volume for PCM"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by ltk5 on 2008-08-06
I have a problem. I'm making myself a little alarm clock and I'm stuck at aumixer's volume controls. I made a small script .aumixrc, that rises the volume up. The problem is that aumixer changes my "front" volume, instead of my "surround" or "PCM" and I don't know how to set it up. I'm doing all of this in command line :)

Any help would be appreciated!:)

---

### Post by mali2297 on 2008-08-06
I use **amixer** for tasks like this.

To set the volume on PCM to 80%:
```

amixer sset PCM,0 80%

```

You can see a list of available controls by typing
```

amixer scontrols

```
in a terminal.

---

