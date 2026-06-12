---
title: "xterm problem"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by tmann1946 on 2014-01-04
I know BSD 4.xx fairly well but this is all new for me. I'm trying to run a progrsm but keep getting "unknown terminal type xterm" . any ideas why this happening & how I solve it?

---

### Post by r3dd on 2014-01-04
```

sudo apt-get install ncurses-term
sudo ln -s /lib/terminfo/x/xterm /usr/share/terminfo/x/xter

```

---

