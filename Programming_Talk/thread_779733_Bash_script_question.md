---
title: "Bash script question"
date: 2008-05-02
forum: Programming Talk
---

### Post by ABX323 on 2008-05-02
I want to know how to erase previous lines of output when running a  bash script in terminal.
Kind of like clear, but not the whole screen. I want to have a dynamic menu in a static screen object.
so..

#############################
-Options-
This part would change but the rest stays the same
#############################

This is just for a homebrew, so a hack is good.

Thanks to any reply.

---

### Post by olejorgen on 2008-05-02
My best guess would be to look into the files in ncurses-bin
```

dpkg -L ncurses-bin

```

---

